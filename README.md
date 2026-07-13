Customer Churn Analytics Dashboard
Tool: Power BI Desktop
Dataset: Telco Customer Churn (Kaggle, ~7,043 customer records)
Author: A Rathna Prabu Ayyappan | [LinkedIn](https://www.linkedin.com/in/rathna-prabu-ayyappan-data-analyst/) | ayyappanrathnaprabu@gmail.com
---
📌 Problem Statement
A telecom company wants to understand why customers churn and where to focus retention efforts. This dashboard analyzes customer, contract, and billing data to identify the highest-risk customer segments, quantify revenue impact, and provide data-backed retention recommendations.
🗂️ Dataset
Source: Telco Customer Churn dataset (Kaggle)
Size: 7,043 customers, 21 original columns
Fields used: Contract type, payment method, tenure, monthly/total charges, senior citizen status, gender, churn status
🧹 Data Cleaning (Power Query)
Fixed `TotalCharges` — originally imported as text due to blank values for customers with 0 tenure; converted to Decimal and set blanks to 0
Converted `SeniorCitizen` from 0/1 integer to Yes/No text for consistency with other categorical fields
Created a Tenure Bucket column (0-12, 13-24, 25-48, 49+ months) with a numeric sort-order helper column to ensure correct chart ordering
Verified row count (7,043) remained consistent after every transformation step
Checked for duplicate customer IDs and confirmed default summarization settings
📊 Approach
Built a 3-page interactive Power BI dashboard:
Executive Overview — KPI cards (Total Customers, Revenue, Churn Rate, Retention Rate, Revenue at Risk, Avg Monthly Charges) with churn breakdowns by Contract Type, Payment Method, and Tenure Bucket, plus interactive slicers (Contract, Senior Citizen, Gender)
Risk Segmentation — A nested matrix (Contract → Payment Method) with conditional-formatted heat maps on Churn Rate % and Churned Revenue, plus a Retained vs. Churned Revenue donut chart
Key Insights & Recommendations — Summary of findings translated into concrete business actions
Key DAX measures: Churn Rate %, Retention Rate, Churned Revenue, Retained Revenue, Avg Monthly Charges — all built using `DIVIDE()` and `CALCULATE()` for safe, filter-context-aware calculations.
💡 Key Insights
Highest-risk segment: Month-to-month customers paying via Electronic Check churn at 53.73% — nearly double the overall average of 26.54%. This single segment accounts for $1.2M (42%) of all churned revenue.
Tenure drives retention: Churn rate drops sharply with customer tenure — 47.4% in the first year vs. just 9.5% after 4+ years. Risk is concentrated almost entirely in the first 12 months.
Revenue exposure: 17.83% of total revenue ($2.86M of $16.06M) is tied to customers who have already churned, despite churned customers making up only 26.5% of the customer base.
Contract type matters most: Two-year contract customers churn at just 2.83% — roughly 15x lower than month-to-month customers (42.71%).
✅ Recommendations
Prioritize retention campaigns for month-to-month, electronic-check customers — the highest churn concentration and revenue exposure.
Offer incentives to shift month-to-month customers onto 1-2 year contracts, given the ~15x churn gap between contract types.
Strengthen onboarding and early-lifecycle engagement — the first 12 months are the highest-risk window for churn.
🖼️ Dashboard Preview
![Executive Overview](screenshots/page1_executive_overview.png)
![Risk Segmentation](screenshots/page2_risk_segmentation.png)
![Key Insights](screenshots/page3_key_insights.png)
📁 Files
`Customer\_Churn\_Dashboard.pbix` — full Power BI file
`screenshots/` — page exports for quick preview without opening Power BI
🔧 How to Use
Download the `.pbix` file
Open in Power BI Desktop (free)
Data can be refreshed by pointing to your own copy of the Telco Customer Churn CSV
---
This project was built as part of a data analytics portfolio to demonstrate skills in data cleaning (Power Query), data modeling, DAX, and dashboard design in Power BI.
