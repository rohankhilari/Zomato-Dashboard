
# Zomato Dashboard

**Interactive Power BI dashboard analysing Zomato restaurant and order data**

> A polished, resume-ready dashboard built in Power BI that visualizes restaurants, orders, revenue, ratings and cuisine trends across locations. This repository contains the Power BI (.pbix) file, exported assets (screenshots / PDF) and instructions to reproduce or host the report for a portfolio or GitHub resume.

---

## Table of Contents

* [About](#about)
* [Key Features](#key-features)
* [What you'll find in this repo](#what-youll-find-in-this-repo)
* [Data & Data Model](#data--data-model)
* [Important visuals & pages](#important-visuals--pages)
* [How to view / share the dashboard](#how-to-view--share-the-dashboard)
* [Run locally / Open the PBIX](#run-locally--open-the-pbix)
* [Exporting static assets (PDF / PNG)](#exporting-static-assets-pdf--png)
* [Tips for adding to your portfolio / resume](#tips-for-adding-to-your-portfolio--resume)
* [Contributing](#contributing)
* [License & Contact](#license--contact)

---

## About

This Power BI dashboard provides an end-to-end view of a Zomato-style dataset (orders, restaurants, cuisines, customers, locations, timestamps and ratings). It is designed for analysis, storytelling, and demonstrating core BI skills: data cleaning & transformation, modeling, DAX measures, and interactive reporting optimized for insights.

> **Note:** Replace any placeholder dataset names or file paths with your actual dataset details before publishing.

---

## Key Features

* High-level KPIs: Total Orders, Total Revenue, Average Order Value, Average Rating, Active Restaurants.
* Time series analysis (orders / revenue over time) with date slicers and drill-down.
* Geographic view showing hotspots by city or area.
* Cuisine and category trend analysis (top cuisines, share of revenue by cuisine).
* Rating & review sentiment (summary statistics, distribution visuals).
* Interactive filters & cross-highlighting (city, cuisine, rating, time range).
* Bookmarked views for quick storytelling and screenshots for portfolio.

---

## What you'll find in this repo

* `Zomato_dashboard.pbix` — Power BI Desktop file (main project).
* `/assets/screenshots/` — exported screenshots used for the README / portfolio.
* `/assets/demo.gif` — optional short GIF showing interactivity (recommended for your GitHub README).
* `README.md` — this file.

---

## Data & Data Model

The dashboard expects a dataset with these core tables (rename / adapt fields as needed):

* **Orders** (order_id, order_date, restaurant_id, customer_id, total_amount, items, rating)
* **Restaurants** (restaurant_id, name, city, area, cuisine_type, opening_date)
* **Customers** (customer_id, city, signup_date)
* **Lookup / Calendar** (date, year, month, day, is_weekend)

**Transformations / Power Query**

* Standardize datetime fields, split compound columns (items), remove duplicates, fill missing values.
* Create a proper Date dimension and mark relationships (one-to-many: Date -> Orders, Restaurants -> Orders).

**DAX measures (examples)**

* `Total Orders = COUNTROWS(Orders)`
* `Total Revenue = SUM(Orders[total_amount])`
* `Average Rating = AVERAGE(Orders[rating])`
* `Orders YoY % = DIVIDE([Total Orders] - CALCULATE([Total Orders], SAMEPERIODLASTYEAR('Date'[Date])), CALCULATE([Total Orders], SAMEPERIODLASTYEAR('Date'[Date])))`

---

## Important visuals & pages

* **Overview / Executive Summary:** KPI cards, revenue trend, order trend, map.
* **Location Analysis:** choropleth / filled map, city ranking, busiest zones.
* **Cuisine & Menu:** bar charts of top cuisines, revenue share by cuisine.
* **Ratings & Feedback:** histogram or violin of ratings, top-rated restaurants.
* **Operations:** hourly order heatmap, cancellation or failure rates (if available).

---

## How to view / share the dashboard

Because GitHub's Markdown does not support embedding interactive Power BI iframes directly in a README, common approaches are:

1. **Publish interactive report via Power BI Service (Publish to web)** and share the public/embed link or host it in GitHub Pages using an iframe (recommended for portfolio sites). *See Microsoft docs on Publish to web for details.*
2. **Include exported static assets** (PNG / PDF / GIF) in your README for GitHub viewers who cannot access the live report.
3. **Use Power BI Embedded or an application** (React / Flask) to securely embed interactive reports for authenticated viewers.

(Technical references and step-by-step guides are provided in the project notes.)

---

## Run locally / Open the PBIX

1. Clone this repo.
2. Open `Zomato_dashboard.pbix` in Power BI Desktop (download from: [https://powerbi.microsoft.com/](https://powerbi.microsoft.com/)).
3. If the file references external data sources, place the source files in the same relative paths or update the Power Query connections.
4. Refresh data and verify measures and relationships.

---

## Exporting static assets (PDF / PNG)

To add visuals to your GitHub README, export report pages as PNG or PDF from Power BI Desktop (File → Export → Export to PDF). Use these images inside `/assets/screenshots/` and reference them in this README. This creates a reliable, shareable snapshot for recruiters and viewers.

---

## Tips for adding to your portfolio / resume

* Add a short animated GIF (`/assets/demo.gif`) that shows slicer interaction or a drilldown — it makes your GitHub project stand out.
* In your resume or LinkedIn, link to the GitHub repo and to a published interactive report (if allowed by your Power BI tenant).
* In the README, include a short summary of technical skills demonstrated (Power Query, DAX, data modelling, mapping visuals).

---

## Contributing

If you'd like to contribute (fix typos, add screenshots or sample data), please open a PR. If you want to license the dataset or include sample data, include a small, anonymized sample CSV in `/data/`.

---

## License & Contact

* **License:** Add a LICENSE file (e.g., MIT) if you want this project public and reusable.
* **Contact:** Replace with your email or GitHub handle.

---

> *This README is designed to be resume-friendly and to follow best practices for sharing Power BI projects on GitHub. Update the placeholders (dataset name, contact, demo links) before publishing.*
