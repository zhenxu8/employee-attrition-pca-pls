# Employee Attrition Analysis: Segmentation, Driver Identification & Prediction using PCA & PLS-DA

## Overview

This project applies multivariate statistical methods to analyze employee attrition using the IBM HR Analytics dataset (1,470 employees, 35 features). The analysis addresses three research questions:

1. **Segmentation** — Do employees with and without attrition exhibit distinct patterns in multivariate feature space?
2. **Driver Identification** — What factors most significantly influence employee attrition?
3. **Prediction** — Can we accurately predict whether an employee will leave?

*Academic project for SEP 767: Multivariate Statistical Methods for Big Data Analysis, McMaster University (April 2026)*

---

## Methods

| Step | Method | Purpose |
|------|--------|---------|
| Dimensionality Reduction | PCA + K-Means | Employee segmentation and cluster interpretation |
| Driver Identification | PLS-DA coefficients + VIP scores | Identify key attrition predictors |
| Prediction | PLS-DA with cross-validation | Attrition risk classification |
| Evaluation | Precision, Recall, F1, PR curve optimization | Handle class imbalance |

**Why PCA & PLS instead of traditional regression?**
The dataset contains highly correlated features (multicollinearity), particularly around tenure and compensation variables. PCA handles this through dimensionality reduction, while PLS-DA maximizes covariance between predictors and the attrition target — making both methods more suitable than standard logistic regression for this data structure.

---

## Tech Stack

- **Language:** Python 3
- **Libraries:** pandas, NumPy, scikit-learn, seaborn, matplotlib, scipy
- **Dataset:** [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) (Kaggle)

---

## Key Findings

**Segmentation (PCA + K-Means, k=4):**
- PC2–PC3 revealed the strongest cluster separation for attrition groups
- 4 employee clusters identified with distinct attrition profiles:
  - **Cluster 0 (R&D, Well-Paid):** Lowest attrition — high pay offsets overtime pressure
  - **Cluster 1 (HR, Junior):** Moderate attrition — compensation more critical than promotion signals
  - **Cluster 2 (Sales Exec, High-Risk):** Highest attrition — driven by excessive travel, overtime, and disproportionately low pay
  - **Cluster 3 (Sales, Experienced):** Lower risk despite high workload — seniority and compensation are protective
- Overtime employees showed 3x higher attrition rate (30.5% vs 10.4%)

**Driver Identification (PLS-DA VIP scores):**
- Top attrition drivers: OverTime, MonthlyIncome, JobLevel, TotalWorkingYears, YearsAtCompany
- Strategic implication: retention strategies must be targeted by segment — a uniform approach is ineffective

**Prediction (PLS-DA):**
- Cross-validation used to select optimal number of latent components
- PR curve threshold optimization applied to address class imbalance
- Model evaluated on Precision, Recall, and F1-Score

---

## Project Structure

```
├── model.ipynb          # Full analysis: EDA, PCA, PLS-DA, prediction
├── README.md
```

---

## Related Project

This project uses the same IBM HR dataset as the [Employee Attrition Analytics Platform](https://github.com/zhenxu8/employee-attrition-azure-data-pipeline), which focuses on the data engineering side — building an Azure Data Factory pipeline, star schema data model, and Power BI dashboard for attrition visualization.
