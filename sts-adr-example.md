# Improve pre-scoring accuracy with ML

## Status

Proposed

## Scope

Scoring (Domain)

## Trigger

Recent study shows many candidates are rejected due to simple rule-based system. Given that we now have access to more historical scoring and credit data we can explore ways to improve the accuracy of pre-scoring by using a ML model build based on that data.

## Context

- **Product(What)**: currently performing very basic scoring, which is rule-based and mostly does a check on provided documentation (does not use historical data).
- **Teams(Who)**: we have 1 team with 3 engineers and 1 product owner working/owning the scoring engine functionality (including pre-scoring). (No ML knowledge in the team).
- **Tech(How)**: pre-scoring is built as a simple application exposed as web service.

## Synthesis & understanding

- We want to improve the pre-scoring by using ML model, that is built based on newly available pre-scoring and credit history.
- Current team has not ML skill, which means this must be added to the team or a supporting team (e.g.: complicated subsystem).
- Computations of ML model must connect to the data warehouse (on Google Cloud BigQuery) that collects the historical scoring data.

## Decision

- Hire a ML Engineer that will focus on creating the data pipeline, setup for model training and integrates the model in the pre-scoring application so we can have improved pre-scoring functionality.
- Model can be computed weekly or monthly, as data does not change substantially every day.

## Consequences

- **Product(What)**: should have increased accuracy on the pre-scoring, which should increase sales and customer happiness. This may also open up new interesting opportunities around using ML other parts of scoring (e.g.: in the main scoring phase).
- **Teams(Who)**: team gets a new person focused on a new skill (ML). Risk: this person should not be the only one building and maintaining ML related activities - this knowledge must be spread in the team.
- **Tech(How)**: pre-scoring web service must integrate the new ML model. The ML model can be updated every week or month for now, as historical data does not change substantially.
- **Interrelated scopes**:
  - other parts of the system will need to handle more load on subsequent steps of the process. We must make sure this is taken in considerations.
  - main scoring system may also be able to benefit from this development and use historical scoring functionality. If this is something we want to explore, we may consider transforming the ML model related activities into a complicated subsystem for all scoring phases.
