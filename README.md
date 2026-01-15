# House Price Prediction – End-to-End Data Science Project

## Project Overview
This project focuses on building a **robust and interpretable house price prediction model** using structured tabular data.  
The primary goal was not just high accuracy, but **clean data handling, leakage-free modeling, and reproducibility using pipelines**.

---

## Key Highlights
- Performed **professional data cleaning** with clear semantic reasoning
- Built a **clean preprocessing + modeling pipeline**
- Improved model performance significantly using **log-transformation of the target**
- Validated results with **train–test comparison**
- Extracted **feature importance** for model interpretability

---

## Dataset
- Input: Tabular housing dataset with numerical and categorical features
- Target variable: `SalePrice`

---

## Step-by-Step Approach

### 1. Data Inspection
- Checked shape, data types, duplicates
- Identified numerical vs categorical features
- Verified logical consistency of values

---

### 2. Data Cleaning & Imputation
- Handled missing values based on **domain meaning**
  - `NaN` → unknown → imputed appropriately
  - `"None"` → absence (e.g., no pool, no alley) → preserved as a valid category
- Removed invalid placeholders (`'', 'NA', 'N/A', '?'`)
- Corrected **semantic data types** (numeric-coded categorical features)
- Verified:
  - No remaining missing values
  - No invalid placeholders
  - Correct feature semantics

✅ Result: **Clean, model-ready dataset**

---

### 3. Feature Preparation
- Separated features (`X`) and target (`y`)
- Performed **train–test split before encoding** to avoid data leakage
- Used:
  - `StandardScaler` for numerical features
  - `OneHotEncoder(handle_unknown='ignore')` for categorical features
- Implemented using `ColumnTransformer`

---

### 4. Baseline Model (Clean Pipeline)
- Built a fully reproducible pipeline using:
  - Preprocessing
  - `LinearRegression`
- Initial performance:
  - **R² ≈ 0.88 (baseline)**

---

### 5. Target Transformation (Key Improvement)
- Applied `log1p` transformation to `SalePrice`
- Reason:
  - House prices are highly skewed
  - Log transformation stabilizes variance and improves linear modeling

📈 **Performance after transformation**:
- **R² improved from ~0.88 → ~0.93**
- Significant reduction in MAE and RMSE

---

### 6. Model Validation
- Compared **Train vs Test R²**
  - Train R² ≈ 0.95
  - Test R² ≈ 0.93
- Small gap confirmed:
  - No overfitting
  - No data leakage
  - Strong generalization

---

### 7. Regularization Check (Ridge Regression)
- Tested Ridge regression for stability
- Performance slightly lower than Linear Regression
- Decision:
  - **Kept Linear Regression** as final model
  - Ridge used as a validation step, not forced improvement

---

### 8. Feature Importance & Insights
- Extracted coefficients from the trained pipeline
- Mapped encoded feature names back to original features
- Analyzed:
  - Direction (positive / negative impact)
  - Magnitude (importance)
- Identified key drivers of house prices such as:
  - Overall quality
  - Location-related features
  - Living area and size attributes

---

## Final Results
- **Final Model**: Linear Regression with log-transformed target
- **Pipeline**: Clean, leakage-free, and fully reproducible
- **Test R²**: ~0.93
- **Key Achievement**:
  > Improved model performance substantially while maintaining interpretability and professional workflow standards

---

## Tools & Libraries
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib / Seaborn (optional, exploratory)

---

## Takeaway
This project demonstrates a **professional data science workflow**:
- Meaning-driven data cleaning
- Proper sequencing of preprocessing steps
- Thoughtful model evaluation
- Emphasis on interpretability, not just metrics

---
