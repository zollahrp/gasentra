# GASENTRA — 3D Digital Twin & Smart LPG Telemetry System
> **Tagline:** Sistem Cerdas Pemantau Kebocoran, Keaslian Isi, dan Konsumsi LPG Langsung di Tingkat Tabung.  
> **Slogan:** *Aman. Utuh. Terpakai. Siap Beralih ke Energi Bersih.*  
> **Konteks:** CATALYST SUMMIT 2026 — Business Plan Competition (SRE Universitas Airlangga)  
> **Pilar HORIZON:** Resilient, Inclusive, Zero-carbon, Networks

---

## 🌟 Tentang Prototipe GASENTRA

GASENTRA adalah sistem Internet of Things (IoT) cerdas yang dirancang untuk mengatasi 3 titik buta (*blind spots*) utama dapur komersial dan UMKM pengguna LPG di Indonesia:
1. **Risiko Keselamatan (94,7% Kasus Luka Bakar Ledakan):** Detektor konvensional hanya memberi tahu bahwa ada gas di ruangan, **bukan tabung mana sumbernya**. GASENTRA menunjuk langsung tabung bermasalah dan memutus alirannya dalam &lt;2.8 detik.
2. **Kecurangan Isi & Oplosan (Rp 19,25 Miliar Kerugian):** Pengurangan isi di SPBE dan pengoplosan LPG 3 kg subsidi ke 12 kg/50 kg non-subsidi. GASENTRA menimbang otomatis tabung baru dipasang (*Cek Isi Tabung*) dan mencatat reputasi agen.
3. **Pemborosan Energi Tak Terukur:** Tabung ditukar sebelum gas benar-benar habis, kompor menyala tanpa pesanan (*ghost burner*), dan ketiadaan kalkulasi HPP biaya gas per menu.

---

## 🛠️ Konfirmasi Arsitektur Hardware: 2 Perangkat Fisik

Sesuai konfirmasi dokumen teknis dan konsep sistem, perangkat keras GASENTRA terdiri dari **2 UNIT FISIK TERPISAH**:

### 1. Perangkat 1: Modul Sensor Gas + Timbangan per Tabung (*GASENTRA Smart Base Pad*)
- **YA, INI ADALAH 1 ALAT/UNIT TERINTEGRASI** berbentuk piringan alas (*disc base*) heavy-duty yang diletakkan langsung di bawah setiap tabung LPG (kompatibel 3 kg Melon, 12 kg Bright Gas, dan 50 kg Komersial).
- **Mengapa Disatukan dalam 1 Unit?**
  - Gas LPG (propana & butana) memiliki massa jenis lebih berat dari udara (&plusmn;1.8&times; udara bebas), sehingga saat terjadi kebocoran mikro, gas akan otomatis mengendap merayap ke lantai di sekitar bibir bawah tabung.
  - Dengan mengintegrasikan **4-Point Shear Beam Load Cells** (timbangan presisi 24-bit ADC) dan **Perimeter Sniffer Chamber** (sensor gas MQ-6 / catalytic bead) dalam satu cangkang anti-percikan (*ATEX Zone 2 / IP66*), sistem dapat mengukur pengurangan massa (&Delta;W/&Delta;t) dan lonjakan konsentrasi gas lokal (ppm) secara simultan di sumbernya langsung.
  - Dilengkapi lampu **360° Circular Halo LED** (Hijau: Aman, Kuning: Warning/Oplosan, Merah Berkedip: Bocor) dan buzzer lokal 85 dB. Baterai LiFePO4 tahan 18+ bulan.

### 2. Perangkat 2: *GASENTRA Central Industrial Gateway & Solenoid Controller*
- Unit pengolah data *edge* yang dipasang di dinding dapur atau panel pipa manifold.
- Menjalankan **Mesin Korelasi Multi-Sensor** 100% offline (fail-safe tanpa butuh internet).
- Mengendalikan langsung **Katup Solenoid Otomatis** pada pipa manifold untuk memutus aliran gas dalam tempo &lt;200 milidetik saat terdeteksi anomali.
- Dilengkapi **Sirene Industri 105 dB**, lampu bahaya (*Hazard Strobe*), **Tombol Darurat Fisik (Emergency Slam Switch)**, layar OLED 2.42", serta konektivitas redundan (LoRa Concentrator, WiFi, 4G LTE, dan RS-485 Modbus untuk sinkronisasi POS kasir).

---

## 🚀 3 Output Prototipe

GASENTRA disajikan dalam **3 berkas mandiri (*standalone*)** yang dapat dibuka terpisah maupun melalui portal utama:

