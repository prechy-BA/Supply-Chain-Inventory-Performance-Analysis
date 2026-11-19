# Supply-Chain-Inventory-Performance-Analysis
Excel dashboard analysing 5,000 purchase orders: delivery reliability, supplier performance and inventory risk
# Supply Chain Inventory & Delivery Performance Analysis

An Excel data analytics project that cleans and analyses 5,000 purchase orders (January to December 2025) to answer four questions: are suppliers delivering on time and in full, how long do orders really take, how much stock is at risk, and where does the money go. The results are presented in an interactive Excel dashboard.

![Dashboard](images/dashboard.png)

## Business questions

| # | Question | Answer in brief |
|---|---|---|
| 1 | What share of orders arrive late, and by how much? | 68.1% late, 4.7 days on average |
| 2 | How much quantity is missing? | 98.0% fill rate; shortfall worth 2.0% of spend |
| 3 | Which suppliers, regions or warehouses perform worst? | None differ meaningfully |
| 4 | Do real lead times match agreed ones? | No: 14.7 vs 11.6 days (+27%) |
| 5 | How much stock is at risk or in excess? | 25.0% below reorder level, 29.2% at 3x or more, 4 stockouts |
| 6 | Where does spend go? | Evenly spread across suppliers (16.0% to 17.8% each) |
| 7 | Do late deliveries cause low stock? | No link found in this data |

## Key findings

- **Delivery reliability is the core problem.** Only 12.9% of orders arrive on time and in full (27.7% if 95% of the quantity counts as "in full").
- **It is systemic, not one bad supplier.** Chi-square tests show no supplier, region, warehouse, business unit, category or month differs beyond normal random variation.
- **Planning is too optimistic.** Orders take 14.7 days against 11.6 agreed, so reorder points based on agreed lead times under-protect stock.
- **Quantity is mostly fine, but small orders suffer.** Orders of 129 units or fewer fill only 93.0%; shortfalls average about 5 units whatever the order size.
- **A few badly short orders matter most.** 4.5% of orders (filled below 80%) cause about 30% of the shortfall value.
- **Inventory is out of balance.** 25.0% of stock records are below reorder level while 29.2% hold three times the reorder level or more.

## Data

- Source: `Dirty_Supply_Chain_Inventory_Performance_Dataset.xlsx` (5,050 rows, 20 columns, 6 suppliers, 15 products, 4 categories).
- Period: 1 January to 31 December 2025.
- Currency: source amounts are in Nigerian naira (NGN).

## Data cleaning summary

| Issue | Fix |
|---|---|
| 50 duplicate orders | Removed (5,050 to 5,000 rows) |
| 13 supplier spellings, 63 product spellings, warehouse abbreviations | Standardised to 6 suppliers, 15 products, full warehouse names |
| Category typos and blanks | Corrected using a product-to-category map |
| Blank region, warehouse, business unit | Labelled "Unknown", not guessed |
| 31 order dates with day and month swapped | Rebuilt as expected delivery date minus lead time |
| 150 blank received quantities | 57 inferred from status; 93 Partial orders excluded from fill rate |
| 150 blank delivery dates | 23 inferred; 127 left blank and excluded from late rate |
| Unrealistic unit costs | Flagged, not changed; no price comparisons made |

## Method and tools

- **Microsoft Excel:** Tables, helper columns (IF, MONTH, RANK, TEXT, COUNTIF), PivotTables, PivotCharts, calculated fields, slicers, timeline, conditional formatting.

Key definitions: **OTIF** = delivered on or before the expected date with the full quantity. **Fill rate** = total units received divided by total units ordered (orders with unknown receipts excluded from both totals). **Late rate** is measured from the delivery delay, because the Partial status overrides Late.

## Recommendations

1. **Reset lead times:** give a delivery date targets and a monthly OTIF review into supplier agreements and escalate any order still open 2 days after expected date
2. **Rebalance stock:** Prioritize stockout items and investigate inventory levels exceeding 3x the reorder point before adjusting replenishment quantities.
3. **Fix small orders:** set minimum order sizes or consolidate small orders, and require suppliers to confirm quantities at dispatch.
4. **Chase badly short orders:** follow up any order filled below 80% within 2 days.
5. **Strengthen Supplier Performance Management :** Introduce quarterly scorecards covering delivery reliability, fulfillment rates and lead time adherence. Prioritize suppliers with recurring performance weakness

## Repository structure

```
├── README.md
├── data/        Source dataset
├── dashboard/   Excel workbook with the interactive dashboard
├── docs/        Full project documentation (Word)
└── images/      Dashboard screenshot
```

## Limitations

- No demand or sales data, so inventory turnover and days of cover cannot be calculated.
- Stock Level and Reorder Level vary between records of the same product, so results are shares of records.
- Many differences between groups are small; the honest conclusion is that the problem is shared across the supply base.

## Documentation

The full documentation covers objectives, data cleaning, formulas used at each stage, insights, recommendations and challenges: see `docs/Supply_Chain_Project_Documentation.docx`.

## Author

Precious Obinna· https://www.linkedin.com/in/precious-obinna-30b6b43a2?utm_source=share_via&utm_content=profile&utm_medium=member_ios
