# Global Data Center Atlas

An interactive web map of **10,000+ data centers** across 157 countries,
built with [Leaflet.js](https://leafletjs.com) and hosted on GitHub Pages.

## Files in this repository

| File | Description |
|------|-------------|
| `index.html` | The map — everything runs in this one file |
| `datacenters.geojson` | All data center locations and metadata |

## How to publish on GitHub Pages

1. **Create a GitHub account** at github.com if you don't have one.

2. **Create a new repository** — click the **+** button top-right → *New repository*.
   Name it anything (e.g. `datacenter-atlas`). Set it to **Public**.

3. **Upload both files** — on the repository page click *Add file → Upload files*,
   drag in `index.html` and `datacenters.geojson`, then click *Commit changes*.

4. **Enable GitHub Pages** — go to *Settings → Pages*, under *Source* choose
   **Deploy from a branch**, select **main** and **/ (root)**, click *Save*.

5. **Wait ~60 seconds**, then your map is live at:
   ```
   https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
   ```
   Share that URL with anyone — no account required to view it.

## Map features

- **Clustered pins** — groups nearby data centers at world zoom, expands as you zoom in
- **Colour-coded by precision**
  - 🟢 Green — exact street address geocoded
  - 🟡 Yellow — city / town level
  - 🔴 Red — country centre (no city found)
- **Search** — filter by name, country, or address
- **Country filter** — jump to all data centers in a specific country
- **Popups** — click any pin to see name, address, specs, description, and a link back to datacenters.com

## Updating the data

Run the pipeline scripts to regenerate the data files, then re-upload
`datacenters.geojson` (and optionally the KML for Google Earth).

```bash
python enrich_addresses.py   # search for missing addresses (~3 hrs)
python make_kml.py           # geocode + export KML + GeoJSON (~3 hrs)
```

Then drag the new `datacenters.geojson` into the GitHub repository
(it will replace the old one automatically).

## Data source

Data scraped from [datacenters.com](https://www.datacenters.com) —
a public directory of data center facilities worldwide.
Geocoding via [OpenStreetMap Nominatim](https://nominatim.org).
