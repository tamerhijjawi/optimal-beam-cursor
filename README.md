# Optimal Beam for Cursor

Connect Cursor to Optimal Beam for beam analysis and steel-section lookup. The plugin uses the hosted service at **https://mcp.optimalbeam.com/cursor/mcp**. No Optimal Beam account, API key, local solver, or additional dependency is required.

## Install

Install this public package locally using [Cursor's plugin instructions](https://cursor.com/docs/plugins):

```sh
git clone https://github.com/tamerhijjawi/optimal-beam-cursor.git ~/.cursor/plugins/local/optimal-beam
```

Reload Cursor, then open **Customize → Plugins** and confirm Optimal Beam is enabled. If that folder already exists, update the existing checkout rather than cloning over it. Review tool permissions when Cursor requests them.

Alternatively, add the following remote server to your existing Cursor MCP configuration, preserving any other servers. Use either installation method to avoid duplicate connections:

```json
{
  "mcpServers": {
    "optimal-beam": {
      "url": "https://mcp.optimalbeam.com/cursor/mcp"
    }
  }
}
```

A public repository does not mean Cursor Marketplace approval. Marketplace availability is controlled by Cursor's review process.

## Try it

> Use Optimal Beam to analyze a 6 m beam, pinned at 0 m and roller-supported at 6 m, with a 10 kN downward point load at 3 m. Use E = 200,000 MPa, I = 200,000,000 mm⁴, area = 5,000 mm², and top/bottom fiber distances of 100 mm. Exclude self-weight. Give reactions, maximum moment and deflection, and a link to open the model in Optimal Beam.

The reference result has 5 kN reaction magnitudes, 15 kN·m peak moment and 1.125 mm downward deflection. Ask to double the point load, inspect another position, or compare steel candidates. Explicitly state your material properties, support conditions, loads, units, and self-weight treatment; review any assumptions returned by the tools.

## Tools

| Tool | Purpose |
| --- | --- |
| `analyze_beam` | Calculate reactions, shear, moment, slope, deflection and available stresses. |
| `show_beam_results` | Retrieve a calculation snapshot, full numerical results and calculator links. |
| `search_steel_sections` | Search steel catalogs by designation or property filters. |
| `get_steel_section` | Retrieve a specific section's dimensions and properties. |
| `find_steel_alternatives` | Find nearby sections for comparison. |
| `show_steel_sections` | Display section properties and catalog links. |
| `compare_steel_sections` | Analyze candidate sections against the same beam and stated limits. |

All tools perform read-only lookups or calculations. They do not modify saved models or accounts. Cursor receives complete text and structured results; an embedded interactive chart is not required. Calculator links carry `source=cursor` and reproduce the model on the website.

## Data, limits and support

Tool calls send the model inputs or section query selected by your assistant to Optimal Beam's hosted service. Calculation snapshots remain in bounded server memory for up to 30 minutes and are cleared on restart. An expired result must be recalculated. Rate limits are shared with the other Optimal Beam connectors; retry a busy request later. The plugin does not require local file access, shell commands, login credentials or hooks. Your AI client may have its own tools and permissions.

Calculations depend on the supplied model and assumptions and require appropriate engineering review. The calculator website's account features and plans are separate from this free connector.

- [Support and service details](https://optimalbeam.com/plugin-support.html)
- [Privacy](https://optimalbeam.com/privacy.php)
- [Terms](https://optimalbeam.com/terms.php)
- Support: contact@optimalbeam.com

## License

The MIT license covers the files in this plugin repository. It does not license the remotely hosted Optimal Beam service, solver, or website. Optimal Beam's name and logo identify the service; the license does not grant trademark rights or imply endorsement of modified packages.
