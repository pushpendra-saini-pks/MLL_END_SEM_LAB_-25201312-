# Customer Segmentation & Churn Prediction
### K-Means Clustering | Decision Tree Classification | K-Means + Logistic Regression

---

## 📌 Project Overview
This project demonstrates the use of **unsupervised and supervised machine learning**
to analyze customer behavior and predict churn.

Three models are implemented:
1. **K-Means Clustering** – Customer Segmentation
2. **Decision Tree Classifier** – Churn Prediction
3. **Hybrid Model (K-Means + Logistic Regression)** – Improved Churn Prediction

---

## 📂 Datasets

### 1️⃣ Mall Customer Segmentation – Clustering
**Source (Kaggle):**  
https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python  

**Use Case:** Customer segmentation using spending behavior  
**Learning Type:** Unsupervised Learning  

---

### 2️⃣ Telco Customer Churn – Binary Classification
**Source (Kaggle):**  
https://www.kaggle.com/datasets/blastchar/telco-customer-churn  

**Target Variable:** `Churn` (Yes / No)  
**Learning Type:** Supervised Learning  

---

#  Model 1: K-Means Customer Segmentation

##  Objective
To group customers into **behaviorally similar clusters**
based on income and spending patterns.

---

##  EDA Summary
- Dataset shape checked (200 × 5)
- No missing values
- No target variable (unsupervised task)
- Plots used:
  - Annual Income distribution
  - Annual Income vs Spending Score

---

## Features Used
| Feature | Why it is used |
|---------------|---------------|
| `Annual Income (k$)` | Indicates purchasing power |
| `Spending Score (1–100)` | Reflects customer spending behavior |

---

## Model Pipeline
```python
StandardScaler → KMeans
```
---

# Model 2: Decision Tree – Telco Customer Churn Prediction

## Objective
The objective of this model is to predict whether a telecom customer will **churn or not**
using a **Decision Tree classifier** trained on customer demographic, service usage,
and billing information.

---

## Dataset
**Name:** Telco Customer Churn  
**Source:** Kaggle  
https://www.kaggle.com/datasets/blastchar/telco-customer-churn  

**Target Variable:** `Churn` (Yes / No)

---

## Exploratory Data Analysis (EDA)

- Dataset shape examined to understand size and feature count
- `TotalCharges` converted from string to numeric
- Rows with missing values removed
- Target distribution analyzed (imbalanced classes)

### Plots Used
- Churn distribution
- Monthly Charges vs Churn

---

## Features Used

- **Demographic Features**
  - Gender
  - SeniorCitizen

- **Service Usage Features**
  - PhoneService
  - InternetService
  - Contract

- **Billing Features**
  - MonthlyCharges
  - TotalCharges

---

## Model Pipeline

```text
OneHotEncoder → DecisionTreeClassifier
```
---

# Model 3: K-Means + Logistic Regression (Hybrid Model)

## Objective
The objective of this model is to improve churn prediction performance by incorporating
customer cluster information derived from **K-Means clustering** into a
**Logistic Regression classifier**.

---

## Dataset
**Name:** Telco Customer Churn  
**Source:** Kaggle  
https://www.kaggle.com/datasets/blastchar/telco-customer-churn  

---

## Key Idea
Customers belonging to different behavioral segments exhibit different churn tendencies.
By adding **Cluster ID** as a feature, the model gains high-level behavioral context,
effectively combining **unsupervised learning** with **supervised learning**.

---

## Exploratory Data Analysis (EDA)

- Reused EDA performed on the Telco Customer Churn dataset
- Derived numeric features specifically for clustering:
  - `tenure`
  - `MonthlyCharges`
  - `Average Monthly Spend`
- Analyzed the distribution of customers across clusters to understand segment sizes

---

## Model Pipeline

```text
OneHotEncoder + StandardScaler → LogisticRegression
```