<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Warung Ibu - POS</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter :wght@400;500;600;700&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  background: linear-gradient(135deg, #f8fafc 0%, #f1f5f8 100%);
  min-height: 100vh;
  padding-bottom: 95px;
}

header {
  background: linear-gradient(135deg, #1e40af 0%, #1d4ed8 100%);
  color: white;
  padding: 1.25rem 1rem;
  text-align: center;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  position: sticky;
  top: 0;
  z-index: 100;
}

header h1 {
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: -0.025em;
}

.container {
  max-width: 520px;
  margin: 0 auto;
  padding: 1.5rem 1rem;
}

.card {
  background: white;
  border-radius: 16px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  border: 1px solid #e2e8f0;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

input, button {
  width: 100%;
  padding: 0.875rem 1rem;
  border-radius: 12px;
  border: 1px solid #cbd5e1;
  font-size: 1rem;
  font-family: inherit;
  transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.15);
}

input::placeholder {
  color: #94a3b8;
}

button {
  background: #3b82f6;
  color: white;
  border: none;
  font-weight: 600;
  cursor: pointer;
  letter-spacing: 0.01em;
}

button:hover {
  background: #2563eb;
  transform: translateY(-1px);
}

button:active {
  transform: translateY(0);
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}

.btn-primary {
  background: linear-gradient(135deg, #2563eb 0%, #3b82f6 100%);
}

.btn-primary:hover {
  background: linear-gradient(135deg, #1d4ed8 0%, #2563eb 100%);
}

.btn-success {
  background: linear-gradient(135deg, #16a34a 0%, #22c55e 100%);
}

.btn-success:hover {
  background: linear-gradient(135deg, #15803d 0%, #16a34a 100%);
}

.btn-danger {
  background: linear-gradient(135deg, #dc2626 0%, #ef4444 100%);
}

.btn-danger:hover {
  background: linear-gradient(135deg, #b91c1c 0%, #dc2626 100%);
}

.btn-secondary {
  background: #64748b;
  color: white;
}

.btn-secondary:hover {
  background: #475569;
}

.btn-warning {
  background: linear-gradient(135deg, #ca8a04 0%, #eab308 100%);
}

.btn-warning:hover {
  background: linear-gradient(135deg, #b45309 0%, #ca8a04 100%);
}

.btn-lunas {
  background: linear-gradient(135deg, #0ea5e9 0%, #38bdf8 100%);
}

.btn-lunas:hover {
  background: linear-gradient(135deg, #0284c7 0%, #0ea5e9 100%);
}

nav {
  display: flex;
  justify-content: space-around;
  background: white;
  position: fixed;
  bottom: 0;
  width: 100%;
  max-width: 520px;
  margin: 0 auto;
  left: 0;
  right: 0;
  padding: 0.75rem 0;
  box-shadow: 0 -4px 6px -1px rgba(0, 0, 0, 0.1), 0 -2px 4px -1px rgba(0, 0, 0, 0.06);
  border-top: 1px solid #e2e8f0;
  z-index: 100;
}

nav button {
  background: none;
  border: none;
  color: #64748b;
  padding: 0.5rem;
  font-weight: 600;
  font-size: 0.875rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  transition: all 0.2s ease;
}

nav button:hover {
  color: #3b82f6;
  transform: translateY(-2px);
}

nav button.active {
  color: #3b82f6;
}

.icon {
  font-size: 1.5rem;
  line-height: 1;
}

.hidden {
  display: none;
}

.empty-state {
  text-align: center;
  padding: 2rem 1rem;
  color: #64748b;
}

.empty-state svg {
  width: 64px;
  height: 64px;
  margin-bottom: 1rem;
  opacity: 0.6;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.product-card {
  position: relative;
  overflow: hidden;
  cursor: default;
}

.product-image {
  width: 100%;
  aspect-ratio: 1/1;
  background: #f8fafc;
  border-radius: 10px;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  font-size: 2.5rem;
  object-fit: cover;
}

.product-actions {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-top: 0.75rem;
}

.product-actions button {
  padding: 0.5rem 0.75rem;
  font-size: 0.875rem;
}

.cart-item {
  padding: 1rem 0;
  border-bottom: 1px solid #f1f5f9;
}

.cart-item:last-child {
  border-bottom: none;
  margin-bottom: 0;
}

.cart-item-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.5rem;
}

.cart-item-name {
  font-weight: 600;
  color: #1e293b;
  font-size: 1rem;
}

.cart-item-price {
  color: #0f766e;
  font-weight: 600;
  font-size: 0.95rem;
}

.cart-item-qty {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 0.5rem;
}

.cart-item-qty button {
  width: auto;
  padding: 0.375rem 0.75rem;
  font-size: 0.875rem;
}

.cart-total {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.25rem 0;
  font-size: 1.125rem;
  font-weight: 700;
  color: #1e293b;
  border-top: 2px solid #f1f5f9;
  margin-top: 1rem;
}

.cart-total-value {
  color: #0f766e;
}

.payment-section {
  margin-top: 1.5rem;
}

.change-display {
  background: #f0fdf4;
  border-radius: 12px;
  padding: 1.25rem;
  margin-top: 1.5rem;
  border-left: 4px solid #10b981;
}

.change-display p {
  margin: 0;
  color: #166534;
  font-weight: 600;
  font-size: 1.125rem;
}

.transaction-item {
  margin-bottom: 1.25rem;
  padding-bottom: 1.25rem;
  border-bottom: 1px solid #f1f5f9;
}

.transaction-item:last-child {
  border-bottom: none;
  margin-bottom: 0;
  padding-bottom: 0;
}

.transaction-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.transaction-date {
  font-weight: 700;
  color: #1e40af;
  font-size: 1rem;
}

.transaction-time {
  background: #dbeafe;
  color: #1d4ed8;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 600;
}

.transaction-items {
  margin: 0.75rem 0;
  padding-left: 1.25rem;
}

.transaction-items li {
  margin-bottom: 0.5rem;
  color: #475569;
  font-size: 0.95rem;
}

.transaction-total {
  text-align: right;
  font-weight: 700;
  color: #0f766e;
  font-size: 1.125rem;
  margin-top: 0.75rem;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #334155;
  font-weight: 600;
  font-size: 0.95rem;
}

#search {
  padding-left: 2.5rem;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 24 24' fill='none' stroke='%2394a3b8' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Ccircle cx='11' cy='11' r='8'%3E%3C/circle%3E%3Cline x1='21' y1='21' x2='16.65' y2='16.65'%3E%3C/line%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: 0.75rem center;
}

.toast {
  position: fixed;
  top: 20px;
  right: 20px;
  background: #16a34a;
  color: white;
  padding: 1rem 1.5rem;
  border-radius: 16px;
  font-weight: 700;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  transform: translateX(200%);
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  z-index: 1000;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.toast.error {
  background: #dc2626;
}

.toast.show {
  transform: translateX(0);
}

.toast-icon {
  font-size: 1.5rem;
}

/* Dropdown styles for product search */
.dropdown {
  position: relative;
  width: 100%;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: white;
  border: 1px solid #cbd5e1;
  border-radius: 12px;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  z-index: 10;
  max-height: 200px;
  overflow-y: auto;
  margin-top: 0.25rem;
  display: none;
}

.dropdown-menu.show {
  display: block;
}

.dropdown-item {
  padding: 0.75rem 1rem;
  cursor: pointer;
  transition: background-color 0.2s;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.dropdown-item:hover {
  background-color: #f1f5f9;
}

.dropdown-item-name {
  font-weight: 500;
  color: #1e293b;
}

.dropdown-item-price {
  color: #0f766e;
  font-weight: 600;
}

/* Debts section */
.debt-item {
  background: #fffbeb;
  border-left: 4px solid #ca8a04;
  padding: 1.25rem;
  margin-bottom: 1.25rem;
  border-radius: 12px;
}

.debt-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.75rem;
}

.debt-name {
  font-weight: 700;
  color: #b45309;
  font-size: 1.1rem;
}

.debt-date {
  color: #94a3b8;
  font-size: 0.875rem;
}

.debt-items {
  margin: 0.75rem 0;
}

.debt-items li {
  margin-bottom: 0.5rem;
  color: #475569;
  font-size: 0.95rem;
}

.debt-total {
  text-align: right;
  font-weight: 700;
  color: #b45309;
  font-size: 1.125rem;
  margin-top: 0.75rem;
  padding-top: 0.75rem;
  border-top: 1px dashed #f59e0b;
}

/* Debt search summary */
.debt-summary {
  background: linear-gradient(135deg, #ca8a04 0%, #eab308 100%);
  color: white;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1.5rem;
  text-align: center;
}

.debt-summary h3 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.debt-summary p {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0;
}

/* Responsive adjustments */
@media (max-width: 480px) {
  .product-grid {
    grid-template-columns: 1fr;
  }
  
  .container {
    padding: 1rem 0.75rem;
  }
  
  .card {
    padding: 1.25rem;
  }
}
</style>
</head>
<body>
<header>
  <h1>Warung Ibu</h1>
</header>

<div class="container">
  <!-- PRODUK -->
  <div id="produk">
    <div class="card">
      <input id="search" placeholder="Cari produk..." oninput="renderProduk()">
    </div>
    
    <div class="card">
      <h2 style="font-size: 1.25rem; font-weight: 700; margin-bottom: 1.25rem; color: #1e40af;">Tambah Produk Baru</h2>
      <div class="form-group">
        <label for="gambar">URL Gambar (opsional)</label>
        <input id="gambar" placeholder="https://example.com/image.jpg ">
      </div>
      <div class="form-group">
        <label for="nama">Nama Produk</label>
        <input id="nama" placeholder="Contoh: Nasi Goreng">
      </div>
      <div class="form-group">
        <label for="harga">Harga (Rp)</label>
        <input id="harga" type="text" inputmode="numeric" pattern="[0-9]*" placeholder="Contoh: 15000" oninput="formatRupiah(this)">
      </div>
      <button class="btn-primary" onclick="tambahProduk()">Tambah Produk</button>
    </div>
    
    <div id="listProduk" class="product-grid"></div>
  </div>

  <!-- KASIR -->
  <div id="kasir" class="hidden">
    <div class="card">
      <h2 style="font-size: 1.25rem; font-weight: 700; margin-bottom: 1.25rem; color: #1e40af;">Keranjang Belanja</h2>
      <div id="cart"></div>
      <div id="emptyCart" class="empty-state" style="display:none;">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
        </svg>
        <p>Keranjang masih kosong</p>
        <p style="font-size: 0.9rem; margin-top: 0.5rem;">Tambahkan produk dari tab Produk</p>
      </div>
      
      <div id="cartTotal" class="cart-total" style="display: none;">
        <span>Total:</span>
        <span class="cart-total-value">Rp <span id="total">0</span></span>
      </div>
      
      <div class="payment-section" id="paymentSection" style="display: none;">
        <div class="form-group">
          <label for="bayar">Jumlah Bayar (Rp)</label>
          <input id="bayar" type="text" inputmode="numeric" pattern="[0-9]*" placeholder="Masukkan jumlah uang" oninput="formatRupiah(this); hitungKembalian()" autocomplete="off">
        </div>
        <button class="btn-success" onclick="prosesBayar()" id="bayarBtn">Proses Pembayaran</button>
        <div id="kembaliContainer" class="change-display" style="display: none;">
          <p>Kembalian: Rp <span id="kembali">0</span></p>
        </div>
      </div>
    </div>
  </div>

  <!-- HUTANG -->
  <div id="hutang" class="hidden">
    <div class="card">
      <h2 style="font-size: 1.25rem; font-weight: 700; margin-bottom: 1.25rem; color: #ca8a04;">Catat Hutang</h2>
      <div class="form-group">
        <label for="namaPembeli">Nama Pembeli</label>
        <input id="namaPembeli" placeholder="Contoh: Budi Santoso">
      </div>
      
      <div class="form-group">
        <label for="nominalHutang">Nominal Hutang (Rp)</label>
        <input id="nominalHutang" type="text" inputmode="numeric" pattern="[0-9]*" placeholder="Contoh: 50000" oninput="formatRupiah(this)">
      </div>
      
      <div class="form-group">
        <label for="deskripsiHutang">Deskripsi (opsional)</label>
        <input id="deskripsiHutang" placeholder="Contoh: Belanja sembako">
      </div>
      
      <button class="btn-warning" onclick="tambahCatatanHutang()" style="margin-top: 1.5rem;">Buat Catatan Hutang</button>
    </div>
    
    <!-- Debt Search Section -->
    <div class="card">
      <input id="searchHutang" placeholder="Cari nama pembeli..." oninput="searchHutang()" style="padding-left: 2.5rem; background-image: url('data:image/svg+xml,%3Csvg xmlns=%27http://www.w3.org/2000/svg%27 width=%2720%27 height=%2720%27 viewBox=%270 0 24 24%27 fill=%27none%27 stroke=%27%2394a3b8%27 stroke-width=%272%27 stroke-linecap=%27round%27 stroke-linejoin=%27round%27%3E%3Ccircle cx=%2711%27 cy=%2711%27 r=%278%27%3E%3C/circle%3E%3Cline x1=%2721%27 y1=%2721%27 x2=%2716.65%27 y2=%2716.65%27%3E%3C/line%3E%3C/svg%3E'); background-repeat: no-repeat; background-position: 0.75rem center;">
    </div>
    
    <!-- Debt Summary -->
    <div id="debtSummary" class="debt-summary hidden">
      <h3>Total Hutang</h3>
      <p>Rp <span id="totalHutang">0</span></p>
    </div>
    
    <!-- Debt List -->
    <div class="card">
      <h2 style="font-size: 1.25rem; font-weight: 700; margin-bottom: 1.25rem; color: #ca8a04;">Daftar Hutang</h2>
      <div id="daftarHutang"></div>
      <div id="emptyHutang" class="empty-state" style="display:none;">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1" />
        </svg>
        <p>Belum ada catatan hutang</p>
        <p style="font-size: 0.9rem; margin-top: 0.5rem;">Buat catatan hutang baru di atas</p>
      </div>
    </div>
  </div>

  <!-- PROFIL -->
  <div id="profil" class="hidden">
    <div class="card">
      <h2 style="font-size: 1.25rem; font-weight: 700; margin-bottom: 1.25rem; color: #1e40af;">Riwayat Transaksi</h2>
      <div id="riwayat"></div>
      <div id="emptyRiwayat" class="empty-state" style="display:none;">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
        </svg>
        <p>Belum ada transaksi</p>
        <p style="font-size: 0.9rem; margin-top: 0.5rem;">Transaksi akan muncul di sini setelah pembayaran</p>
      </div>
    </div>
  </div>
</div>

<nav>
  <button onclick="show('produk')" id="nav-produk" class="active">
    <span class="icon">🛍️</span>
    Produk
  </button>
  <button onclick="show('kasir')" id="nav-kasir">
    <span class="icon">🧾</span>
    Kasir
  </button>
  <button onclick="show('hutang')" id="nav-hutang">
    <span class="icon">📝</span>
    Hutang
  </button>
  <button onclick="show('profil')" id="nav-profil">
    <span class="icon">📈</span>
    Profil
  </button>
</nav>

<div id="toast" class="toast">
  <span class="toast-icon">✅</span>
  <span id="toast-message">Notifikasi</span>
</div>

<script>
/* ===== UTIL ===== */
function rupiah(val) {
  return String(val || '').replace(/[^0-9]/g, '').replace(/\B(?=(\d{3})+(?!\d))/g, '.');
}

function formatRupiah(el) {
  el.value = rupiah(el.value);
}

function num(v) {
  return Number(String(v).replace(/\./g, '')) || 0;
}

function showToast(message, type = 'success') {
  const toast = document.getElementById('toast');
  const toastMessage = document.getElementById('toast-message');
  toastMessage.textContent = message;
  toast.className = `toast ${type} show`;
  
  setTimeout(() => {
    toast.className = 'toast';
  }, 3000);
}

/* ===== LOCAL STORAGE ===== */
function saveToLocalStorage() {
  try {
    localStorage.setItem('warungIbu_products', JSON.stringify(products));
    localStorage.setItem('warungIbu_history', JSON.stringify(history));
    localStorage.setItem('warungIbu_debts', JSON.stringify(debts));
  } catch (e) {
    console.error('Error saving to localStorage:', e);
  }
}

function loadFromLocalStorage() {
  try {
    const savedProducts = localStorage.getItem('warungIbu_products');
    const savedHistory = localStorage.getItem('warungIbu_history');
    const savedDebts = localStorage.getItem('warungIbu_debts');
    
    if (savedProducts) products = JSON.parse(savedProducts);
    if (savedHistory) history = JSON.parse(savedHistory);
    if (savedDebts) debts = JSON.parse(savedDebts);
  } catch (e) {
    console.error('Error loading from localStorage:', e);
    products = [];
    history = [];
    debts = [];
  }
}

/* ===== DATA ===== */
let products = [];
let cart = [];
let history = [];
let debts = [];

// Initialize with data from localStorage
function initSampleData() {
  loadFromLocalStorage();
}

/* ===== NAV ===== */
function show(id) {
  document.querySelectorAll('.container > div').forEach(d => d.classList.add('hidden'));
  document.getElementById(id).classList.remove('hidden');
  
  document.querySelectorAll('nav button').forEach(btn => btn.classList.remove('active'));
  document.getElementById(`nav-${id}`).classList.add('active');
  
  if (id === 'profil') {
    renderRiwayat();
  } else if (id === 'kasir') {
    renderCart();
  } else if (id === 'hutang') {
    renderDaftarHutang();
    // Also trigger search to show summary if search query exists
    searchHutang();
  }
}

/* ===== PRODUK ===== */
function tambahProduk() {
  const namaInput = document.getElementById('nama');
  const hargaInput = document.getElementById('harga');
  const gambarInput = document.getElementById('gambar');
  
  if (!namaInput.value.trim()) {
    showToast('Nama produk wajib diisi', 'error');
    return;
  }
  
  if (!hargaInput.value.trim()) {
    showToast('Harga wajib diisi', 'error');
    return;
  }
  
  const harga = num(hargaInput.value);
  if (harga <= 0) {
    showToast('Harga harus lebih dari 0', 'error');
    return;
  }
  
  if (namaInput.value.trim().length > 50) {
    showToast('Nama produk maksimal 50 karakter', 'error');
    return;
  }
  
  const existingProduct = products.find(p => p.nama.toLowerCase() === namaInput.value.trim().toLowerCase());
  if (existingProduct) {
    showToast('Produk dengan nama ini sudah ada', 'error');
    return;
  }
  
  products.push({
    nama: namaInput.value.trim(),
    harga: harga,
    gambar: gambarInput.value.trim() || null
  });
  
  namaInput.value = '';
  hargaInput.value = '';
  gambarInput.value = '';
  
  renderProduk();
  saveToLocalStorage();
  showToast('Produk berhasil ditambahkan!', 'success');
}

function hapusProduk(index) {
  const productName = products[index].nama;
  if (confirm(`Yakin ingin menghapus produk "${productName}"?`)) {
    products.splice(index, 1);
    renderProduk();
    saveToLocalStorage();
    showToast('Produk berhasil dihapus!', 'success');
    
    // Also remove from cart if present
    cart = cart.filter(item => item.nama !== productName);
    if (document.getElementById('kasir').classList.contains('hidden') === false) {
      renderCart();
    }
  }
}

function renderProduk() {
  const listProduk = document.getElementById('listProduk');
  listProduk.innerHTML = '';
  
  const q = (document.getElementById('search').value || '').toLowerCase().trim();
  const filteredProducts = products.filter(p => p.nama.toLowerCase().includes(q));
  
  if (filteredProducts.length === 0) {
    listProduk.innerHTML = `
      <div class="card" style="text-align: center; padding: 2rem;">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" style="width: 64px; height: 64px; margin: 0 auto 1rem; color: #94a3b8;">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
        </svg>
        <p style="color: #64748b; font-size: 1.1rem;">Tidak ada produk ditemukan</p>
        <p style="color: #94a3b8; font-size: 0.9rem; margin-top: 0.5rem;">Coba kata kunci yang berbeda</p>
      </div>
    `;
    return;
  }
  
  filteredProducts.forEach((p, i) => {
    const productCard = document.createElement('div');
    productCard.className = 'product-card card';
    productCard.innerHTML = `
      ${p.gambar ? `
        <img src="${p.gambar}" alt="${p.nama}" class="product-image" style="aspect-ratio: 1/1; object-fit: cover;" onerror="this.parentElement.querySelector('.product-image').innerHTML='🖼️'; this.style.display='none'">
      ` : `
        <div class="product-image">🖼️</div>
      `}
      <div style="font-weight: 600; color: #1e293b; font-size: 1.1rem; margin-bottom: 0.5rem;">${p.nama}</div>
      <div style="color: #0f766e; font-weight: 700; font-size: 1.25rem; margin-bottom: 1rem;">Rp ${rupiah(p.harga)}</div>
      <div class="product-actions">
        <button class="btn-primary" onclick="addCart(${i})">Tambah ke Keranjang</button>
        <button class="btn-danger" onclick="hapusProduk(${i})">Hapus Produk</button>
      </div>
    `;
    listProduk.appendChild(productCard);
  });
}

/* ===== CART ===== */
function addCart(i) {
  const p = products[i];
  const ada = cart.find(c => c.nama === p.nama);
  if (ada) {
    ada.qty++;
  } else {
    cart.push({ nama: p.nama, harga: p.harga, qty: 1 });
  }
  renderCart();
  showToast(`${p.nama} ditambahkan ke keranjang!`, 'success');
}

function ubahQty(index, qty) {
  if (qty <= 0) {
    hapusItem(index);
  } else {
    cart[index].qty = qty;
    renderCart();
  }
}

function hapusItem(i) {
  const itemName = cart[i].nama;
  cart.splice(i, 1);
  renderCart();
  showToast(`${itemName} dihapus dari keranjang`, 'success');
}

function renderCart() {
  const cartDiv = document.getElementById('cart');
  const emptyCart = document.getElementById('emptyCart');
  const cartTotal = document.getElementById('cartTotal');
  const paymentSection = document.getElementById('paymentSection');
  const kembaliContainer = document.getElementById('kembaliContainer');
  
  if (cart.length === 0) {
    cartDiv.innerHTML = '';
    emptyCart.style.display = 'block';
    cartTotal.style.display = 'none';
    paymentSection.style.display = 'none';
    kembaliContainer.style.display = 'none';
    return;
  }
  
  emptyCart.style.display = 'none';
  cartTotal.style.display = 'flex';
  paymentSection.style.display = 'block';
  
  cartDiv.innerHTML = '';
  let total = 0;
  
  cart.forEach((c, idx) => {
    const sub = c.harga * c.qty;
    total += sub;
    
    const cartItem = document.createElement('div');
    cartItem.className = 'cart-item';
    cartItem.innerHTML = `
      <div class="cart-item-header">
        <span class="cart-item-name">${c.nama}</span>
        <span class="cart-item-price">Rp ${rupiah(sub)}</span>
      </div>
      <div class="cart-item-qty">
        <span style="color: #64748b;">Rp ${rupiah(c.harga)} × ${c.qty}</span>
        <div style="margin-left: auto; display: flex; gap: 0.5rem;">
          <button class="btn-secondary" onclick="ubahQty(${idx}, ${c.qty - 1})">−</button>
          <button class="btn-secondary" onclick="ubahQty(${idx}, ${c.qty + 1})">+</button>
          <button class="btn-danger" onclick="hapusItem(${idx})">Hapus</button>
        </div>
      </div>
    `;
    cartDiv.appendChild(cartItem);
  });
  
  document.getElementById('total').textContent = rupiah(total);
  document.getElementById('bayar').value = '';
  kembaliContainer.style.display = 'none';
}

/* ===== BAYAR ===== */
function hitungKembalian() {
  const totalElement = document.getElementById('total');
  const bayarElement = document.getElementById('bayar');
  const kembaliElement = document.getElementById('kembali');
  const kembaliContainer = document.getElementById('kembaliContainer');
  
  if (totalElement && bayarElement) {
    const total = num(totalElement.textContent);
    const bayarVal = num(bayarElement.value);
    
    if (bayarVal > 0 && total > 0) {
      const kembali = bayarVal - total;
      kembaliElement.textContent = rupiah(kembali);
      kembaliContainer.style.display = 'block';
    } else {
      kembaliContainer.style.display = 'none';
    }
  }
}

function prosesBayar() {
  if (cart.length === 0) {
    showToast('Keranjang kosong', 'error');
    return;
  }
  
  const total = num(document.getElementById('total').textContent);
  const bayarVal = num(document.getElementById('bayar').value);
  
  if (!bayarVal || bayarVal === 0) {
    showToast('Masukkan jumlah uang bayar', 'error');
    return;
  }
  
  if (bayarVal < total) {
    showToast('Uang bayar kurang!', 'error');
    return;
  }
  
  const kembali = bayarVal - total;
  document.getElementById('kembali').textContent = rupiah(kembali);
  document.getElementById('kembaliContainer').style.display = 'block';
  
  const now = new Date();
  history.push({
    tanggal: now.toLocaleDateString('id-ID', { day: '2-digit', month: '2-digit', year: 'numeric' }),
    waktu: now.toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' }),
    items: JSON.parse(JSON.stringify(cart)),
    total: total
  });
  
  cart = [];
  document.getElementById('bayar').value = '';
  renderCart();
  saveToLocalStorage();
  
  showToast('Transaksi berhasil!', 'success');
}

/* ===== RIWAYAT ===== */
function renderRiwayat() {
  const riwayatDiv = document.getElementById('riwayat');
  const emptyRiwayat = document.getElementById('emptyRiwayat');
  
  if (history.length === 0) {
    riwayatDiv.innerHTML = '';
    emptyRiwayat.style.display = 'block';
    return;
  }
  
  emptyRiwayat.style.display = 'none';
  riwayatDiv.innerHTML = '';
  
  const recentHistory = history.slice(-15).reverse();
  
  recentHistory.forEach(h => {
    const transactionCard = document.createElement('div');
    transactionCard.className = 'transaction-item';
    transactionCard.innerHTML = `
      <div class="transaction-header">
        <span class="transaction-date">${h.tanggal}</span>
        <span class="transaction-time">${h.waktu}</span>
      </div>
      <ul class="transaction-items">
        ${h.items.map(i => `<li>${i.nama} <span style="color: #64748b;">(x${i.qty})</span></li>`).join('')}
      </ul>
      <div class="transaction-total">Total: Rp ${rupiah(h.total)}</div>
    `;
    riwayatDiv.appendChild(transactionCard);
  });
}

/* ===== HUTANG ===== */
function tambahCatatanHutang() {
  const namaPembeli = document.getElementById('namaPembeli').value.trim();
  const nominalHutang = document.getElementById('nominalHutang').value.trim();
  const deskripsiHutang = document.getElementById('deskripsiHutang').value.trim();
  
  if (!namaPembeli) {
    showToast('Nama pembeli wajib diisi', 'error');
    return;
  }
  
  if (!nominalHutang) {
    showToast('Nominal hutang wajib diisi', 'error');
    return;
  }
  
  const nominal = num(nominalHutang);
  if (nominal <= 0) {
    showToast('Nominal hutang harus lebih dari 0', 'error');
    return;
  }
  
  const now = new Date();
  debts.push({
    namaPembeli: namaPembeli,
    nominal: nominal,
    deskripsi: deskripsiHutang || "Tidak ada deskripsi",
    tanggal: now.toLocaleDateString('id-ID', { day: '2-digit', month: '2-digit', year: 'numeric' }),
    waktu: now.toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' }),
    timestamp: now.getTime()
  });
  
  document.getElementById('namaPembeli').value = '';
  document.getElementById('nominalHutang').value = '';
  document.getElementById('deskripsiHutang').value = '';
  
  renderDaftarHutang();
  saveToLocalStorage();
  
  showToast('Catatan hutang berhasil dibuat!', 'success');
}

function lunasHutang(index) {
  const debt = debts[index];
  if (confirm(`Yakin ingin melunasi hutang "${debt.namaPembeli}" sebesar Rp ${rupiah(debt.nominal)}?`)) {
    debts.splice(index, 1);
    renderDaftarHutang();
    saveToLocalStorage();
    showToast('Hutang berhasil dilunasi!', 'success');
  }
}

function searchHutang() {
  const query = document.getElementById('searchHutang').value.toLowerCase().trim();
  const daftarHutang = document.getElementById('daftarHutang');
  const emptyHutang = document.getElementById('emptyHutang');
  const debtSummary = document.getElementById('debtSummary');
  const totalHutang = document.getElementById('totalHutang');
  
  if (!query) {
    renderDaftarHutang();
    debtSummary.classList.add('hidden');
    return;
  }
  
  const filteredDebts = debts.filter(debt => 
    debt.namaPembeli.toLowerCase().includes(query)
  );
  
  if (filteredDebts.length === 0) {
    daftarHutang.innerHTML = '';
    emptyHutang.style.display = 'block';
    debtSummary.classList.add('hidden');
    return;
  }
  
  emptyHutang.style.display = 'none';
  const sortedDebts = filteredDebts.sort((a, b) => b.timestamp - a.timestamp);
  const total = sortedDebts.reduce((sum, debt) => sum + debt.nominal, 0);
  
  totalHutang.textContent = rupiah(total);
  debtSummary.classList.remove('hidden');
  
  daftarHutang.innerHTML = sortedDebts.map((debt, idx) => `
    <div class="debt-item">
      <div class="debt-header">
        <span class="debt-name">${debt.namaPembeli}</span>
        <span class="debt-date">${debt.tanggal} ${debt.waktu}</span>
      </div>
      <p style="margin: 0.75rem 0; color: #475569;">${debt.deskripsi}</p>
      <div class="debt-total">Total: Rp ${rupiah(debt.nominal)}</div>
      <button class="btn-lunas" onclick="lunasHutang(${idx})" style="margin-top: 1rem; width: auto;">Lunas</button>
    </div>
  `).join('');
}

function renderDaftarHutang() {
  const daftarHutang = document.getElementById('daftarHutang');
  const emptyHutang = document.getElementById('emptyHutang');
  const debtSummary = document.getElementById('debtSummary');
  
  if (debts.length === 0) {
    daftarHutang.innerHTML = '';
    emptyHutang.style.display = 'block';
    debtSummary.classList.add('hidden');
    return;
  }
  
  emptyHutang.style.display = 'none';
  debtSummary.classList.add('hidden');
  
  const sortedDebts = [...debts].sort((a, b) => b.timestamp - a.timestamp);
  
  daftarHutang.innerHTML = sortedDebts.map((debt, idx) => `
    <div class="debt-item">
      <div class="debt-header">
        <span class="debt-name">${debt.namaPembeli}</span>
        <span class="debt-date">${debt.tanggal} ${debt.waktu}</span>
      </div>
      <p style="margin: 0.75rem 0; color: #475569;">${debt.deskripsi}</p>
      <div class="debt-total">Total: Rp ${rupiah(debt.nominal)}</div>
      <button class="btn-lunas" onclick="lunasHutang(${idx})" style="margin-top: 1rem; width: auto;">Lunas</button>
    </div>
  `).join('');
}

// Initialize
initSampleData();
renderProduk();
</script>
</body>
</html>

