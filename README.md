# Midterm-Project

# More Electricity, Not More Women Working

**Electricity access and female labor force participation in 177 countries, 2000–2024**

ECON 3916 Midterm Project · November 9, 2026

## Question

Do countries where more people have access to electricity have higher female labor force participation?

- **Outcome (Y):** female labor force participation rate (% of women aged 15+)
- **Main explanatory variable (X):** access to electricity (% of population)
- **Controls:** urban population share (%), log GDP per capita (constant PPP international dollars), and country and year dummies

## Main finding

Within the same country, a 10-percentage-point increase in electricity access is associated with about 0.8 percentage points **lower** female labor force participation (coefficient −0.083 per point, 95% CI −0.097 to −0.069, N = 4,389). With robust standard errors, the interval is −0.101 to −0.065. The result stays negative with and without log GDP and after dropping influential observations, but its size ranges from about −0.06 to −0.08. This is a conditional association, not a causal effect. The full explanation is in the report.

## Data

All four variables come from the World Bank's World Development Indicators.

| Variable | Indicator code | Original source | Link |
| Female labor force participation (% of women 15+) | SL.TLF.CACT.FE.ZS | ILO modeled estimates | https://data.worldbank.org/indicator/SL.TLF.CACT.FE.ZS |
| Access to electricity (% of population) | EG.ELC.ACCS.ZS | World Bank | https://data.worldbank.org/indicator/EG.ELC.ACCS.ZS |
| GDP per capita, PPP (constant international $) | NY.GDP.PCAP.PP.KD | World Bank / International Comparison Program | https://data.worldbank.org/indicator/NY.GDP.PCAP.PP.KD |
| Urban population (% of total population) | SP.URB.TOTL.IN.ZS | UN Population Division | https://data.worldbank.org/indicator/SP.URB.TOTL.IN.ZS |

- **Downloaded:** [2026-10-31]
- **Years used:** 2000–2024
- **Unit of observation:** one row is one country-year
- **Full panel:** 5,425 rows (217 countries × 25 years)
- **Final sample:** 4,389 country-years from 177 countries, after dropping rows with any missing value

The country metadata file is used to remove the World Bank's regional and income-group totals (like "Sub-Saharan Africa"), so every row is one country.

## How to run the notebook

1. Open the notebook in Google Colab.
2. In the left sidebar, open the Files panel, create a folder named `data`, and upload the five CSV files from this repository's `data/` folder into it.
3. Click **Runtime › Run all**.

The notebook reshapes each file from wide to long, merges the four files on country code and year, fits the models, and saves every table and figure to an `outputs/` folder. Colab deletes uploaded files when the runtime restarts, so if you get a "file not found" error, upload the data again and rerun.

The last code cell, **"Numbers my report quotes,"** prints every number used in the report.

## What the notebook produces

| File | What it shows | Report location |
| `table1_summary_stats.csv` | Summary statistics for the final sample | Section 1, Table 1 |
| `fig1_distributions.png` | Distributions of female participation and electricity access | Section 2, Figure 1 |
| `fig2_flfp_vs_electricity.png` | Female participation against electricity access | Section 2, Figure 2 |
| `fig3_within_country_changes.png` | Change in electricity vs change in participation within each country | Section 2, Figure 3 |
| `table2_regression.csv` | OLS models with and without log GDP | Appendix Table A1 |
| `tableA1_robust_se.csv` | Usual vs robust standard errors | Appendix Table A2 |
| `tableA2_vif.csv` | Variance inflation factors | Appendix Table A3 |
| `tableA3_influential_obs.csv` | Electricity coefficient after dropping influential observations | Appendix Table A4 |
| `fig4_residuals.png` | Residuals against fitted values and against electricity access | Appendix Figure 4 |
| `paper_numbers.csv` | Key numbers collected while the notebook runs | All sections |

## Main limitations

- **Not causal.** Other changes within a country, like the shift of workers away from farming, could affect both electricity access and female participation.
- **Modeled values.** Many participation values are ILO estimates rather than survey results, and some of the most influential observations look modeled.
- **Missing countries.** Conflict-affected and closed economies with missing GDP are left out, so the results may not apply to them.
- **Not a straight line.** The relationship bends across levels of electricity access, so one coefficient averages a changing pattern.
