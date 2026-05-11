# AdventureWorks Auction & Store Expansion

Academic project for **Relational and Non-Relational Databases**.

This project extends the Microsoft AdventureWorks database with an online auction system and uses SQL analysis to recommend two US cities for brick-and-mortar store expansion.

---

## Objective

Address two business problems using SQL Server and T-SQL:

1. **Stock clearance through online auctions**  
   Design and implement a database-backed auction subsystem for clearing eligible products.

2. **Physical store expansion**  
   Analyse customer and sales data to recommend two promising US cities for new retail stores.

---

## Repository contents

| File | Description |
|---|---|
| `auction.sql` | Main idempotent T-SQL script with schema, tables, stored procedures, and analytical queries |
| `report.md` | Markdown report documenting the solution design, assumptions, methodology, and results |
| `report.docx` | Report document version |
| `README.md` | Project overview |

---

## Auction system

The script creates an `Auction` schema with the core objects required to manage auction listings and bids.

### Main database objects

| Object | Type | Purpose |
|---|---|---|
| `Auction.Configuration` | Table | Stores configurable auction rules |
| `Auction.Product` | Table | Tracks products listed for auction |
| `Auction.Bids` | Table | Stores bids and bid status |
| `uspAddProductToAuction` | Stored procedure | Adds an eligible product to auction |
| `uspTryBidProduct` | Stored procedure | Validates and places bids |
| `uspRemoveProductFromAuction` | Stored procedure | Cancels an active auction |
| `uspListBidsOffersHistory` | Stored procedure | Lists customer bid history |
| `uspUpdateProductAuctionStatus` | Stored procedure | Finalises expired auctions and marks winners/losers |

### Business rules implemented

- Only eligible active products can be auctioned
- One active auction per product at a time
- Initial bid depends on product type/configuration
- Minimum bid increment and maximum bid limits are configurable
- Bid history is preserved even when auctions close or are cancelled

---

## Store expansion analysis

The analytical queries recommend **Bellflower** and **Berkeley**, California based on:

- Exclusion of cities already dominated by top resellers
- Presence of sales across major consumer-facing categories
- Individual customer revenue potential
- Geographic separation using zip-code logic
- Positive sales trends across the analysed years

---

## How to run

1. Open `auction.sql` in SQL Server Management Studio or Azure Data Studio.
2. Connect to a SQL Server instance with the AdventureWorks database available.
3. Execute the script against the AdventureWorks database.
4. Review the generated objects and query outputs.

The script is designed to be idempotent, so it can be re-run during development without manually dropping all objects first.

---

## Technologies

`SQL Server` · `T-SQL` · `Stored Procedures` · `Database Design` · `AdventureWorks` · `Business Analysis`

---

## Notes

This is an academic database project. The store recommendations depend on the AdventureWorks sample data and should be interpreted as a database-analysis exercise rather than a real market-entry strategy.
