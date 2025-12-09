# personal-ml-gca

Goal Context Abstraction (GCA) for distributed personal ML setups across phone, tablet, laptop/desktop, and an optional cloud container.

## What this is

An experiment in orchestrating small/local ML models ("MLMs") around a shared, goal-centric state:

- **Devices**: phone, tablet, laptop/desktop, cloud container (plus optional PDA/assistant as a black-box endpoint)
- **Contexts**:
  - Local (device-specific: battery, network, sensors, compute)
  - Distributed (user-shared: prefs, history)
  - Goal (task-agnostic JSON describing what the user is trying to achieve)

## Core idea: Goal Context Abstraction (GCA)

A small, synced JSON document:

```json
{
  "goal_id": "string",
  "state": {
    "progress": 0.0,
    "metadata": {}
  },
  "timestamp": "ISO-8601"
}
```

Each device:

1. Pulls the current GCA
2. Adapts it based on local context (phone vs laptop vs cloud)
3. Pushes an updated GCA back to shared storage

## Examples

See `examples/` for concrete GCA instances:

- `gca-meal-planning.json` – "meal planning for my new diet"
- `gca-pii-redaction.json` – "keeping on top of privacy across my devices"
- `gca-news-blindspot.json` – "blind spot analysis for my news/social media habits"

## Status

Early design / thought experiment:

- Goal discovery: explicit text prompt + confirmation
- Architecture: sketched (triple context + shared KV store + transparent sync lag)
- Gaps: adaptation logic, conflict resolution, local context schema, privacy model

See `docs/design-note-v1.md` for the current design snapshot.

## License

TBD.
