# Statisitc_R_Project_Proposal
Modeling Azure VM CPU utilization with multiple linear regression, using Microsoft's public production traces (2.7M VMs) — STAT 420 project in R.


# Predicting Azure VM CPU Utilization

Multiple linear regression analysis of Microsoft Azure's 2019 production
VM workload, asking: **what predicts a virtual machine's average CPU
utilization?** Answering this is the core of cloud capacity planning —
knowing expected utilization from a VM's characteristics drives packing,
rightsizing, and oversubscription decisions.

## Data

[Azure Public Dataset V2](https://github.com/Azure/AzurePublicDataset) —
a sanitized trace of 2,695,548 real VMs across 6,687 subscriptions over
30 days, published by Microsoft (CC-BY). This analysis joins the VM table
with the deployment and subscription tables.

- **Response:** average CPU utilization (`avg_cpu`)
- **Continuous predictors:** VM lifetime, deployment size, subscription
  VM count, p95 max CPU
- **Categorical predictors:** VM category, core-count bucket, memory bucket

## Status

- [x] Proposal (see `Project_Proposal.Rmd`)
- [x] Preliminary MLR — R² ≈ 0.75 with all predictors
- [ ] EDA and transformations
- [ ] Model selection and diagnostics
- [ ] Final report

## Reproducing

Data files are not committed (821MB). Download `vmtable`, `deployments`,
and `subscriptions` from the [dataset-v2 release](https://github.com/Azure/AzurePublicDataset/releases/tag/dataset-v2)
into the project root, then knit `Project_Proposal.Rmd`.

## References

Cortez, E., et al. (2017). Resource Central: Understanding and predicting
workloads for improved resource management in large cloud platforms.
*SOSP '17*. https://doi.org/10.1145/3132747.3132772

Microsoft Azure. (2019). *AzurePublicDataset* (V2) [Data set]. GitHub.
https://github.com/Azure/AzurePublicDataset
