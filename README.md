# Comparing SARIMA and SVR for Inflation Rate Forecasting in Bandar Lampung (2006–2025)

---

This project compares the performance of SARIMA and SVR in forecasting the monthly inflation rate of Bandar Lampung City using data from BPS Lampung Province spanning January 2006 to December 2025. SARIMA is a classical statistical model built for seasonal time series, while SVR is a machine learning approach capable of handling non-linear patterns. Both models are evaluated using RMSE and SMAPE to determine which method produces more accurate forecasts for this dataset.

---

## Dataset

| | |
|---|---|
| **Source** | [BPS Provinsi Lampung](https://lampung.bps.go.id/en/statistics-table/2/MSMy/laju-inflasi-kota-bandar-lampung.html) |
| **Period** | January 2006 – December 2025 |
| **Total** | 240 monthly records |

> Data was downloaded year-by-year from BPS and merged programmatically — the integration process is documented in the notebook.

---

## Workflow

```
Data Integration → Preprocessing → EDA → Stationarity Test
→ SARIMA Modeling → SVR Modeling → Evaluation & Comparison
```

---

## Forecast Results

![Comparison Plot](images/comparison_plot.png)

---

## Evaluation

| Metric | SARIMA | SVR |
|--------|--------|-----|
| RMSE | 0.5905 | **0.5146** ✅ |
| SMAPE | 118.10% | **103.43%** ✅ |

**SVR wins on both metrics.**

> *Note: SMAPE is used instead of standard MAPE because the inflation data contains near-zero and negative values (deflation), which cause MAPE to produce unreliably large numbers.*

---

## Key Takeaways

- Bandar Lampung's inflation has a clear **12-month seasonal pattern** — prices tend to spike around Ramadan/Eid and dip after holiday seasons.
- **SARIMA** is stable and interpretable, but too smooth — it misses extreme spikes and deflation events.
- **SVR** adapts better to the non-linear and volatile nature of inflation data.
- Both models still struggle with near-zero values — a known limitation of univariate forecasting on highly volatile data.

---

## Repository Structure

```
├── sarima_svr_inflation_bandar_lampung.ipynb   # Main notebook
├── inflation_bandar_lampung_2006_2025.csv      # Merged dataset
├── images/                                     # All plots
└── README.md
```

---

## Tech Stack

`Python` `pandas` `numpy` `matplotlib` `seaborn` `statsmodels` `pmdarima` `scikit-learn`

---

