# Preterm Birth Risk Across U.S. Counties

> **Geospatial Modeling of Preterm Birth Risk Across U.S. Counties: A Health Security Perspective**
> An interactive dashboard companion to a spatial epidemiology analysis benchmarking nine modeling approaches — including Geographically Weighted Regression — against county-level preterm birth data for 2023.

**Live dashboard:** https://tadedoyinsola.github.io/REPO-NAME/
*(replace `REPO-NAME` with the actual repository name)*

---

## Project Overview

This project analyzes the geographic distribution of preterm birth rates across 570 U.S. counties with populations above 100,000, using publicly available data for calendar year 2023. The analysis tests whether the relationships between social determinants of health and preterm birth outcomes exhibit spatial non-stationarity — that is, whether predictor–outcome relationships vary meaningfully across geographic regions.

**Author:** Tolulope Adedoyin Oladeji
**Affiliation:** Digital Epidemiology Laboratory, University of Cincinnati
**Course:** GEOG 5199/6099 — Exploratory Data Analytics with GIS (Spring 2026)

---

## Key Findings

| Metric | Value | Interpretation |
|---|---|---|
| Best-fit model | GWR (R² = 0.665) | Spatial non-stationarity drives predictive gains |
| OLS baseline | R² = 0.443 | 50% improvement by moving to local coefficients |
| Moran's I on OLS residuals | 0.0749 (p < 0.001) | Residuals remain spatially clustered |
| Moran's I on GWR residuals | 0.0057 (p = 0.22) | Approaches spatial independence |
| Autocorrelation reduction | 92.4% | Validates local-coefficient specification |
| Top predictor | % Black Population | Positive coefficient in 100% of counties |

---

## Data Sources

All data are publicly available:

- **Outcome:** CDC WONDER Natality files (2023) — county-level preterm birth counts
- **Predictors:** American Community Survey 1-Year Estimates (2023) — poverty, uninsured rate, educational attainment, median household income, unemployment, demographics
- **Geography:** U.S. Census Bureau 2023 Gazetteer Files — county centroids

**Note:** CDC WONDER suppresses data for counties with populations below 100,000 to protect privacy. The analytic sample is restricted accordingly.

---

## Methodology

The analysis proceeds in three phases:

1. **Module 3 — Initial Analysis:** Data integration, cleaning, descriptive statistics, multicollinearity assessment, and exploratory spatial visualization.
2. **Phase 2 — Machine Learning:** Random Forest, Gradient Boosting, and baseline OLS with train/test evaluation.
3. **Phase 2B — Advanced Modeling:** Hyperparameter-tuned ensembles, deep learning (MLP, deep NN), XGBoost, stacking ensemble, Geographically Weighted Regression (mgwr), and residual spatial autocorrelation diagnostics.

The final GWR specification uses seven predictors (Pct_Poverty, Log_Pct_Uninsured, Pct_Bachelors, Unemployment_Rate, Log_Pct_Black, Median_Age, Log_Population) with a bisquare kernel and adaptive bandwidth (n = 131 nearest neighbors).

---

## Repository Structure

```
.
├── index.html                              # Interactive dashboard (entry point)
├── README.md                               # This file
├── LICENSE                                 # MIT License
├── .gitignore                              # Standard Python/Jupyter exclusions
├── data/
│   ├── preterm_birth_analysis_dataset_transformed.csv   # Cleaned 570-county dataset
│   └── ptb_dashboard_data.csv              # Enriched with model outputs (residuals, GWR coefficients)
└── notebooks/
    ├── Module3_Initial_Analysis_Final.ipynb
    └── Phase2B_Advanced_Modeling_v2.ipynb
```

---

## Reproducing the Analysis

```bash
# 1. Clone the repository
git clone https://github.com/tadedoyinsola/REPO-NAME.git
cd REPO-NAME

# 2. Install dependencies (Python 3.10+ recommended)
pip install pandas numpy scikit-learn xgboost mgwr libpysal esda \
            matplotlib seaborn geopandas shapely jupyter

# 3. Run notebooks in order
jupyter notebook notebooks/Module3_Initial_Analysis_Final.ipynb
jupyter notebook notebooks/Phase2B_Advanced_Modeling_v2.ipynb
```

The dashboard (`index.html`) is self-contained — all data is embedded — and requires no build step.

---

## Citation

If you reference this work, please cite:

> Oladeji, T. A. (2026). *Geospatial Modeling of Preterm Birth Risk Across U.S. Counties: A Health Security Perspective.* Digital Epidemiology Laboratory, University of Cincinnati.

---

## References

- March of Dimes. (2025). *2025 March of Dimes Report Card.* https://www.marchofdimes.org/report-card
- Waitzman, N. J., Jalali, A., & Grosse, S. D. (2021). Preterm birth lifetime costs in the United States in 2016: An update. *Seminars in Perinatology*, 45(3), 151390.
- Centers for Disease Control and Prevention. (2024). *Natality, 2016–2024 expanded.* CDC WONDER Online Database.
- U.S. Census Bureau. (2024). *American Community Survey 1-Year Estimates, 2023.*

---

## License

This project is licensed under the MIT License — see the `LICENSE` file for details. Data is subject to its original source terms (CDC, Census Bureau public-use data).

---

**Contact:** Tolulope Oladeji · [Google Scholar](https://scholar.google.com/citations?user=pPv5YB8AAAAJ&hl=en) · [LinkedIn](https://www.linkedin.com/in/tolulope-oladeji-aa988a192/) · [GitHub](https://github.com/tadedoyinsola)