| File | Output | Deskripsi & Fitur Kunci |
|---|---|---|
| **`index.html`** | **Master Experience Hub** | Portal utama terpadu dengan navigasi cepat ke seluruh output, ringkasan masalah (data 94.7%, Rp19.25M), arsitektur 3 lapis perlindungan, keselarasan HORIZON, dan paket produk. |
| **`hardware.html`** | **1. Mockup 2 Hardware (Terpisah)** | Studio teknis interaktif khusus 2 perangkat: 3D WebGL Model 360°, mode bongkar lapisan (*Exploded View*), simulator slider berat tabung (3kg, 12kg, 50kg) & gas PPM, visualisasi ADC raw, tombol uji sirene & emergency slam button, diagram pinout, serta tabel Bill of Materials (BOM). |
| **`dashboard.html`** | **2. Dashboard Web Telemetri** | Dashboard operasional dapur komersial: matriks telemetri multi-tabung real-time, simulasi mesin korelasi kebocoran, *Cek Isi Tabung* (anti-oplosan & rating agen SPBE), integrasi POS (HPP gas per menu & deteksi kompor menyala tanpa pesanan), laporan karbon bulanan Scope 1, dan *Penasihat Transisi Energi Cerdas* (kalkulator BEP induksi, biogas, PLTS). |
| **`digital-twin-3d.html`** | **3. 3D Digital Twin (Opsional)** | Lingkungan 3D Three.js WebGL realistis ruang manifold dan dapur komersial: pipa manifold kuning, katup solenoid merah, tabung gas di atas Smart Base Pad, emisi partikel asap kebocoran gas realistis, api kompor wok biru dinamis yang padam seketika saat katup tertutup, 5 preset kamera fly-to, dan mode pencahayaan (Siang/Malam/Bahaya). |

---

## 💡 Fitur Unggulan Sistem

### 1. Deteksi Tingkat Tabung & Katup Otomatis
Mengisolasi tabung yang bocor dan memutus alirannya dalam &lt;2.8 detik tanpa internet. Tabung lain yang tidak bocor tetap aman dan operasional dapur dapat berlanjut tanpa kepanikan total.

### 2. Cek Isi Tabung (Anti-Oplosan)
Tabung baru ditimbang otomatis begitu diletakkan di atas alas pintar. Jika berat netto kurang dari standar kuota (misal tabung 12 kg hanya terisi 11.2 kg), sistem langsung mencatat tekor 0.8 kg, menurunkan rating agen pemasok, dan menyiapkan klaim resmi via WhatsApp API.

### 3. Tukar Tepat Waktu & Auto-Reorder
Berdasarkan laju pemakaian historis, sistem memprediksi kapan gas akan habis dan memesan otomatis ke agen terpercaya sebelum jam sibuk (*lunch/dinner rush*), mencegah gas terbuang akibat penukaran tabung prematur.

### 4. Biaya Gas per Porsi & Ghost Burner Alert
Terhubung ke sistem kasir POS (Moka, ESB, Pawoon):
- Nasi Goreng Seafood: Rp 420 / porsi (0.021 kg LPG)
- Bebek Goreng Crispy: Rp 1.160 / porsi (0.058 kg LPG)
- Memberi peringatan jika tungku kompor menyala lebih dari 15 menit tanpa ada tiket pesanan aktif (*ghost flame*), menghemat hingga Rp 380.000/bulan per outlet.

### 5. Penasihat Transisi Energi & Laporan Karbon (HORIZON Zero-Carbon)
- Rekap bulanan emisi Scope 1 GHG ($2.983 \text{ kg CO}_2\text{e/kg LPG}$).
- Kalkulator finansial balik modal (*Payback Period / BEP*) untuk beralih ke Kompor Induksi 5 kW, Biogas dari limbah sisa dapur, atau PLTS Atap.

---

## 🎯 Keselarasan dengan Tema HORIZON

- **R — Resilient:** Mencegah kebakaran (94,7% luka bakar ledakan LPG) dan gangguan operasional dapur.
- **I — Inclusive:** Paket Lite terjangkau bagi jutaan UMKM pengguna LPG 3 kg & perlindungan dari LPG oplosan.
- **Z — Zero-Carbon:** Laporan karbon siap-ESG dan kalkulator transisi menuju energi bersih.
- **N — Networks:** Ekosistem yang mengintegrasikan dapur, agen LPG resmi, sistem kasir POS, dan perusahaan asuransi kebakaran.

---

## 💼 Model Bisnis & Paket Produk

1. **GASENTRA Lite (UMKM · LPG 3 kg):** Alas timbang + sensor gas + buzzer lokal. Peringatan kebocoran dan pengingat habis via WhatsApp. Model sewa terjangkau.
2. **GASENTRA Essential (Restoran & Kafe · LPG 12 kg):** Deteksi per tabung, Katup Solenoid Otomatis, Cek Isi Tabung, dan Tukar Tepat Waktu. Biaya sewa per tabung per bulan.
3. **GASENTRA Enterprise (Hotel, Catering & Multi-Outlet · LPG 12 & 50 kg):** Seluruh fitur Essential + Integrasi POS (HPP menu & ghost flame), Laporan Karbon ESG, Penasihat Transisi Energi, dan dashboard analitik multi-cabang.

---

## 💻 Cara Menjalankan Prototipe

### Opsi 1: Langsung Buka File HTML di Browser
Cukup klik ganda (*double click*) file berikut menggunakan peramban modern (Google Chrome, Microsoft Edge, Firefox, atau Safari):
- Buka **`index.html`** untuk Portal Utama.
- Buka **`hardware.html`** untuk Mockup 2 Perangkat Keras.
- Buka **`dashboard.html`** untuk Web Dashboard Telemetri.
- Buka **`digital-twin-3d.html`** untuk Simulasi 3D Digital Twin.

### Opsi 2: Menggunakan Local HTTP Server
```powershell
# Di folder C:\Users\Zolla\Documents\GASENTRA
python -m http.server 8080
```
Lalu buka peramban di: `http://localhost:8080`.

---
*GASENTRA — Aman. Utuh. Terpakai. Siap beralih ke energi bersih.*  
*Catalyst Summit 2026 Business Plan Competition · SRE Universitas Airlangga*
#   g a s e n t r a  
 