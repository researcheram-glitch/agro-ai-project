# agro-ai-project

Simple Python project structure for an agronomy AI workflow that:
- reads CSV scouting data,
- calculates weed risk score per field,
- prepares data for visualization.

## Project Structure

```text
agro-ai-project/
├── data/
│   └── scouting_sample.csv
├── src/
│   └── agro_ai/
│       ├── __init__.py
│       ├── io.py          # CSV ingestion + schema checks
│       ├── risk.py        # Weed risk scoring logic by field
│       ├── viz_prep.py    # Visualization-ready output payloads
│       └── main.py        # Pipeline entrypoint
└── pyproject.toml
```

## Quick Start

```bash
python -m pip install -e .
python -m agro_ai.main
```

## Data Contract

Input CSV should include:
- `field_id`
- `weed_density` (0-100)
- `weed_species_count` (integer)
- `crop_stage` (`emergence`, `vegetative`, `reproductive`, `maturity`)

## Pipeline Overview

1. `read_scouting_csv` loads and validates scouting data.
2. `calculate_weed_risk_by_field` computes a field-level weed risk score and risk level.
3. `prepare_field_risk_viz_data` creates chart-ready records (`bar_chart`, `risk_distribution`).
