# RevoFin Loan Portfolio Risk Dashboard

An interactive loan portfolio analytics dashboard built for the RevoFin data analyst project.  
This dashboard analyzes portfolio health, default exposure, cohort-level risk, and potential underwriting signals using SQL-generated aggregation tables.

## Project Context

RevoFin is a fictional financial technology company that provides lending solutions to individuals and small businesses. The purpose of this project is to evaluate the condition of RevoFin’s loan portfolio and identify risk patterns that may support better lending and underwriting decisions.

The dashboard is designed for:

- Risk Management Team
- Executive Management

## Dashboard Objectives

This dashboard aims to answer the following business questions:

1. What is the overall condition of RevoFin’s loan portfolio?
2. How much outstanding exposure is currently in the portfolio?
3. What is the current ENR and TKB30 of the portfolio?
4. Which loan cohorts show higher risk?
5. Which borrower or loan attributes are associated with higher default exposure?
6. What recommendations can be drawn to improve the underwriting process?

## Key Metrics

| Metric | Definition |
|---|---|
| Portfolio OS | Total funded amount of loans that are still in the portfolio |
| ENR | Outstanding exposure excluding default loans |
| Default OS | Funded amount of loans with `Default` status |
| Default OS Rate | Default OS divided by Portfolio OS |
| TKB30 | `1 - Default OS / Portfolio OS` |
| Total Loans | Number of loans in the portfolio |
| Total Customers | Number of unique cleaned customer IDs |

Because DPD is not directly observed in the dataset, default loans are used as the proxy for loans with DPD greater than 30 days.

## Dashboard Sections

The dashboard contains the following sections:

1. **Executive Overview**  
   Shows portfolio-level KPI cards such as Portfolio OS, ENR, TKB30, Default Exposure, Default OS Rate, and Total Loans.

2. **Loan Status Composition**  
   Shows portfolio exposure by loan status and summarizes the distribution of current, grace period, and default loans.

3. **Cohort Risk Analysis**  
   Analyzes default exposure, default rate, and TKB30 across yearly and monthly loan cohorts.

4. **Anomaly Cohort Deep Dive**  
   Compares the 2016 anomaly cohort with other cohorts across borrower and loan characteristics such as income bucket, home ownership, employment length, loan purpose, state, term, and interest rate bucket.

5. **Default Contribution Ranking**  
   Ranks the largest contributors to default exposure by cohort, purpose, state, income bucket, interest rate bucket, and term.

6. **Default Loan Detail**  
   Displays detailed information for loans with default status.

## Data Sources

The dashboard uses SQL-generated aggregation outputs exported as Excel files and stored in the `/data` folder.

Required files:

```text
data/pbi_agg_portfolio_kpi.xlsx
data/pbi_agg_loan_status.xlsx
data/pbi_agg_cohort_long.xlsx
data/pbi_agg_cohort_group_summary.xlsx
data/pbi_agg_cohort_group_profile_long.xlsx
data/pbi_default_contribution_ranking.xlsx
data/pbi_default_loan_detail.xlsx