# EDA-Study-from-Data-Bootcamp-Class
Work done by Weiyi Lu, Nick Gobejishvili, and Christina Faith

## Overview
This project presents an exploratory data analysis (EDA) of loan default risk using two related datasets: `application_data.csv` and `previous_application.csv`. The goal is to identify which customer and historical behavioral factors are most strongly associated with repayment difficulty.

The analysis is divided into two parts:
- **Part 1:** Customer-level risk analysis using current application data.
- **Part 2:** Behavioral risk analysis using previous loan application history.

The notebook focuses on comparing default vs. non-default groups and visualizing patterns across demographic, financial, and historical variables.

## Task
The main task of this project was to investigate what factors are linked to loan default and to extract practical business insights that could help a lender make better approval decisions.

The analysis specifically examined:
- how borrower stability indicators (such as age, employment length, education, income type, and family status) relate to default risk,
- and whether prior application behavior, especially refusal history, can serve as a strong risk signal.

## Data Sources
- `application_data.csv`: current customer application information and default target.
- `previous_application.csv`: customers' past application records, including approval and refusal outcomes.
- `columns_description.xlsx`: variable descriptions used for reference.

## Methods
The project uses pandas for data cleaning and feature engineering, and matplotlib/seaborn for visualization.

## Main Findings
### 1. Baseline default rate is relatively low
About **8%** of customers experienced payment difficulties, while about **92%** repaid on time. This serves as the baseline risk level for all later comparisons.

### 2. Loan size and income are not the strongest predictors
The analysis found only limited differences in:
- income between defaulters and non-defaulters,
- requested credit amounts,
- and credit-to-income ratio.

This suggests that **loan amount alone does not explain default risk well**.

### 3. Borrower stability matters more than raw financial size
Several borrower characteristics show clearer relationships with default risk:
- **Age:** Younger applicants have higher default rates, and risk declines steadily with age.
- **Employment length:** Customers with shorter work histories default more often. Applicants with fewer than 2 years of employment show much higher default risk than those with long-term employment histories.
- **Education:** Lower education levels are associated with higher default rates, while applicants with academic degrees show the lowest risk.
- **Income type:** More stable income sources, such as pensioners or state servants, generally correspond to lower default rates.
- **Family status:** Single and civil-marriage applicants tend to show higher default rates than married or widowed applicants.

Overall, these variables suggest that **financial and social stability are stronger indicators of repayment behavior than simple borrowing amount**.

### 4. Previous refusal history is the strongest behavioral signal
One of the clearest findings is that customers with a high ratio of previously refused applications are much more likely to default.

As `PREV_REFUSED_RATIO` increases, default risk rises in a strong, monotonic pattern. Clients with the highest refusal history have the highest observed default rates. This makes prior refusal history one of the most useful behavioral predictors in the project.

### 5. Operational patterns are informative but less predictive
The notebook also examines patterns such as application activity by day of the week and relationships between requested and granted credit. These views help explain lending workflow and approval behavior, but they are less powerful for predicting default than stability and refusal-history features.

## Business Implications
The findings suggest that lenders should prioritize **borrower stability indicators** and **historical behavior** when assessing credit risk.

Potential actions include:
- applying stricter review to applicants with unstable employment histories,
- monitoring younger or less financially established borrowers more carefully,
- incorporating education and income stability into approval logic,
- and using prior refusal history as a major warning signal for future repayment difficulty.

Rather than relying mainly on requested loan size, lenders can use these insights to make more balanced decisions that reduce risk while still approving reliable borrowers.

## Conclusion
This EDA shows that loan default is driven less by how much a customer wants to borrow and more by whether the customer appears financially and behaviorally stable. Among all features explored, **employment stability, age, education, income stability, and especially previous refusal history** emerge as the most meaningful indicators of repayment difficulty.

These results provide a strong foundation for future predictive modeling and risk-based lending strategies.
