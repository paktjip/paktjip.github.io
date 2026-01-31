# 🔐 Panduan Password Authentication - PAKTJIP Digital Printing

## 🔄 Cara Generate Hash Password Baru

### Metode 1: Menggunakan Browser Console (Paling Mudah)

1. **Buka halaman index_clean.html di browser**
2. **Tekan F12** untuk buka Developer Tools
3. **Pilih tab Console**
4. **Copy-paste code ini** (ganti PASSWORD_BARU dengan password Anda):

```javascript
async function generateHash(password) {
    const msgBuffer = new TextEncoder().encode(password);
    const hashBuffer = await crypto.subtle.digest('SHA-256', msgBuffer);
    const hashArray = Array.from(new Uint8Array(hashBuffer));
    const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
    console.log('Password:', password);
    console.log('SHA-256 Hash:', hashHex);
    return hashHex;
}

// Gunakan function ini:
await generateHash("PASSWORD_BARU");
```

**Contoh output:**
```
Password: PAKTJIP2026
SHA-256 Hash: 8a7f2d3e5c9b1a4f6e8d2c5b9a3e7f1d4c8b6a2f5e9d3c7a1b4f8e2d6c9a5b3f
```

5. **Copy hash yang dihasilkan**


---

## 🔧 Cara Update Password di Source Code

### Langkah 1: Generate Hash Baru
Gunakan salah satu metode di atas untuk generate hash.

### Langkah 2: Edit File HTML
1. Buka `index_clean.html` dengan text editor
2. Cari baris ini:

```javascript
const STORED_HASH = "39783f3fe190ffd874f8382bd2787fd1e8ea76ba1bba13de41584e6f7ef3aee3";
```

3. Ganti dengan hash baru:

```javascript
const STORED_HASH = "8a7f2d3e5c9b1a4f6e8d2c5b9a3e7f1d4c8b6a2f5e9d3c7a1b4f8e2d6c9a5b3f";
```

### Langkah 3: Save & Test
1. Save file
2. Refresh browser (Ctrl+F5 untuk hard refresh)
3. Test dengan password baru
4. ✅ Seharusnya berhasil login!

