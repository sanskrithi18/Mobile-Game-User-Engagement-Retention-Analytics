# Mobile-Game-User-Engagement-Retention-Analytics

A/B test analysis of the **Cookie Cats** mobile game, evaluating whether moving the first progression gate from **Level 30 to Level 40** improves player engagement and retention.

**Tools:** Python (Pandas, Matplotlib), SQL (SQLite), Power BI, Statistical Testing (Chi-square)

---

## Business Question

> Does moving the progression gate from Level 30 to Level 40 improve player engagement and retention — and what should the product team do?

Players were randomly assigned to one of two experiment groups:
- **gate_30** — gate placed at level 30 (control)
- **gate_40** — gate placed at level 40 (treatment)

---

## Dataset

- **90,189** total players
  - 44,700 in gate_30
  - 45,489 in gate_40
- **5 columns:** `userid`, `version`, `sum_gamerounds`, `retention_1`, `retention_7`
- No missing values, no duplicate rows
- Loaded into a SQLite database (`mobile_game.db`) for SQL-based analysis

---

## Methodology

1. **Exploratory Data Analysis** — Pandas (shape, nulls, duplicates, group counts)
2. **SQL Analysis** — SQLite queries for player counts, average game rounds, retention rates, and engagement segments by group
3. **Visualization** — Matplotlib charts comparing groups; Power BI dashboard for interactive exploration
4. **Statistical Testing** — Chi-square tests to determine whether observed retention differences are statistically significant
5. **Business Recommendation** — Translating findings into a product decision

---

## Key Results

### Overview

| Metric | Gate 30 | Gate 40 |
|---|---|---|
| Players | 44,700 | 45,489 |
| Avg. Game Rounds | 52.46 | 51.30 |
| Day-1 Retention | 44.82% | 44.23% |
| Day-7 Retention | 19.02% | 18.20% |

### Engagement Segments

| Segment | Gate 30 | Gate 40 |
|---|---|---|
| Low | 17,673 | 18,316 |
| Medium | 20,932 | 20,883 |
| High | 6,095 | 6,290 |

### Statistical Significance

**Day-1 Retention**
- Difference: -0.59 percentage points (Gate 40 vs. Gate 30)
- p-value: 0.0755
- **Not statistically significant**

**Day-7 Retention**
- Difference: -0.82 percentage points
- Relative decline: 4.31%
- p-value: 0.0016
- **Statistically significant**
- In absolute terms: Gate 30 retained 8,502 players at Day 7 vs. 8,279 for Gate 40 — **223 more players retained under Gate 30**

### Visualizations

The notebook includes:
- Player retention by experiment group
- Average game rounds by gate version
- Player engagement segments by gate version
- Retention comparison (D1 vs. D7)
- Engagement distribution

A companion **Power BI dashboard** presents average game rounds by version, and overall D1 (45%) and D7 (19%) retention as interactive cards/visuals.

---

## Business Conclusion

**Recommendation: Retain the Level-30 progression gate.**

Moving the gate to Level 40 did not improve player engagement or retention:
- Average game rounds **decreased 2.21%**
- Day-1 retention decreased slightly (not statistically significant)
- Day-7 retention decreased **significantly** (p = 0.0016), with a 4.31% relative decline

Since Day-7 retention is a stronger indicator of long-term player value than Day-1, this decline is the more important signal. The data does not support delaying the gate to level 40. Recommended next step: keep the gate at level 30 and test alternative progression points or gate mechanics in follow-up experiments.

---

## Repository Structure

```
mobile-game-user-analytics/
│
├── data/
│   └── cookie_cats.csv
│
├── notebooks/
│   └── mobile_game_ab_testing_analysis.ipynb
│
├── sql/
│   └── analysis_queries.sql
│
├── visualizations/
│   └── (chart images / Power BI screenshots)
│
└── README.md
```

> **Note:** Check the dataset's license/redistribution terms on Kaggle before committing the raw CSV to a public repo — it is currently listed as unspecified/unknown.

---

## Skills Demonstrated

- A/B test design and evaluation
- SQL querying (aggregation, filtering, grouping) via SQLite
- Exploratory data analysis with Pandas
- Statistical hypothesis testing (Chi-square)
- Data visualization (Matplotlib, Power BI)
- Translating statistical results into a product recommendation
