cat > /home/claude/procurement_app.html << 'HTMLEOF'
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ProcureTrack — Vendor & Harga Manager</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #F5F3EE;
    --surface: #FFFFFF;
    --surface2: #EEECE7;
    --border: #E0DDD6;
    --border-dark: #C8C4BA;
    --text: #1A1916;
    --text2: #6B685F;
    --text3: #9B9890;
    --accent: #2B5C3F;
    --accent-light: #E8F0EB;
    --accent-mid: #4A8C62;
    --warn: #C17B2A;
    --warn-light: #FBF3E8;
    --danger: #B83B3B;
    --danger-light: #FAEAEA;
    --info: #2B4F8C;
    --info-light: #EAF0FA;
    --radius: 10px;
    --radius-lg: 16px;
    --shadow: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
    --shadow-lg: 0 4px 16px rgba(0,0,0,0.08), 0 2px 6px rgba(0,0,0,0.04);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; font-size: 14px; line-height: 1.5; }

  /* LAYOUT */
  .app-shell { display: flex; height: 100vh; overflow: hidden; }
  .sidebar { width: 240px; background: var(--surface); border-right: 1px solid var(--border); display: flex; flex-direction: column; flex-shrink: 0; }
  .main { flex: 1; overflow-y: auto; background: var(--bg); }

  /* SIDEBAR */
  .sidebar-logo { padding: 24px 20px 16px; border-bottom: 1px solid var(--border); }
  .sidebar-logo h1 { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 700; color: var(--text); letter-spacing: -0.3px; }
  .sidebar-logo p { font-size: 11px; color: var(--text3); margin-top: 2px; }
  .sidebar-nav { padding: 12px 10px; flex: 1; }
  .nav-label { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text3); padding: 0 10px; margin: 16px 0 6px; }
  .nav-label:first-child { margin-top: 4px; }
  .nav-item { display: flex; align-items: center; gap: 10px; padding: 9px 10px; border-radius: var(--radius); cursor: pointer; font-size: 13px; color: var(--text2); font-weight: 400; transition: all 0.15s; margin-bottom: 1px; }
  .nav-item:hover { background: var(--surface2); color: var(--text); }
  .nav-item.active { background: var(--accent-light); color: var(--accent); font-weight: 500; }
  .nav-item svg { width: 16px; height: 16px; flex-shrink: 0; opacity: 0.7; }
  .nav-item.active svg { opacity: 1; }
  .nav-badge { margin-left: auto; background: var(--warn-light); color: var(--warn); font-size: 10px; font-weight: 600; padding: 1px 7px; border-radius: 20px; }
  .sidebar-footer { padding: 16px 20px; border-top: 1px solid var(--border); font-size: 11px; color: var(--text3); }

  /* TOPBAR */
  .topbar { background: var(--surface); border-bottom: 1px solid var(--border); padding: 16px 28px; display: flex; align-items: center; gap: 12px; position: sticky; top: 0; z-index: 10; }
  .topbar-title { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 600; flex: 1; }
  .topbar-subtitle { font-size: 12px; color: var(--text3); font-family: 'DM Sans', sans-serif; font-weight: 400; }

  /* CONTENT */
  .content { padding: 24px 28px; }

  /* CARDS / METRICS */
  .metrics-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; margin-bottom: 24px; }
  .metric-card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-lg); padding: 18px 20px; }
  .metric-card .label { font-size: 11px; color: var(--text3); text-transform: uppercase; letter-spacing: 0.06em; font-weight: 500; margin-bottom: 8px; }
  .metric-card .value { font-family: 'Syne', sans-serif; font-size: 26px; font-weight: 700; line-height: 1; }
  .metric-card .sub { font-size: 11px; color: var(--text3); margin-top: 6px; }
  .metric-card.accent { background: var(--accent); border-color: var(--accent); }
  .metric-card.accent .label, .metric-card.accent .value, .metric-card.accent .sub { color: #fff; }

  /* TABLE CARD */
  .card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-lg); overflow: hidden; margin-bottom: 20px; }
  .card-header { padding: 16px 20px; border-bottom: 1px solid var(--border); display: flex; align-items: center; gap: 12px; }
  .card-header h3 { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 600; flex: 1; }

  .tbl-wrap { overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; font-size: 13px; }
  th { text-align: left; padding: 10px 14px; background: var(--bg); border-bottom: 1px solid var(--border); font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.05em; color: var(--text3); white-space: nowrap; }
  td { padding: 11px 14px; border-bottom: 1px solid var(--border); vertical-align: middle; }
  tr:last-child td { border-bottom: none; }
  tbody tr:hover td { background: var(--bg); }

  /* BADGES */
  .badge { display: inline-flex; align-items: center; gap: 4px; padding: 3px 9px; border-radius: 20px; font-size: 11px; font-weight: 500; }
  .badge-green { background: #E4F2E8; color: #1E6B35; }
  .badge-yellow { background: var(--warn-light); color: var(--warn); }
  .badge-red { background: var(--danger-light); color: var(--danger); }
  .badge-gray { background: var(--surface2); color: var(--text2); }
  .badge-blue { background: var(--info-light); color: var(--info); }

  /* BUTTONS */
  .btn { display: inline-flex; align-items: center; gap: 6px; padding: 8px 14px; border-radius: var(--radius); font-size: 13px; font-weight: 500; cursor: pointer; border: 1px solid var(--border); background: var(--surface); color: var(--text); transition: all 0.15s; font-family: 'DM Sans', sans-serif; }
  .btn:hover { background: var(--surface2); border-color: var(--border-dark); }
  .btn-primary { background: var(--accent); color: #fff; border-color: var(--accent); }
  .btn-primary:hover { background: #204a31; border-color: #204a31; }
  .btn-sm { padding: 5px 10px; font-size: 12px; }
  .btn-icon { padding: 6px; border: 1px solid var(--border); border-radius: 8px; background: transparent; cursor: pointer; color: var(--text2); transition: all 0.15s; }
  .btn-icon:hover { background: var(--surface2); color: var(--text); }
  .btn-icon.danger:hover { background: var(--danger-light); color: var(--danger); border-color: #e8b4b4; }

  /* FORMS */
  .form-group { margin-bottom: 14px; }
  .form-group label { display: block; font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.05em; color: var(--text3); margin-bottom: 5px; }
  input, select, textarea { width: 100%; padding: 9px 12px; border: 1px solid var(--border); border-radius: var(--radius); font-size: 13px; font-family: 'DM Sans', sans-serif; background: var(--surface); color: var(--text); outline: none; transition: border 0.15s; }
  input:focus, select:focus, textarea:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(43,92,63,0.1); }
  textarea { resize: vertical; min-height: 72px; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .form-full { grid-column: 1 / -1; }

  /* SEARCH BAR */
  .search-bar { display: flex; gap: 10px; align-items: center; padding: 14px 20px; background: var(--bg); border-bottom: 1px solid var(--border); }
  .search-input-wrap { position: relative; flex: 1; max-width: 320px; }
  .search-input-wrap svg { position: absolute; left: 10px; top: 50%; transform: translateY(-50%); width: 15px; height: 15px; color: var(--text3); pointer-events: none; }
  .search-input-wrap input { padding-left: 34px; }
  select.filter { width: auto; min-width: 140px; }

  /* MODAL */
  .modal-overlay { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.35); z-index: 1000; align-items: center; justify-content: center; padding: 20px; backdrop-filter: blur(2px); }
  .modal-overlay.open { display: flex; }
  .modal { background: var(--surface); border-radius: var(--radius-lg); width: 600px; max-width: 100%; max-height: 88vh; overflow-y: auto; box-shadow: var(--shadow-lg); animation: slideUp 0.2s ease; }
  @keyframes slideUp { from { opacity:0; transform:translateY(12px) } to { opacity:1; transform:translateY(0) } }
  .modal-header { padding: 20px 24px 16px; border-bottom: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; }
  .modal-header h2 { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 700; }
  .modal-body { padding: 20px 24px; }
  .modal-footer { padding: 16px 24px; border-top: 1px solid var(--border); display: flex; gap: 8px; justify-content: flex-end; }

  /* AI BOX */
  .ai-box { background: var(--info-light); border: 1px solid #c0d4f4; border-radius: var(--radius); padding: 14px; margin-top: 14px; }
  .ai-box-title { font-size: 12px; font-weight: 600; color: var(--info); display: flex; align-items: center; gap: 6px; margin-bottom: 8px; }
  .ai-result { border-top: 1px solid #c0d4f4; padding: 10px 0; display: grid; grid-template-columns: 1fr auto; gap: 10px; align-items: start; }
  .ai-result:first-of-type { border-top: none; padding-top: 4px; }
  .spinner { display: inline-block; width: 14px; height: 14px; border: 2px solid var(--info-light); border-top-color: var(--info); border-radius: 50%; animation: spin 0.7s linear infinite; }
  @keyframes spin { to { transform: rotate(360deg) } }
  .progress { height: 3px; background: #c0d4f4; border-radius: 2px; overflow: hidden; margin-top: 8px; }
  .progress-fill { height: 100%; background: var(--info); border-radius: 2px; transition: width 0.3s; }

  /* HISTORY */
  .history-item { display: grid; grid-template-columns: auto 1fr auto auto; gap: 14px; align-items: center; padding: 11px 0; border-bottom: 1px solid var(--border); }
  .history-item:last-child { border-bottom: none; }
  .price-arrow { color: var(--text3); font-size: 13px; }
  .up { color: var(--danger); font-weight: 600; font-size: 12px; }
  .dn { color: var(--accent); font-weight: 600; font-size: 12px; }

  /* DETAIL PANE */
  .detail-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 16px; }
  .detail-item label { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.06em; color: var(--text3); display: block; margin-bottom: 3px; }
  .detail-item .val { font-size: 14px; font-weight: 500; }

  /* VENDOR CARD GRID */
  .vendor-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px,1fr)); gap: 14px; padding: 20px; }
  .vendor-card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-lg); padding: 16px; transition: box-shadow 0.15s; }
  .vendor-card:hover { box-shadow: var(--shadow-lg); }
  .vendor-card h4 { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 600; margin-bottom: 10px; }
  .vendor-row { display: flex; align-items: flex-start; gap: 8px; font-size: 12px; color: var(--text2); margin-bottom: 6px; }
  .vendor-row svg { width: 13px; height: 13px; color: var(--text3); flex-shrink: 0; margin-top: 1px; }

  /* EMPTY */
  .empty { text-align: center; padding: 48px 20px; color: var(--text3); }
  .empty svg { width: 36px; height: 36px; margin-bottom: 10px; opacity: 0.4; }
  .empty p { font-size: 13px; }

  /* TABS */
  .view { display: none; }
  .view.active { display: block; }

  /* TOAST */
  #toast { position: fixed; bottom: 24px; right: 24px; background: var(--text); color: #fff; padding: 10px 18px; border-radius: var(--radius); font-size: 13px; z-index: 9999; opacity: 0; pointer-events: none; transition: opacity 0.3s; }
  #toast.show { opacity: 1; }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border-dark); border-radius: 3px; }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    .metrics-grid { grid-template-columns: repeat(2, 1fr); }
    .form-row { grid-template-columns: 1fr; }
  }
  @media (max-width: 640px) {
    .sidebar { display: none; }
    .metrics-grid { grid-template-columns: 1fr 1fr; }
    .content { padding: 16px; }
    .topbar { padding: 12px 16px; }
  }
