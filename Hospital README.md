# 🏥 Hospital Readmission Analysis — Novartis Hospital

### Reducing Readmissions: A Data Analytics Case Study for Improved Patient Care

> **Analyst:** Ronak Sagar | **Dataset:** 66,587 Patient Encounters | **Status:** Complete — Basic + Medium + Advanced (AQ1–AQ5)

-----

## 📌 Project Overview

This project analyzes hospital admission data for Novartis Hospital to identify patterns and factors driving high 30-day readmission rates. The hospital had seen a spike in readmissions, raising healthcare costs and signalling potential quality-of-care issues. As the data analyst, the goal was to uncover root causes, build a predictive risk model, segment patients, and design a data-driven post-discharge program to reduce avoidable readmissions.

**Overall Readmission Rate: 46.2%** (30,764 of 66,587 patients readmitted within 30 days)  
**Estimated Total Cost of Readmissions: ~$461.5M | Potentially Avoidable: ~$124.6M (27%)**

-----

## 📂 Repository Structure

```
📁 Hospital-Readmission-Analysis/
├── 📄 README.md
├── 📊 Hospital_Readmission_Analysis_CORRECTED.xlsx   # Full analysis workbook
└── 📑 DACS08_Hospital_Administration_Analysis.pdf    # Case study brief
```

**Sheets inside the workbook:**

|Sheet              |Analysis                                                                                           |
|-------------------|---------------------------------------------------------------------------------------------------|
|📋 Cover            |Project index and contents                                                                         |
|📈 Summary Dashboard|Executive summary — all findings at a glance                                                       |
|📊 Raw Data (Sample)|First 200 of 66,587 patient encounters                                                             |
|Q1 – Q10           |Basic-level analysis (10 questions)                                                                |
|MQ1 – MQ7          |Medium-level analysis (7 questions)                                                                |
|AQ1 – AQ5          |Advanced analysis: predictive model, clustering, financials, social determinants, follow-up program|

-----

## 🗃️ Dataset

