# 🧪 A/B Testing Analysis — Landing Page Conversion

An end-to-end statistical analysis comparing an **old vs. new landing page** to determine whether the new design significantly improves user engagement and conversion rate.

## 📌 Objective

Determine whether the new landing page significantly improves the conversion rate and time-on-page compared to the old page, using hypothesis testing at a 95% confidence level (α = 0.05).

## 📊 Dataset

- **Rows:** 100 users (50 control / 50 treatment)
- **Columns:** `user_id`, `group`, `landing_page`, `time_spent_on_the_page`, `converted`, `language_preferred`
- **Data quality:** 0 missing values, 0 duplicate rows
- **Source file:** `abtest.csv`

## 🔬 Workflow

1. Data loading and inspection (`head`, `shape`, `info`)
2. Data quality checks — null values and duplicates
3. Variable classification (numeric vs. categorical)
4. Exploratory Data Analysis:
   - Frequency tables (converted, landing page, language)
   - Crosstabs: landing page vs conversion, language vs conversion
   - Boxplot: time spent on page by landing page
5. Statistical testing:
   - **Two-sample t-test** — time spent on new vs old page
   - **Two-proportion z-test** — conversion rate new vs old
   - **Chi-square test** — conversion vs preferred language
   - **One-way ANOVA** — time spent by language on new page
6. Results summary table with decisions at α = 0.05

## 📈 Results

### Conversion by Landing Page

| Landing Page | Not Converted | Converted | Conversion Rate |
|--------------|---------------|-----------|-----------------|
| New | 17 | 33 | **66.0%** |
| Old | 29 | 21 | **42.0%** |

**Absolute lift:** +24 percentage points  

**Relative lift:** +57%

### Statistical Tests

| # | Research Question | Test | Statistic | p-value | Decision |
|---|-------------------|------|-----------|---------|----------|
| 1 | Time spent: new vs old page | Two-sample t-test | t = 5.244 | **<0.00001** | Reject H₀ |
| 2 | Conversion rate: new vs old page | Two-proportion z-test | z = 2.408 | **0.01605** | Reject H₀ |
| 3 | Conversion vs preferred language | Chi-square | χ² = 3.093 | 0.213 | Fail to reject H₀ |
| 4 | Time spent by language (new page) | One-way ANOVA | F = 0.854 | 0.432 | Fail to reject H₀ |

## ✅ Conclusions

1. **Time on page:** Users spend significantly more time on the new page (p = 0.00013).
2. **Conversion rate:** The new page converts significantly better — 66% vs 42% (p = 0.008).
3. **Language:** Preferred language does **not** significantly affect conversion (p = 0.213) or time spent (p = 0.432).

## 💼 Business Recommendation

**Ship the new landing page.** Both primary metrics — time-on-page and conversion rate — show statistically significant improvements, and neither improvement is confounded by user language.

## 📁 Project Structure

```
ab-testing-analysis/
├── abtest.ipynb         # Full analysis notebook
├── .gitignore
└── README.md
```

## 🚀 How to Run

```bash
git clone https://github.com/ojwangmaxwell3-ux/ab-testing-analysis.git
cd ab-testing-analysis
pip install pandas numpy scipy statsmodels matplotlib seaborn jupyter
jupyter notebook
```

Open `abtest.ipynb` and run all cells. The notebook expects `abtest.csv` in the same folder.

## 🛠️ Tech Stack

Python · Pandas · NumPy · SciPy · Statsmodels · Matplotlib · Seaborn · Jupyter

## 👤 Author

**Maxwell Odhiambo**

- GitHub: [@ojwangmaxwell3-ux](https://github.com/ojwangmaxwell3-ux)
