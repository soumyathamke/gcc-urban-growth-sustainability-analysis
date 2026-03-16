# Urban Growth & Sustainability Assessment — GCC Countries

## Overview

This project analyses urban growth trends and sustainability performance across 6 GCC countries (UAE, Saudi Arabia, Qatar, Kuwait, Bahrain, Oman) using real-world data covering 2000–2022. Linear regression models project urbanisation trajectories to 2040, and a composite sustainability index ranks countries by climate and urban risk.

**Tools:** Python (Pandas, Matplotlib, Seaborn, Scikit-learn)  
**Data:** Kaggle — Global Urbanization & Climate Metrics dataset  
**Period:** 2000–2022 | **Countries:** 6 GCC nations | **Observations:** 138 rows

---

## Key Findings

### 1. Urban Growth
- All 6 GCC countries exceed 75% urbanisation — Kuwait and Qatar are near-fully urbanised (>98%)
- Linear regression models (R² up to 1.000) project most GCC countries will reach 99–100% urbanisation by 2040
- UAE and Saudi Arabia show the steepest urban growth trajectories over 2000–2022

### 2. Carbon Emissions
- Qatar is the most carbon-intensive country — consistently above the 20 t/cap SDG threshold
- Oman is the only GCC country near or below the SDG threshold
- CO₂ emissions remain a critical breach point for most GCC nations

### 3. Renewables Gap
- Renewable energy share is critically low across GCC — most countries sit near 0–1%
- This is the single biggest sustainability gap in the region
- UAE is beginning to close the gap through solar investments

### 4. Composite Sustainability Index
- Index built from 3 components: renewable energy (40%), sanitation access (35%), CO₂ (25%)
- Oman and Bahrain score highest; Qatar and Kuwait score lowest due to high emissions and low renewables

## Methodology

### Data Cleaning
- Filtered global dataset to 6 GCC countries, years 2000–2022
- Renamed columns for readability
- Computed GDP per capita from raw GDP and population columns
- Verified 0% nulls in all key columns after filtering

### Composite Sustainability Index
Built from 3 normalised indicators (0–100 scale):
| Component | Weight | Direction |
|---|---|---|
| Renewable energy share (%) | 40% | Higher = better |
| Sanitation access (%) | 35% | Higher = better |
| CO₂ per capita (tonnes) | 25% | Lower = better (inverted) |

### Linear Regression — 2040 Projections
- Fitted a `LinearRegression` model (Scikit-learn) per country on `year → urban_pct`
- R² ranges from 0.147 (Kuwait — near-plateau) to 1.000 (Saudi Arabia — near-linear trend)
- Projections clipped at 100% (urbanisation cannot exceed 100%)

### Sustainability Threshold Stress-Test
Five SDG-aligned thresholds checked against each country's latest available data:
| Indicator | Threshold | Breach if |
|---|---|---|
| CO₂ per capita | < 20 t/cap | Above |
| Sanitation access | ≥ 95% | Below |
| Electricity access | ≥ 99% | Below |
| Renewable energy | ≥ 10% | Below |
| Sustainability Index | ≥ 50 | Below |

---

## Data Source

**Dataset:** Global Urbanization & Climate Metrics  
**Platform:** Kaggle  
**Indicators used:**
- `urban_pop_perc` — Urban population (% of total)
- `co2_emiss_excl_lulucf` — CO₂ emissions per capita (tonnes)
- `elect_access_pop` — Access to electricity (% of population)
- `basic_sanitation_pop` — Access to basic sanitation (% of population)
- `ren_energy_cons_perc` — Renewable energy consumption (% of total)
- `gdp` — GDP (USD)
- `total_pop` — Total population
