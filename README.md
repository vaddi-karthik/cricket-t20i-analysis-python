# 🏏 Cricket T20I Analysis: Country-wise Team and Player Performance

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-green?style=flat&logo=pandas)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup4-scraping-orange?style=flat)
![Matplotlib](https://img.shields.io/badge/Matplotlib-visualization-red?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-visualization-teal?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

---

## 📌 Project Overview

This project performs end-to-end **Web Scraping, Data Cleaning and Exploratory Data Analysis (EDA)** on T20 International (T20I) batting statistics scraped from **ESPN Cricinfo**.

The goal is to analyze player and country-level batting performance to uncover trends, identify top performers and compare nations based on batting quality.

---

## 🎯 Problem Statement

> Analyze T20I batting statistics country-wise and player-wise to identify performance patterns, top performers and trends across 111 countries using data-driven EDA techniques.

---

## 📂 Project Structure

```
Cricket-T20I-Analysis/
│
├── espncricinfo_scraper.py          # Web scraping script
├── T20i_batting_stats.csv           # Raw scraped data
├── T20i_batting_stats_cleaned.csv   # Cleaned data
├── Cricket_T20I_Analysis.ipynb      # Main Jupyter Notebook (EDA)
├── Cricket_T20I_Analysis.pptx       # Project presentation
└── README.md                        # Project documentation
```

---

## 🌐 Data Source

| Detail | Info |
|---|---|
| **Website** | [ESPN Cricinfo](https://stats.espncricinfo.com/ci/engine/stats/index.html?class=11;page=1;template=results;type=batting) |
| **Format** | T20 International (T20I) |
| **Type** | Batting Statistics — Overall Career Figures |

---

## 📊 Dataset

| Feature | Details |
|---|---|
| Raw Rows | 7,800 |
| Clean Rows | 7,646 |
| Columns | 12 |
| Countries | 111 |
| Tools | Python, BeautifulSoup, Requests, Pandas |

### Columns

| Column | Description |
|---|---|
| `Player` | Player name (cleaned) |
| `Country` | Player's home country (extracted) |
| `Span` | Career year range |
| `Matches` | Total matches played |
| `Innings` | Total innings batted |
| `NO` | Not outs |
| `Runs` | Career runs scored |
| `Highest_Score` | Highest individual score |
| `Average` | Batting average |
| `100s` | Number of centuries |
| `50s` | Number of half-centuries |
| `0s` | Number of ducks |

---

## 🔧 Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| BeautifulSoup4 | HTML parsing for web scraping |
| Requests | HTTP requests to fetch web pages |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Regular Expressions | Extracting country codes from player names |
| Jupyter Notebook | Interactive analysis and documentation |

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/your-username/Cricket-T20I-Analysis.git
cd Cricket-T20I-Analysis
```

### 2. Install dependencies
```bash
pip install requests beautifulsoup4 pandas numpy matplotlib seaborn
```

### 3. Run the scraper
```bash
python espncricinfo_scraper.py
```
> This will generate `T20i_batting_stats.csv` (~4 minutes for 40 pages)

### 4. Open the Jupyter Notebook
```bash
jupyter notebook Cricket_T20I_Analysis.ipynb
```
> Run all cells to reproduce the full cleaning and EDA pipeline

---

## 🧹 Data Cleaning Steps

1. **Extracted Country** from Player column using Regex — e.g. `KC Sangakkara (Asia/ICC/SL)` → `SL`
2. **Removed non-country labels** — `ICC`, `Asia`, `Afr`, `World`, numbers `1–5`
3. **Stripped `*`** from Highest Score — 2,322 values had asterisk (not out marker)
4. **Replaced `-` with NaN** — 154 rows had dashes across multiple columns
5. **Renamed columns** — removed special characters (`100's` → `100s`)
6. **Converted data types** — all numeric columns from `object` to `float64`
7. **Dropped non-batting players** — 154 rows where `Innings = NaN`
8. **Filled Average NaN** — 504 values filled with `0` (never got out)

---

## 📈 EDA Highlights

### Univariate Analysis
- Histogram, Box Plot, Violin Plot and KDE Plot on Runs and Average
- Bar Plot and Pie Chart on Country player distribution

### Bivariate Analysis
- **Correlation Heatmap** — Runs & Innings have 0.97 correlation
- **Scatter Plot** — Runs vs Average (Tendulkar, Kohli annotated)
- **Box Plot** — Batting Average by Top 10 Countries
- **Bar Plot** — Mean Average by Country (min. 20 players)
- **Pivot Table** — Country-wise mean Runs, Average, 100s, 50s
- **Crosstab** — % of players with at least 1 century per country

---

## 🔍 Key Findings

| # | Finding |
|---|---|
| 1 | **SR Tendulkar** leads all-time with **34,357 runs** — nearly 6,000 ahead of Kohli |
| 2 | **Runs & Innings** have a correlation of **0.97** — longevity is the biggest factor in run accumulation |
| 3 | **India leads in batting quality** (mean avg 28.4) despite fewer players than England (760 vs 400) |
| 4 | **68% of players** scored fewer than 500 career runs — classic Pareto distribution in sports |
| 5 | **High Average ≠ High Runs** — some players have high averages but low total runs (fewer matches) |
| 6 | T20I cricket spans **111 countries** — the most globally played cricket format |

---

## 📉 Visualizations

| Plot | Variable | Insight |
|---|---|---|
| Histogram | Career Runs | Right-skewed — most players score < 500 runs |
| Box Plot | Runs, Average, Matches | Many upper outliers — elite players |
| Violin Plot | Average | Most players average between 10–30 |
| KDE Plot | Average | Mean > Median — skewed by elite players |
| Bar Plot | Country count | England leads, India selective |
| Pie Chart | Country share | Top 10 = 65% of all players |
| Heatmap | All numeric | Runs–Innings r=0.97 |
| Scatter Plot | Runs vs Average | Elite cluster top-right |
| Bar Plot | Mean avg by country | India #1 in quality |
| Box Plot | Avg by country | India, AUS higher medians |
| Crosstab | Century scorers | India, AUS highest % |
| Bar (horizontal) | Top 10 players | Tendulkar leads clearly |

---

## 💡 Conclusion

1. **Longevity drives run accumulation** — staying in the team longer is the single biggest factor
2. **India punches above its weight** — strict selection produces higher quality per player
3. **T20I is truly global** — 111 countries represented, but quality gap between nations is large
4. **Elite players are rare** — only the top 1% consistently score 10,000+ runs
5. **Both Average and Total Runs** must be considered together for fair player evaluation

---

## 👤 Author

**Karthik Vaddi**
- GitHub: https://github.com/vaddi-karthik
- LinkedIn: https://www.linkedin.com/in/karthik-vaddi-581193268/

---

⭐ If you found this project helpful, please give it a star!
