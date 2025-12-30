# 🎣 FishCast Pro v2

**Real-time fishing intelligence platform** combining water conditions, weather data, solunar forecasting, and live nature cameras into one comprehensive dashboard.

![FishCast Pro](https://img.shields.io/badge/version-2.0-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Status](https://img.shields.io/badge/status-active-success)

## ✨ Features

### 📊 Fishing Score Algorithm
Calculates a 0-100 score based on real-time conditions:
- **Moon Phase** - Solunar activity rating
- **Barometric Pressure** - Low pressure = better fishing
- **Wind Speed** - Calm conditions preferred
- **Air & Water Temperature** - Ideal range bonuses
- **Stream Flow** - Active gauge data nearby

*Expandable breakdown shows exactly how each factor contributes to the score.*

### 🗺️ Interactive Map
- **5 Base Layers**: Dark, Satellite, Topographic, Streets, Nautical
- **Weather Overlays**: Radar, Cloud Cover, Temperature, Wind
- **Animated Radar**: Play/pause precipitation movement
- **Click anywhere** to analyze that location

### 💧 Water Data (USGS)
- Stream flow (discharge in cfs)
- Gage height
- Water temperature
- Turbidity
- 10,000+ gauges nationwide

### 🌊 Tide Information (NOAA)
- Real-time water levels
- Tide predictions
- Coastal station data

### ⛅ Weather (NWS)
- Current conditions
- Hourly forecast
- Barometric pressure
- Wind speed & direction
- Cloud cover predictions

### 🌙 Solunar Calendar
- Moon phase display
- Major/minor feeding periods
- Activity rating percentage

### 📷 Live Cameras
**100+ curated nature webcams including:**

| Source | Coverage |
|--------|----------|
| **USGS Volcano Observatory** | Kīlauea, Mauna Loa, Mt. St. Helens, Yellowstone geysers, Alaska volcanoes |
| **National Park Service** | 30+ parks - Yellowstone, Yosemite, Grand Canyon, Glacier, etc. |
| **Explore.org** | Brooks Falls bears, eagles, manatees, marine life |
| **Regional** | Beaches, harbors, mountains, state parks |

### 📝 Community Notes
- Rate locations (1-5 stars) across 4 categories
- Share notes with other users
- Clustered markers for multiple notes
- Persistent local storage

---

## 🚀 Quick Start

### Option 1: Use Directly
1. Download `index.html` from this repository
2. Open in any modern web browser
3. Click on the map to start exploring

### Option 2: Host on GitHub Pages
1. Fork this repository
2. Go to Settings → Pages
3. Select Branch: `main`, Folder: `/ (root)`
4. Your site will be live at `https://YOUR-USERNAME.github.io/fishcast-pro/`

### Option 3: Embed in Your Website
```html
<iframe 
  src="https://YOUR-USERNAME.github.io/fishcast-pro/"
  style="width: 100%; height: 900px; border: none; border-radius: 12px;"
  allow="geolocation"
></iframe>
```

---

## 📖 How to Use

1. **Select Location**: Click anywhere on the map
2. **Adjust Radius**: Use the slider to change search area (5-100 miles)
3. **View Score**: See the fishing score and click "View Score Breakdown" for details
4. **Explore Tabs**:
   - **Overview** - Score, solunar, cloud forecast
   - **Water** - USGS stream gauges
   - **Tides** - NOAA tide stations
   - **Weather** - Current & forecast conditions
   - **Cameras** - Live nature webcams
   - **Notes** - Save & share location notes
5. **Toggle Layers**: Change map style or enable weather overlays
6. **Animate Weather**: Click play to see radar/cloud movement

---

## 🛠️ Technical Details

### Built With
- **Vanilla JavaScript** - No frameworks required
- **Leaflet.js** - Interactive mapping
- **Leaflet.markercluster** - Note clustering

### Data Sources (All Free, No API Keys Required)
| Service | Data Provided |
|---------|---------------|
| [USGS Water Services](https://waterservices.usgs.gov/) | Stream flow, gage height, water temp |
| [NOAA Tides & Currents](https://tidesandcurrents.noaa.gov/) | Tide predictions, water levels |
| [NWS Weather API](https://www.weather.gov/documentation/services-web-api) | Forecasts, current conditions |
| [RainViewer](https://www.rainviewer.com/api.html) | Weather radar, satellite imagery |
| [OpenWeatherMap](https://openweathermap.org/) | Temperature & wind tiles |
| [OpenStreetMap](https://www.openstreetmap.org/) | Base map tiles |

### Browser Support
- Chrome (recommended)
- Firefox
- Safari
- Edge

### File Structure
```
fishcast-pro/
├── index.html          # Main application (single file)
├── README.md           # This file
└── SQUARESPACE_SETUP.md # Detailed deployment guide
```

---

## 📱 Responsive Design

Works on desktop, tablet, and mobile devices with adaptive layouts:
- **Desktop**: 3-column layout (sidebar, map, data panel)
- **Tablet**: Adjusted proportions
- **Mobile**: Stacked single-column view

---

## 🔧 Customization

### Change Default Location
Edit the map initialization in `index.html`:
```javascript
const map = L.map('map').setView([39.8283, -98.5795], 5);
//                                 ↑ lat    ↑ lng   ↑ zoom
```

### Adjust Score Weights
Modify the `calculateFishingScore()` function to change how factors contribute:
```javascript
// Example: Make pressure more important
if (pressure < 1010) {
    pressurePoints = 15;  // Changed from 10
    score += 15;
}
```

### Add More Cameras
Extend the `webcamDatabase` object in `getRegionalWebcams()`:
```javascript
'YOUR_STATE': [
    { 
        id: 'unique-id', 
        name: 'Camera Name', 
        type: 'Wildlife', 
        lat: 40.0, 
        lng: -100.0, 
        embedUrl: 'https://...', 
        source: 'Source Name' 
    }
]
```

---

## 📄 License

MIT License - Feel free to use, modify, and distribute.

---

## 🙏 Credits

- Weather data: [National Weather Service](https://www.weather.gov/)
- Water data: [USGS](https://www.usgs.gov/)
- Tide data: [NOAA](https://www.noaa.gov/)
- Wildlife cams: [Explore.org](https://explore.org/)
- Volcano cams: [USGS Volcano Hazards Program](https://www.usgs.gov/programs/VHP)
- Map tiles: [OpenStreetMap](https://www.openstreetmap.org/), [CARTO](https://carto.com/), [Esri](https://www.esri.com/)

---

## 🐛 Known Limitations

- **Shared Notes**: Currently uses localStorage (demo mode). Production deployment requires a backend server.
- **Camera Availability**: Live streams depend on third-party sources and may occasionally be offline.
- **US Coverage Only**: USGS and NWS data limited to United States.
- **Weather Radar**: RainViewer provides ~2 hours of past data and ~2 hours of forecast.

---

## 💡 Future Ideas

- [ ] Backend API for true shared notes
- [ ] User accounts & authentication
- [ ] Fish species database
- [ ] Catch logging & statistics
- [ ] Push notifications for optimal conditions
- [ ] Offline mode (PWA)
- [ ] Historical data charts

---

**Made for anglers who want every advantage.** 🎣

