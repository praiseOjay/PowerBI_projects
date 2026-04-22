📊 UK Online Retail Sales Performance & Customer Insights (2009–2011)
📌 Project Overview
This Power BI dashboard provides a comprehensive analysis of UK online retail sales data spanning from 2009 to 2011. It delivers actionable insights into product demand, revenue performance, customer behaviour, and seasonal trends — enabling data-driven decision-making for retail stakeholders.
---
🗂️ Dataset
Source: UK Online Retail Dataset (commonly sourced from the UCI Machine Learning Repository)
Period Covered: 2009 – 2011
Scope: Transactional retail data from a UK-based online store selling gift and homeware products to customers worldwide
Fields in the Data Model (`Year 2009–2011` table):
Field	Type	Description
Country	Text	Customer's country of origin
Customer ID	Text	Unique identifier for each customer
Description	Text	Product description
Invoice	Text	Invoice number per transaction
InvoiceDate	Date/Time	Date and time of the transaction
Month	Text	Month of the transaction
MonthNumber	Calculated	Numeric representation of the month
One-Time Customers	Measure	Count of customers with a single purchase
Price	Numeric	Unit price of the product
Quantity	Numeric	Quantity of items purchased
Repeat Customer Rate	Measure	Percentage of customers who made repeat purchases
Repeat Customers	Measure	Count of customers with more than one purchase
Revenue	Calculated	Total revenue (Price × Quantity)
Season	Calculated	Season derived from the invoice date
SeasonOrder	Calculated	Numeric order for sorting seasons
StockCode	Text	Unique product stock code
Total Customers	Measure	Total distinct customer count
Total Quantity	Measure	Total units sold
Total Revenue	Measure	Total revenue generated
Year	Calculated	Year extracted from InvoiceDate
---
📈 Dashboard Visuals
The dashboard is organized into 8 key visualizations with interactive filters:
🔝 Top Performance
Visual	Description
Top 10 Countries by Product Demand	Horizontal bar chart showing countries with the highest total quantity ordered. United Kingdom leads significantly.
Top 10 Products by Revenue	Horizontal bar chart highlighting the highest-grossing products (e.g., REGENCY, WHITE items).
Top 10 Customers by Revenue	Identifies the most valuable customers by total revenue contribution.
🔻 Bottom Performance
Visual	Description
Bottom 10 Countries by Product Demand	Countries with the lowest order volumes (e.g., RSA, Bahrain, Korea).
Bottom 10 Products by Revenue	Lowest-revenue products, useful for discontinuation or promotion decisions.
📅 Seasonal & Customer Analysis
Visual	Description
Product Demand by Season	Clustered bar chart comparing total quantity sold across Autumn, Winter, Summer, and Spring.
One-Time vs. Repeat Customer Rate	Donut chart showing 95.75% repeat customers (2K) vs. 4.25% one-time customers (0.07K).
Repeat Customers KPI Card	Highlights the repeat customer metric at 424.7K% (a calculated rate metric).
---
🎛️ Filters & Slicers
The dashboard includes two interactive slicers for dynamic filtering:
Year Slicer: Filter by 2009, 2010, or 2011
Season Slicer: Filter by Autumn, Spring, Summer, or Winter
---
🔑 Key Insights
The United Kingdom dominates product demand, accounting for the vast majority of total quantity ordered compared to all other countries.
Repeat customers make up 95.75% of the customer base, indicating strong customer loyalty and retention.
Autumn is the peak season for product demand, followed by Winter — suggesting a strong holiday/gifting season effect.
A small group of top customers (e.g., Customer IDs 18102, 14646) contribute disproportionately to total revenue.
Some products generate near-zero revenue, presenting opportunities for product portfolio optimization.
---
🛠️ Tools & Technologies
Power BI Desktop — Dashboard development and data modelling
DAX (Data Analysis Expressions) — Calculated columns and measures (e.g., Revenue, Repeat Customer Rate, Season, SeasonOrder)
Power Query (M Language) — Data transformation and cleaning
---
📐 DAX Measures (Examples)
```dax
-- Total Revenue
Total Revenue = SUMX('Year 2009-2011', 'Year 2009-2011'[Price] * 'Year 2009-2011'[Quantity])

-- Repeat Customers
Repeat Customers = 
COUNTROWS(
    FILTER(
        SUMMARIZE('Year 2009-2011', 'Year 2009-2011'[Customer ID], "PurchaseCount", COUNTROWS('Year 2009-2011')),
        [PurchaseCount] > 1
    )
)

-- Repeat Customer Rate
Repeat Customer Rate = DIVIDE([Repeat Customers], [Total Customers], 0)

-- Season (Calculated Column)
Season = 
SWITCH(
    TRUE(),
    MONTH('Year 2009-2011'[InvoiceDate]) IN {12, 1, 2}, "Winter",
    MONTH('Year 2009-2011'[InvoiceDate]) IN {3, 4, 5}, "Spring",
    MONTH('Year 2009-2011'[InvoiceDate]) IN {6, 7, 8}, "Summer",
    "Autumn"
)
```
---
📁 Project Structure
```
📦 UK-Online-Retail-PowerBI
 ┣ 📊 UK_Retail_Dashboard.pbix       # Power BI report file
 ┣ 📄 README.md                      # Project documentation
 ┣ 📂 data/
 ┃ ┗ 📄 online_retail_2009_2011.csv  # Raw dataset
 ┗ 📂 screenshots/
   ┗ 🖼️ dashboard_preview.png        # Dashboard screenshot
```
---
🚀 Getting Started
Prerequisites
Power BI Desktop (free download)
Steps
Clone or download this repository.
Open `UK_Retail_Dashboard.pbix` in Power BI Desktop.
If prompted, update the data source path to point to your local `online_retail_2009_2011.csv`.
Refresh the data and explore the dashboard.
---
👤 Author
> Developed as part of a retail analytics project to explore customer behaviour and sales trends using Power BI.
---
📜 License
This project is for educational and portfolio purposes. The dataset is publicly available via the UCI Machine Learning Repository.
