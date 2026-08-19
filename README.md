# Online Retail Business Intelligence using Apache Pig, Apache Hive & R Markdown
<p align="center">
  <img width="1584" height="396" alt="Image" src="https://github.com/user-attachments/assets/3adf71c6-1db2-43ca-905a-74e5594e0ee1" />
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#dataset">Dataset</a> •
  <a href="#data-cleaning">Data Cleaning</a> •
  <a href="#analysis">Analysis</a> •
  <a href="#insights">Insights</a> •
  <a href="#recommendations">Recommendations</a> •
  <a href="#reproducibility">Reproducibility</a> •
  <a href="#about">About</a>
</p>

> **Academic Project — STQD6324 Data Management**

> A business intelligence project using Apache Pig, Apache Hive and R Markdown to process and analyse the Online Retail II dataset. The project covers large-scale data cleaning, SQL-based business analysis and interactive dashboard development.

---

## Overview

This project processes the **Online Retail II** dataset through a Business Intelligence workflow, from raw transaction data to interactive business insights. Python is used for initial data preparation, Apache Pig for data cleaning, Apache Hive for analytical querying, and R Markdown for dashboard development.

The overall workflow is:

```mermaid
flowchart LR

A[Online Retail II Dataset]
--> B[Python]

B --> C[Apache Pig]

C --> D[Apache Hive]

D --> E[Business Analytics]

E --> F[Export Query Results]

F --> G[R Markdown Dashboard]
```

### Workflow Structure

```yaml
online-retail-business-intelligence
│
├── 1. Python
│   ├── Dataset exploration
│   ├── Simple EDA before data cleaning
│   └── Convert xlsx to TSV
│
├── 2. Apache Pig
│   ├── Load dataset
│   ├── Remove missing values
│   ├── Remove duplicate records
│   ├── Remove invalid quantity
│   ├── Remove invalid price
│   └── Create sales_amount
│
├── 3. Apache Hive
│   ├── Create database
│   ├── Create table
│   ├── Load cleaned data
│   ├── Data validation
│   └── Business analysis
│
└── 4. R Markdown Dashboard
    ├── Business KPIs
    ├── Revenue trend
    ├── Top products by revenue
    ├── Monthly trend
    ├── Top products by quantity sold
    ├── Top customers by spending
    └── top countries by revenue
```

---

## Dataset

**Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii)↗️

The Online Retail II dataset contains transactional records from a UK-based online retail company between 1 December 2009 and 9 December 2011. The company primarily sells unique all-occasion gifts and many customers are wholesalers.

The dataset contains 1,067,371 transaction records and 8 variables with detailed information about products, customers and transactions. It enables the analysis of:

- Sales performance over time
- Customer purchasing behaviour
- Product performance
- Geographic distribution of sales
- Business key performance indicators (KPIs)

### Variables Used

| Variable | Description |
|---|---|
| `Invoice` | Invoice number identifying each transaction |
| `StockCode` | Unique product identifier |
| `Description` | Product name or description |
| `Quantity` | Number of units purchased |
| `InvoiceDate` | Date and time of the transaction |
| `Price` | Unit price of the product |
| `Customer ID` | Unique customer identifier |
| `Country` | Customer country |

### Dataset Summary

| Item | Value |
|---|---|
| Source | UCI Machine Learning Repository |
| Time Period | December 2009 – December 2011 |
| Total Records | 1,067,371 |
| Variables | 8 |
| Industry | E-commerce / Online Retail |

---

## Data Cleaning

The dataset was initially explored using Python before being converted from XLSX to TSV format to facilitate data cleaning in Apache Pig. Apache Pig was then used to clean and preprocess the data, as well as create a new `sales_amount` variable.

The cleaning process reduced the dataset from 1,067,371 records to 779,425 records for subsequent analysis in Apache Hive.

### Cleaning Steps

- Removed records with missing values
- Removed duplicate records
- Removed transactions with invalid quantity (≤ 0)
- Removed transactions with invalid price (≤ 0)
- Created a new variable named **sales_amount** (`Quantity × Price`)

### Apache Pig Script

*<img width="1401" height="875" alt="Image" src="https://github.com/user-attachments/assets/229982cb-693b-4423-a407-3788b42a1f19" />*

