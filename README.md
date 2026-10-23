# Student Performance Dashboard – Power BI

## 📌 Project Overview
This project analyzes student academic performance, attendance, and behavior using Microsoft Power BI. The dashboard helps identify student performance levels and understand attendance patterns.

## 🎯 Objectives
- Calculate the total number of students.
- Analyze average student scores.
- Calculate overall attendance percentage.
- Analyze behavior records by behavior type.
- Categorize student performance into High, Medium, and Low.
- Present key findings through interactive dashboard visuals.

## 📂 Dataset
The project uses the Excel dataset `Practicle Exam Power Bi.xlsx`.

The dataset contains four main tables:

1. **Students** — StudentID, Name, Gender, Class, Section
2. **Scores** — StudentID, Subject, Score, MaxScore, Term
3. **Attendance** — StudentID, Date, Status, Reason
4. **Behavior** — StudentID, BehaviorType, Date, Notes

## 🛠️ Tools and Technologies
- Microsoft Power BI Desktop
- Microsoft Excel
- Power Query
- DAX (Data Analysis Expressions)
- Data visualization and reporting

## 📊 Key Measures and Calculated Columns

### 1. Total Students
```dax
Total Students =
DISTINCTCOUNT('Students.csv'[StudentID])
```

### 2. Score Percentage
```dax
% Score =
DIVIDE(
    'Scores.csv'[Score],
    'Scores.csv'[MaxScore],
    0
)
```
Format this column as Percentage.

### 3. Average Score Percentage
```dax
Average Score % =
DIVIDE(
    SUM('Scores.csv'[Score]),
    SUM('Scores.csv'[MaxScore]),
    0
)
```
Format this measure as Percentage.

### 4. Attendance Percentage
```dax
Attendance % =
DIVIDE(
    CALCULATE(
        COUNTROWS('Attendance.csv'),
        'Attendance.csv'[Status] = "Present"
    ),
    COUNTROWS('Attendance.csv'),
    0
)
```
Format this measure as Percentage.

### 5. Behavior Count
```dax
Behavior Count =
COUNTROWS('Behavior.csv')
```

### 6. Performance Category
```dax
Performance Category =
VAR ScorePercent =
    DIVIDE(
        'Scores.csv'[Score],
        'Scores.csv'[MaxScore],
        0
    )
RETURN
    SWITCH(
        TRUE(),
        ScorePercent >= 0.75, "High",
        ScorePercent >= 0.50, "Medium",
        "Low"
    )
```

Performance categories use these thresholds:
- **High:** 75% or above
- **Medium:** 50% to below 75%
- **Low:** Below 50%

## 📈 Dashboard Visualizations

The dashboard can include the following visuals:

- **KPI Card:** Total Students
- **KPI Card:** Average Score %
- **KPI Card:** Attendance %
- **KPI Card:** Total Behavior Records
- **Column Chart:** Average Score by Subject
- **Donut Chart:** Attendance by Status
- **Bar Chart:** Performance Category
- **Column Chart:** Behavior Count by Type

## 🔍 Analysis and Insights
The dashboard helps users:
- Understand overall student performance.
- Compare scores across different subjects.
- Monitor attendance rates.
- Identify the distribution of performance categories.
- Review behavior records by type.

Actual findings should be documented after validating the results in Power BI.

## 🚀 Project Workflow
1. Import the Excel dataset into Power BI Desktop.
2. Inspect and clean the data using Power Query.
3. Create relationships between tables using StudentID.
4. Create calculated columns and DAX measures.
5. Build KPI cards and charts.
6. Format the report with a consistent theme.
7. Validate the measures and finalize the dashboard.

## ✅ Conclusion
The Student Performance Dashboard provides a consolidated view of academic results, attendance, and student behavior. It demonstrates practical skills in data modeling, DAX calculations, KPI creation, and interactive reporting using Power BI.

## 👨‍💻 Author
**Name:** Your Name  
**Project:** Student Performance Dashboard  
**Tool:** Microsoft Power BI Desktop