- **Source:** [Kaggle — Hospital Administration Data by Shiva Vashishtha](https://www.kaggle.com/datasets/shivavashishtha/hospital-administration-data/)
- **Size:** 66,587 patient encounters
- **Key Fields:** Demographics (race, gender, age), clinical data (diagnoses, medications, lab procedures), visit history (inpatient/outpatient/emergency prior-year counts), diabetes medication status, medication change flag, and 30-day readmission outcome (binary)
- **Data Quality Issue:** Weight field is 96.8% missing — flagged and excluded from primary analysis

-----

## 🛠️ Tools & Technologies

- **Microsoft Excel** — Full analysis environment (formulas, pivot tables, statistical calculations, charts)
- **Statistical Methods Used:**
  - Pearson Correlation (r values for continuous variable relationships)
  - Logistic Regression (AQ1 — Predictive Model, AUC = 0.652)
  - K-Means Clustering (AQ2 — Patient Segmentation, k=4)
  - Cross-tabulation / Heatmaps (MQ6 — Race × Age analysis)
  - Comorbidity Scoring (MQ1 — based on diagnosis count tiers)
- **Benchmarks:** CMS 2023 cost data, NEJM/JAMA evidence for follow-up program design (AQ5)

-----

## 📊 What Was Analysed — Section by Section

### Part 1: Basic Analysis (Q1–Q10)

**Q1 — Readmission by Age Group:** Rates rise steadily from 22% (0–10 yrs) to a peak of 48.3% at 80–90 years. The 70–90 age band accounts for 43% of all patients, making elderly care the largest intervention opportunity.

**Q2 — Length of Stay by Specialty:** Physical Medicine & Rehab leads at 8.9 days average. Nephrology, despite a moderate LOS (4.8 days), has the highest readmission rate of any specialty at 55.1%. Cardiothoracic Surgery has the lowest readmission rate (25.4%), suggesting strong post-op protocols. Analysis applied a minimum 50-patient filter for statistical reliability.

**Q3 — Emergency Visits vs Readmission:** Pearson r = 0.108 (weak). However, patients with 4+ prior emergency visits show readmission rates exceeding 79% — a concentrated high-risk subgroup requiring care coordination despite the low overall correlation.

**Q4 — Diabetes & Readmission:** Patients on diabetic medication have a 47.96% readmission rate vs 40.3% for those not on it — a 7.6 percentage point gap, the largest single-variable difference found in Part 1.

**Q5 — Medication Change vs Readmission:** Patients whose diabetic medication was changed have a 48.6% readmission rate vs 44.1% for those with no change. This likely reflects reverse causation — medication changes signal worsening conditions.

**Q6 — Lab Procedures vs Readmission:** r = 0.036 (very weak). Lab volume alone does not drive readmissions. The relationship is non-linear — the highest-volume group (101+ tests) actually shows the lowest readmission rate (31%), likely because the most complex cases receive the most intensive care.

**Q7 — Race & Gender:** Caucasian (47.0%) and African American (46.0%) patients have the highest readmission rates. The gender gap is narrow — Female: 46.9% vs Male: 45.4%. These differences warrant an equity audit.

**Q8 — Weight Analysis:** Weight data is 96.8% missing (only 2,133 of 66,587 patients have recorded weight). No reliable conclusions can be drawn. Weight recording at admission should be mandated.

**Q9 — Medications vs Length of Stay:** r = 0.466 — the strongest correlation in the entire analysis. Patients on 26–30 medications average 8+ days in hospital vs 2–3 days for those on 1–5. Polypharmacy is both a marker of severity and a driver of extended stays.

**Q10 — Outpatient Visits vs Readmission:** Outpatient correlation is weak (r = 0.082). Prior inpatient visit history is the stronger predictor (r = 0.217) — patients previously hospitalised are the highest-risk group for return.

-----

### Part 2: Medium Analysis (MQ1–MQ7)

**MQ1 — Comorbidity Analysis:** Patients with 7–9 diagnoses (High comorbidity) have a 49.4% readmission rate vs 34.0% for those with 1–3 diagnoses. They also require 1.6× more medications and significantly more lab tests. A formal comorbidity scoring system is recommended for risk stratification at admission.

**MQ2 — Demographic Disparities:** African American patients receive slightly more lab tests (44.1 avg) but fewer medications than Caucasian patients. Asian patients receive the fewest medications (avg 13.2). Caucasian patients have the highest readmission rate despite the highest medication counts, suggesting factors beyond treatment intensity are at play.

**MQ3 — Visit Patterns by Diagnosis:** Chronic Bronchitis (60.5%) and Heart Failure (58.6%) have both the highest readmission rates and the highest prior inpatient visit averages — confirming chronic conditions drive repeat hospitalisations. Osteoarthritis has the lowest rate (35.9%), consistent with its more elective nature.

**MQ4 — Specialty Prescribing Patterns:** Nephrology has the highest readmission rate (55.1%) despite mid-range medication counts — disease severity, not prescribing volume, is the driver. Orthopedics prescribes the most medications (20.8 avg) but has one of the lowest readmission rates (33.4%).

**MQ5 — Diabetic Medication Effectiveness:** Among diabetic-only patients, medication changes correlate with higher readmission (48.6%) vs no change (46.9%). Medium medication tiers (11–20) show the most balanced outcomes. Very high medication counts (31+ meds) show elevated risk — polypharmacy complexity.

**MQ6 — Race × Age Heatmap:** Caucasian patients aged 80–90 show the highest rate among statistically reliable cells (48.9%). African American patients show elevated rates consistently across working-age groups (40–70), suggesting structural or chronic disease disparities not purely age-driven.

**MQ7 — Integrated Risk Profile:** The highest-risk combination identified: Young (<40) + Diabetic + Prior Inpatient Stay → 69.4% readmission rate. Elderly (70+) + Diabetic + Prior Inpatient Stay → 58.7%. **Prior inpatient history is the single strongest binary predictor across all age and diabetes groups.**

-----

### Part 3: Advanced Analysis (AQ1–AQ5)

**AQ1 — Predictive Risk Model (Logistic Regression, AUC = 0.652):**  
Trained on 80% of the dataset (53,269 patients), tested on 20% (13,318 patients). Achieves 61.6% accuracy, 81.1% specificity, 63.6% precision. Top predictors in order: Prior Inpatient Visits (coef: 0.46) → Prior Emergency Visits (0.20) → Number of Diagnoses (0.14) → Diabetes Medication (0.11). Critical Risk patients (top scoring tier) show 70.2% actual readmission — 24pp above the dataset mean. Recommended deployment: flag patients scoring >0.55 for intensive follow-up at discharge.

**AQ2 — Patient Segmentation (K-Means, k=4):**

|Segment                   |Patients      |Readmit Rate|Key Profile                                |
|--------------------------|--------------|------------|-------------------------------------------|
|🔴 Chronic High-Utilizers  |4,482 (6.7%)  |74.8%       |Avg 3.6 prior inpatient, 17.2 meds         |
|🟣 Complex Polypharmacy    |14,134 (21.2%)|47.5%       |Longest LOS (8.0 days), 25.2 avg meds      |
|🔵 Moderate-Acuity Standard|28,872 (43.4%)|47.2%       |Mid-range everything, largest group        |
|🟢 Low-Acuity Short Stay   |19,099 (28.7%)|37.1%       |Shortest LOS (3.0 days), fewest medications|

**AQ3 — Financial Impact:**  
Total estimated readmission cost: **$461.5M**. Avoidable readmissions (27% per CMS benchmark): **$124.6M potential annual savings**. Chronic High-Utilizers cost ~$11,200 per patient. Investing $2,000–$5,000 per high-risk patient in intensive follow-up could yield a **10–15× ROI**. Hospitals exceeding CMS expected readmit ratios risk up to 3% Medicare reimbursement penalties.

**AQ4 — Social Determinants of Health:**  
African American patients receive fewer medications (15.4 avg vs 16.3 for Caucasian) despite similar acuity levels — warranting an equity audit. Patients with 6+ prior outpatient visits show 65.1% readmission — reverse causation (sicker patients use more services). Hispanic patients show below-average readmission (40.7%) despite socioeconomic risk factors — potentially a model for community-based support effectiveness.

**AQ5 — Post-Discharge Follow-Up Program Design:**  
A 4-tier risk-stratified program covering all 66,587 patients. The base case (20% reduction in Critical + High Risk patients) prevents 2,398 readmissions, saving **$35.97M with a 157% ROI** on a $14M program investment. The full program (20% reduction across all tiers) projects **$70.3M net savings and 320% ROI**. 12-month phased rollout from EHR model integration → pilot → full deployment → optimisation.

-----

## ⚡ Challenges Faced

**1. The 96.8% Missing Weight Data Problem**  
The weight column contained `?` for nearly all patients (64,454 of 66,587). Any weight-based analysis was statistically unreliable. The decision was made to report the data quality issue clearly rather than draw misleading conclusions from 2,133 data points — a more honest analytical choice, but one that eliminated an entire planned analysis dimension.

**2. Separating Correlation from Causation in Medication Changes**  
Q5 showed patients with medication changes have higher readmission rates. The temptation was to conclude medication changes cause readmissions. The correct interpretation is reverse causation — clinicians change medications in response to deteriorating conditions, so the change is a symptom of high risk, not a driver. This required careful framing in the findings.

**3. The Lab Procedures Non-Linear Relationship**  
Q6’s Pearson correlation (r = 0.036) looked like “no relationship” but the grouped analysis revealed a U-shaped pattern: readmission peaked in the 61–80 test range and dropped sharply for 101+ tests. A simple correlation would have missed this — requiring additional group-level analysis to tell the complete story.

**4. Small Sample Specialties Distorting Averages**  
Q2’s specialty analysis initially showed Pediatrics-Pulmonology with the longest average stay (10.7 days), but with only 16 patients. Hematology showed 66.7% readmission on just 57 patients. A minimum 50-patient filter was applied to exclude statistically unreliable specialties, but this required deliberate documentation so stakeholders understood why certain specialties weren’t ranked.

**5. Building the Logistic Regression in Excel**  
AQ1 required implementing logistic regression — coefficient estimation, ROC curve generation, and confusion matrix construction — all within Excel without statistical software. This meant manually computing log-odds, probability scores, and threshold-based classifications across the full dataset, which is computationally intensive and error-prone compared to Python or R.

**6. K-Means Clustering Without Native Excel Tooling**  
AQ2’s patient segmentation required implementing K-Means iteratively in Excel. Initialising centroids, computing Euclidean distances across 7 clustering variables, reassigning cluster labels, and iterating until convergence — all in a spreadsheet environment — was the most technically demanding part of the project.

**7. Defining “Avoidable” Readmissions for Financial Analysis**  
AQ3 required quantifying avoidable readmissions, which has no universally agreed clinical definition. The 27% CMS benchmark was used as the industry standard, with clear documentation of this assumption. Any sensitivity to this assumption directly changes the $124.6M savings estimate — so transparency about the assumption was critical.

-----

## 💡 Insights Gained

**Prior inpatient history dominates all other predictors.** Across every analysis — correlation, logistic regression, risk profiling, and clustering — the single most powerful signal is whether a patient has been hospitalised before. This is the variable the hospital should most urgently flag and act on at discharge.

**A 46.2% readmission rate means the hospital is getting roughly half of discharged patients back.** This is not a marginal problem. Nearly every other patient returns within 30 days — and ~27% of those returns are potentially preventable with better discharge planning, follow-up, and medication reconciliation.

**The Chronic High-Utilizer cluster is 6.7% of patients but generates disproportionate costs.** At 74.8% readmission and ~$11,200 cost per patient, this 4,482-patient group is where the highest ROI interventions should focus first. A small investment per patient in this group yields massive returns relative to broader programs.

**Nephrology is the specialty that needs the most post-discharge attention — not the longest LOS.** With a 55.1% readmission rate and moderate length of stay, Nephrology patients are being discharged but returning frequently. The LOS analysis alone would have missed this — readmission rate by specialty was a more useful metric.

**Medication volume is a marker of complexity, not independently a driver of outcomes.** The strongest correlation in the dataset (r = 0.466) is between medications and LOS, not between medications and readmission. Polypharmacy reflects patient severity more than it independently causes returns — this distinction matters for what interventions are actually effective.

**The Access Paradox in outpatient visits reveals reverse causation.** Patients with 6+ prior outpatient visits have the highest readmission rate (65.1%). This looks counterintuitive — shouldn’t more outpatient care reduce readmissions? It reflects that the sickest patients both use the most outpatient services and return to hospital most often. True access barriers show up differently, in the underrepresentation of certain demographic groups.

**An AUC of 0.652 is acceptable and deployable for clinical use.** Using only administrative data (no vitals, no lab results, no imaging), the logistic regression achieves meaningful discrimination. A more feature-rich dataset would push this higher — but even at 0.652, the Critical Risk tier (70.2% actual readmit) is clinically actionable as a discharge flag.

-----

## 🔧 Recommendations for Improvement

**Collect weight data systematically.** The single largest analytical gap in this dataset is 96.8% missing weight. Mandating weight recording at admission would unlock BMI-based risk stratification, which is a known predictor of readmission for cardiovascular and metabolic conditions. This is a data governance fix, not an analytics fix.

**Enrich the model with clinical variables.** The AQ1 logistic regression uses only administrative data. Adding vitals (blood pressure, heart rate at discharge), lab values (HbA1c for diabetic patients, creatinine for nephrology), and discharge disposition (home vs SNF vs transfer) would likely push AUC from 0.652 toward 0.75+, dramatically improving sensitivity.

**Implement the risk model in the EHR at discharge.** The AQ1 model’s value is zero if it exists only in a spreadsheet. Integrating the risk score into the hospital’s EHR system so it automatically flags patients at the point of discharge planning is the critical implementation step. The 12-month rollout plan in AQ5 details how to do this.

**Conduct a formal equity audit on treatment protocols.** African American patients receive fewer medications than Caucasian patients despite similar readmission risk levels. Whether this reflects appropriate clinical differences or implicit bias in prescribing cannot be determined from this dataset alone — but the pattern is clear enough to justify a structured audit.

**Add time-series/seasonal data.** The dataset lacks timestamps beyond the encounter ID. Analysing readmissions by month or season (the Medium Question 1 that couldn’t be fully answered here) could reveal whether certain periods have higher readmission risk — enabling proactive resource planning, not just reactive care.

**Build a live dashboard for the hospital board.** The Summary Dashboard sheet shows what this could look like, but it’s static. A Power BI or Tableau version connected to live EHR data would give department heads real-time visibility into readmission rates by specialty, risk tier, and segment — turning this one-time analysis into an ongoing monitoring tool.

**Pilot the follow-up program on Nephrology and Heart Failure patients first.** These two groups (55.1% and 58.6% readmission respectively) represent the highest-confidence intervention targets — both have high readmission rates, both involve chronic manageable conditions, and both have strong clinical literature supporting structured follow-up programs. A focused pilot here would yield measurable results fastest.

-----

## 📬 Acknowledgements

Case study designed by **Shiva Vashishtha**  
Mentor LinkedIn: [linkedin.com/in/shivavashishtha](https://www.linkedin.com/in/shivavashishtha/)  
Dataset: [Kaggle — Hospital Administration Data](https://www.kaggle.com/datasets/shivavashishtha/hospital-administration-data/)  
Cost benchmarks: CMS 2023, Kaiser Family Foundation (KFF)