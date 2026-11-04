# Golgappa360 — Golgappa Business Intelligence & Sales Analytics System

> **Master of Computer Applications (MCA) Major Capstone Project — Final Submission**  
> **Target Enterprise:** Local Indian Golgappa / Pani Puri Business Operations (*Sharma Ji Golgappa Center*)  
> **Technology Stack:** React 19 + Vite, Tailwind CSS (Dark Glassmorphism), Node.js + Express, MySQL 8.0, Tableau Desktop/Public, Microsoft Excel  
> **Dataset Scope:** 6 Months of Calibrated Operational Data (2026-05-01 to 2026-10-29; 31,938 Orders, ₹17.6L Turnover)

---

## 1. Project Overview

**Golgappa360** is a full-stack, enterprise-grade business intelligence and analytics system designed to transition Indian street-food operations from intuition-driven habits to structured, data-driven decision making.

The system tracks:
1. **Sales & Gross Revenue:** Real-time turnover, plate counts, commuter rush hours (3:00 PM – 10:00 PM), and digital payment adoption (UPI QR vs. Cash).
2. **Menu Engineering & BOM Costing:** Recipe Bill of Materials (BOM) cost per plate, unit contribution margins, and variety popularity rankings.
3. **Food Waste & Spoilage Auditing:** Root causes of shrinkage (puri transit breakage, afternoon pani souring, fermented boiled potato mash) with data-driven prevention guidelines.
4. **Inventory Control & Stock Runway:** Ingredient ledger tracking purchases, recipe consumption, and spoilage with automated reorder threshold alerts.
5. **Full Executive P&L:** Net turnover, ingredient COGS, stall overhead vouchers (rent, packaging, gas, electricity, sanitation), and estimated operating profit.

---

## 2. Key Features

- **Responsive Dark Glassmorphism SaaS Interface:** Charcoal canvas (`#171717`), translucent glass cards (`rgba(48, 48, 50, 0.88)`), subtle background blur, sage-green profitability highlights (`#A7D78A`), and saffron accents (`#EAB64B`).
- **Seven Core Dashboard Views:**
  1. *Business Overview:* Executive KPI ribbon, daily revenue velocity area chart with 7-day MA, hourly profile, and quick restock/waste modals.
  2. *Sales Analytics:* Multi-period granularity toggle (Daily / Weekly / Monthly), commuter rush heatmap matrix, and tender breakdown.
  3. *Products & Margins:* Recipe costing breakdowns, unit margins, and dynamic variety additions.
  4. *Inventory Control:* Live stock balances, days of runway, minimum safety thresholds, and restock logging.
  5. *Food Waste Analysis:* Spoilage cost tracking, high-waste anomaly days, and data-driven recommendations.
  6. *Reports & BI Hub:* Direct downloads for 6 star-schema Tableau CSV exports and 30 production SQL queries.
  7. *System Configuration & Settings:* Stall profile, target margin benchmarks, and database connectivity diagnostics.
- **Dual-Engine Architecture:** High-performance MySQL 8.0 connection pool with automatic, zero-crash fallback to an in-memory synthetic analytics engine.
- **Unified Accounting Standards ($₹0.00$ Variance):**
  - $\text{Net Revenue} = \text{Gross Sales} - \text{Discounts}$
  - $\text{COGS} = \sum(\text{Quantity Plates} \times \text{Ingredient BOM Cost})$
  - $\text{Gross Profit} = \text{Net Revenue} - \text{COGS}$
  - $\text{Gross Margin \%} = (\text{Gross Profit} \div \text{Net Revenue}) \times 100$
  - $\text{Operating Profit} = \text{Gross Profit} - \text{Operating Expenses}$
- **Tableau & Excel BI Deliverables:** Six verified RFC 4180 CSV datasets, calculated-field formulas, and dark glassmorphism dashboard build guides.

---

## 3. Technology Stack

| Layer | Technologies Used | Version |
|:---|:---|:---:|
| **Frontend Framework** | React (Hooks, Context, Functional Components) | 19.0.0 |
| **Build Tool & Bundler** | Vite (Rollup production bundling) | 8.3.0 |
| **Styling & Icons** | Tailwind CSS v4, Lucide React Icons | 4.0.0 / 1.16 |
| **Data Visualization** | Recharts (ResponsiveContainer, AreaChart, BarChart, LineChart, PieChart) | 2.15.0 |
| **Backend Runtime** | Node.js (ES Modules) | v24.14.0 (18+ compatible) |
| **API Framework** | Express.js (CORS, JSON Body Parser, Validation Middleware) | 4.21.0 |
| **Relational Database** | MySQL Server 8.0+ (InnoDB Engine) via `mysql2/promise` | 8.0.x / 3.12 |
| **Business Intelligence** | Tableau Desktop / Tableau Public (Logical Relationships) | 2020.2+ |
| **Spreadsheet Modeling** | Microsoft Excel (Power Query UTF-8, Pivot Tables, SUMIFS, XLOOKUP) | 2016 / 2019 / 365 |

---

## 4. Repository Folder Structure

