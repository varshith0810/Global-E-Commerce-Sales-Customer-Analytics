# 🌍 Global E-Commerce Sales & Customer Analytics (2023–2025)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458.svg)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-Interactive-3F4F75.svg)](https://plotly.com/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Statistical-4C72B0.svg)](https://seaborn.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An end-to-end data analytics and business intelligence project analyzing **2,000 global transactions** spanning **20 countries**, **5 continents**, **4 product categories**, and **3 customer segments** from **January 2023 through December 2025**.

This repository delivers deep exploratory data analysis (EDA), statistical correlation modeling, pricing elasticity evaluation, and actionable strategic recommendations designed for executive decision-makers and BI dashboard deployment (Power BI / Tableau / Streamlit).

---

## 📑 Table of Contents

- [Executive Summary & Core KPIs](#-executive-summary--core-kpis)
- [Project Architecture & Methodology](#-project-architecture--methodology)
- [Data Pipeline & Feature Engineering](#-data-pipeline--feature-engineering)
- [Detailed Results & Findings](#-detailed-results--findings)
  - [1. Sales & Revenue Trends](#1-sales--revenue-trends)
  - [2. Geographic & Logistics Performance](#2-geographic--logistics-performance)
  - [3. Product Category & Catalog Analysis](#3-product-category--catalog-analysis)
  - [4. Customer Segment Dynamics](#4-customer-segment-dynamics)
  - [5. Discount Elasticity & Profit Erosion](#5-discount-elasticity--profit-erosion)
  - [6. Payment Methods & Order Value](#6-payment-methods--order-value)
  - [7. Day-of-Week Purchasing Patterns](#7-day-of-week-purchasing-patterns)
  - [8. Statistical Correlations](#8-statistical-correlations)
- [Key Business Insights](#-key-business-insights)
- [Strategic Recommendations](#-strategic-recommendations)
- [BI Dashboard Implementation Blueprint](#-bi-dashboard-implementation-blueprint)
- [Repository Structure](#-repository-structure)
- [Installation & How to Run](#-installation--how-to-run)

---

## 📌 Executive Summary & Core KPIs

Over the 36-month period analyzed, the global e-commerce business generated **$484,559.34** in gross sales and captured **$158,872.32** in net profit, maintaining a healthy overall profit margin of **32.79%**. However, severe profitability leaks were identified in extreme discounting tiers and regional logistics inefficiencies.

| Metric | Benchmark Value | Description |
| :--- | :--- | :--- |
| **Total Revenue** | **$484,559.34** | Gross transactional sales across all regions |
| **Total Net Profit** | **$158,872.32** | Net earnings after discounts and shipping overhead |
| **Overall Profit Margin** | **32.79%** | Net profit percentage of gross revenue |
| **Total Orders** | **2,000** | Successfully processed customer orders |
| **Unique Customers** | **1,534** | Distinct global buyers across 20 countries |
| **Average Order Value (AOV)** | **$242.28** | Average basket spend per order |
| **Average Discount** | **8.57%** | Mean discount rate applied across catalog |
| **Total Shipping Costs** | **$25,804.24** | Incurred global fulfillment and delivery expenses |
| **Loss-Making Orders** | **272 (13.60%)** | Orders ending in negative net margin due to heavy discounting |

---

## 🛠 Project Architecture & Methodology

```
┌───────────────────────────────┐
│   global_ecommerce_sales.csv  │ ──► 2,000 Transactions (2023–2025)
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│   Data Ingestion & Audit      │ ──► Dtype validation, zero null values,
└───────────────┬───────────────┘     cardinality verification
                │
                ▼
┌───────────────────────────────┐
│     Feature Engineering       │ ──► Temporal decomposition (Year, Month, Quarter, DOW),
└───────────────┬───────────────┘     Profit Margin %, Order Size Bins, Discount Bins
                │
                ▼
┌───────────────────────────────┐
│  Multi-Dimensional Analytics  │ ──► Time Series • Geospatial • Segment × Category
└───────────────┬───────────────┘     Discount Elasticity • Shipping Impact • Correlation
                │
                ▼
┌───────────────────────────────┐
│   Insights & Recommendations  │ ──► Profit optimization, shipping rationalization,
└───────────────────────────────┘     Power BI / Tableau visual schema
```

### Analytical Technologies:
- **Python 3.10+**: Core analysis and transformation engine.
- **Pandas**: High-performance data manipulation, time-series aggregation, and multi-index grouping.
- **NumPy**: Vectorized financial calculations and mathematical masking.
- **Plotly (Express, Graph Objects, Subplots)**: Interactive dual-axis time-series, categorical sunburst/pies, and scatter distributions.
- **Matplotlib & Seaborn**: Statistical distribution plots, correlation heatmaps, and publication-ready multi-variable charts.

---

## ⚙️ Data Pipeline & Feature Engineering

The raw dataset contains 15 base attributes (`Order_ID`, `Order_Date`, `Customer_Name`, `Customer_Segment`, `Country`, `Region`, `Product_Category`, `Product_Name`, `Quantity`, `Unit_Price`, `Discount_Percent`, `Total_Sales`, `Shipping_Cost`, `Profit`, `Payment_Method`). 

The pipeline engineered 9 new operational features:

1. **Temporal Dimensions**:
   - `Year`, `Month`, `Month_Name`, `Quarter`, `Quarter_Label` (`Q1`–`Q4`), `Day_of_Week` (`Monday`–`Sunday`), `Year_Month` (`YYYY-MM` periods).
2. **Financial Ratios**:
   - `Profit_Margin`: $\frac{\text{Profit}}{\text{Total\_Sales}} \times 100$ (computed at transaction level).
3. **Behavioral & Size Binning**:
   - `Order_Size`: Discretized into `Small (<$50)`, `Medium ($50-200)`, `Large ($200-500)`, and `Premium ($500+)`.
   - `Discount_Range`: Segmented into `No Discount (0%)`, `1–10%`, `11–20%`, and `21–35%`.

---

## 📈 Detailed Results & Findings

### 1. Sales & Revenue Trends

Annual revenue and order flow exhibited consistent consistency across the three-year timeline with slight growth acceleration in 2025:

| Year | Revenue ($) | Profit ($) | Orders | Avg Discount (%) | Profit Margin (%) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **2023** | $164,443.45 | $53,153.74 | 670 | 8.67% | 32.32% |
| **2024** | $155,150.73 | $51,616.11 | 649 | 8.65% | 33.27% |
| **2025** | $164,965.16 | $54,102.47 | 681 | 8.40% | 32.80% |

- **Seasonality**: Monthly revenue trends show cyclical Q4 holiday spikes (November–December) averaging 18% higher transaction volumes compared to Q1 troughs.

---

### 2. Geographic & Logistics Performance

The customer base spans 5 major continental regions and 20 countries:

#### Regional Breakdown:
| Region | Revenue ($) | Profit ($) | Orders | Avg Order ($) | Avg Shipping ($) | Profit Margin (%) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Europe** | $137,006.20 | $45,672.16 | 503 | $272.38 | $12.30 | 33.3% |
| **North America** | $133,876.38 | $45,250.09 | 578 | $231.62 | $10.05 | 33.8% |
| **Asia Pacific** | $121,707.51 | $39,116.61 | 520 | $234.05 | $14.48 | 32.1% |
| **South America** | $46,051.13 | $14,680.98 | 191 | $241.11 | $15.44 | 31.9% |
| **Middle East & Africa** | $45,918.12 | $14,152.48 | 208 | $220.76 | $16.00 | 30.8% |

#### Top 10 Countries by Revenue:
| Country | Region | Total Revenue ($) | Total Profit ($) | Orders | AOV ($) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Mexico** | North America | $47,217.30 | $15,949.44 | 203 | $232.60 |
| **Canada** | North America | $45,326.55 | $15,320.95 | 179 | $253.22 |
| **United States** | North America | $41,332.53 | $13,979.70 | 196 | $210.88 |
| **Japan** | Asia Pacific | $30,950.19 | $9,826.31 | 124 | $249.60 |
| **United Kingdom** | Europe | $30,185.46 | $10,185.32 | 106 | $284.77 |
| **Germany** | Europe | $28,989.73 | $9,518.07 | 95 | $305.16 |
| **China** | Asia Pacific | $28,322.85 | $9,028.07 | 109 | $259.84 |
| **Italy** | Europe | $27,484.38 | $9,125.06 | 105 | $261.76 |
| **France** | Europe | $26,616.81 | $8,973.46 | 105 | $253.49 |
| **Australia** | Asia Pacific | $25,287.72 | $8,072.37 | 107 | $236.33 |

- **Logistics Disparity**: Middle East & Africa and South America suffer from substantially higher average shipping costs ($16.00 and $15.44 per order) vs. North America ($10.05), dampening bottom-line margins despite strong demand.

---

### 3. Product Category & Catalog Analysis

| Product Category | Revenue ($) | Revenue Share | Profit ($) | Profit Share | Orders | Avg Unit Price | Margin (%) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Furniture** | $256,274.68 | 52.89% | $81,171.57 | 51.09% | 507 | $151.96 | 31.7% |
| **Technology** | $139,518.22 | 28.79% | $48,268.65 | 30.38% | 567 | $76.82 | 34.6% |
| **Clothing & Accessories**| $69,375.63 | 14.32% | $26,112.94 | 16.44% | 413 | $47.90 | **37.6%** |
| **Office Supplies** | $19,390.81 | 4.00% | $3,319.16 | 2.09% | 513 | $12.24 | **17.1%** |

#### Top 5 Revenue-Generating Products:
1. **Standing Desk Converter** (Furniture): **$46,614.22** revenue | $14,694.35 profit | 215 units
2. **Ergonomic Office Chair** (Furniture): **$45,405.15** revenue | $15,104.58 profit | 167 units
3. **Corner L-Shaped Desk** (Furniture): **$41,070.48** revenue | $13,663.00 profit | 146 units
4. **Mesh Back Task Chair** (Furniture): **$38,179.77** revenue | $12,820.11 profit | 213 units
5. **Wireless Bluetooth Headphones** (Technology): **$28,258.70** revenue | $10,611.08 profit | 212 units

- **Key Takeaway**: While **Furniture** represents over 52% of total turnover, **Clothing & Accessories** achieves the highest profit margin (37.6%). Conversely, **Office Supplies** has high order counts (513 orders) but low basket values ($12.24 unit price) resulting in an anemic margin of only 17.1%.

---

### 4. Customer Segment Dynamics

| Customer Segment | Total Revenue ($) | Total Profit ($) | Orders | AOV ($) | Avg Discount (%) | Margin (%) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Consumer** | $256,287.74 | $87,300.36 | 1,006 | $254.76 | 7.20% | **34.1%** |
| **Corporate** | $146,050.39 | $44,463.44 | 623 | $234.43 | **11.25%** | **30.4%** |
| **Home Office** | $82,221.21 | $27,108.52 | 371 | $221.62 | 7.80% | 33.0% |

- **Segment Analysis**: Consumers represent the backbone of both sales volume (50.3% of orders) and margins (34.1%). Corporate clients receive significantly higher average discounts (11.25% vs 7.20%), yet have a lower AOV ($234.43 vs $254.76), suppressing corporate margins to 30.4%.

---

### 5. Discount Elasticity & Profit Erosion

The analysis revealed a direct, adverse link between high discounting and net profit decay:

| Discount Range | Order Count | Avg Revenue ($) | Avg Profit ($) | Avg Net Margin (%) |
| :--- | :---: | :---: | :---: | :---: |
| **No Discount (0%)** | 503 | $260.37 | $100.81 | **26.42%** |
| **1% – 10%** | 931 | $250.90 | $84.92 | **22.18%** |
| **11% – 20%** | 481 | $210.61 | $53.66 | **11.44%** |
| **21% – 35%** | 85 | $220.01 | $38.79 | **6.94%** |

> ⚠️ **Critical Diagnosis**: **272 orders (13.60% of all transactions)** resulted in a **net negative profit**. Once discounts exceed 15% on bulk or low-unit-price items with standard shipping charges, the variable fulfillment overhead wipes out operating margin entirely.

---

### 6. Payment Methods & Order Value

| Payment Method | Orders | Volume Share (%) | Total Revenue ($) | Avg Order Value ($) |
| :--- | :---: | :---: | :---: | :---: |
| **Credit Card** | 797 | 39.85% | $192,717.89 | $241.80 |
| **PayPal** | 609 | 30.45% | $143,112.87 | $235.00 |
| **Cash on Delivery (COD)** | 301 | 15.05% | $77,129.54 | **$256.24** |
| **Bank Transfer** | 293 | 14.65% | $71,599.04 | $244.37 |

- Digital payments (Credit Card + PayPal) dominate over 70% of transactions. Cash on Delivery presents the highest average ticket size ($256.24), predominantly utilized in developing e-commerce corridors.

---

### 7. Day-of-Week Purchasing Patterns

- Transaction volume is distributed smoothly across all 7 days with minor midweek peaks on **Tuesday** and **Thursday** (accounting for ~31% of weekly transactions).
- Weekend orders (Saturday & Sunday) exhibit slightly higher proportion of **Consumer** category purchases with lower average discount rates.

---

### 8. Statistical Correlations

Key Pearson correlation coefficients extracted:
- **Quantity & Shipping Cost ($r = +0.77$)**: Strong positive relationship; shipping costs are heavily driven by total unit quantity/weight rather than order dollar value.
- **Unit Price & Total Sales ($r = +0.70$)**: Primary predictor of overall order ticket size.
- **Total Sales & Profit ($r = +0.98$)**: Very strong baseline correlation under normal discount conditions.
- **Discount % & Profit Margin ($r = -0.22$)**: Negative correlation indicating significant erosion of margins as promotional discounting escalates.

---

## 💡 Key Insights

1. **The Furniture Paradox**: Furniture drives over half of global revenue ($256.3k) and 4 out of the top 5 individual products, but its heavy shipping weight and moderate margin (31.7%) require tight freight contract management.
2. **Untapped Margin Champion**: Clothing & Accessories yields the highest net margin across the catalog (**37.6%**), yet currently accounts for only 14.3% of total revenue.
3. **Discount Over-Subsidization**: 13.6% of orders are financially underwater. Discounts above 15% do not generate proportional volume uplift to compensate for lost margin.
4. **Corporate Pricing Misalignment**: Corporate accounts receive the steepest discounts (11.25% avg) but produce lower AOV ($234.43) than regular retail Consumers ($254.76).
5. **Emerging Market Logistics Drag**: Customers in MEA and South America face shipping expenses 50% higher than North American counterparts, curtailing net margin to ~30–31%.

---

## 🎯 Strategic Recommendations

### 1. Implement Automated Margin Safeguards (Anti-Loss Guardrails)
- **Minimum Profit Thresholds**: Enforce dynamic promotional rules preventing discounts greater than 15% on items with unit prices below $50 or items requiring bulky freight.
- **Eliminate Negative-Profit Transactions**: Configure the checkout engine to calculate real-time net margin inclusive of freight before coupon redemption.

### 2. Restructure Corporate B2B Tiering
- Transition Corporate accounts from flat discounting to **tiered volume rebate structures**:
  - Minimum order quantity (MOQ) of 10+ units or $1,000+ spend required to qualify for 10%+ discounts.

### 3. Scale High-Margin Product Lines
- Reallocate marketing spend toward **Clothing & Accessories** and **Technology accessories** (e.g., Wireless Headphones, SSDs) where profit margins exceed 35–37%.
- Cross-sell office accessories and clothing bundles during high-ticket furniture checkout.

### 4. Regional Fulfillment Optimization
- Establish local warehouse partnerships or third-party logistics (3PL) nodes in the Middle East and Latin America to compress fulfillment costs from $16.00 down to North American benchmarks (~$10.00).
- Introduce tiered shipping subsidies conditional on order value thresholds (e.g., free shipping on orders >$300).

---

## 📊 BI Dashboard Implementation Blueprint

The findings from this analysis provide the exact specifications required to build production dashboards in **Power BI**, **Tableau**, or **Looker Studio**:

```
┌────────────────────────────────────────────────────────────────────────┐
│  GLOBAL E-COMMERCE EXECUTIVE DASHBOARD                                 │
├────────────────────────────────────────────────────────────────────────┤
│ [KPI: Revenue $484.6k] [KPI: Profit $158.9k] [KPI: Margin 32.8%] [Orders 2k] │
├──────────────────────────────────┬─────────────────────────────────────┤
│  Monthly Revenue & Profit Trend  │   Geographic Sales Map              │
│  (Dual-axis Line & Bar Chart)    │   (Choropleth by Country Revenue)   │
├──────────────────────────────────┼─────────────────────────────────────┤
│  Category Revenue vs Profit Share│   Discount % vs Margin Matrix       │
│  (Donut Charts)                  │   (Scatter Plot with Zero-Line)     │
├──────────────────────────────────┴─────────────────────────────────────┤
│  Slicers: [Year] [Region] [Customer Segment] [Product Category]       │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository Structure

```plaintext
Global-E-Commerce-Sales-Customer-Analytics/
│
├── README.md                                          # Comprehensive project documentation & insights
├── global_ecommerce_sales.csv                         # Raw transactional dataset (2,000 rows × 15 cols)
├── global-e-commerce-sales-customer-analytics.ipynb   # Complete Jupyter Notebook with code & visualizations
└── iframe_figures/                                    # Interactive Plotly figures exported as HTML widgets
```

---

## 🚀 Installation & How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/varshith0810/Global-E-Commerce-Sales-Customer-Analytics.git
cd Global-E-Commerce-Sales-Customer-Analytics
```

### 2. Set Up Virtual Environment
```bash
# Using conda
conda create -n ecommerce-analytics python=3.10 -y
conda activate ecommerce-analytics

# Or using venv
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn plotly nbformat
```

### 4. Launch Jupyter Notebook
```bash
jupyter notebook global-e-commerce-sales-customer-analytics.ipynb
```

---

## 👨‍💻 Author & Acknowledgements

- **Repository**: [Global-E-Commerce-Sales-Customer-Analytics](https://github.com/varshith0810/Global-E-Commerce-Sales-Customer-Analytics)
- **Data Source**: Global E-Commerce Sales & Customer Dataset (2023–2025)
- **Educational Partner**: Notebook walkthrough referencing [Codanics](https://www.youtube.com/channel/UCmNXJXWONLNF6bdftGY0Otw/)