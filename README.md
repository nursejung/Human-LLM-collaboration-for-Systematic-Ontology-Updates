# Human-LLM Collaboration for Systematic Ontology Updates

This notebook implements a Human-LLM collaborative system for ontology updates.

## Directory Structure

Before running the project, create the following directory structure:

```
project/
├── Human-LLM_collaboration_for_Systematic_Ontology_Updates.ipynb
├── data/
│   ├── final_with_n_prefix.txt          # Input hierarchy text file
│   ├── DILON_1.csv                      # First DILON CSV file
│   ├── DILON_2.csv                      # Second DILON CSV file (auto-generated)
│   ├── DILON_merged.csv                 # Merged CSV file (auto-generated)
│   ├── DILON_merged_with_hierarchy.csv  # CSV with hierarchy levels (auto-generated)
│   ├── DILON_merged_with_hierarchy.owl  # OWL format output (auto-generated)
│   ├── DILON_merged_with_hierarchy.ttl  # Turtle format output (auto-generated)
│   ├── DILONv0.2.ttl                    # Existing ontology with annotations
│   ├── DILON_annotation_merged_original.ttl  # Final merged result (auto-generated)
│   └── DILON_annotation_merged_original.owl  # Final merged result in OWL (auto-generated)
└── README.md
```

## Required Libraries

```bash
pip install pandas openpyxl rdflib
```

## Usage

### 1. Parse Hierarchy Text
- Input: `data/final_with_n_prefix.txt`
- Output: `data/DILON_2.csv`
- Converts hierarchy text (with `>` separators) into Superclass-Subclass relationships

### 2. Merge CSV Files
- Input: `data/DILON_1.csv`, `data/DILON_2.csv`
- Output: `data/DILON_merged.csv`
- Merges two CSV files and removes duplicates

### 3. Expand Hierarchy and Convert to OWL
- Input: `data/DILON_merged.csv`
- Output: 
  - `data/DILON_merged_with_hierarchy.csv`
  - `data/DILON_merged_with_hierarchy.owl`
  - `data/DILON_merged_with_hierarchy.ttl`
- Expands the hierarchy structure and converts to OWL/Turtle formats

### 4. Merge Annotations
- Input: 
  - `data/DILONv0.2.ttl` (existing annotations)
  - `data/DILON_merged_with_hierarchy.ttl` (new hierarchy structure)
- Output:
  - `data/DILON_annotation_merged_original.ttl`
  - `data/DILON_annotation_merged_original.owl`
- Merges annotations from the existing ontology into the new hierarchy structure

## Notes

- All input files should be located in the `data/` directory
- Execute each notebook cell in order
- Each step uses the output from the previous step as input
