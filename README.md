# California Safe Cosmetics Program (CSCP) Hazardous Chemical Reporting Analysis (2007–2025)

## Project Overview

This project presents a regulatory aware analytical study of cosmetic products sold in California that contain chemicals known or suspected to cause cancer, birth defects, or other developmental or reproductive harm. The analysis is based on data reported to the **California Safe Cosmetics Program (CSCP)** under the **California Safe Cosmetics Act (2005)**.

Using publicly available disclosure data from the California Department of Public Health (CDPH), the project builds a four page Power BI dashboard to explore:
* The scale and structure of chemical reporting.
* Product categories and subcategories where reporting is concentrated.
* Chemical reporting patterns across time and product types.
* Company and brand level reporting footprint and complexity.

> **Important Note on Scope**
> This project is descriptive and analytical, not toxicological. It does not assess exposure risk, dosage, or product safety. Counts and frequencies reflect regulatory reporting behavior, not health outcomes.

## Project Objectives

1.  Provide transparent, reproducible insights into CSCP chemical reporting patterns.
2.  Analyze how reporting is distributed across products, chemicals, companies, and time.
3.  Demonstrate analyst grade data modeling, cleaning, and dashboard design.
4.  Ensure no assumptions are made beyond what is explicitly supported by the data and official documentation.

## Data Sources

### Primary Dataset
*   **Title**: Chemicals in Cosmetics
*   **Program**: California Safe Cosmetics Program (CSCP)
*   **Time Coverage**: 2007 to Present
*   **Geographic Scope**: California
*   **Public Portal**: [Chemicals in Cosmetics Dataset on Data.gov](https://catalog.data.gov/dataset/chemicals-in-cosmetics-d55bf)

### Files Used
*   `chemicals-in-cosmetics.csv` – The main fact table containing reported product-chemical records.
*   `chemicals-in-cosmetics-subcategories.csv` – Category and subcategory mapping reference.
*   `data-dictionary.csv` – Official metadata and field definitions.
*   `datapackage.json` – Dataset description and schema.
*   Official CSCP documentation and FAQ PDFs from the [CDPH website](https://www.cdph.ca.gov/).

## Understanding the Data and Reporting Context

Under the California Safe Cosmetics Act, companies must report cosmetic products sold in California if they contain ingredients listed as carcinogens or reproductive/developmental toxicants, provided the company meets two criteria:
1.  Has one million dollars or more in annual cosmetic sales.
2.  Sold products in California on or after January 1, 2007.

**Key Characteristics of the Data:**
*   It is self-reported by companies and maintained by the California Department of Public Health (CDPH).
*   The data is intended for public transparency and is not used as an enforcement scoring mechanism.
*   Some ingredients may be reported as **"Trade Secret"**, which acknowledges the presence of a reportable chemical but keeps its identity confidential.

## Data Cleaning and Preparation Methodology

All data preparation was performed in the Power BI Query Editor, adhering to public health data governance principles to ensure integrity and transparency.

### Data Processing Steps
*   **Type Enforcement**: Ensured correct data types (IDs as text, dates as date).
*   **Text Standardization**: Trimmed spaces and corrected encoding artifacts in text fields.
*   **Value Preservation**: All original reporting values were preserved; no imputation or correction of company-reported data was performed.
*   **Field Selection**: Removed fields with extreme sparsity and low analytical signal to streamline the model, specifically:
    *   `ChemicalDateRemoved`
    *   `DiscontinuedDate`

### Explicitly Omitted Steps
*   No filling of missing values.
*   No merging or "cleaning" of company, brand, or chemical names beyond standardization.
*   No addition of external toxicity scores, severity groupings, or hazard ratings.
*   No assumptions regarding consumer exposure, dosage, or risk.

## Data Model Design

A star schema oriented model was implemented for analytical clarity and performance.

### Fact Table Structure
*   One row represents one chemical reported for one product. This may include variations for specific colors, scents, or flavors.

### Core Dimension Tables
*   Company
*   Brand
*   Primary Category
*   Subcategory
*   Chemical
*   Date (A dedicated calendar table)

### Date Relationship Strategy
A dynamic **Date table** was created using all relevant date columns from the dataset:
*   InitialDateReported
*   MostRecentDateReported
*   ChemicalCreatedAt
*   ChemicalUpdatedAt

Only **InitialDateReported** was used as the active relationship in the model to maintain unambiguous time-based analysis.

## Dashboard Structure and Page Descriptions

The final Power BI report contains four analytical pages, each designed for a specific analytical perspective.

### Page 1: Executive Overview
*   **Focus**: Communicates the overall scale and structure of reporting.
*   **Key Visuals**: Total reported products, companies, and chemicals; product category distribution; high-level reporting trends over time.

### Page 2: Product and Category Analysis
*   **Focus**: Investigates where chemical reporting is most concentrated.
*   **Key Visuals**: Chemical counts by product category; top subcategories by reported chemical volume; list of products with the highest reported chemical counts.

### Page 3: Chemical Reporting Patterns
*   **Focus**: Analyzes reporting behavior at the individual chemical level.
*   **Key Visuals**: Most frequently reported chemicals; chemical distribution across product categories; chemical reporting activity timeline.

### Page 4: Company and Brand Reporting Landscape
*   **Focus**: Examines the reporting scale and formulation complexity across entities.
*   **Key Visuals**: Top reporting companies by product count; leading brands by reporting presence; scatter plot analyzing reporting scale versus average chemical complexity per product.

## Key Descriptive Observations

### Scale and Data Completeness
*   Approximately **36,900 reported products**.
*   Roughly **635 reporting companies**.
*   About **58,000 reported chemical instances**.
*   Very high disclosure completeness, with trade secret entries representing a minimal share of total records.

### Product Category Coverage
*   Reporting is heavily concentrated in **makeup (non-permanent)** and **nail products**.
*   Significant contributions also come from skin care, hair care, bath products, and sun-related products.
*   Subcategories such as foundations, face powders, eye products, shampoos, and conditioners show high chemical reporting density.

### Chemical Reporting Patterns
*   Certain chemicals (e.g., titanium dioxide, talc, mica, retinoids, carbon black) appear with high frequency across multiple product types.
*   **Important**: Frequency reflects reporting prevalence under the law, not a toxicity ranking.

### Company and Brand Structure
*   Reporting is concentrated among large cosmetic manufacturers and entities with multi-brand portfolios.
*   Analysis reveals different business models:
    *   Large product portfolios with moderate average chemical complexity.
    *   Smaller portfolios with higher average chemical counts per product.

## Limitations and Ethical Notes

*   The dataset is **self-reported**; under-reporting or reporting inaccuracies are possible.
*   **Reporting frequency is not equivalent to chemical danger**; this analysis makes no toxicological judgments.
*   This project does **not** measure actual consumer exposure or health risk.
*   Results should be interpreted strictly as **patterns in regulatory disclosure**.

## Tools and Technologies Used

*   **Power BI Desktop**
    *   Power Query Editor (M language) for data transformation.
    *   DAX (Data Analysis Expressions) for measures and calculated columns.
*   **External Documentation**: CSV data dictionaries and official PDF documentation from CDPH.
*   **Version Control**: GitHub for project tracking and documentation.

## Project Significance

This project demonstrates professional competency in:
*   Standard grade data modeling and governance.
*   The careful and ethical handling of health related regulatory data.
*   Balancing clear visual storytelling with methodological rigor.

## Author

**Abdullah Shaikh**
Data Analytics and Business Intelligence Portfolio Project
*(Power BI | SQL | Python | Data Modeling)*