```
d:/antigravty/
├── data/
│   ├── synthetic/                  # Calibrated 6-month synthetic source CSVs
│   │   ├── sales.csv               # 31,938 order transactions
│   │   ├── products.csv            # 5 product varieties & BOM costs
│   │   ├── ingredients.csv         # 8 raw materials & safety thresholds
│   │   ├── inventory_transactions.csv # 2,391 stock movements
│   │   └── daily_expenses.csv      # 845 stall overhead vouchers
│   └── tableau/                    # Duplicate verified Tableau CSVs
├── dist/                           # Vite production build output
├── docs/                           # Official MCA Capstone Documentation
│   ├── project_report.md           # Comprehensive MCA major project report
│   ├── system_architecture.md      # Multi-tier dual-engine architecture guide
│   ├── database_design.md          # 3NF relational schema & view materializations
│   ├── data_dictionary.md          # Semantic catalog & attribute dictionary
│   ├── testing_report.md           # 70-check QA & reconciliation test report
│   ├── user_manual.md              # Operator user manual & module walkthrough
│   ├── viva_questions.md           # 25+ viva voce questions with model answers
│   └── presentation_outline.md     # 12-slide presentation structure
├── server/
│   ├── sql/
│   │   ├── schema.sql              # Normalized 3NF DDL (6 tables + 4 views)
│   │   ├── seed.sql                # Complete standalone SQL seed script
│   │   └── analytics_queries.sql   # 30 pedagogical queries across 20 categories
│   ├── src/
│   │   ├── config/db.js            # mysql2 connection pool & fallback manager
│   │   ├── controllers/            # Route controllers (dashboard, sales, products...)
│   │   ├── data/syntheticStore.js  # High-fidelity in-memory analytical store
│   │   ├── middleware/             # validateQuery.js & errorHandler.js
│   │   ├── routes/                 # Express REST routers & Tableau export stream
│   │   ├── scripts/                # ETL importData.js & exportTableauData.js
│   │   ├── services/               # Centralized AnalyticsService.js
│   │   ├── app.js                  # Express application setup & middleware
│   │   └── index.js                # Port 5000 bootstrap runner
│   ├── .env.example                # Safe database credential template
│   ├── test_phase3_endpoints.js    # 19-route API regression suite
│   └── test_phase5_qa_suite.js     # 51-check QA, calculation & boundary test suite
├── src/
│   ├── golgappa/
│   │   ├── analytics/              # golgappaAnalytics.js pure calculation core
│   │   ├── components/             # GlassCard, StatCard, Badge, Modal, Layout
│   │   ├── context/                # GolgappaContext.jsx state & hash-router sync
│   │   ├── pages/                  # 7 responsive glassmorphism dashboard views
│   │   ├── services/api.js         # Frontend fetch client & export links
│   │   └── GolgappaApp.jsx         # Application router
│   ├── App.jsx                     # Root application entrypoint
│   └── main.jsx                    # React 19 DOM root
├── tableau/
│   ├── exports/                    # Certified RFC 4180 Tableau CSV datasets
│   │   ├── tableau_sales.csv       # Primary sales fact table (31,938 rows)
│   │   ├── tableau_products.csv    # Menu catalog dimension (5 rows)
│   │   ├── tableau_inventory.csv   # Inventory & waste fact table (2,391 rows)
│   │   ├── tableau_daily_summary.csv # Aggregated P&L fact table (182 rows)
│   │   ├── tableau_expenses.csv    # Overhead expense fact table (845 rows)
│   │   └── tableau_data_dictionary.csv # Semantic attribute catalog (54 rows)
│   ├── calculated_fields.md        # 18 copy-ready Tableau formulas
│   ├── dashboard_build_guide.md    # 4 glassmorphism dashboards build guide
│   ├── data_model_guide.md         # Logical Relationships & fan-trap avoidance
│   ├── excel_workflow_guide.md     # Power Query, Pivot Tables & SUMIFS guide
│   ├── export_validation_report.md # Zero-variance audit sign-off
│   └── validate_tableau_exports.js # Automated 15-metric reconciliation script
├── package.json                    # Project dependencies & scripts
├── vite.config.js                  # Vite configuration
└── README.md                       # This document
```

---

## 5. Prerequisites & Environment Setup

### Prerequisites
- **Node.js:** v18.0.0 or higher (Tested and certified on Node v24.14.0).
- **npm:** v9.0.0 or higher.
- **MySQL Server (Optional):** Version 8.0+ (if uninstalled or credentials are omitted, the backend runs in resilient synthetic fallback mode).

### Environment Configuration
1. The backend template is located at `server/.env.example`.
2. To connect to a local MySQL instance:
   ```bash
   cp server/.env.example server/.env
   ```
3. Edit `server/.env` with your local credentials:
   ```env
   PORT=5000
   DB_HOST=localhost
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=your_mysql_password
   DB_NAME=golgappa360
   ```
*(Note: If MySQL is unavailable, no `.env` file is required; the server boots in synthetic fallback mode).*

---

## 6. Installation & Execution Runbook

### Step 1: Install Dependencies
From the repository root directory:
```bash
# Install frontend dependencies
npm install

# Install backend dependencies
cd server
npm install
cd ..
```

