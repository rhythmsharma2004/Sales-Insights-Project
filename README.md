India Retail Revenue Intelligence Dashboard
An end-to-end sales analytics project built using MySQL for data extraction and transformation and Power BI for interactive dashboarding. The project analyzes over 984 million in total revenue across 14 Indian markets spanning 2017 to 2020.

Tools & Technologies
ToolPurposeMySQLDatabase setup, ETL, multi-table SQL queriesPower BI DesktopData modeling, DAX measures, dashboardingDAXCalculated columns and KPI measures

Objective
A retail business operating across multiple Indian markets needed a visual interface to track revenue performance, monitor market-wise sales, identify top customers and products, and understand monthly and yearly trends. This project delivers that solution by combining SQL querying with Power BI dashboards.

Database Schema
The sales database consists of 5 relational tables:
TableDescriptioncustomers38 customers across Brick & Mortar and E-Commerce typesproductsProduct IDs and detailstransactionsTransaction-level sales and revenue recordsmarkets14 city-level markets across North, South, and Central IndiadateCalendar table covering June 2017 to June 2020
Key relationships:

transactions → customers (via customer_code)
transactions → products (via product_id)
customers → markets (via market_code)
transactions → date (via order_date)


Data Preparation in SQL
Key SQL operations performed:

Joined fact and dimension tables across 5 relational tables
Created aggregated views for Power BI import
Calculated revenue as sales_qty multiplied by price
Filtered NULL values and verified data consistency across markets

Example aggregation query:
sqlSELECT
    m.markets_name,
    SUM(t.sales_qty * p.price) AS revenue,
    SUM(t.sales_qty) AS total_qty
FROM transactions t
JOIN products p ON t.product_id = p.product_id
JOIN customers c ON t.customer_code = c.customer_code
JOIN markets m ON c.market_code = m.markets_code
GROUP BY m.markets_name
ORDER BY revenue DESC;

Power BI Modeling & Measures
After importing cleaned SQL data into Power BI:

Established a star-schema with transactions as the fact table
Created a date hierarchy for time-series analysis (year, month)
Built DAX measures including:

Total Revenue = SUM(Revenue)
Total Sales Qty = SUM(Sales_Qty)
Revenue by Market and Revenue by Customer




Dashboard Overview
The Power BI dashboard includes the following:

KPI Cards: Total revenue (984.81M) and total sales quantity (2M+)
Bar Charts: Revenue by market and sales quantity by market across 14 cities
Line Chart: Monthly revenue trend from 2017 to 2020
Top 5 Customers: Ranked by total revenue contribution
Top 5 Products: Ranked by sales performance
Slicers: Year and month filters for dynamic exploration


Key Business Insights

Delhi NCR is the top-performing market, contributing 519.51M — approximately 52% of total revenue
Electricalsara Stores is the highest-value customer with 413.33M in revenue, significantly ahead of second-ranked Electricalslytical at 49.64M
Mumbai and Ahmedabad rank second and third with 150.08M and 132.31M respectively
Revenue shows a declining trend from mid-2018 to 2020, suggesting need for market strategy review
A product with missing name data accounts for the highest product revenue (468.96M), indicating a data quality issue to be resolved
E-Commerce customers such as Nixon (43.89M) compete closely with Brick & Mortar stores in the top 5


Project Files
FileDescriptiondatabase.sqlMySQL dump file to recreate the full sales databaseSales_Insights_Data_Analysis_Project.pbitPower BI template file with all dashboardsProject_Report_Sales_Insights_Data_Analysis.pdfFull project report with methodology and insightspower_bi_report_ss.pngDashboard screenshot

How to Use

Clone this repository

bash   git clone https://github.com/rhythmsharma2004/Sales-Insights-Project

Open MySQL Workbench and import database.sql to restore the database
Open Sales_Insights_Data_Analysis_Project.pbit in Power BI Desktop
Connect Power BI to your local MySQL instance
Refresh the data and explore the dashboards with slicers


Skills Demonstrated
SQL | ETL Pipeline | Relational Database Design | Data Modeling | Power BI | DAX | KPI Development | Business Intelligence | Data Visualization | Revenue Analysis

Author
Rhythm Sharma
B.Tech, Indian Institute of Technology Jodhpur
b22ci035@iitj.ac.in
