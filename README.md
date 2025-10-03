# Identification and Prediction of Absenteeism in Employees

## 1. Problem Definition
- What are the factors that can affect the absenteeism of an employee?  
- How can the absenteeism of an employee be predicted?  

---

## 2. Data Collection
**Dataset:** [Fictitious Employee Absence Dataset](https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset)  

- Uploaded on Kaggle for HR data exploration with analytical/statistical tools.  
- Disclaimer: This is synthetic/fake data.  
- **Structure:** 13 columns (9 string, 3 decimal, 1 integer) and 8336 rows.  
- **Columns:**  
  - Employee number, Surname, GivenName, Gender, City, JobTitle, DepartmentName, StoreLocation, Division, Age, LengthService, AbsentHours, BusinessUnit.  

---

## 3. Data Cleaning
- Filtered dataset to employee numbers **1–2024** (smaller sample).  
- Used Excel formatting for better visualization.  
- Applied **TRIM** to remove extra spaces in text fields.  
- Used **Special Go-To** to search blank spaces.  
- Checked for duplicates using Employee Number.  
- Verified no **N/A** values.  
- Rounded numeric columns to **two decimal places**.  
- Converted columns to correct data types (numeric → number, text → string).  
- In cases of lagging performance, filtered down another 100 rows.  

---

## 4. Data Exploration
- **Mode of AbsentHours = 0**, suggesting majority of employees had no absences.  
- Means and medians of numeric columns are close → no major outliers.  

**Key Findings:**  
- Age and Length of Service showed low correlations with absenteeism across departments.  
- **Most relevant factor:** Employee **Age**.  

**Correlation Summary:**  
| Column        | Department       | Degree  | Type        |
|---------------|------------------|---------|-------------|
| Age           | Bakery           | Low     | Positive    |
| LengthService | Accounts Payable | Low     | Negative    |
| Age           | Accounting       | Low     | Positive    |
| Age           | Accounts Payable | Low     | Positive    |
| LengthService | Accounting       | Low     | Negative    |
| LengthService | Bakery           | Low     | Negative    |

---

## 5. Data Transformation
- Converted **Gender** and **DepartmentName** into numerical values.  

**Insights:**  
- No strong correlation between **gender** and absenteeism hours.  
- No significant correlation between **department** and absenteeism at individual level.  
- **However:**  
  - Bakery department showed **higher total absenteeism** → may indicate internal/management issues.  
  - Female employees showed **higher absenteeism hours** than males → warrants investigation.  
  - Employees in **Stores business unit** were more absent compared to **Head Office** employees.  

---

## 6. Data Analysis
- Trained a **Multiple Linear Regression (MLR)** model to predict **AbsentHours**.  
- **Features used:** Gender, DepartmentName, Age, LengthService, BusinessUnit.  

**Model Result:**  
- Accuracy = **41.71%** (low, but baseline).  

**Model Script:** [Absenteeism_ML_model.ipynb](https://colab.research.google.com/drive/1M__pODDMvQeRztqpOCQwObBO_9ot9Lya?usp=sharing)  

---

## 7. Interpretation of Results
- Employee productivity is impacted by absenteeism → prediction is valuable for workforce planning.  

**Discovered Factors Affecting Absenteeism:**  
1. **Age** – Positive correlation with absenteeism, though more analysis is needed to distinguish impact on young vs older employees.  
2. **Gender** – Female employees recorded higher cumulative absenteeism hours. This may relate to workplace conditions, harassment, family issues, etc.  
3. **Department/Business Unit** – Bakery department (under Stores unit) recorded the highest absenteeism. May reflect leadership, welfare, or environmental issues.  

**Model Insight:**  
- Built a **Multiple Linear Regression model** with limited data (~100 rows).  
- Accuracy of 41.71% suggests the need for:  
  - Larger dataset,  
  - Alternative ML models (e.g., Random Forest, Gradient Boosting),  
  - More feature engineering.  

---

## 8. Conclusion
- Identified three main factors influencing absenteeism: **Age, Gender, and Department**.  
- Built a baseline regression model for absenteeism prediction.  
- Recommendations:  
  - Conduct deeper root-cause analysis on discovered factors.  
  - Use larger datasets for training.  
  - Explore advanced ML models for higher accuracy.  

---
