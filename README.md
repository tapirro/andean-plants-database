# Andean & Latin American Medicinal Plants Database

An open dataset of 250 medicinal plants used across the Andes, Amazon, and broader Latin America. Includes scientific names, common names in Spanish and English, traditional uses, and cross-references to drug interaction data.

**[Browse the encyclopedia](https://botanicaandina.com/noticias/)** | **[Check drug interactions](https://botanicaandina.com/herramientas/interacciones/)** | **[Botanica Andina](https://botanicaandina.com)**

## Dataset

### plants.json

250 medicinal plants with:

| Field | Description |
|-------|-------------|
| `id` | Unique identifier |
| `name` | Common name (Spanish) |
| `scientific` | Binomial nomenclature |
| `aliases` | Alternative names (Spanish, English, indigenous languages) |
| `article` | Link to detailed monograph on Botanica Andina |

### drug_interactions.json

592 documented interactions between these plants and 53 drug classes, sourced from:
- EMA/ESCOP herbal monographs
- PubMed Central systematic reviews
- WHO monographs on medicinal plants
- TRAMIL database

## Coverage

This database covers plants that are underrepresented in English-language pharmacological databases:

- **Andean highlands**: maca, quinoa, canihua, kiwicha, muña, coca
- **Amazon basin**: cat's claw, sangre de drago, sacha inchi, ayahuasca, chuchuhuasi
- **Central America & Caribbean**: chanca piedra, guanabana, moringa
- **Widely used**: turmeric, ginger, valerian, St. John's Wort, ginkgo

## Usage

```python
import json

plants = json.load(open("data/plants.json"))

# Find all plants with "claw" in aliases
results = [p for p in plants if any("claw" in a.lower() for a in p["aliases"])]

# Find Andean plants by scientific name pattern
andean = [p for p in plants if "Lepidium" in p["scientific"] or "Chenopodium" in p["scientific"]]
```

## Contributing

If you know of documented medicinal plants from Latin America that are missing from this database, open an issue with:
1. Scientific name
2. Common names (any language)
3. At least one published reference (PubMed, WHO, or equivalent)

## License

MIT License. Free to use for research, education, and application development.

## About

Maintained by [Botanica Andina](https://botanicaandina.com) -- evidence-based research on Latin American medicinal plants.

Related tools:
- [Herb-Drug Interaction Checker](https://github.com/tapirro/herb-drug-interaction-checker) -- check interactions between these plants and medications
- [Live tool](https://botanicaandina.com/herramientas/interacciones/) -- browser-based interaction checker
