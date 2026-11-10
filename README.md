<p align="center"><img src="icon.png" alt="Sweeprice" width="96" height="96"></p>

# Sweeprice MCP server

Remote MCP server for [Sweeprice](https://www.sweeprice.com/en): competitor prices, Buy Box and recommended prices for sellers on 14 marketplaces (Amazon, Cdiscount, Fnac, ManoMano, Darty, eBay, Leroy Merlin, Boulanger, BUT, Conforama, La Redoute, Back Market, Etsy, Decathlon). Products are matched across marketplaces by GTIN/EAN.

This repository holds the public description of the server. The server itself is hosted by Sweeprice; there is nothing to install.

| | |
|---|---|
| Endpoint | `https://mcp.sweeprice.com/mcp` (Streamable HTTP) |
| Authentication | OAuth 2.1 per the MCP authorization spec, with a Sweeprice account (14-day free trial, no credit card) |
| Registry name | `com.sweeprice/sweeprice` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=sweeprice) |
| Maintainer | [MossPig LAB](https://www.sweeprice.com/en/about), Marseille, France |

## Connect

Add `https://mcp.sweeprice.com/mcp` as a remote MCP server in your client (Claude.ai and Claude Desktop custom connectors, Claude Code, Cursor, VS Code, Windsurf and others that support OAuth). The client opens the Sweeprice sign-in page, you approve the connection, and the tools appear. Step-by-step instructions: [sweeprice.com/en/docs/connect-claude](https://www.sweeprice.com/en/docs/connect-claude).

`initialize` and `tools/list` answer without a token, so a client or a directory can read the tool catalog before signing in. Every tool call requires a signed-in account.

## Tools

| Tool | What it does |
|---|---|
| `get_account_summary` | Subscription state, plan limits, number of tracked products, default line mode, permissions |
| `list_tracked_products` | Tracked products with their collection state, marketplaces and last reading |
| `get_product_offers` | Current offers of one product, cheapest first: seller, marketplace, price, shipping, Buy Box |
| `get_product_price_history` | One entry per day over 1 to 90 days: rank, gap to the best price, offers |
| `list_price_positions` | Account-wide position: Buy Box, top 1 to 3 counts, average rank, gap to the best price |
| `list_recommended_prices` | Prices Sweeprice currently recommends, per marketplace, with the basis of each |
| `list_alerts` | Price alerts: product, marketplace, previous and new price and rank |
| `list_notifications` | Undercut, Buy Box won, price drop, price rise, first collection, action needed |
| `mark_notifications_read` | Marks notifications as read |
| `add_tracked_product` | Adds a product from a marketplace URL or a GTIN and starts collecting it |
| `set_product_line_mode` | Sets what Sweeprice does with one product: alert only, repricing, or win the featured offer |
| `set_product_price_bounds` | Sets the floor and ceiling prices that a recommended price never crosses |

## Example questions

- "Which of my Cdiscount listings lost the Buy Box this week?"
- "Show the competing offers and the recommended price for GTIN 4014549312148."
- "Set a floor price of 82 EUR on my Bosch GSR 12V listing."

## Pricing

Plans start at $83 per month billed yearly ($990 per year), or $99 month to month, for 500 products, every marketplace included. In euros: €74 per month billed yearly (€890 per year), or €89 month to month, excl. VAT. Details: [sweeprice.com/en#pricing](https://www.sweeprice.com/en/#pricing).

## Listings

- Official MCP Registry: `com.sweeprice/sweeprice`
- [Claude connector directory](https://claude.ai/directory/sweeprice)
- [Glama](https://glama.ai/mcp/connectors/com.sweeprice/sweeprice)
- [mcptry](https://mcptry.com/servers/com.sweeprice/sweeprice)

## Contact

contact@sweeprice.com. [Terms of use](https://www.sweeprice.com/en/terms-of-use), [privacy policy](https://www.sweeprice.com/en/privacy-policy), [legal notice](https://www.sweeprice.com/en/legal-notice).
