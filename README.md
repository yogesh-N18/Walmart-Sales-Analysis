# Walmart Sales Analysis (SQL)

Exploratory Data Analysis on Walmart retail sales data using MySQL — from raw transaction records to business insights, entirely in SQL.

## Problem Statement

A retail chain operating three branches (Yangon, Mandalay, Naypyitaw) needs answers to key business questions from its raw transaction data: which branch/product line drives the most revenue, when customers shop most, which payment methods and customer segments dominate, and how satisfaction (ratings) varies by time, day, and branch.

## Dataset

- **Source file**: `WalmartSalesData.csv`
- **Size**: 1,000 rows × 17 columns
- **Columns**: Invoice ID, Branch, City, Customer type, Gender, Product line, Unit price, Quantity, Tax 5%, Total, Date, Time, Payment, COGS, Gross margin percentage, Gross income, Rating

## Tech Stack

- MySQL / MySQL Workbench

## Project Workflow

1. **Database & Table Setup** — created the `walmartSales` database and a `sales` table with a normalized schema (primary key on `invoice_id`, `DECIMAL` types for currency precision, `DATE`/`TIME` types for temporal fields).
2. **Data Import** — loaded `WalmartSalesData.csv` into the `sales` table.
3. **Feature Engineering** — derived 3 new analytical columns from raw date/time fields:
   - `time_of_day` (Morning / Afternoon / Evening) via a `CASE` statement
   - `day_name` via MySQL's `DAYNAME()` function
   - `month_name` via MySQL's `MONTHNAME()` function
4. **Exploratory Data Analysis** — 20+ SQL queries answering business questions using `GROUP BY`, aggregate functions (`SUM`, `AVG`, `COUNT`, `MAX`), subqueries, `CASE` classification, and `UNION`.

## Key Business Questions Answered

- Which branch, city, and product line generate the most revenue?
- What is the most common payment method and customer type?
- Which product lines perform above/below the average sales?
- What time of day and day of the week see the most sales and highest ratings?
- Which customer segments (by gender, customer type) contribute most to revenue and VAT?

## How to Run

1. Open `WalmartSalesDataAnalysis.sql` in MySQL Workbench.
2. Run the database and table creation block.
3. Import `WalmartSalesData.csv` into the `sales` table (Table Data Import Wizard or `LOAD DATA INFILE`).
4. Run the feature engineering block (adds `time_of_day`, `day_name`, `month_name`). If MySQL blocks the `UPDATE` statements with a safe-update-mode error, run `SET SQL_SAFE_UPDATES = 0;` first.
5. Run the EDA queries at the bottom of the script individually or all at once.

## Files

| File | Description |
|---|---|
| `WalmartSalesData.csv` | Raw transaction dataset (1,000 rows) |
| `WalmartSalesDataAnalysis.sql` | Full SQL script: schema, feature engineering, EDA queries |

## Techniques Used

- Schema design with appropriate data types (`DECIMAL` for currency, `DATE`/`TIME` for temporal data)
- Feature engineering with `CASE` statements and built-in date functions
- Aggregation and grouping (`GROUP BY`, `SUM`, `AVG`, `COUNT`, `MAX`)
- Subqueries for dynamic benchmarking (e.g., comparing product lines against overall average sales)
- `UNION` to combine segmented query results into unified outputs
