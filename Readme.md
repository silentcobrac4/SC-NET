# SC NET — Network & Wi-Fi Utility Suite 🚀

![SC NET Icon](sc-net-android/app/src/main/res/mipmap-xxhdpi/ic_launcher.png)

**SC NET** (`com.scnet.networktool`) is a full-featured, original Android network diagnostic and Wi-Fi utility suite built with Kotlin. Designed with a sleek dark green theme matching the custom cobra icon, it offers 16 diagnostic and management tools for local and wide-area networks.

---

## 🛠️ Included Features (1–16)

### 📡 1. Network & Connection Diagnostics
1. **Network Overview:** Live inspection of active transports (Wi-Fi, Cellular, Ethernet), IPv4/IPv6 addresses, subnet prefix lengths, default gateways, system DNS servers, and network interface names.
2. **Wi-Fi Inspector:** Real-time Wi-Fi details including SSID, BSSID, RSSI (signal strength in dBm with dynamic visual indicator), Link Speed (Mbps), frequency band (2.4 GHz / 5 GHz / 6 GHz), and Wi-Fi channel calculation.
3. **Public IP & ASN Lookup:** Fetches your external IP address, Internet Service Provider (ISP) / Autonomous System Number (ASN), country/city location, and timezone via external lookup.
4. **Network Event History:** Tracks and logs connection state transitions (connection available/lost events) with local timestamps.

### 🔍 2. Subnet Scanning & Host Tools
5. **LAN Subnet Scanner:** Scans the active IPv4 local network to discover reachable devices and hostnames.
6. **OUI / Vendor Lookup:** Resolves hardware manufacturer prefixes (OUI) from MAC addresses when available.
7. **Device Tagging:** Distinguishes between user-defined "Trusted" devices and newly discovered network hosts.
8. **TCP Port Scanner:** Probes target IP addresses across custom lists of TCP ports (e.g., `22, 53, 80, 443`).

### ⚡ 3. Diagnostics & Speed Testing
9. **Ping Tool:** Measures ICMP/Socket reachability, packet loss percentage, and round-trip times (Min, Avg, Max RTT in ms).
10. **DNS Resolver:** Queries domain DNS records (`A/IPv4`, `AAAA/IPv6`) with profile selections (`System DNS`, `Cloudflare 1.1.1.1`, `Google 8.8.8.8`).
11. **Traceroute Probes:** Evaluates reachability hops and delay timings towards a target host.
12. **Download Speed Test:** Benchmarks current network throughput (Mbps) by downloading test payloads from public endpoints.

### 🛠️ 4. Network Utilities & Preferences
13. **IP & Subnet Calculator:** Computes CIDR network addresses, subnet masks, broadcast addresses, total usable hosts, and IP ranges.
14. **Wake-on-LAN (WOL):** Sends UDP Magic Packets to wake configured MAC addresses across the local broadcast domain.
15. **Report Exporter:** Saves all network scan outputs, diagnostic results, and configuration summaries as formatted `.txt` or structured `.json` files in app internal storage.
16. **Custom Dark Theme & Persistent State:** Modern green/black UI optimized for modern Android displays, with automatic saving of target hosts, port ranges, and CIDR preferences.

---

## 📂 Project Structure

```text
.
├── app-source.zip                  # Full source zip archive
├── build-release.yml               # GitHub Actions CI/CD release workflow
├── README.md                       # Main project documentation
├── release_notes.txt               # Release notes for GitHub Releases
└── sc-net-android/                 # Android source directory
    ├── build.gradle.kts
    ├── settings.gradle.kts
    ├── gradlew / gradlew.bat
    ├── .github/workflows/
    │   └── build-release.yml
    └── app/
        ├── build.gradle.kts
        └── src/main/
            ├── AndroidManifest.xml
            ├── java/com/scnet/networktool/
            │   ├── MainActivity.kt
            │   └── NetworkEngine.kt
            └── res/                # Layouts, colors, themes, launcher icons
```

---

## 🏗️ How to Build

### Option A: Automated Build via GitHub Actions (Recommended)

1. Upload `app-source.zip` and `.github/workflows/build-release.yml` to your GitHub repository root.
2. Push a git release tag starting with `v` (e.g., `v1.0.0`):
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
3. GitHub Actions will automatically unzip the source, compile the APK using `./gradlew assembleRelease`, upload the APK artifact, and publish a GitHub Release with the APK attached.

### Option B: Local Manual Build

**Prerequisites:** JDK 17+ and Android SDK 34 (Android 14) installed.

1. Unzip `app-source.zip` locally.
2. Open terminal in `sc-net-android/`:
   ```bash
   cd sc-net-android
   ./gradlew assembleRelease
   ```
3. The generated release APK will be located at:
   `app/build/outputs/apk/release/app-release.apk`

---

## 🔐 Permissions & Android Limits

* **Permissions Used:** `INTERNET`, `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE`, `ACCESS_FINE_LOCATION`, `NEARBY_WIFI_DEVICES`.
* **Privacy Notes:** Modern Android OS versions restrict full MAC address visibility for remote devices on local subnets for user privacy. Local interface details require Location/Nearby permission approval at runtime.

---

## 📜 License

This project is open-source under the [MIT License](sc-net-android/LICENSE).