</style>
</head>
<body>
<div class="app-shell">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-logo">
      <h1>ProcureTrack</h1>
      <p>Vendor & Harga Manager</p>
    </div>
    <nav class="sidebar-nav">
      <div class="nav-label">Menu</div>
      <div class="nav-item active" onclick="showView('items',this)">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M3 9h18M9 21V9"/></svg>
        Daftar Item
        <span class="nav-badge" id="badge-update">0</span>
      </div>
      <div class="nav-item" onclick="showView('vendors',this)">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
        Distributor
      </div>
      <div class="nav-item" onclick="showView('history',this)">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
        Riwayat Harga
      </div>
      <div class="nav-item" onclick="showView('export',this)">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
        Export Data
      </div>
      <div class="nav-label">Tools</div>
      <div class="nav-item" onclick="openImport()">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
        Import Excel
      </div>
    </nav>
    <div class="sidebar-footer">
      Data tersimpan di browser lokal<br>v1.0 — Patra Malioboro
    </div>
  </aside>

  <!-- MAIN -->
  <main class="main">
    <div class="topbar">
      <div>
        <div class="topbar-title" id="view-title">Daftar Item</div>
        <div class="topbar-subtitle" id="view-subtitle">Semua permintaan pemenuhan barang</div>
      </div>
      <button class="btn btn-primary" id="topbar-action" onclick="openAddItem()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
        Tambah Item
      </button>
    </div>

    <!-- ITEMS VIEW -->
    <div class="view active" id="view-items">
      <div class="content">
        <div class="metrics-grid" id="metrics-area"></div>
      </div>
      <div class="card" style="margin: 0 28px 24px;">
        <div class="search-bar">
          <div class="search-input-wrap">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
            <input type="text" id="search-input" placeholder="Cari produk, merk, spesifikasi..." oninput="renderTable()">
          </div>
          <select class="filter" id="filter-cat" onchange="renderTable()">
            <option value="">Semua kategori</option>
          </select>
          <select class="filter" id="filter-status" onchange="renderTable()">
            <option value="">Semua status</option>
            <option>Lengkap</option>
            <option>Perlu Update</option>
            <option>Belum Ada</option>
          </select>
        </div>
        <div class="tbl-wrap">
          <table>
            <thead>
              <tr>
                <th>#</th>
                <th>Produk</th>
                <th>Kategori</th>
                <th>Vol</th>
                <th>Harga Satuan</th>
                <th>Total</th>
                <th>Distributor</th>
                <th>Status</th>
                <th style="width:90px">Aksi</th>
              </tr>
            </thead>
            <tbody id="items-tbody"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- VENDORS VIEW -->
    <div class="view" id="view-vendors">
      <div class="content">
        <div class="card" style="margin:0">
          <div class="card-header">
            <h3>Database Distributor</h3>
            <div class="search-input-wrap" style="max-width:220px">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
              <input type="text" id="vendor-search" placeholder="Cari distributor..." oninput="renderVendors()">
            </div>
            <button class="btn" onclick="openAddVendor()">
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
              Tambah
            </button>
          </div>
          <div class="vendor-grid" id="vendor-grid"></div>
        </div>
      </div>
    </div>

    <!-- HISTORY VIEW -->
    <div class="view" id="view-history">
      <div class="content">
        <div class="card" style="margin:0">
          <div class="card-header"><h3>Riwayat Perubahan Harga</h3></div>
          <div style="padding:0 20px 8px" id="history-list"></div>
        </div>
      </div>
    </div>

    <!-- EXPORT VIEW -->
    <div class="view" id="view-export">
      <div class="content">
        <div class="metrics-grid" style="grid-template-columns:1fr 1fr;max-width:600px">
          <div class="metric-card">
            <div class="label">Total Item</div>
            <div class="value" id="exp-total">0</div>
            <div class="sub">dalam database</div>
          </div>
          <div class="metric-card accent">
            <div class="label">Total Nilai</div>
            <div class="value" id="exp-nilai" style="font-size:20px">Rp 0</div>
            <div class="sub">estimasi keseluruhan</div>
          </div>
        </div>
        <div class="card" style="margin:0;max-width:600px">
          <div class="card-header"><h3>Pilih Format Export</h3></div>
          <div style="padding:20px;display:flex;flex-direction:column;gap:12px">
            <button class="btn btn-primary" style="justify-content:flex-start;gap:10px" onclick="exportCSV()">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
              Download CSV (siap buka di Excel)
            </button>
            <button class="btn" style="justify-content:flex-start;gap:10px" onclick="copyToClipboard()">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
              Salin ke Clipboard (paste ke Excel)
            </button>
          </div>
          <div style="padding:0 20px 20px">
            <p style="font-size:11px;color:var(--text3);margin-bottom:8px;font-weight:600;text-transform:uppercase;letter-spacing:0.05em">Preview (5 baris pertama)</p>
            <div class="tbl-wrap" id="export-preview"></div>
          </div>
        </div>
      </div>
    </div>
  </main>
