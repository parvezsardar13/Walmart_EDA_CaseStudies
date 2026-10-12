# Walmart_EDA_CaseStudies
Walmart Exploratory Data Analysis &amp; Business Case Study An end-to-end exploratory data analysis project examining customer purchase behavior on Black Friday.
# Walmart Black Friday Exploratory Data Analysis & Statistical Validation
*An end-to-end exploratory data analysis and Central Limit Theorem validation examining customer purchase behavior on Black Friday.*

## Badges
![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Data%20Visualization-3776AB.svg)
![SciPy](https://img.shields.io/badge/SciPy-Statistics-8CAAE6.svg)

## Project Overview
This project investigates customer transaction records from Walmart's Black Friday sales event to understand purchasing patterns across demographics. By analyzing 550,068 transactions, the study evaluates whether average purchase amounts differ significantly by gender, marital status, and age. Using bootstrapping and the Central Limit Theorem (CLT), the analysis provides robust statistical insights to guide data-driven retail strategies and customer segmentation.

## Business Problem / Objectives
* Does customer gender have a statistically significant impact on average purchase amounts during Black Friday?
* Does marital status meaningfully alter how much customers spend per transaction?
* How do different age groups compare in terms of preferred product categories and average spending?
* How does sample size affect the precision of estimates and the sampling distribution of the mean?

## Dataset
* **Rows:** 550,068
* **Columns:** 10

| Column Name | Type | Description |
| :--- | :--- | :--- |
| `User_ID` | String (converted) | Unique customer identifier |
| `Product_ID` | String | Unique product identifier |
| `Gender` | String | Customer gender (M / F) |
| `Age` | String | Customer age bracket (e.g., 0-17, 26-35, 55+) |
| `Occupation` | String (converted) | Coded occupation identifier |
| `City_Category` | String | City classification category (A, B, C) |
| `Stay_In_Current_City_Years` | String | Number of years residing in current city |
| `Marital_Status` | String (converted) | Marital status indicator (0 = Unmarried, 1 = Married) |
| `Product_Category` | String (converted) | Coded product category identifier |
| `Purchase` | Integer/Float | Purchase transaction amount in currency units |

## Tools & Libraries
* **Python**: Core programming language for data processing
* **Pandas & NumPy**: Data manipulation, aggregation, numerical clipping, and array operations
* **Matplotlib & Seaborn**: Statistical data visualization (boxplots, countplots, histograms, error bars)
* **SciPy**: Statistical functions

## Methodology
1. **Data Loading & Structure Checks**: Imported raw CSV data, inspected data types (`df.info()`), reviewed dataset shape (550,068 rows, 10 columns), and verified zero missing values.
2. **Data Cleaning & Type Conversion**: Converted categorical identifier columns (`User_ID`, `Occupation`, `Marital_Status`, `Product_Category`) from numeric storage types to strings.
3. **Outlier Detection & Robustness Checks**: Inspected purchase distributions via boxplots; calculated IQR bounds ([-3523.50, 21400.50]) identifying 2,677 outliers (0.49%), and generated a clipped column (`Purchase_clipped`) between the 5th (1984.0) and 95th (19336.0) percentiles for robustness checking while retaining extreme values for real-transaction revenue analysis.
4. **Exploratory Data Analysis (EDA)**: Analyzed top product categories across age groups, evaluated average spend by age and marital status, and mapped product category preferences by gender.
5. **Bootstrapping & CLT Simulation**: Built a custom bootstrapping function (`bootstrap_ci`) to resample purchase data across multiple sample sizes ($n = 300, 3,000, 30,000$, and full data) to construct 95% confidence intervals and observe sampling distributions.
6. **Hypothesis Evaluation & Reporting**: Assessed confidence interval overlap across gender, marital status, and age brackets to derive concrete business implications.

## Key Insights & Findings
* **Transaction Volume vs. Spend Level**: The overall dataset contains 550,068 transactions with an average purchase amount of ₹9,263.97 (std = ₹5,023.07).
* **Gender Spend Disparity**: Male transactions ($n = 414,259$) exhibit a full-data 95% CI of [9,422.34, 9,453.75], while female transactions ($n = 135,809$) show a CI of [8,707.44, 8,760.40]. Their confidence intervals do not overlap, indicating men spend roughly 8–9% more per transaction on average.
* **Marital Status Parity**: Unmarried customers (mean = ₹9,265.91, 95% CI [9,249.99, 9,282.39]) and married customers (mean = ₹9,261.17, 95% CI [9,239.20, 9,281.69]) show substantial confidence interval overlap, demonstrating no meaningful difference in average purchase amount based on marital status.
* **Age Group Variation**: Average purchase amounts vary by age, with the youngest group (0–17) recording the lowest mean spend (₹8,933.46, 95% CI [8,847.78, 9,015.72]) and the 51–55 group recording a higher mean spend (₹9,534.81, 95% CI [9,481.95, 9,589.22]).
* **Core Product Dominance**: Product Categories 1, 5, and 8 dominate purchase volume across all age groups and genders (e.g., Category 1 accounts for 115,547 purchases among men and 24,831 among women).
* **Sample Size Effect on CLT**: Increasing sample sizes from $n = 300$ to $n = 30,000$ narrowed confidence interval widths by roughly 10x, and transformed sampling distributions into tighter, symmetric, bell-shaped curves matching Central Limit Theorem expectations.


## Recommendations
* **Prioritize Gender over Marital Status**: Because gendered average spend differs significantly while marital status shows no statistical difference, allocate personalized marketing and promotional budgets toward gender segments rather than marital segmentation.
* **Grow Female Customer Acquisition**: Women represent a smaller share of transactions (~25%) with a slightly lower average basket value; focus on acquisition campaigns and curated categories to capture untapped female customer volume.
* **Secure High-Volume Inventory**: Ensure uninterrupted stock availability for Product Categories 1, 5, and 8 during Black Friday events, as these drive the vast majority of purchase volume across all demographics.
* **Implement Age-Tiered Offers**: Target younger cohorts (0–25) with value-oriented bundles or lower-basket incentives, and deploy premium bundle upsells for older adult segments (36–55+) who exhibit higher average transaction values.
* **Leverage Bootstrapped Validation**: Utilize CLT-based bootstrapping for future A/B testing and metric evaluations given the right-skewed nature of raw retail transaction data.

## Limitations & Future Work
* **Dataset Scope**: The dataset lacks external macroeconomic variables, customer income brackets, and timestamp details beyond multi-year city residency.
* **Coded Features**: Occupations and product categories are represented by numerical codes without descriptive metadata labels.
* **Future Work**: Integrate predictive machine learning models to forecast customer purchase amounts and evaluate repeat-buyer retention metrics across campaigns.

## How to Run
1. Open the interactive notebook directly in Google Browser via Colab: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/10hYORKW6Nx_DgPm_ftCHyNDWct7fYozA)
2. Or clone the repository locally and run the Jupyter notebook:
   ```bash
   git clone [ADD GITHUB URL]
   cd Walmart_EDA_CaseStudies
   jupyter notebook Walmart_EDA_Case_Study.ipynb