### Cleaned Dataset Output

*<img width="1249" height="718" alt="Image" src="https://github.com/user-attachments/assets/9c0d3371-515e-445f-8cc6-2ec0a731c584" />*

---

# Analysis

The cleaned dataset was imported into Apache Hive for business-oriented analytical querying. The query results were exported as CSV files and used to develop an interactive R Markdown dashboard.

### Apache Hive Queries

*<img width="1297" height="888" alt="Image" src="https://github.com/user-attachments/assets/643e8063-a18a-43f9-9957-af3d54d27ddb" />*

### Query Output

*<img width="1339" height="361" alt="Image" src="https://github.com/user-attachments/assets/d9115b49-3b83-46ed-9f46-0e39c5fe3bc9" />*

---

## Dashboard Overview

*<img width="1920" height="878" alt="Image" src="https://github.com/user-attachments/assets/6dde1881-b0e2-4d31-90f6-3c8aa96c094a" />*

The dashboard brings together key business performance indicators, sales trends, product performance, customer spending and geographic revenue.

---

### Business KPIs

*<img width="1920" height="264" alt="Image" src="https://github.com/user-attachments/assets/b917c93c-eadf-4670-a540-297341811ad8" />*

### Findings

The business generated approximately **£17.37 million** in total revenue from **36,969 completed orders**, involving **5,878 customers** and **4,631 products**. The average order value was **£469.98**, meaning the average completed order generated approximately £470 in revenue.

---

### Monthly Revenue Trend

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/12a16540-4c68-4af9-886f-17ac5b103ba1" />*

### Findings

Monthly revenue fluctuated throughout the two-year period, with revenue consistently peaking in November. Revenue reached **£1.17 million in November 2010** and **£1.16 million in November 2011**, before declining in December. The December figures should be interpreted with caution because the dataset only contains transactions up to **9 December 2011**.

---

### Monthly Order Trend

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/2c05b05e-7d1d-4a38-98e3-c8f0b65e4745" />*

### Findings

The number of completed orders followed a similar pattern to monthly revenue. Order volume increased towards the end of each year and reached its highest level in **November 2011 (2,657 orders)**. The similar movement between order volume and revenue suggests that higher order activity was an important contributor to the increase in revenue.

---

### Top Products by Revenue

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/89924349-72d5-46aa-a30c-6702751330b9" />*

### Findings

The **REGENCY CAKESTAND 3 TIER** generated the highest total revenue, followed by **WHITE HANGING HEART T-LIGHT HOLDER** and **PAPER CRAFT, LITTLE BIRDIE**. These products were among the largest contributors to the retailer's total revenue during the period analyzed.

---

### Top Products by Quantity Sold

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/fc4587c3-6f96-4031-9210-ebb428b22e37" />*

### Findings

The **WORLD WAR 2 GLIDERS ASSTD DESIGNS** recorded the highest sales quantity, followed by **WHITE HANGING HEART T-LIGHT HOLDER** and **PAPER CRAFT, LITTLE BIRDIE**. Comparing quantity sold with revenue shows that the products with the highest sales volume were not necessarily the highest revenue generators, highlighting the influence of product price on total revenue.

---

### Top Customers by Spending

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/488db80c-3961-4e56-b296-91b6fa45d401" />*

### Findings

Customer **18102** recorded the highest total spending at approximately **£580,987**, followed by customers **14646 (£528,603)** and **14156 (£313,438)**. The large difference between the top customers and the rest of the customer base suggests that a small group of customers had substantially higher spending than others.

---

### Revenue by Country

*<img width="603" height="474" alt="Image" src="https://github.com/user-attachments/assets/916f4e3b-074c-44c5-96af-cafd836f07fa" />*

### Findings

The **United Kingdom** generated the largest share of revenue at approximately **£14.39 million**, substantially higher than any other country. Among the international markets, **EIRE, the Netherlands, Germany and France** generated the highest revenue outside the UK.

---

## Insights

The dashboard provides several important business insights:

### 1. Strong Seasonal Sales Pattern

Both monthly revenue and order volume increased towards October and November, indicating a recurring seasonal pattern in sales activity.

### 2. Product Price Influences Revenue

Comparing the revenue and quantity analyses shows that products with the highest sales volumes were not always the highest revenue generators. This highlights how both sales volume and product price contribute to total revenue.

