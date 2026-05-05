# inMóvil — Real Estate & Vehicle Marketplace

An Android application for browsing and searching real estate listings (houses, apartments, offices, land) and vehicles, built for the Latin American market.

---

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/b1a868c6-bd85-4cb7-9acb-c3ce47537486" width="200"></td>
    <td><img src="https://github.com/user-attachments/assets/2ab7ecb7-de35-42df-b589-9f1520ef9392" width="200"></td>
    <td><img src="https://github.com/user-attachments/assets/70b779d6-d4a1-44ec-a70d-081fe94d9b97" width="200"></td>
    <td><img src="https://github.com/user-attachments/assets/fd70a65f-63b3-4d7e-afc8-63f9720b80b4" width="200"></td>
  </tr>
</table>



## Features

- Browse properties by category: houses, apartments, offices, and land
- Filter listings by transaction type: sale, rental, or anticretico financing
- Advanced search with price range, surface area, rooms, and bathrooms filters
- Vehicle listings with filters for type, brand, model, year, and mileage
- Property and vehicle detail views with photo galleries and interactive maps
- Click-to-call contact integration for direct inquiries
- Image gallery with zoom and pan support

---

## Tech Stack

| Layer         | Technology                                           |
| ------------- | ---------------------------------------------------- |
| Language      | Java                                                 |
| Min SDK       | 19 (Android 4.4 KitKat)                              |
| Target SDK    | 25 (Android 7.1 Nougat)                              |
| Networking    | Volley                                               |
| Maps          | Google Maps SDK for Android                          |
| UI            | Android Support Library, ConstraintLayout, ViewPager |
| Image Loading | Volley ImageLoader + LruCache                        |
| Local Storage | SharedPreferences                                    |
| HTTP Requests | Custom AsyncTask with delegate callbacks             |

---

## Architecture

Activity-based architecture with a custom callback pattern for asynchronous HTTP operations.

- Activities handle UI rendering and business logic
- `HttpPost` wraps AsyncTask network calls and surfaces results through `HttpPostInterface` (success/error callbacks)
- `MySingleton` manages a shared Volley `RequestQueue` and `ImageLoader` instance
- Model objects (`Casa`, `Vehiculo`) implement `Serializable` for Intent-based navigation
- `SharedPreferences` stores server-provided filter boundaries (e.g., max price)

---

## Project Structure

```
app/src/main/java/com/roscosoft/inmovil/
├── Activities
│   ├── InicioActivity.java        # Home screen with animated category selector
│   ├── CasasSubActivity.java      # Transaction type selector
│   ├── CasasActivity.java         # Property listings
│   ├── CasaActivity.java          # Property detail (gallery, map, contact)
│   ├── VehiculosActivity.java     # Vehicle listings
│   ├── VehiculoActivity.java      # Vehicle detail
│   ├── BuscarInmActivity.java     # Advanced property search
│   ├── BuscarVehiActivity.java    # Advanced vehicle search
│   ├── ContactoActivity.java      # Contact information
│   └── InfoActivity.java          # About screen
├── Models
│   ├── Casa.java                  # Property data model
│   └── Vehiculo.java              # Vehicle data model
├── Networking
│   └── HttpPost.java              # Async HTTP POST with callback interface
├── Adapters
│   └── ImgsPagerAdapter.java      # ViewPager adapter for photo galleries
└── Utils
    ├── MySingleton.java            # Volley singleton
    ├── DownloadImageTask.java      # Async image downloader
    └── RangeBar/                   # Custom range slider widget
```

---

## Getting Started

### Prerequisites

- Android Studio (Arctic Fox or later recommended)
- Android SDK 25
- Google Maps API key

### Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/ruizricardo/Inmovil-app.git
   ```

2. Open the project in Android Studio.

3. Add your Google Maps API key in `AndroidManifest.xml`:

   ```xml
   <meta-data
       android:name="com.google.android.geo.API_KEY"
       android:value="YOUR_API_KEY_HERE" />
   ```

4. Build and run on a device or emulator (API 19+).

---

## License

This project is for portfolio purposes. All rights reserved.
