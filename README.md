# perpustkaan-digital
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perpustakaan Digital Sekolah</title>
    <style>
        /* Reset dan Variabel */
        :root {
            --primary: #3498db;
            --secondary: #2ecc71;
            --dark: #2c3e50;
            --light: #ecf0f1;
            --danger: #e74c3c;
            --warning: #f39c12;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark);
        }
        
        /* Layout */
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar */
        .sidebar {
            width: 250px;
            background-color: var(--dark);
            color: white;
            padding: 20px 0;
            box-shadow: var(--shadow);
        }
        
        .sidebar-logo {
            padding: 0 20px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            text-align: center;
            margin-bottom: 20px;
        }
        
        .sidebar-logo h2 {
            font-size: 24px;
            margin-top: 10px;
        }
        
        .sidebar-menu {
            list-style: none;
        }
        
        .sidebar-menu li {
            margin-bottom: 5px;
        }
        
        .sidebar-menu a {
            display: flex;
            align-items: center;
            color: #bdc3c7;
            text-decoration: none;
            padding: 12px 20px;
            transition: all 0.3s;
        }
        
        .sidebar-menu a:hover, .sidebar-menu a.active {
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
            border-left: 4px solid var(--secondary);
        }
        
        .menu-icon {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }
        
        /* Main Content */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #ddd;
        }
        
        .user-profile {
            display: flex;
            align-items: center;
        }
        
        .user-profile img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        .search-bar {
            position: relative;
            width: 50%;
        }
        
        .search-bar input {
            width: 100%;
            padding: 10px 15px;
            border-radius: 5px;
            border: 1px solid #ddd;
            padding-left: 40px;
        }
        
        .search-icon {
            position: absolute;
            top: 50%;
            left: 15px;
            transform: translateY(-50%);
            color: #95a5a6;
        }
        
        .content {
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            min-height: 80vh;
        }
        
        .card {
            background: white;
            border-radius: 8px;
            box-shadow: var(--shadow);
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .card-header {
            background-color: var(--primary);
            color: white;
            padding: 15px 20px;
            font-weight: bold;
            font-size: 18px;
        }
        
        .card-body {
            padding: 20px;
        }
        
        /* Beranda */
        .hero-section {
            display: flex;
            margin-bottom: 30px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
        }
        
        .hero-image {
            width: 50%;
            background-image: url('/api/placeholder/800/400');
            background-size: cover;
            background-position: center;
        }
        
        .hero-content {
            width: 50%;
            background-color: var(--primary);
            color: white;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: white;
            border-radius: 8px;
            box-shadow: var(--shadow);
            padding: 20px;
            text-align: center;
        }
        
        .stat-card h3 {
            font-size: 32px;
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .book-section {
            margin-top: 30px;
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .book-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 20px;
        }
        
        .book-card {
            background: white;
            border-radius: 8px;
            box-shadow: var(--shadow);
            overflow: hidden;
            transition: transform 0.3s;
        }
        
        .book-card:hover {
            transform: translateY(-5px);
        }
        
        .book-cover {
            height: 250px;
            background-color: #ddd;
            background-image: url('/api/placeholder/180/250'); 
            background-size: cover;
            background-position: center;
        }
        
        .book-info {
            padding: 15px;
        }
        
        .book-title {
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .book-author {
            color: #666;
            font-size: 14px;
            margin-bottom: 10px;
        }
        
        .book-status {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 3px;
            font-size: 12px;
        }
        
        .status-available {
            background-color: #e3f5e9;
            color: var(--secondary);
        }
        
        .status-borrowed {
            background-color: #feeae1;
            color: var(--danger);
        }
        
        /* Katalog Buku */
        .filter-section {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .filter-dropdown {
            padding: 8px 15px;
            border-radius: 5px;
            border: 1px solid #ddd;
            background-color: white;
        }
        
        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 10px 15px;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
        
        .btn {
            padding: 10px 20px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.3s;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #2980b9;
        }
        
        .btn-secondary {
            background-color: var(--secondary);
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #27ae60;
        }
        
        .btn-danger {
            background-color: var(--danger);
            color: white;
        }
        
        /* Table Styles */
        .table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .table th, .table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        .table th {
            background-color: #f8f9fa;
            font-weight: 600;
        }
        
        .badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .badge-success {
            background-color: #e3f5e9;
            color: var(--secondary);
        }
        
        .badge-warning {
            background-color: #fef5e7;
            color: var(--warning);
        }
        
        .badge-danger {
            background-color: #feeae1;
            color: var(--danger);
        }
        
        /* Anggota Styles */
        .profile-section {
            display: flex;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .profile-image {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background-color: #ddd;
            background-image: url('/api/placeholder/150/150');
            background-size: cover;
            background-position: center;
        }
        
        .profile-details {
            flex: 1;
        }
        
        .profile-details h2 {
            margin-bottom: 15px;
        }
        
        .profile-stats {
            display: flex;
            gap: 30px;
            margin-top: 20px;
        }
        
        .profile-stat {
            text-align: center;
        }
        
        .profile-stat h3 {
            font-size: 24px;
            color: var(--primary);
            margin-bottom: 5px;
        }
        
        /* Help/Guide Styles */
        .accordion {
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-bottom: 10px;
            overflow: hidden;
        }
        
        .accordion-header {
            background-color: #f8f9fa;
            padding: 15px 20px;
            cursor: pointer;
            font-weight: 500;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .accordion-content {
            padding: 20px;
            border-top: 1px solid #ddd;
        }
        
        /* Contact Styles */
        .contact-info {
            margin-bottom: 30px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .contact-icon {
            width: 40px;
            height: 40px;
            background-color: var(--primary);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
        }
        
        .tab-content > div {
            display: none;
        }
        
        .tab-content > div.active {
            display: block;
        }
        
        /* Mobile Responsiveness */
        @media (max-width: 992px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                padding: 10px 0;
            }
            
            .sidebar-menu a {
                padding: 10px 15px;
            }
            
            .hero-section {
                flex-direction: column;
            }
            
            .hero-image, .hero-content {
                width: 100%;
            }
            
            .hero-content {
                padding: 20px;
            }
            
            .stats-container {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .search-bar {
                width: 100%;
                margin-bottom: 15px;
            }
            
            .header {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .profile-section {
                flex-direction: column;
                align-items: center;
                text-align: center;
            }
            
            .profile-details {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="sidebar-logo">
                <h2>PERPUSTAKAAN</h2>
                <div>Digital Sekolah</div>
            </div>
            <ul class="sidebar-menu">
                <li>
                    <a href="#" class="active" onclick="showPage('beranda')">
                        <span class="menu-icon">📚</span> Beranda
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('katalog')">
                        <span class="menu-icon">📋</span> Katalog Buku
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('pinjam')">
                        <span class="menu-icon">📖</span> Pinjam Buku
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('riwayat')">
                        <span class="menu-icon">🕒</span> Riwayat Peminjaman
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('anggota')">
                        <span class="menu-icon">👥</span> Anggota
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('bantuan')">
                        <span class="menu-icon">❓</span> Bantuan
                    </a>
                </li>
                <li>
                    <a href="#" onclick="showPage('kontak')">
                        <span class="menu-icon">📞</span> Kontak Kami
                    </a>
                </li>
            </ul>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <div class="search-bar">
                    <span class="search-icon">🔍</span>
                    <input type="text" placeholder="Cari buku, penulis, atau topik...">
                </div>
                <div class="user-profile">
                    <img src="/api/placeholder/40/40" alt="Profile">
                    <span>Selamat datang, <strong>Siswa</strong></span>
                </div>
            </div>
            
            <div class="tab-content">
                <!-- Beranda -->
                <div id="beranda" class="active">
                    <div class="hero-section">
                        <div class="hero-image"></div>
                        <div class="hero-content">
                            <h1>Selamat Datang di Perpustakaan Digital Sekolah</h1>
                            <p style="margin: 20px 0;">Nikmati kemudahan akses berbagai koleksi buku secara digital. Baca dan pinjam buku kapan saja dan di mana saja.</p>
                            <button class="btn btn-secondary" onclick="showPage('katalog')">Jelajahi Koleksi</button>
                        </div>
                    </div>
                    
                    <div class="stats-container">
                        <div class="stat-card">
                            <h3>5,000+</h3>
                            <p>Koleksi Buku</p>
                        </div>
                        <div class="stat-card">
                            <h3>1,500+</h3>
                            <p>Anggota Aktif</p>
                        </div>
                        <div class="stat-card">
                            <h3>250+</h3>
                            <p>Peminjaman/Bulan</p>
                        </div>
                        <div class="stat-card">
                            <h3>50+</h3>
                            <p>Penambahan Koleksi/Bulan</p>
                        </div>
                    </div>
                    
                    <div class="book-section">
                        <div class="section-header">
                            <h2>Buku Terbaru</h2>
                            <a href="#" onclick="showPage('katalog')">Lihat Semua</a>
                        </div>
                        
                        <div class="book-grid">
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Matematika Kelas X</div>
                                    <div class="book-author">Departemen Pendidikan</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Fisika Dasar</div>
                                    <div class="book-author">Prof. Dr. Ahmad</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Sejarah Indonesia</div>
                                    <div class="book-author">Dr. Siti Nurhaliza</div>
                                    <span class="book-status status-borrowed">Dipinjam</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Biologi Molekuler</div>
                                    <div class="book-author">Dr. Budi Santoso</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="book-section">
                        <div class="section-header">
                            <h2>Buku Populer</h2>
                            <a href="#" onclick="showPage('katalog')">Lihat Semua</a>
                        </div>
                        
                        <div class="book-grid">
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Kimia Dasar</div>
                                    <div class="book-author">Prof. Indra Wijaya</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Bahasa Inggris</div>
                                    <div class="book-author">Eliza Johnson</div>
                                    <span class="book-status status-borrowed">Dipinjam</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Algoritma Pemrograman</div>
                                    <div class="book-author">Dr. Rudi Hartono</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                            <div class="book-card">
                                <div class="book-cover"></div>
                                <div class="book-info">
                                    <div class="book-title">Ekonomi Mikro</div>
                                    <div class="book-author">Dra. Maya Putri</div>
                                    <span class="book-status status-available">Tersedia</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Katalog Buku -->
                <div id="katalog">
                    <h1>Katalog Buku</h1>
                    <p>Temukan berbagai koleksi buku kami dengan mudah.</p>
                    
                    <div class="filter-section">
                        <select class="filter-dropdown">
                            <option>Semua Kategori</option>
                            <option>Matematika</option>
                            <option>Fisika</option>
                            <option>Kimia</option>
                            <option>Biologi</option>
                            <option>Sejarah</option>
                            <option>Bahasa</option>
                            <option>Komputer</option>
                            <option>Ekonomi</option>
                        </select>
                        
                        <select class="filter-dropdown">
                            <option>Terbaru</option>
                            <option>Terpopuler</option>
                            <option>A-Z</option>
                            <option>Z-A</option>
                        </select>
                        
                        <select class="filter-dropdown">
                            <option>Semua Status</option>
                            <option>Tersedia</option>
                            <option>Dipinjam</option>
                        </select>
                    </div>
                    
                    <div class="book-grid">
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Matematika Kelas X</div>
                                <div class="book-author">Departemen Pendidikan</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Fisika Dasar</div>
                                <div class="book-author">Prof. Dr. Ahmad</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Sejarah Indonesia</div>
                                <div class="book-author">Dr. Siti Nurhaliza</div>
                                <span class="book-status status-borrowed">Dipinjam</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Biologi Molekuler</div>
                                <div class="book-author">Dr. Budi Santoso</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Kimia Dasar</div>
                                <div class="book-author">Prof. Indra Wijaya</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Bahasa Inggris</div>
                                <div class="book-author">Eliza Johnson</div>
                                <span class="book-status status-borrowed">Dipinjam</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Algoritma Pemrograman</div>
                                <div class="book-author">Dr. Rudi Hartono</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Ekonomi Mikro</div>
                                <div class="book-author">Dra. Maya Putri</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Matematika Kelas XI</div>
                                <div class="book-author">Departemen Pendidikan</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Fisika Kuantum</div>
                                <div class="book-author">Prof. Dr. Hendra</div>
                                <span class="book-status status-borrowed">Dipinjam</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Kimia Organik</div>
                                <div class="book-author">Dr. Anita Wijaya</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                        <div class="book-card">
                            <div class="book-cover"></div>
                            <div class="book-info">
                                <div class="book-title">Biologi Sel</div>
                                <div class="book-author">Prof. Dina Hasanah</div>
                                <span class="book-status status-available">Tersedia</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Pinjam Buku -->
                <div id="pinjam">
                    <h1>Pinjam Buku</h1>
                    <p>Pilih buku yang ingin Anda pinjam dari daftar tersedia di bawah ini.</p>
                    
                    <div class="card">
                        <div class="card-header">Buku Tersedia untuk Dipinjam</div>
                        <div class="card-body">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Judul Buku</th>
                                        <th>Pengarang</th>
                                        <th>Kategori</th>
                                        <th>Aksi</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>Matematika Kelas X</td>
                                        <td>Departemen Pendidikan</td>
                                        <td>Matematika</td>
                                        <td>
                                            <button class="btn btn-primary btn-sm">Pinjam</button>
                                            <button class="btn btn-secondary btn-sm">Baca Online</button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>Fisika Dasar</td>
                                        <td>Prof. Dr. Ahmad</td>
                                        <td>Fisika</td>
                                        <td>
                                            <button class="btn btn-primary btn-sm">Pinjam</button>
                                            <button class="btn btn-secondary btn-sm">Baca Online</button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>Biologi Molekuler</td>
                                        <td>Dr. Budi Santoso</td>
                                        <td>Biologi</td>
                                        <td>
                                            <button class="btn btn-primary btn-sm">Pinjam</button>
                                            <button class="btn btn-secondary btn-sm">Baca Online</button>
                                        </td>
                                    </tr>
