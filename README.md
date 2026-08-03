# ✈️ Airline Data Lakehouse Project

Welcome to the **Airline Data Lakehouse Project** repository! 🚀

This project demonstrates a modern, production-style data lakehouse solution built on **Databricks**, from raw incremental ingestion to business-ready analytical models.


Designed as a portfolio project, it highlights industry best practices in data engineering using **Delta Lake**, **Unity Catalog**, **Delta Live Tables (DLT)** and **Databricks Workflows**.

<hr>

## 📖 Project Overview

This project involves:
1. **Data Architecture**: Designing a modern Lakehouse using Medallion Architecture - **Raw**, **Bronze**, **Silver** and **Gold** layers, governed end-to-end by **Unity Catalog**.
2. **Incremental Ingestion**: Streaming raw airline data into Bronze Delta tables using **Auto Loader**, with schema evolution and checkpointing.
3. **ETL Pipelines & Data Quality**: Transforming Bronze to Silver using **Delta Live Tables (DLT)**, enforcing data quality rules and implementing **CDC-based SCD Type 1**.
4. **Data Modelling**: Building a reusable, parameter-driven **Gold layer dim/fact framework** with surrogate keys and Delta **MERGE** upserts for star schema modeling.
5. **Orchestration**: Automating the full pipeline end-to-end via **Databricks Workflows**, chaining ingestion and DLT pipelines with dynamic multi-source parameters.

🎯 This repository showcases expertise in:

- Databricks Lakehouse Architecture
- Unity Catalog (Governance, Volumes, Access Control)
- Delta Lake & Delta MERGE (Upserts)
- Auto Loader (Incremental Streaming Ingestion)
- Delta Live Tables (DLT) & Data Quality Enforcement
- Change Data Capture (CDC) & SCD Type 1
- Dimensional Modelling (Star Schema)
- Databricks Workflows / Pipeline Orchestration

<hr>

## 📌 Project Requirements

### Building the Lakehouse (Data Engineering)

#### Objective
Architect an end-to-end data pipeline on Databricks to ingest, cleanse, and model airline operational data, enabling reliable analytical reporting and scalable governance.

#### Specifications
- **Data Sources**: Ingest raw airline data (multi-source) landed in cloud storage / Unity Catalog Volumes.
- **Ingestion**: Incrementally stream raw files into Bronze Delta tables using Auto Loader — with schema evolution and checkpointing to handle changing source schemas reliably.
- **Data Quality**: Enforce data quality rules (expectations) at the Silver layer using DLT, and track record-level changes via CDC-based SCD Type 1.
- **Integration**: Combine cleansed Silver data into a parameter-driven Gold layer, dynamically generating dimension and fact tables.
- **Governance**: Use Unity Catalog for centralized access control, lineage, and volume-based storage across all layers.
- **Orchestration**: Automate the complete flow — ingestion → DLT pipelines → Gold builder — using Databricks Workflows with dynamic multi-source parameters.
- **Documentation**: Provide clear documentation of the architecture and data flow to support both engineering and analytics stakeholders.

<hr>

## 🏗 Data Architecture

The data architecture for this project follows the Medallion Architecture with an added **Raw** landing zone, all governed through **Unity Catalog**:

1. **Raw Layer**: Source files land as-is in Unity Catalog Volumes (cloud storage) with no transformation — the immutable landing zone.
2. **Bronze Layer**: Raw files are incrementally ingested into Delta tables using **Auto Loader**, with schema evolution and checkpointing for fault-tolerant streaming ingestion.
3. **Silver Layer**: Built using **Delta Live Tables (DLT)** — applies data quality expectations, cleansing, and **CDC-based SCD Type 1** to keep records up to date.
4. **Gold Layer**: A reusable, **parameter-driven dim/fact builder** dynamically generates dimension and fact tables with surrogate keys, using **Delta MERGE** upserts — modeled into a star schema for reporting.

```
Raw (Volumes) → Bronze (Auto Loader) → Silver (DLT + CDC/SCD1) → Gold (Dim/Fact Builder, Star Schema)
                            |
                 Orchestrated end-to-end via Databricks Workflows
```

<hr>

## 📁 Repository Structure

```
airline-data-lakehouse-project/
|
|-- data/                             # Sample raw airline datasets used for ingestion
|
|-- docs/                             # Project documentation and architecture details
|   |-- data_architecture.drawio      # Diagram of Raw -> Bronze -> Silver -> Gold flow
|   |-- data_flow.drawio              # Diagram of ingestion & orchestration flow
|   |-- data_models.drawio            # Star schema (dim/fact) diagram
|   |-- data_catalog.md               # Catalog of tables, fields & metadata
|   |-- naming_conventions.md         # Naming guidelines for catalogs, schemas, tables
|
|-- notebooks/                        # Databricks notebooks for each layer
|   |-- bronze/                       # Auto Loader ingestion notebooks (streaming, schema evolution)
|   |-- silver/                       # DLT pipeline notebooks (data quality, CDC, SCD Type 1)
|   |-- gold/                         # Parameter-driven dim/fact builder notebooks (MERGE upserts)
|
|-- workflows/                        # Databricks Workflows job definitions (orchestration configs)
|
|-- tests/                            # Data quality and pipeline test scripts
|
|-- README.md                         # Project overview and instructions
|-- LICENSE                           # License information for the repository
```

-----------------------------------------------------
-----------------------------------------------------

#### License
This project is licensed under the MIT License.
