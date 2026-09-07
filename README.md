Retail Customer Analytics

An end-to-end retail analytics project that transforms customer transaction data into actionable business insights using Python, SQL, and Power BI.

Project note: This repository is an adapted and substantially modified version of an MIT-licensed retail analytics project. The original license is retained, and this version documents its own analytical workflow and modifications.

Overview

This project analyzes a retail customer snapshot containing 3,900 customer records across 25 products and 4 product categories.

The workflow combines:

Data cleaning and validation with Python

Feature engineering and exploratory data analysis

Customer value and engagement segmentation

SQL-based business analysis

Cross-validation of Python and SQL results

Interactive Power BI reporting

Business recommendations based on the analytical findings

The goal is to move from raw transaction data → analysis → business insight → decision support.

Business Questions

The analysis focuses on practical retail questions such as:

Which customer segments contribute the most revenue?

How does customer spending vary across engagement levels?

Do subscribers have higher average order values than non-subscribers?

Does discounting increase order value?

Which product categories generate the most revenue?

Which products combine strong revenue with weaker customer ratings?

Which high-value customers are not subscribed?

Which categories show relatively high discount dependence?

How does demand vary across seasons and categories?

Key Results

Metric

Result

Customer records

3,900

Unique customers

3,900

Products

25

Categories

4

Recorded revenue

$233,081

Average order value

$59.76

Subscribers

1,053 (27.0%)

Discounted transactions

1,677 (43.0%)

Customer insights

High-value customers contributed $106,965, representing 45.89% of recorded revenue.

The largest value-engagement segment was Medium Value – Medium Engagement, contributing $40,937.

Subscriber AOV was $59.65, compared with $59.80 for non-subscribers, indicating little difference in single-transaction spend.

A cohort of 431 high-value, highly engaged non-subscribers was identified as a potential subscription-conversion target.

Product insights

Clothing generated approximately $104,264 in revenue.

Accessories generated approximately $74,200.

Together, Clothing and Accessories represented 76.56% of recorded revenue.

Blouse, Shirt, and Dress were the three highest-revenue products.

Shirt generated $10,332 but had an average rating of 3.62, creating a potential product-quality investigation area.

Promotion insights

Discounted orders represented 43.0% of transactions.

Discounted AOV was $59.28, compared with $60.13 for full-price orders.

This dataset therefore does not show evidence that discounts increased average transaction value.

Analytical Workflow

Raw Retail Data
       ↓
Data Quality & Cleaning
       ↓
Feature Engineering
       ↓
Python EDA
       ↓
Customer Intelligence ──┐
                        ├──→ SQL Business Analysis
Product Intelligence ───┘
                              ↓
                    Python ↔ SQL Validation
                              ↓
                       Power BI Dashboard
                              ↓
                   Business Insights & Actions

Data Preparation

The raw dataset was prepared by:

Standardizing column names

Checking duplicate records

Handling missing review ratings using category-level medians

Removing redundant attributes

Harmonizing purchase-frequency categories

Creating analytical features for customer segmentation

Producing cleaned and aggregated datasets for downstream analysis

Engineered Features

Feature

Purpose

age_group

Groups customers into demographic age brackets

purchase_frequency_days

Encodes reported purchase-frequency categories

customer_value_tier

Classifies transaction spend as Low, Medium, or High

engagement_tier

Classifies previous-purchase volume

value_engagement_segment

Combines value and engagement into a 9-segment matrix

Python Analysis

The Python workflow performs:

Dataset profiling

Missing-value analysis

Descriptive statistics

Customer segmentation

Product and category analysis

Revenue comparisons

Exploratory visualizations

Main notebook:

Customer_Shopping_Behavior_Analysis.ipynb

Visualization outputs are stored under:

assets/eda_plots/

SQL Analysis

The SQL layer contains 14 business-oriented analytical queries covering four areas:

Customer Intelligence

Segment revenue contribution

Demographic revenue patterns

Engagement vs. spending

Subscription distribution

Product Intelligence

Category performance

Top products

Product-rating rankings

Value-tier analysis

Commercial Intelligence

Discount vs. order value