</div>

<!-- ======= MODAL: ADD/EDIT ITEM ======= -->
<div class="modal-overlay" id="modal-item">
  <div class="modal">
    <div class="modal-header">
      <h2 id="modal-item-title">Tambah Item Baru</h2>
      <button class="btn-icon" onclick="closeModal('modal-item')">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
      </button>
    </div>
    <div class="modal-body">
      <div class="form-row">
        <div class="form-group form-full">
          <label>Nama Produk *</label>
          <input type="text" id="f-name" placeholder="Handy Talky Motorola CP1660">
        </div>
        <div class="form-group">
          <label>Kategori</label>
          <select id="f-cat">
            <option>Engineering & Electronic</option>
            <option>FB Equipment</option>
            <option>Furniture</option>
            <option>Dining & Tableware</option>
            <option>Lainnya</option>
          </select>
        </div>
        <div class="form-group">
          <label>Satuan</label>
          <input type="text" id="f-unit" placeholder="unit / set / pcs">
        </div>
        <div class="form-group">
          <label>Merk</label>
          <input type="text" id="f-brand" placeholder="Motorola">
        </div>
        <div class="form-group">
          <label>Type / Model</label>
          <input type="text" id="f-type" placeholder="CP1660">
        </div>
        <div class="form-group">
          <label>Volume</label>
          <input type="number" id="f-vol" placeholder="5" min="0">
        </div>
        <div class="form-group form-full">
          <label>Spesifikasi</label>
          <textarea id="f-spec" placeholder="VHF 136-174MHz, IP54, 99 channel..."></textarea>
        </div>
        <div class="form-group">
          <label>Harga Satuan (Rp)</label>
          <input type="number" id="f-price" placeholder="2100000">
        </div>
        <div class="form-group">
          <label>Distributor</label>
          <select id="f-vendor"><option value="">-- Pilih distributor --</option></select>
        </div>
      </div>
      <div id="ai-suggest-area"></div>
    </div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal('modal-item')">Batal</button>
      <button class="btn" id="ai-btn" onclick="runAISuggest()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>
        AI Suggest Distributor
      </button>
      <button class="btn btn-primary" onclick="saveItem()">Simpan</button>
    </div>
  </div>
</div>

<!-- ======= MODAL: ADD VENDOR ======= -->
<div class="modal-overlay" id="modal-vendor">
  <div class="modal">
    <div class="modal-header">
      <h2>Tambah Distributor</h2>
      <button class="btn-icon" onclick="closeModal('modal-vendor')">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
      </button>
    </div>
    <div class="modal-body">
      <div class="form-row">
        <div class="form-group form-full"><label>Nama Distributor *</label><input type="text" id="v-name" placeholder="PT. Pusat Sound System"></div>
        <div class="form-group"><label>No. HP / WhatsApp</label><input type="text" id="v-hp" placeholder="0852-1888-6000"></div>
        <div class="form-group"><label>Wilayah</label><input type="text" id="v-area" placeholder="Jakarta Barat"></div>
        <div class="form-group form-full"><label>Website</label><input type="url" id="v-web" placeholder="https://pusatsoundsystem.com"></div>
        <div class="form-group form-full"><label>Kategori Produk</label><input type="text" id="v-cats" placeholder="Speaker, Microphone, Audio"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal('modal-vendor')">Batal</button>
      <button class="btn btn-primary" onclick="saveVendor()">Simpan</button>
    </div>
  </div>
</div>

<!-- ======= MODAL: DETAIL ======= -->
<div class="modal-overlay" id="modal-detail">
  <div class="modal">
    <div class="modal-header">
      <h2 id="detail-name">Detail Item</h2>
      <button class="btn-icon" onclick="closeModal('modal-detail')">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
      </button>
    </div>
    <div class="modal-body" id="detail-body"></div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal('modal-detail')">Tutup</button>
      <button class="btn btn-primary" id="detail-edit-btn">Edit Item</button>
    </div>
  </div>
