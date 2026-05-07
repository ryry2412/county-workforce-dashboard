# U.S. County Workforce Snapshot — 2024
### Interactive Tableau Dashboard | BLS Labor Market Analysis

🔗 **[View Live Dashboard on Tableau Public](https://public.tableau.com/views/county_workforce_2024/Dashboard1)**

---

## Project Overview

This project presents an interactive Tableau Public dashboard analyzing U.S. labor market conditions at the county level using 2024 data from the Bureau of Labor Statistics (BLS) Quarterly Census of Employment & Wages (QCEW).

The dashboard is designed to answer a core business question relevant to any multinational organization managing or evaluating U.S. operations:

> *"Where is the U.S. workforce concentrated, which regions command premium wages, and how do labor costs compare across states?"*

This type of regional workforce intelligence supports talent strategy, site selection, compensation benchmarking, and market entry decisions.

---

## Live Dashboard

[![Dashboard Preview](https://public.tableau.com/thumb/views/county_workforce_2024/Dashboard1)](https://public.tableau.com/views/county_workforce_2024/Dashboard1)

---

## Dashboard Views

### 1. County Wage Heat Map
A filled choropleth map of all ~3,200 U.S. counties, color-encoded by average weekly wage. Color scale anchored between $500–$2,000 to maximize regional contrast and reveal true geographic wage variation.

**Key insight:** High-wage counties cluster around coastal metros (New York, San Francisco, Seattle, Boston) and isolated energy/tech hubs inland — while the rural South and Midwest show consistently lower compensation.

### 2. Average Weekly Wage by State
Ranked horizontal bar chart showing all 50 states by average weekly wage, colored by average employment level. Identifies which states combine high wages with large workforces — a critical signal for talent market competitiveness.

**Key insight:** Connecticut, Massachusetts, and New Jersey lead on weekly wages among states — driven by finance, biotech, and professional services concentration in the Northeast corridor.

### 3. Average Annual Pay by State
Ranked bar chart showing total annual compensation by state, colored by employment density. Provides a complementary annual view to weekly wages, useful for full compensation benchmarking.

**Key insight:** Annual pay rankings closely mirror weekly wage rankings, with the Northeast and Pacific Coast states consistently outpacing the national average.

---

## Data Source & Preparation

**Source:** [BLS Quarterly Census of Employment & Wages (QCEW)](https://www.bls.gov/cew/) — 2024 Annual Data  
**Coverage:** All U.S. counties, all industries combined (NAICS code 10, ownership code 0)  
**Raw rows:** ~19,300 | **Clean rows after filtering:** 3,245 counties

### Data Preparation Steps

The raw BLS file required several real-world data quality fixes before visualization:

1. **Ownership code filtering** — Raw file contained multiple ownership categories (federal, state, local, private). Filtered to `own_code = 0` (Total, All Ownerships) to avoid double-counting employment figures.

2. **FIPS code padding** — County FIPS codes are standardized 5-digit identifiers. Excel/Sheets stripped leading zeros from counties in states 01–09, converting valid codes like `01001` to `1001`. Fixed using `TEXT(A2,"00000")` to restore zero-padding before geographic mapping.

3. **State name lookup** — BLS FIPS codes are non-sequential (gaps exist at 03, 07, 11, 14, etc.) making alphabetical CHOOSE formulas unreliable. Built a manual FIPS-to-state lookup table with correct code-to-name mappings, then used VLOOKUP with `LEFT(TEXT(fips,"00000"),2)` to extract the state prefix and return accurate state names.

4. **Geographic role assignment** — Configured `area_fips` as a County geographic role in Tableau and added supporting fields (`state_name`, `avg_annual_pay`, `annual_avg_estabs`) to the Detail shelf to enable full tooltip functionality.

5. **Color scale calibration** — Initial map rendered with low contrast due to extreme outliers skewing the gradient. Applied a manual range ($500–$2,000) to anchor the color scale where 90%+ of counties fall, dramatically improving regional differentiation.

---

## Tools & Skills Demonstrated

| Category | Details |
|---|---|
| **Visualization** | Tableau Public — choropleth map, ranked bar charts, dashboard assembly |
| **Data Sourcing** | BLS QCEW government data — real, authoritative, production-quality source |
| **Data Preparation** | Google Sheets — FIPS padding, ownership filtering, VLOOKUP state mapping |
| **Dashboard Design** | Multi-view layout, color palette selection, tooltip customization, legend positioning |
| **Business Storytelling** | Framed analysis around a real business question relevant to workforce strategy |
| **Domain Knowledge** | U.S. labor market structure, FIPS geography, BLS data conventions |

---

## Key Findings

- **Northeast dominates wage rankings** — CT, MA, NJ, and NY consistently lead on both weekly and annual pay metrics, reflecting high concentrations of finance, tech, and professional services.
- **Geographic wage inequality is significant** — The gap between the highest-wage counties (urban coastal) and lowest-wage counties (rural South/Midwest) exceeds 4x on average weekly wage.
- **Large states ≠ highest wages** — California and New York rank high on employment volume but fall behind smaller Northeastern states on per-worker wage metrics, reflecting internal variation between metro and rural counties.
- **Energy sector drives inland wage spikes** — Several isolated high-wage counties in Wyoming, North Dakota, and West Texas reflect oil, gas, and mining sector concentration rather than broad regional prosperity.

---

## Repository Structure

```
county-workforce-dashboard/
│
├── data/
│   └── county_workforce_2024.csv       # Cleaned BLS QCEW data (3,245 rows)
│
├── README.md                           # This file
```

---

## Related Portfolio Projects

| Project | Skills | Link |
|---|---|---|
| SQL Data Exploration | SQL, PostgreSQL, data querying | [github.com/ryry2412/retail-ecommerce-sql](https://github.com/ryry2412/retail-ecommerce-sql) |
| Python EDA + A/B Test | Python, Pandas, statistical analysis | [github.com/ryry2412/bank-marketing-eda-ab-test](https://github.com/ryry2412/bank-marketing-eda-ab-test) |
| Data Cleaning Pipeline | Python, data wrangling, Pandas | [github.com/ryry2412/nyc-311-cleaning](https://github.com/ryry2412/nyc-311-cleaning) |

---

## About

**Riley Allen** | Data Analyst  
📧 rileyallen2412@gmail.com | 📍 Columbus, OH  
🔗 [LinkedIn](https://linkedin.com/in/rileyallen2412) | 🐙 [GitHub](https://github.com/ryry2412)
