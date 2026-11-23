# pumpfunsteve

A Claude Code agent that profiles pump.fun traders and callers (e.g. `bestcook`) using the
[pump.fun MCP server](https://docs.pump.fun/mcp/).

It is a research agent. The pump.fun MCP is read-only social and PnL data, so the agent
cannot trade and has no price, liquidity or on-chain data.

## Setup

1. Get a `pf_live_...` API key. Access is by approval in the pump.fun developer console
   (https://docs.pump.fun/getting-started/). Default limits: 2 req/s, 50,000 req/day.
2. Export it and start Claude Code in this repo:

   ```bash
   export PUMP_API_KEY=pf_live_...
   claude
   ```

   `.mcp.json` wires up `https://mcp.pump.fun/mcp` with a bearer header from `PUMP_API_KEY`.
   Never commit the key.
3. Check `/mcp` shows `pump` connected. Note: a wrong but well-formed key connects fine
   and only fails on the first tool call.

## Use

```
Use the memecoin-analyst agent to profile bestcook
```

Reports are written to `reports/<handle>-<date>.md`.

## What it checks

Callout hit rate and median multiple, dependence on one lucky call, whether tailers
actually profit, whether the caller was pre-loaded and sold into the callout, PnL
consistency, copyability at realistic entry, and signs of a botted audience or
repeat wallet cluster.