</div>

<!-- ======= MODAL: IMPORT ======= -->
<div class="modal-overlay" id="modal-import">
  <div class="modal">
    <div class="modal-header">
      <h2>Import dari Excel</h2>
      <button class="btn-icon" onclick="closeModal('modal-import')">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
      </button>
    </div>
    <div class="modal-body">
      <p style="font-size:13px;color:var(--text2);margin-bottom:14px">Salin data dari Excel lalu paste di sini. Urutan kolom: <strong>Nama, Kategori, Merk, Type, Vol, Satuan, Harga Satuan, Nama Distributor</strong></p>
      <div class="form-group">
        <label>Data Excel (tab-separated)</label>
        <textarea id="import-text" style="min-height:160px;font-family:monospace;font-size:12px" placeholder="Handy Talky Motorola&#9;Engineering & Electronic&#9;Motorola&#9;CP1660&#9;5&#9;unit&#9;2100000&#9;KAI Communication"></textarea>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal('modal-import')">Batal</button>
      <button class="btn btn-primary" onclick="doImport()">Import Data</button>
    </div>
  </div>
</div>

<div id="toast"></div>

<script>
const KEYS = { items:'pt_items_v4', vendors:'pt_vendors_v4', history:'pt_history_v4' };
let items=[], vendors=[], history=[], editingId=null;

function load(){
  try{
    items = JSON.parse(localStorage.getItem(KEYS.items)||'[]');
    vendors = JSON.parse(localStorage.getItem(KEYS.vendors)||'[]');
    history = JSON.parse(localStorage.getItem(KEYS.history)||'[]');
  }catch(e){ items=[]; vendors=[]; history=[]; }
  if(!items.length) seed();
  render();
}

function save(){
  localStorage.setItem(KEYS.items, JSON.stringify(items));
  localStorage.setItem(KEYS.vendors, JSON.stringify(vendors));
  localStorage.setItem(KEYS.history, JSON.stringify(history));
}