Shipping-channel performance

Payment distribution

Seasonal category analysis

Strategic Opportunities

High-value non-subscriber identification

Category revenue vs. discount analysis

SQL techniques include:

GROUP BY
HAVING
CASE WHEN
CTEs
Window Functions
RANK()
DENSE_RANK()
ROW_NUMBER()
Conditional Aggregation
UNION ALL

Main SQL file:

customer_behavior_sql_queries.sql

Analytical Validation

To reduce discrepancies between analytical layers, key outputs were reconciled between Pandas and SQL.

Examples include:

Total revenue

Transaction count

Customer count

Category revenue

Top product

Customer segment revenue

Subscriber count

Discounted transaction count

Product count

Category count

The documented validation checks showed matching results across these dimensions.

Power BI Dashboard

The Power BI report contains four analytical areas:

1. Executive Overview

Revenue

Orders

Customer metrics

Category contribution

Top products

2. Customer Intelligence

Customer segmentation

Demographic analysis

Subscription analysis

Engagement patterns

3. Product Intelligence

Category rankings

Product revenue

Ratings

Product/value comparisons

4. Commercial Opportunities

High-value customer cohorts

Discount analysis

Seasonal demand

Strategic opportunities

Power BI file:

customer_behavior_dashboard.pbix

Business Recommendations

1. Target high-value non-subscribers

Use the identified high-value, highly engaged non-subscriber cohort for targeted subscription-conversion campaigns.

2. Prioritize major revenue categories

Clothing and Accessories account for most recorded revenue, making them important categories for inventory and merchandising decisions.

3. Re-evaluate discount dependence

Discounted orders have slightly lower AOV than full-price orders in this dataset. Promotional strategies should therefore be evaluated on incremental value rather than discount usage alone.

4. Investigate high-revenue / low-rating products

Products with strong revenue but comparatively weaker ratings deserve additional customer-feedback and quality analysis.

5. Align merchandising with seasonal patterns

Observed category-season patterns can be used as a starting point for future promotional and inventory experiments.

Project Structure

Retail-Customer-Analytics/
│
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_behavior_sql_queries.sql
├── customer_behavior_dashboard.pbix
├── customer_shopping_behavior.csv
│
├── data/
│   └── processed/
│       ├── customer_shopping_behavior_cleaned.csv
│       ├── customer_intelligence.csv
│       ├── product_intelligence.csv
│       ├── category_intelligence.csv
│       └── retail_bi.db
│
├── assets/
│   └── eda_plots/
│       ├── eda_dashboard_part1.png
│       └── eda_dashboard_part2.png
│
├── docs/
│   ├── sql_reconciliation_and_results.md
│   └── power_bi_dashboard_documentation.md
│
├── build_powerbi_dashboard.py
├── generate_phase1_notebook.py
├── run_sql_analysis.py
├── LICENSE
└── README.md

Technology Stack

Area

Tools

Programming

Python

Data Analysis

Pandas, NumPy

Visualization

Matplotlib, Seaborn

Database / SQL

SQL, SQLite

BI & Reporting

Power BI, DAX

Development

Jupyter Notebook, VS Code

Version Control

Git, GitHub

Limitations

This dataset is a customer transaction snapshot, so some real-world retail analyses are outside its scope.

No transaction timestamps → true retention, churn, and time-based CLV cannot be calculated.

One record per customer snapshot → basket-level product affinity cannot be reliably measured.

No product cost or COGS → profitability and margin cannot be determined.

Purchase frequency is based on reported categories rather than observed transaction intervals.

The dataset has synthetic-data characteristics, so findings should be treated as analytical observations rather than direct forecasts of real retail performance.

Future Improvements

Potential extensions include:

Adding timestamped transaction history

Building customer retention and churn analysis

Calculating time-based Customer Lifetime Value

Adding product cost and margin data

Performing market-basket analysis

Building automated ETL pipelines

Automating Power BI data refreshes

Adding predictive customer segmentation or propensity models



Author

Rayan Sharma

Built as a retail analytics portfolio project demonstrating practical skills in Python, SQL, data visualization, Power BI, and business analysis.