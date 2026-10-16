# Signal Desk: AI Campaign Planner (concept)

**Live demo:** https://samiksha721.github.io/Signal-Desk-Campaign-Builder/

A product prototype that explores how data signals can act as *verifiers* in an AI-assisted campaign planner for martech.

A marketer picks a campaign objective, switches on data layers (**location**, **transaction**, **behavioral**), and the tool recomputes the audience funnel, suggested subject lines, channel mix, send timing, expected revenue, cost to build, cost to run, and a model-confidence score.

## What's simulated

No real customer or company data is used. Funnel rates, lift multipliers and cost figures are **illustrative assumptions** chosen to show the decision architecture, not to predict real results.

| Signal | Effect in the model |
|---|---|
| Transaction data | Refines the pool to proven buyers (×0.85 reach), conversion ×1.55, AOV ×1.28 |
| Behavioral data | Open rate ×1.42, click rate ×1.50, unlocks send-time optimization |
| Location data | Conversion ×1.12, adds SMS as a proximity channel |

Lift multipliers are relative changes that stack multiplicatively. In production they would be measured against a holdout group, not assumed.

## Product thinking

- **Human approval before anything launches.** Nothing auto-sends.
- **Confidence scales with the number of independent signals** that agree.
- **Reasoning trace.** Every number is explained step by step, in the colour of the data signal that produced it.

### Known gaps and guardrails a production version needs

- **False precision.** Point estimates should become confidence intervals.
- **Wrong objective.** The prototype shows ROAS, which rewards reaching people who would have bought anyway. The intended north star is **incremental margin per campaign**, measured against a holdout group.
- **Privacy and consent.** Fusing location, transaction and behavioral data is highly re-identifying. It needs consent, purpose limitation and regional rules (GDPR, CCPA, TCPA, CAN-SPAM, India's DPDP Act).
- **Disparate impact.** Targeting logic needs fairness audits and blocked protected attributes.
- **Generated copy.** LLM-written subject lines must be grounded in verified offer parameters and pass a brand and compliance check.
- **Send fatigue.** Frequency caps should apply across all campaigns, not per campaign.

## Roadmap

- [ ] Holdout-percentage control and a gross-margin input, with incremental margin as the headline metric
- [ ] LLM-generated subject lines and copy through a small serverless proxy (API key kept server-side)
- [ ] Before/after comparison mode (plan with vs. without signals)

## Run it locally

It's a single static file. Open `index.html` in any browser. There is no build step.