function seed(){
  vendors = [
    {id:'v1',name:'KAI Communication Indonesia',hp:'0817-9118-766',area:'Jakarta Barat (Glodok Makmur)',web:'https://kaicommunication.co.id',cats:'HT, Radio, Motorola'},
    {id:'v2',name:'Pusat Sound System',hp:'0852-1888-6000',area:'Jakarta Barat (Pinangsia, Glodok)',web:'https://pusatsoundsystem.com',cats:'Speaker, Microphone, Audio, BOSE, Shure'},
    {id:'v3',name:'PT. Trikomindo Karunia Utama',hp:'021-6120196',area:'Jakarta Pusat (Harco Mangga Dua)',web:'https://toko-trikomindo.com',cats:'Proyektor, AV, Panasonic'},
    {id:'v4',name:'Astro Mesin',hp:'021-2309-5266',area:'Jakarta Barat (Kalideres)',web:'https://astromesin.com',cats:'Kulkas, Mesin Dapur, GEA, Hotel Equipment'},
    {id:'v5',name:'Multimo Furniture',hp:'0231-8544449',area:'Sidoarjo (Kirim Nasional)',web:'https://multimo.co.id',cats:'Meja Bundar, Kursi, Furniture Ballroom'},
    {id:'v6',name:'Dipalanta Cutlery',hp:'-',area:'Jakarta Barat',web:'https://tokopedia.com/dipalanta',cats:'Sendok, Garpu, Cutlery Nicklaus'},
    {id:'v7',name:'ZEN Tableware (PT. Indo Porcelain)',hp:'0877-7409-2622',area:'Jakarta Selatan (Nasional)',web:'https://zentableware.com',cats:'Piring, Cangkir, Porcelain, Chinaware'},
    {id:'v8',name:'Informa (Ruparupa)',hp:'1500-191',area:'Jakarta & Tangerang (Multi-cabang)',web:'https://ruparupa.com/informastore',cats:'Placemat, Home Living, Dekorasi'},
  ];
  items = [
    {id:'i1',name:'Handy Talky Motorola C2660',cat:'Engineering & Electronic',brand:'Motorola',type:'CP1660',vol:5,unit:'unit',spec:'VHF 136-174MHz, IP54, 99 channel, Li-Ion 11 jam',price:2100000,vendorId:'v1',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i2',name:'APD + Safety Rack',cat:'Engineering & Electronic',brand:'No Brand',type:'2 Pintu',vol:1,unit:'set',spec:'Plat mild steel 1.2mm, kaca 5mm, 180x120x40cm, powder coating red',price:null,vendorId:'',status:'Belum Ada',createdAt:'2025-06-01'},
    {id:'i3',name:'Speaker Ruang Meeting Bose S1 Pro',cat:'Engineering & Electronic',brand:'BOSE',type:'S1PRO',vol:2,unit:'unit',spec:'Baterai 11 jam, Bluetooth streaming, 3 saluran input, ToneMatch',price:13000000,vendorId:'v2',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i4',name:'Wireless Microphone Shure BLX24/SM58',cat:'Engineering & Electronic',brand:'SHURE',type:'BLX24/SM58',vol:2,unit:'unit',spec:'Range 100m, 14 jam, 12 channel per band, QuickScan',price:6900000,vendorId:'v2',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i5',name:'Proyektor 5000 Lumens Panasonic',cat:'Engineering & Electronic',brand:'Panasonic',type:'PT-VW530 WXGA',vol:1,unit:'unit',spec:'5000 Lumens, resolusi 1280x800, HDMI, LAN, 7000 jam eco',price:20035000,vendorId:'v3',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i6',name:'Mini Refrigerator GEA',cat:'FB Equipment',brand:'GEA',type:'RS-06DR',vol:65,unit:'unit',spec:'45L, 50W, R600a, suhu 0~8°C, 439x470x510mm',price:1200000,vendorId:'v4',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i7',name:'Wood Tray (Custom Kayu Jati)',cat:'FB Equipment',brand:'Custom',type:'Tray Room Service',vol:10,unit:'unit',spec:'P50 x L40 x T4 cm, Kayu Jati Solid, warna cokelat',price:null,vendorId:'',status:'Belum Ada',createdAt:'2025-06-01'},
    {id:'i8',name:'Round Table Diameter 120cm',cat:'Furniture',brand:'Fortune HPL (Multimo)',type:'Fortune 120 HPL',vol:4,unit:'unit',spec:'Ø120x75cm, multiplek 15mm+HPL, rangka besi powder coating, lipat',price:1950000,vendorId:'v5',status:'Lengkap',createdAt:'2025-06-01'},
    {id:'i9',name:'Set Cutleries Nicklaus',cat:'Dining & Tableware',brand:'Nicklaus',type:'Dessert Spoon / Fork / Tea Spoon / Cake Fork',vol:450,unit:'pcs',spec:'Stainless steel 18/10, panjang 13-18cm, mirror polished',price:35000,vendorId:'v6',status:'Perlu Update',createdAt:'2025-06-01'},
    {id:'i10',name:'Set Chinaware ZEN',cat:'Dining & Tableware',brand:'ZEN',type:'Dessert Plate / BnB Plate / Cereal Bowl / Tea Cup',vol:950,unit:'unit',spec:'Porcelain putih polos, SNI certified, microwave & dishwasher safe',price:35000,vendorId:'v7',status:'Perlu Update',createdAt:'2025-06-01'},
    {id:'i11',name:'Place Mat Informa PVC',cat:'Dining & Tableware',brand:'PLACEMAT INFORMA',type:'Placemat PVC',vol:80,unit:'unit',spec:'30x40cm, bahan PVC, warna cokelat, alas piring restoran',price:49000,vendorId:'v8',status:'Lengkap',createdAt:'2025-06-01'},
  ];
  history = [
    {itemId:'i3',itemName:'Speaker Bose S1 Pro',oldPrice:12500000,newPrice:13000000,date:'2025-05-10',by:'Tim Procurement'},
    {itemId:'i9',itemName:'Cutleries Nicklaus',oldPrice:30000,newPrice:35000,date:'2025-06-01',by:'Admin'},
    {itemId:'i10',itemName:'Chinaware ZEN',oldPrice:28000,newPrice:35000,date:'2025-06-01',by:'Admin'},
  ];
  save();
}

function render(){ updateMetrics(); renderTable(); renderVendors(); renderHistory(); populateCats(); populateVendorSel(); updateBadge(); renderExport(); }
function fmt(n){ return n ? 'Rp '+parseInt(n).toLocaleString('id') : '—'; }
function uid(){ return 'x'+Date.now()+Math.random().toString(36).slice(2,7); }

function updateMetrics(){
  const total=items.length, withPrice=items.filter(i=>i.price).length;
  const totalVal=items.reduce((s,i)=>i.price&&i.vol?s+i.price*i.vol:s,0);
  const needUpdate=items.filter(i=>i.status!=='Lengkap').length;
  document.getElementById('metrics-area').innerHTML=`
    <div class="metric-card"><div class="label">Total Item</div><div class="value">${total}</div><div class="sub">dalam database</div></div>
    <div class="metric-card"><div class="label">Data Lengkap</div><div class="value" style="color:var(--accent)">${withPrice}</div><div class="sub">dari ${total} item</div></div>
    <div class="metric-card"><div class="label">Perlu Update</div><div class="value" style="color:var(--warn)">${needUpdate}</div><div class="sub">item belum lengkap</div></div>
    <div class="metric-card accent"><div class="label">Estimasi Total</div><div class="value" style="font-size:${totalVal>1e9?'16px':'20px'}">Rp ${(totalVal/1e6).toFixed(1)}M</div><div class="sub">nilai keseluruhan</div></div>`;
}

function updateBadge(){
  const n = items.filter(i=>i.status!=='Lengkap').length;
  document.getElementById('badge-update').textContent = n;
  document.getElementById('badge-update').style.display = n>0?'':'none';
}

function populateCats(){
  const cats=[...new Set(items.map(i=>i.cat))];
  const sel=document.getElementById('filter-cat');
  const cur=sel.value;
  sel.innerHTML='<option value="">Semua kategori</option>'+cats.map(c=>`<option${c===cur?' selected':''}>${c}</option>`).join('');
}

function populateVendorSel(){
  const sel=document.getElementById('f-vendor');
  sel.innerHTML='<option value="">-- Pilih distributor --</option>'+vendors.map(v=>`<option value="${v.id}">${v.name}</option>`).join('');
}

function getFiltered(){
  const q=(document.getElementById('search-input')||{}).value?.toLowerCase()||'';
  const cat=(document.getElementById('filter-cat')||{}).value||'';
  const st=(document.getElementById('filter-status')||{}).value||'';
  return items.filter(i=>{
    const txt=(i.name+i.brand+i.type+i.cat+(i.spec||'')).toLowerCase();
    return (!q||txt.includes(q))&&(!cat||i.cat===cat)&&(!st||i.status===st);
  });
}

function renderTable(){
  updateMetrics(); updateBadge(); populateCats();
  const rows=getFiltered();
  const tbody=document.getElementById('items-tbody');
  if(!rows.length){tbody.innerHTML=`<tr><td colspan="9"><div class="empty"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="5" width="20" height="14" rx="2"/><path d="M2 10h20"/></svg><p>Tidak ada item ditemukan</p></div></td></tr>`;return;}
  tbody.innerHTML=rows.map((it,idx)=>{
    const v=vendors.find(x=>x.id===it.vendorId);
    const bc=it.status==='Lengkap'?'badge-green':it.status==='Perlu Update'?'badge-yellow':'badge-red';
    const total=it.price&&it.vol?'Rp '+(it.price*it.vol).toLocaleString('id'):'—';
    return `<tr>
      <td style="color:var(--text3);font-size:12px">${idx+1}</td>
      <td><div style="font-weight:500;max-width:180px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${it.name}</div><div style="font-size:11px;color:var(--text3)">${it.brand} · ${it.type}</div></td>
      <td><span class="badge badge-gray" style="font-size:10px">${it.cat}</span></td>
      <td>${it.vol} <span style="color:var(--text3)">${it.unit}</span></td>
      <td style="font-weight:500">${it.price?'Rp '+it.price.toLocaleString('id'):'<span style="color:var(--text3)">—</span>'}</td>
      <td style="color:var(--text2);font-size:12px">${total}</td>
      <td>${v?`<div style="font-size:12px;font-weight:500;max-width:140px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${v.name}</div><div style="font-size:11px;color:var(--text3)">${v.area}</div>`:'<span style="color:var(--text3);font-size:12px">Belum ada</span>'}</td>
      <td><span class="badge ${bc}">${it.status}</span></td>
      <td>
        <div style="display:flex;gap:4px">
          <button class="btn-icon" title="Detail" onclick="openDetail('${it.id}')"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/><circle cx="12" cy="12" r="3"/></svg></button>
          <button class="btn-icon" title="Edit" onclick="openEditItem('${it.id}')"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg></button>
          <button class="btn-icon danger" title="Hapus" onclick="deleteItem('${it.id}')"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14a2 2 0 01-2 2H8a2 2 0 01-2-2L5 6"/><path d="M10 11v6M14 11v6M9 6V4a1 1 0 011-1h4a1 1 0 011 1v2"/></svg></button>
        </div>
      </td>
    </tr>`;
  }).join('');
}

function renderVendors(){
  const q=(document.getElementById('vendor-search')||{}).value?.toLowerCase()||'';
  const list=vendors.filter(v=>(v.name+v.area+(v.cats||'')).toLowerCase().includes(q));
  const grid=document.getElementById('vendor-grid');
  if(!list.length){grid.innerHTML='<div class="empty" style="grid-column:1/-1"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg><p>Belum ada distributor</p></div>';return;}
  grid.innerHTML=list.map(v=>{
    const cnt=items.filter(i=>i.vendorId===v.id).length;
    return `<div class="vendor-card">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:8px">
        <h4>${v.name}</h4>
        <span class="badge badge-blue">${cnt} item</span>
      </div>
      <div class="vendor-row"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13S3 17 3 10a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>${v.area}</div>
      ${v.hp&&v.hp!=='-'?`<div class="vendor-row"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81 19.79 19.79 0 010 1.18 2 2 0 012 0h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 14.92v2z"/></svg>${v.hp}</div>`:''}
      ${v.cats?`<div class="vendor-row"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20.59 13.41l-7.17 7.17a2 2 0 01-2.83 0L2 12V2h10l8.59 8.59a2 2 0 010 2.82z"/><line x1="7" y1="7" x2="7.01" y2="7"/></svg><span style="font-size:11px">${v.cats}</span></div>`:''}
      ${v.web&&v.web!=='-'?`<div class="vendor-row"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 014 10 15.3 15.3 0 01-4 10 15.3 15.3 0 01-4-10 15.3 15.3 0 014-10z"/></svg><a href="${v.web}" target="_blank" style="color:var(--info);font-size:11px;text-overflow:ellipsis;overflow:hidden;white-space:nowrap;max-width:180px;display:inline-block">${v.web.replace('https://','')}</a></div>`:''}
    </div>`;
  }).join('');
}

function renderHistory(){
  const el=document.getElementById('history-list');
  if(!history.length){el.innerHTML='<div class="empty"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg><p>Belum ada riwayat perubahan harga</p></div>';return;}
  const sorted=[...history].sort((a,b)=>b.date.localeCompare(a.date));
  el.innerHTML=sorted.map(h=>{
    const diff=h.oldPrice&&h.newPrice?((h.newPrice-h.oldPrice)/h.oldPrice*100).toFixed(1):null;
    const cls=diff>0?'up':'dn';
    const arrow=diff>0?'↑':'↓';
    return `<div class="history-item">
      <div style="width:36px;height:36px;border-radius:50%;background:var(--surface2);display:flex;align-items:center;justify-content:center">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
      </div>
      <div>
        <div style="font-weight:500;font-size:13px">${h.itemName}</div>
        <div style="font-size:11px;color:var(--text3)">${h.date} · ${h.by}</div>
      </div>
      <div style="font-size:12px;text-align:right">
        <div style="color:var(--text3);text-decoration:line-through">${fmt(h.oldPrice)}</div>
        <div style="font-weight:600">${fmt(h.newPrice)}</div>
      </div>
      ${diff!==null?`<span class="${cls}">${arrow} ${Math.abs(diff)}%</span>`:'<span></span>'}
    </div>`;
  }).join('');
}

function renderExport(){
  const total=items.length;
  const totalVal=items.reduce((s,i)=>i.price&&i.vol?s+i.price*i.vol:s,0);
  const el1=document.getElementById('exp-total');
  const el2=document.getElementById('exp-nilai');
  if(el1) el1.textContent=total;
  if(el2) el2.textContent='Rp '+(totalVal/1e6).toFixed(1)+'M';
  const header=['No','Nama Produk','Kategori','Merk','Type','Spesifikasi','Vol','Satuan','Harga Satuan','Jumlah','Nama Distributor','No HP','Wilayah','Website'];
  const rows=items.map((it,i)=>{const v=vendors.find(x=>x.id===it.vendorId);return [i+1,it.name,it.cat,it.brand,it.type,it.spec||'',it.vol,it.unit,it.price||'',it.price&&it.vol?it.price*it.vol:'',v?.name||'',v?.hp||'',v?.area||'',v?.web||''];});
  const prev=document.getElementById('export-preview');
  if(prev) prev.innerHTML=`<table><thead><tr>${header.map(h=>`<th>${h}</th>`).join('')}</tr></thead><tbody>${rows.slice(0,5).map(r=>`<tr>${r.map(c=>`<td>${c}</td>`).join('')}</tr>`).join('')}</tbody></table>`;
}

function showView(name, el){
  document.querySelectorAll('.view').forEach(v=>v.classList.remove('active'));
  document.getElementById('view-'+name).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  el.classList.add('active');
  const titles={items:'Daftar Item',vendors:'Database Distributor',history:'Riwayat Harga',export:'Export Data'};
  const subs={items:'Semua permintaan pemenuhan barang',vendors:'Kelola kontak distributor Jabodetabek',history:'Perubahan harga dari waktu ke waktu',export:'Download data dalam format Excel/CSV'};
  const acts={items:'Tambah Item',vendors:'Tambah Distributor',history:null,export:null};
  document.getElementById('view-title').textContent=titles[name];
  document.getElementById('view-subtitle').textContent=subs[name];
  const ab=document.getElementById('topbar-action');
  if(acts[name]){ab.style.display='';ab.textContent=acts[name];ab.onclick=name==='items'?openAddItem:openAddVendor;}
  else ab.style.display='none';
  if(name==='history') renderHistory();
  if(name==='vendors') renderVendors();
  if(name==='export') renderExport();
}

function openAddItem(){
  editingId=null;
  document.getElementById('modal-item-title').textContent='Tambah Item Baru';
  ['f-name','f-unit','f-brand','f-type','f-spec'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('f-price').value='';
  document.getElementById('f-vol').value='';
  document.getElementById('f-cat').value='Engineering & Electronic';
  populateVendorSel();
  document.getElementById('f-vendor').value='';
  document.getElementById('ai-suggest-area').innerHTML='';
  document.getElementById('modal-item').classList.add('open');
}

function openEditItem(id){
  const it=items.find(i=>i.id===id); if(!it) return;
  editingId=id;
  document.getElementById('modal-item-title').textContent='Edit Item';
  document.getElementById('f-name').value=it.name||'';
  document.getElementById('f-cat').value=it.cat||'';
  document.getElementById('f-brand').value=it.brand||'';
  document.getElementById('f-type').value=it.type||'';
  document.getElementById('f-spec').value=it.spec||'';
  document.getElementById('f-vol').value=it.vol||'';
  document.getElementById('f-unit').value=it.unit||'';
  document.getElementById('f-price').value=it.price||'';
  document.getElementById('ai-suggest-area').innerHTML='';
  populateVendorSel();
  document.getElementById('f-vendor').value=it.vendorId||'';
  document.getElementById('modal-item').classList.add('open');
}

function openDetail(id){
  const it=items.find(i=>i.id===id); if(!it) return;
  const v=vendors.find(x=>x.id===it.vendorId);
  const hist=history.filter(h=>h.itemId===id).sort((a,b)=>b.date.localeCompare(a.date));
  document.getElementById('detail-name').textContent=it.name;
  document.getElementById('detail-body').innerHTML=`
    <div class="detail-grid">
      <div class="detail-item"><label>Kategori</label><div class="val">${it.cat}</div></div>
      <div class="detail-item"><label>Merk / Type</label><div class="val">${it.brand} ${it.type}</div></div>
      <div class="detail-item"><label>Volume</label><div class="val">${it.vol} ${it.unit}</div></div>
      <div class="detail-item"><label>Harga Satuan</label><div class="val" style="color:var(--accent)">${fmt(it.price)}</div></div>
      <div class="detail-item"><label>Total Nilai</label><div class="val">${it.price&&it.vol?'Rp '+(it.price*it.vol).toLocaleString('id'):'—'}</div></div>
      <div class="detail-item"><label>Status</label><div><span class="badge ${it.status==='Lengkap'?'badge-green':it.status==='Perlu Update'?'badge-yellow':'badge-red'}">${it.status}</span></div></div>
    </div>
    ${it.spec?`<div style="background:var(--bg);border-radius:var(--radius);padding:12px;margin-bottom:16px;font-size:13px;color:var(--text2);line-height:1.6"><div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:0.05em;color:var(--text3);margin-bottom:6px">Spesifikasi</div>${it.spec}</div>`:''}
    ${v?`<div style="background:var(--accent-light);border:1px solid #c0d9c9;border-radius:var(--radius);padding:14px;margin-bottom:16px">
      <div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:0.05em;color:var(--accent);margin-bottom:8px">Distributor</div>
      <div style="font-weight:600;font-size:14px;margin-bottom:4px">${v.name}</div>
      <div style="font-size:12px;color:var(--text2)">${v.area} · ${v.hp}</div>
      ${v.web&&v.web!=='-'?`<a href="${v.web}" target="_blank" style="font-size:12px;color:var(--info)">${v.web}</a>`:''}
    </div>`:''}
    ${hist.length?`<div><div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:0.05em;color:var(--text3);margin-bottom:8px">Riwayat Harga</div>${hist.map(h=>{const d=h.oldPrice&&h.newPrice?((h.newPrice-h.oldPrice)/h.oldPrice*100).toFixed(1):null;return `<div class="history-item"><div style="font-size:12px;font-weight:500">${fmt(h.oldPrice)} → ${fmt(h.newPrice)}</div><div style="font-size:11px;color:var(--text3)">${h.date} · ${h.by}</div>${d?`<span class="${parseFloat(d)>0?'up':'dn'}">${parseFloat(d)>0?'↑':'↓'} ${Math.abs(d)}%</span>`:'<span></span>'}</div>`;}).join('')}</div>`:''}`; 
  document.getElementById('detail-edit-btn').onclick=()=>{closeModal('modal-detail');openEditItem(id);};
  document.getElementById('modal-detail').classList.add('open');
}

function saveItem(){
  const name=document.getElementById('f-name').value.trim();
  if(!name){toast('Nama produk wajib diisi','warn');return;}
  const newPrice=parseFloat(document.getElementById('f-price').value)||null;
  const vendorId=document.getElementById('f-vendor').value;
  const status=newPrice&&vendorId?'Lengkap':newPrice||vendorId?'Perlu Update':'Belum Ada';
  if(editingId){
    const idx=items.findIndex(i=>i.id===editingId);
    const oldPrice=items[idx].price;
    if(oldPrice&&newPrice&&oldPrice!==newPrice) history.push({itemId:editingId,itemName:name,oldPrice,newPrice,date:new Date().toISOString().slice(0,10),by:'Tim'});
    items[idx]={...items[idx],name,cat:document.getElementById('f-cat').value,brand:document.getElementById('f-brand').value,type:document.getElementById('f-type').value,spec:document.getElementById('f-spec').value,vol:parseInt(document.getElementById('f-vol').value)||0,unit:document.getElementById('f-unit').value,price:newPrice,vendorId,status};
  } else {
    items.push({id:uid(),name,cat:document.getElementById('f-cat').value,brand:document.getElementById('f-brand').value,type:document.getElementById('f-type').value,spec:document.getElementById('f-spec').value,vol:parseInt(document.getElementById('f-vol').value)||0,unit:document.getElementById('f-unit').value,price:newPrice,vendorId,status,createdAt:new Date().toISOString().slice(0,10)});
  }
  save(); closeModal('modal-item'); render(); toast('Item berhasil disimpan');
}

function deleteItem(id){
  if(!confirm('Hapus item ini? Tindakan tidak bisa dibatalkan.')) return;
  items=items.filter(i=>i.id!==id);
  save(); render(); toast('Item dihapus');
}

function openAddVendor(){
  ['v-name','v-hp','v-area','v-web','v-cats'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('modal-vendor').classList.add('open');
}

function saveVendor(){
  const name=document.getElementById('v-name').value.trim();
  if(!name){toast('Nama distributor wajib diisi','warn');return;}
  vendors.push({id:uid(),name,hp:document.getElementById('v-hp').value,area:document.getElementById('v-area').value,web:document.getElementById('v-web').value,cats:document.getElementById('v-cats').value});
  save(); closeModal('modal-vendor'); renderVendors(); populateVendorSel(); toast('Distributor ditambahkan');
}

function closeModal(id){document.getElementById(id).classList.remove('open');}
function openImport(){document.getElementById('import-text').value='';document.getElementById('modal-import').classList.add('open');}

function doImport(){
  const text=document.getElementById('import-text').value.trim();
  if(!text) return;
  const lines=text.split('\n').filter(l=>l.trim());
  let added=0;
  lines.forEach(line=>{
    const cols=line.split('\t');
    if(cols.length<2) return;
    const [name,cat,brand,type,vol,unit,price,vName]=cols;
    if(!name?.trim()||name.trim()==='Nama') return;
    const v=vendors.find(x=>x.name.toLowerCase().includes((vName||'').toLowerCase().trim()));
    items.push({id:uid(),name:name.trim(),cat:cat?.trim()||'Lainnya',brand:brand?.trim()||'',type:type?.trim()||'',spec:'',vol:parseInt(vol)||0,unit:unit?.trim()||'unit',price:parseFloat(price)||null,vendorId:v?.id||'',status:price&&v?'Lengkap':'Belum Ada',createdAt:new Date().toISOString().slice(0,10)});
    added++;
  });
  save(); closeModal('modal-import'); render(); toast(`${added} item berhasil diimport`);
}

async function runAISuggest(){
  const name=document.getElementById('f-name').value.trim();
  const brand=document.getElementById('f-brand').value.trim();
  const type=document.getElementById('f-type').value.trim();
  const cat=document.getElementById('f-cat').value;
  if(!name){toast('Isi nama produk terlebih dahulu','warn');return;}
  const area=document.getElementById('ai-suggest-area');
  area.innerHTML=`<div class="ai-box"><div class="ai-box-title"><div class="spinner"></div> AI sedang mencari distributor di Jabodetabek...</div><div class="progress"><div class="progress-fill" id="ai-prog" style="width:0%"></div></div></div>`;
  let prog=0;
  const t=setInterval(()=>{prog=Math.min(prog+6,88);const el=document.getElementById('ai-prog');if(el)el.style.width=prog+'%';},250);
  try{
    const resp=await fetch('https://api.anthropic.com/v1/messages',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:1000,messages:[{role:'user',content:`Kamu adalah asisten procurement hotel di Indonesia. Carikan 2-3 distributor di wilayah Jabodetabek untuk produk berikut:\nNama: ${name}\nBrand: ${brand||'-'}\nType: ${type||'-'}\nKategori: ${cat}\n\nBalas HANYA dalam format JSON array, tanpa teks lain:\n[\n  {"nama":"Nama Distributor","hp":"08xx-xxxx-xxxx","wilayah":"Jakarta Barat","link":"https://...","harga_estimasi":"Rp X.XXX.XXX","catatan":"singkat"}\n]`}]})});
    const data=await resp.json();
    clearInterval(t);
    const el=document.getElementById('ai-prog');if(el)el.style.width='100%';
    const txt=data.content?.[0]?.text||'[]';
    let results=[];
    try{results=JSON.parse(txt.replace(/```json|```/g,'').trim());}catch(e){}
    if(!results.length){area.innerHTML='<div class="ai-box"><div class="ai-box-title" style="color:var(--warn)">⚠ AI tidak menemukan hasil spesifik. Coba detail nama produk lebih lengkap.</div></div>';return;}
    area.innerHTML=`<div class="ai-box">
      <div class="ai-box-title">✦ AI menemukan ${results.length} rekomendasi</div>
      <p style="font-size:11px;color:var(--info);margin-bottom:6px">Klik "Pakai" untuk langsung mengisi form, atau "Simpan" untuk tambahkan ke database distributor.</p>
      ${results.map((r,i)=>`<div class="ai-result">
        <div>
          <div style="font-weight:600;font-size:13px">${r.nama}</div>
          <div style="font-size:11px;color:var(--text2);margin-top:2px">${r.wilayah||''} ${r.hp?'· '+r.hp:''}</div>
          ${r.harga_estimasi?`<div style="font-size:11px;color:var(--accent);font-weight:500;margin-top:2px">Estimasi: ${r.harga_estimasi}</div>`:''}
          ${r.catatan?`<div style="font-size:11px;color:var(--text3);margin-top:2px">${r.catatan}</div>`:''}
        </div>
        <div style="display:flex;flex-direction:column;gap:4px">
          <button class="btn btn-sm btn-primary" onclick='applyAI(${JSON.stringify(r).replace(/'/g,"\\'")})'> Pakai</button>
          <button class="btn btn-sm" onclick='saveAIVendor(${JSON.stringify(r).replace(/'/g,"\\'")})'> Simpan</button>
        </div>
      </div>`).join('')}
    </div>`;
  }catch(e){
    clearInterval(t);
    area.innerHTML='<div class="ai-box" style="border-color:#e8b4b4;background:var(--danger-light)"><div class="ai-box-title" style="color:var(--danger)">Gagal menghubungi AI. Periksa koneksi internet.</div></div>';
  }
}

function applyAI(r){
  let v=vendors.find(x=>x.name===r.nama);
  if(!v){v={id:uid(),name:r.nama,hp:r.hp||'-',area:r.wilayah||'-',web:r.link||'-',cats:''};vendors.push(v);save();}
  populateVendorSel();
  document.getElementById('f-vendor').value=v.id;
  if(r.harga_estimasi){const n=parseInt(r.harga_estimasi.replace(/[^\d]/g,''));if(n)document.getElementById('f-price').value=n;}
  toast('Distributor diterapkan ke form');
}

function saveAIVendor(r){
  if(vendors.find(v=>v.name===r.nama)){toast('Distributor sudah ada','warn');return;}
  vendors.push({id:uid(),name:r.nama,hp:r.hp||'-',area:r.wilayah||'-',web:r.link||'-',cats:''});
  save(); populateVendorSel(); toast('Distributor disimpan ke database');
}

function exportCSV(){
  const h=['No','Nama Produk','Kategori','Merk','Type','Spesifikasi','Vol','Satuan','Harga Satuan','Jumlah','Nama Distributor','No HP','Wilayah','Link Website'];
  const rows=items.map((it,i)=>{const v=vendors.find(x=>x.id===it.vendorId);return [i+1,`"${it.name}"`,`"${it.cat}"`,it.brand,it.type,`"${(it.spec||'').replace(/"/g,"'")}"`,it.vol,it.unit,it.price||'',it.price&&it.vol?it.price*it.vol:'',`"${v?.name||''}"`,v?.hp||'',`"${v?.area||''}"`,v?.web||''];});
  const csv=[h.join(','),...rows.map(r=>r.join(','))].join('\n');
  const blob=new Blob(['\ufeff'+csv],{type:'text/csv;charset=utf-8'});
  const a=Object.assign(document.createElement('a'),{href:URL.createObjectURL(blob),download:'BQ_Vendor_'+new Date().toISOString().slice(0,10)+'.csv'});
  a.click(); URL.revokeObjectURL(a.href); toast('File CSV diunduh');
}

function copyToClipboard(){
  const h=['No','Nama Produk','Kategori','Merk','Type','Spesifikasi','Vol','Satuan','Harga Satuan','Jumlah','Nama Distributor','No HP','Wilayah','Website'];
  const rows=items.map((it,i)=>{const v=vendors.find(x=>x.id===it.vendorId);return [i+1,it.name,it.cat,it.brand,it.type,it.spec||'',it.vol,it.unit,it.price||'',it.price&&it.vol?it.price*it.vol:'',v?.name||'',v?.hp||'',v?.area||'',v?.web||''];});
  navigator.clipboard.writeText([h,...rows].map(r=>r.join('\t')).join('\n')).then(()=>toast('Data disalin! Paste langsung ke Excel.'));
}

function toast(msg, type='ok'){
  const el=document.getElementById('toast');
  el.textContent=msg;
  el.style.background=type==='warn'?'var(--warn)':'var(--text)';
  el.classList.add('show');
  setTimeout(()=>el.classList.remove('show'),2800);
}

document.querySelectorAll('.modal-overlay').forEach(bg=>bg.addEventListener('click',e=>{if(e.target===bg)bg.classList.remove('open');}));

load();
</script>
</body>
</html>
HTMLEOF
echo "Done. Size: $(wc -c < /home/claude/procurement_app.html) bytes"