### 3. High-Value Customers Drive Revenue

The customer spending analysis showed that a small group of customers had substantially higher spending than the rest of the customer base. These high-value customers may be important targets for customer retention and loyalty strategies.

### 4. Strong Domestic Market with International Revenue

The United Kingdom generated the majority of revenue, while EIRE, the Netherlands, Germany and France were the largest international contributors. These markets could be considered when evaluating opportunities for future international marketing and expansion.

---

## Recommendations

- Increase inventory planning ahead of the October–November peak sales period.
- Prioritise inventory management for products with consistently high sales volume or revenue.
- Consider loyalty programmes and personalised promotions for high-value customers.
- Evaluate marketing opportunities in international markets such as EIRE, Germany and France.

---

## Conclusion

This project demonstrates how a large transactional dataset can be transformed into business insights through a Business Intelligence workflow. Apache Pig and Apache Hive were used for data cleaning and analysis, while R Markdown was used to develop an interactive dashboard.

The analysis highlighted seasonal sales patterns, differences between product sales volume and revenue, high-value customers and the geographic distribution of revenue. These findings can support decisions around inventory planning, customer retention, product management and market strategy.

---

## Reproducibility

##3 Development Environment

This project was developed and tested using the following environment:

| Component | Version |
|------------|------------|
| Apache Pig | 0.16.0.2.6.5.0-292 |
| Apache Hive | 1.2.1000.2.6.5.0-292 |
| Hadoop (HDFS) | 2.7.3.2.6.5.0-292 (HDP Sandbox 2.6.5) |
| Python | 3.13.9 |
| R | 4.5.1 |
| R Markdown | 2.31 |

---

### Python Libraries

The Python workflow used Pandas for initial dataset exploration and conversion from XLSX to TSV format.

```python
import pandas as pd
```

---

### R Packages

The interactive dashboard was developed in R Markdown using Flexdashboard and Plotly, with additional packages for data manipulation, reporting and visualisation.

```r
library(rmarkdown)
library(flexdashboard)
library(ggplot2)
library(plotly)
library(dplyr)
library(readr)
library(scales)
library(shiny)
```
---

### Running the Project

To reproduce the analysis and dashboard:

1. Download the **Online Retail II** dataset (XLSX format) from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii).

2. Run `data_preparation.ipynb` to perform initial exploration and convert the dataset from **XLSX** to **TSV** format.

3. Start the **HDP Sandbox** and upload `online_retail_ii.tsv` to HDFS.

4. Run `online_retail_data_cleaning.pig` to clean and preprocess the data.

5. Run `worksheet1.sql` to create the Hive database and table and load the cleaned dataset.

6. Run `worksheet2.sql` to perform the business analysis.

7. Export the Hive query results as CSV files and place them in the `dashboard/` folder.

8. Open `Dashboard.Rmd` in RStudio and knit the file to generate the interactive dashboard.

---

> [!NOTE]
> - All outputs in this repository were generated from the Apache Pig scripts, Apache Hive queries and R Markdown dashboard.
> - The dashboard was developed using R Markdown, Flexdashboard and Plotly.

---

### Repository Structure

```text
Online-Retail-Business-Intelligence/
│
├── python/
│   └── data_preparation.ipynb
│
├── pig/
│   └── online_retail_data_cleaning.pig
│
├── hive/
│   ├── worksheet1.sql
│   └── worksheet2.sql
│
├── dashboard/
│   ├── Dashboard.Rmd
│   └── Dashboard.html
│
├── images/
│   ├── Title.png
│   ├── Pig_Script.png
│   ├── Pig_Output.png
│   ├── Hive_Script.png
│   ├── Hive_Output.png
│   ├── Dashboard.png
│   ├── KPI.png
│   ├── Monthly_Revenue_Trend.png
│   ├── Monthly_Order_Trend.png
│   ├── Top_Products_by_Revenue.png
│   ├── Top_Products_by_Quantity_Sold.png
│   ├── Top_Customers_by_Spending.png
│   └──Top_Countries_by_Revenue.png
│
└── README.md
```

---

## About

This project was completed as part of the **STQD6324 Data Management** course at Universiti Kebangsaan Malaysia.