### Step 2: Database Initialization & Seeding (MySQL Mode)
If using MySQL:
```bash
# Method A: Automated ETL script (creates tables, seeds data, builds seed.sql)
node server/src/scripts/importData.js

# Method B: Direct MySQL CLI
mysql -u root -p < server/sql/schema.sql
mysql -u root -p golgappa360 < server/sql/seed.sql
```

### Step 3: Generate Tableau-Ready CSV Exports
```bash
node server/src/scripts/exportTableauData.js
```
*Outputs 6 verified CSV files to `tableau/exports/` and `data/tableau/`.*

### Step 4: Run the Backend API Server
```bash
node server/src/index.js
```
*Server starts on `http://localhost:5000`.*  
*Health Check: `http://localhost:5000/api/health`.*

### Step 5: Run the Frontend Application
In a separate terminal:
```bash
npm run dev
```
*Vite launches the dashboard on `http://localhost:5173`.*

---

## 7. Testing & Verification Runbook

### 1. Run the Comprehensive Phase 5 QA Suite
```bash
node server/test_phase5_qa_suite.js
```
*Verifies 51 test cases covering analytics calculations, zero-denominator guardrails, empty datasets, date boundaries, and live API endpoints.*

### 2. Run the Tableau Data Reconciliation Audit
```bash
node tableau/validate_tableau_exports.js
```
*Checks cross-file arithmetic parity across all 15 financial metrics ($₹0.00$ variance).*

### 3. Run the Phase 3 REST API Regression Suite
```bash
node server/test_phase3_endpoints.js
```
*Verifies 19 canonical API endpoints, input validation rejections, and CSV streaming.*

### 4. Build the Production Frontend
```bash
npm run build
```
*Compiles 2,471 modules into production assets with 0 Rollup/JSX errors.*

---

## 8. Financial Reconciliation Benchmark (Ground Truth)

| Financial Metric | Verified Value | Calculation Definition |
|:---|:---:|:---|
| **Operational Period** | 182 days | 2026-05-01 through 2026-10-29 |
| **Sales Orders Count** | 31,938 | Total unique order transactions |
| **Plates Sold Volume** | 47,658 plates | Total portions served |
| **Gross Sales Turnover** | ₹1,765,505.00 | $\sum(\text{plates} \times \text{unit price})$ |
| **Promotional Discounts** | ₹5,540.00 | Direct invoice discounts |
| **Net Collected Revenue** | ₹1,759,965.00 | Gross Turnover − Discounts |
| **Cost of Goods Sold (COGS)** | ₹492,957.90 | $\sum(\text{plates} \times \text{ingredient BOM cost})$ |
| **Gross Profit** | ₹1,267,007.10 | Net Revenue − COGS |
| **Gross Margin %** | 71.99% (72.0%) | Gross Profit ÷ Net Revenue |
| **Total Operating Expenses** | ₹126,540.06 | Stall rent, packaging, gas, electricity, sanitation |
| **Food Waste Cost Loss** | ₹11,626.98 | Crushed puris, sour pani, and fermented curd |
| **Estimated Operating Profit** | ₹1,140,467.04 | Gross Profit − Operating Expenses |
| **Operating Margin %** | 64.80% | Operating Profit ÷ Net Revenue |
| **Average Order Value (AOV)** | ₹55.11 | Net Revenue ÷ Orders Count |
| **Average Selling Price (ASP)** | ₹36.93 | Net Revenue ÷ Plates Sold |

---

## 9. Tableau & Excel Workflows

### Tableau Desktop / Public Ingestion
1. Open Tableau Desktop or Tableau Public.
2. Under **Connect > To a File**, choose **Text file** and select `tableau/exports/tableau_sales.csv`.
3. Drag `tableau_products.csv` to establish a **Logical Relationship ("The Noodle")** on `[product_id]`.
4. Drag `tableau_daily_summary.csv` to connect on `[sale_date]`.
5. Open any worksheet and use the formulas documented in `tableau/calculated_fields.md`.
6. Refer to `tableau/dashboard_build_guide.md` for complete build instructions for the 4 dashboards.

### Microsoft Excel Analysis
1. Open Excel and navigate to **Data > Get Data > From Text/CSV**.
2. Select `tableau/exports/tableau_sales.csv` with **Encoding: 65001: UTF-8**.
3. Create Pivot Tables for Monthly variety turnover, hourly footfall heatmaps, and payment tender splits.
4. Verify totals using `=SUMIFS(tableau_sales[net_revenue], tableau_sales[product_name], "Classic Golgappa")`.

---

## 10. Known Limitations

1. **Synthetic Dataset Calibration:** While calibrated to match real-world Delhi NCR chaat stall metrics, the dataset is synthetically generated for reproducible academic evaluation.
2. **Local MySQL Password:** Local MySQL authentication requires user-configured passwords; when unconfigured, the application runs via the built-in synthetic engine.
3. **Tableau Workbook Notice:** Because Tableau Desktop is not pre-installed in the local execution sandbox, verified RFC 4180 CSV exports and a complete manual build guide are provided rather than a fabricated `.twb` file.
