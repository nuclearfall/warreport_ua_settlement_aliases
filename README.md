# War Report UA Settlement Aliases — OSINT-Focused Ukrainian Gazetteer

## 📘 What is `warreport_ua_settlement_aliases_lookup.csv`?

`warreport_ua_settlement_aliases_lookup.csv` is a **curated, high-precision gazetteer of Ukrainian settlements**, designed specifically for OSINT workflows that rely on text-extracted geographic references. It consolidates thousands of locality entries across Ukraine and provides:

- **Official endonyms** (Ukrainian names)
- **Common exonyms** (Russian, Soviet-era, and colloquial variants)
- **Proper English transliterations** from both Ukrainian and Russian
- **War-report transliterations** seen in Telegram channels, military communiqués, and field reports
- **Geo-coordinates** normalized to 6-decimal precision
- **Administrative alignment** (oblast, raion, hromada when available)
- **Wikidata IDs + OSM feature IDs**, when known
- **Coordinate ID** a uniuqe 64 bit encoded id based on the coordinates.

This dataset is built to solve a very specific problem in OSINT: *machine extraction of location names from messy, multilingual war-reporting text where the same village may appear under half a dozen spellings or legacy names.*

---

## ⭐ Why this file is useful to the OSINT community

### **1. Resolves location ambiguity across languages**
Ukrainian, Russian, Soviet, and transliterated English spellings often refer to the *same* place.  
`warreport_ua_settlement_aliases_lookup.csv` links them all to a **single canonical entry**, making automated mapping dramatically more accurate.

Example:
```
Myrne · Мирне · Мирное · Mirne · Mirnoye · Petrovske · Petrovskoye
→ all resolve to one unique settlement
```

---

### **2. Designed for real-world war-reporting text**
Unlike academic or governmental gazetteers, this file includes:

- telegram-style spellings and errors
- frontline-specific naming conventions
- operational grouping context (“in the direction of …”)
- commonly mis-transliterated variants used by analysts and bots

It is tuned for the *actual text* analysts see every day.

---

### **3. Battle-tested in automated NLP pipelines**
The dataset was built as a core component of the **sitrepc2 OSINT engine**, supporting:

- Named-entity matching (spaCy/Holmes)
- Geolocation disambiguation
- Event clustering
- Frontline and operational-zone mapping
- Map rendering (KML/GeoJSON)

It is optimized to avoid duplicates, normalize aliases, and ensure deterministic lookup.

---

### **4. Provides a stable, canonical reference for cross-project use**
This repository offers:

- a low-friction dependency (submodule-friendly)
- high-quality ID alignment (OSM + Wikidata)
- consistent updates tuned to real-time reporting

It is useful for analysts, bot developers, journalists, academic researchers, and anyone performing location extraction from conflict reporting.

---

### **5. Fills a gap no existing gazetteer covers**

Public gazetteers (OSM, Geonames, Wikidata) do **not**:

- unify Ukrainian + Russian + English wartime transliterations  
- remove conflicting duplicates  
- normalize battlefield naming  
- guarantee deterministic text-matching  
- incorporate OSINT-specific usage patterns  

This file does.

---
### ⚠️ What this file does *not* solve

`locale_lookup.csv` is a powerful alias and normalization table, but it is **not** a complete geolocation engine. In particular, it does **not**:

- Perform **disambiguation** between multiple settlements that share the same name.
- Decide which location is correct in a given narrative context  
- Infer meaning from surrounding text ("near", "towards", "in the area of…")  
- Rank candidates by proximity, frontline relevance, or operational direction  
- Provide real-time verification of whether a settlement is occupied, contested, or inactive

It is a *lookup foundation*, not a reasoning system. Disambiguation must be done by an NLP pipeline, ruleset, or analyst using the normalized output this file provides.

**NOTE:**  
*If you are interested in how these challenges are addressed in practice, take a look at the **sitrepc2** project. Though still under construction, most of the groundwork has already been laid. At the NLP level (referred to as the **LSS layer** — Lexical-Syntactic-Semantic), the pipeline uses the **spaCy**, **coreferee**, and **holmes-extractor** libraries and their associated models to handle the heavy lifting of parsing and interpreting text. This includes identifying real events, determining which locations are associated with those events, and distinguishing between true geo-referencing and mere contextual mentions.*


## 🧭 Summary

`warreport_ua_settlement_aliases_lookup.csv` is a **purpose-built, OSINT-focused settlement lookup table** for Ukraine, enabling reliable multilingual geolocation normalization.

If you work in OSINT—mapping, NLP extraction, event analysis, or bot development—this dataset can serve as a dependable foundation for geographic normalization in your own projects.

