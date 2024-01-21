# XYZ Apparel Retailer - Inventory Allocation Improvement

## Problem Statement

XYZ, a leading global apparel retailer, operates a two-echelon supply chain with company-owned retail stores. The current inventory allocation process involves coordination among various stakeholders, leading to sub-optimal decisions. As an analytics consultant, the objective is to provide a data-driven solution to improve the inventory allocation process with the following goals:

- Reduce lost sales opportunities (avoid stockouts)
- Prevent excess stock at stores
- Minimize manual touchpoints in the allocation process

## Technical Case Study

### Data Description

#### Product Master
- SKU_Id
- Dept_Id
- StyleColor_id
- Color
- Size

#### Pack Configuration
- Pack_id
- SKU_id
- Qty

#### DC Inventory
- DC_id
- Pack_id
- Qty

#### Transaction
- Date
- Store_id
- SKU_id
- Qty

#### Forecast
- Year
- Week
- StyleColor_id
- Qty

#### Store-DC Mapping
- Store_id
- DC_id

#### Store Inventory
- Store_id
- SKU_id
- On_Hand
- On_Order
- Min

#### Constraints
- Store_id
- Dept_id
- Max

### Other Information Points
- SKU stock in DC is in packs.
- Product hierarchy: Department > Style > Color > Size.
- DC to store shipments have a one-day lead time.
- Replenishment and new allocation processes run on Mondays.
- Stock should satisfy the next 4 weeks of demand for each SKU and store.

## Data Challenges

1. **Missing Values:**
   - Some products may not be sold throughout the year.
   - Bias may be introduced. Solution: Address during model building.

2. **Inconsistent Data:**
   - Format, values, and data types may have issues.
   - Identify anomalies and clean data.

3. **Outliers:**
   - Outliers in sales data.
   - Identify and treat outliers before analysis.

## Analysis Tasks (Using R/Python)

1. **Aggregate Quantity and Identify Top Products:**
   - Aggregate quantity at Store-Style level on a weekly basis.
   - Identify top products.
   - Check for changes in preferences between 2018 and 2019.

2. **Detect and Treat Outliers:**
   - Detect outliers in Quantity for each Store-Product combination.
   - Apply outlier treatment (e.g., Winsorizing).

3. **Handle Missing Values:**
   - Check for missing values at Store-Product level.
   - Apply missing value treatment (e.g., imputation with mean or median).

4. **Split Future Forecast:**
   - Split Style-Week forecast into Store-SKU-Week using appropriate logic.
   - Address handling of new products.

5. **Generate Allocation Plans:**
   - Utilize Store Inventory data.
   - Generate 4 allocation plans for the first 4 weeks of 2020.
   - Prioritize stores with higher sales potential.

6. **Compare Allocation Plans with Demand Estimate:**
   - Define and calculate a stockout metric.
   - Evaluate effectiveness of each allocation plan.

## Submission Guidelines

- Choose R or Python.
- Highlight assumptions in code and PowerPoint.
- Add comments to explain logic and reasoning.
- Group logical steps into functions.

**Note:** This markdown serves as a guide. For actual code and detailed explanations, refer to the programming language of your choice (R or Python).
