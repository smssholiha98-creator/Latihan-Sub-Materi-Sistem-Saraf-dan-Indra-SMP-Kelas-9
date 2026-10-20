# Latihan-Sub-Materi-Sistem-Saraf-dan-Indra-SMP-Kelas-9
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Ujian IPA: Sistem Saraf & Panca Indra</title>
    <style>
        :root {
            --primary: #0275d8;
            --success: #5cb85c;
            --danger: #d9534f;
            --light: #f4f7f6;
            --dark: #333;
        }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #e9ecef; margin: 0; padding: 0; -webkit-text-size-adjust: 100%; }
        .container { max-width: 900px; margin: 20px auto; background: white; padding: 20px 30px; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .hidden { display: none !important; }
        
        /* Header & Info */
        .header { display: flex; justify-content: space-between; align-items: center; border-bottom: 2px solid #eee; padding-bottom: 15px; margin-bottom: 20px; flex-wrap: wrap; gap: 10px; }
        .timer { font-size: 1.5em; font-weight: bold; color: var(--danger); }
        
        /* Layout Ujian (Responsive) */
        .exam-layout { display: flex; gap: 20px; }
        .main-content { flex: 3; }
        .sidebar { flex: 1; background: var(--light); padding: 15px; border-radius: 8px; max-height: 500px; overflow-y: auto; -webkit-overflow-scrolling: touch; }
        
        /* Panel Nomor */
        .panel-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 10px; margin-top: 15px; }
        .btn-nav { padding: 10px 0; text-align: center; border-radius: 5px; cursor: pointer; border: 1px solid #ccc; font-weight: bold; background: white; transition: 0.2s; -webkit-tap-highlight-color: transparent; }
        .btn-nav.answered { background: var(--success); color: white; border-color: var(--success); }
        .btn-nav.current { border: 3px solid var(--primary); transform: scale(1.1); }
        
        /* Soal & Opsi */
        .question-text { font-size: 1.2em; margin-bottom: 10px; line-height: 1.5; color: var(--dark); }
        .badge-diff { display: inline-block; padding: 4px 8px; font-size: 0.8em; border-radius: 4px; color: white; margin-bottom: 15px; }
        .badge-lots { background: #17a2b8; }
        .badge-mots { background: #f0ad4e; }
        
        .option-label { display: block; background: var(--light); padding: 12px; margin-bottom: 10px; border-radius: 5px; cursor: pointer; border: 1px solid #ddd; transition: 0.2s; -webkit-tap-highlight-color: transparent; }
        .option-label:hover { background: #e2e6ea; }
        .option-label input { margin-right: 10px; }
        .option-label.selected { background: #d0e8fc; border-color: var(--primary); }

        /* Tombol Aksi */
        .action-buttons { display: flex; justify-content: space-between; margin-top: 20px; gap: 10px; flex-wrap: wrap; }
        button { padding: 12px 20px; border: none; border-radius: 5px; cursor: pointer; font-size: 1em; font-weight: bold; transition: 0.2s; flex: 1; -webkit-appearance: none; }
        .btn-primary { background: var(--primary); color: white; }
        .btn-warning { background: #f0ad4e; color: white; }
        .btn-danger { background: var(--danger); color: white; width: 100%; margin-top: 20px;}
        
        /* Pembahasan */
        .result-item { border: 1px solid #ccc; border-radius: 8px; padding: 15px; margin-bottom: 15px; }
        .correct-ans { background: #d4edda; border-color: #c3e6cb; }
        .wrong-ans { background: #f8d7da; border-color: #f5c6cb; }
        .discussion { margin-top: 10px; font-size: 0.95em; background: #fff3cd; padding: 10px; border-left: 4px solid #ffc107; }
        
        input[type="text"], input[type="email"] { width: 100%; padding: 12px; margin: 10px 0 20px 0; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; -webkit-appearance: none;}

        /* MEDIA QUERY UNTUK HP (PHONE MODE & iOS) */
        @media (max-width: 768px) {
            /* Menggunakan min-height 100vh untuk iOS Safari address bar issue */
            .container { margin: 0; padding: 15px; border-radius: 0; min-height: 100vh; min-height: -webkit-fill-available; }
            html { height: -webkit-fill-available; }
            .exam-layout { flex-direction: column; }
            .sidebar { max-height: none; overflow-y: visible; margin-top: 20px; }
            .action-buttons button { font-size: 0.9em; padding: 10px; }
            .panel-grid { grid-template-columns: repeat(6, 1fr); }
            .header { flex-direction: column; align-items: flex-start; }
            .timer { align-self: flex-end; }
        }
    </style>
</head>
<body>

    <!-- HALAMAN LOGIN -->
    <div id="loginPage" class="container">
        <h2 style="text-align: center; color: var(--primary);">Ujian Akhir: Sistem Saraf & Panca Indra</h2>
        <p style="text-align: center;">Mata Pelajaran: IPA Kelas 9 | Durasi: 45 Menit</p>
        <hr>
        <label>Nama Lengkap (Sesuai Absen):</label>
        <input type="text" id="nama" placeholder="Masukkan nama lengkap" required>
        <label>Email Siswa:</label>
        <input type="email" id="email" placeholder="Masukkan alamat email" required>
        
        <div style="background: #fff3cd; padding: 15px; border-left: 4px solid #ffc107; margin-bottom: 20px; font-size: 0.9em;">
            <strong>⚠️ PERHATIAN PENTING:</strong><br>
            1. <b>Soal & Opsi Jawaban diacak</b> untuk setiap siswa.<br>
            2. Dilarang keras menekan tombol Home, berpindah aplikasi, membagi layar, atau membuka tab lain.<br>
            3. Pelanggaran lebih dari 2 kali akan mengakibatkan <b>DISKUALIFIKASI</b>.
        </div>
        
        <button class="btn-primary" style="width: 100%; padding: 15px; font-size: 1.1em;" onclick="mulaiUjian()">Saya Mengerti, Mulai Ujian</button>
    </div>

    <!-- HALAMAN UJIAN -->
    <div id="examPage" class="container hidden">
        <div class="header">
            <div>
                <h3 style="margin:0;">IPA: Sistem Koordinasi</h3>
                <small id="identitasSiswa"></small>
            </div>
            <div class="timer" id="timerDisplay">45:00</div>
        </div>

        <div class="exam-layout">
            <div class="main-content">
                <div id="badgeDiff" class="badge-diff"></div>
                <div id="questionText" class="question-text"></div>
                <div id="optionsContainer"></div>
                
                <div class="action-buttons">
                    <button id="btnPrev" class="btn-primary" onclick="changeQuestion(-1)">&#8592; Sebelumnya</button>
                    <button id="btnSkip" class="btn-warning" onclick="skipQuestion()">Lewati &#8635;</button>
                    <button id="btnNext" class="btn-primary" onclick="changeQuestion(1)">Selanjutnya &#8594;</button>
                </div>
            </div>
            
            <div class="sidebar">
                <h4 style="margin-top:0; text-align: center;">Navigasi Soal</h4>
                <div class="panel-grid" id="panelGrid"></div>
                <button class="btn-danger" style="padding: 15px; font-size: 1.1em;" onclick="konfirmasiSelesai()">SELESAI & KUMPULKAN</button>
            </div>
        </div>
    </div>

    <!-- HALAMAN HASIL & PEMBAHASAN -->
    <div id="resultPage" class="container hidden">
        <h2 style="text-align: center;">Hasil Ujian</h2>
        <div style="text-align: center; font-size: 1.2em; margin-bottom: 20px;">
            Nama: <span id="resNama"></span><br>
            Nilai Akhir: <strong id="resSkor" style="font-size: 2em; color: var(--primary);"></strong>
        </div>
        <hr>
        <h3>Pembahasan:</h3>
        <div id="discussionContainer"></div>
    </div>

    <script>
        // --- DATABASE SOAL 100% SARAF DAN INDRA ---
        const bankSoal = [
            // SISTEM SARAF
            { id: 1, q: "Unit terkecil penyusun sistem saraf manusia disebut...", opt: ["A. Nefron", "B. Neuron", "C. Alveolus", "D. Dendrit"], ans: 1, type: "LOTS", bahas: "Unit fungsional terkecil penyusun sistem saraf adalah sel saraf atau neuron." },
            { id: 2, q: "Bagian dari sel saraf yang berfungsi menerima impuls dari sel saraf lain dan meneruskannya ke badan sel adalah...", opt: ["A. Akson", "B. Nodus Ranvier", "C. Dendrit", "D. Sel Schwann"], ans: 2, type: "LOTS", bahas: "Dendrit adalah tonjolan sitoplasma pada badan sel yang berfungsi menerima impuls dan meneruskannya ke badan sel." },
            { id: 3, q: "Andi menginjak paku payung dan secara refleks menarik kakinya. Urutan jalannya impuls pada gerak refleks tersebut adalah...", opt: ["A. Reseptor - saraf sensorik - otak - saraf motorik - efektor", "B. Reseptor - saraf motorik - sumsum tulang belakang - saraf sensorik - efektor", "C. Reseptor - saraf sensorik - sumsum tulang belakang - saraf motorik - efektor", "D. Efektor - saraf sensorik - sumsum tulang belakang - saraf motorik - reseptor"], ans: 2, type: "MOTS", bahas: "Jalan impuls gerak refleks tidak melewati otak sebagai pusat pengolah utama, melainkan melalui jalan pintas yaitu sumsum tulang belakang." },
            { id: 4, q: "Sistem saraf pusat manusia terdiri atas...", opt: ["A. Otak dan serabut saraf", "B. Otak dan sumsum tulang belakang", "C. Sumsum tulang belakang dan saraf tepi", "D. Saraf simpatis dan parasimpatis"], ans: 1, type: "LOTS", bahas: "Saraf pusat merupakan pusat koordinasi yang terdiri dari otak dan sumsum tulang belakang (medula spinalis)." },
            { id: 5, q: "Seseorang yang mengalami benturan keras di kepala bagian belakang mengalami kesulitan menjaga keseimbangan tubuh saat berjalan. Bagian otak yang kemungkinan besar mengalami gangguan adalah...", opt: ["A. Serebrum (Otak besar)", "B. Serebelum (Otak kecil)", "C. Medula oblongata (Sumsum lanjutan)", "D. Hipotalamus"], ans: 1, type: "MOTS", bahas: "Otak kecil (Serebelum) yang terletak di bawah otak besar bagian belakang berfungsi sebagai pusat keseimbangan dan koordinasi gerak otot." },
            { id: 6, q: "Celah pertemuan antara ujung akson suatu neuron dengan dendrit neuron lainnya disebut...", opt: ["A. Sinapsis", "B. Nodus Ranvier", "C. Myelin", "D. Ganglion"], ans: 0, type: "LOTS", bahas: "Sinapsis adalah celah yang menghubungkan antar neuron. Di sini impuls diteruskan dengan bantuan zat neurotransmiter." },
            { id: 7, q: "Perhatikan fungsi saraf otonom berikut! 1) Mempercepat denyut jantung. 2) Memperbesar pupil mata. 3) Menghambat pencernaan. Saraf yang bekerja memberikan efek tersebut adalah...", opt: ["A. Saraf Somatik", "B. Saraf Kranial", "C. Saraf Parasimpatis", "D. Saraf Simpatis"], ans: 3, type: "MOTS", bahas: "Saraf simpatis umumnya bekerja untuk memacu kerja organ dalam kondisi siaga (fight or flight), seperti mempercepat detak jantung dan melebarkan pupil." },
            { id: 8, q: "Selaput pembungkus otak dan sumsum tulang belakang yang berfungsi melindunginya dari benturan disebut...", opt: ["A. Pleura", "B. Perikardium", "C. Meninges", "D. Periosteum"], ans: 2, type: "LOTS", bahas: "Meninges adalah selaput pelindung sistem saraf pusat (otak dan sumsum tulang belakang). Terdiri dari piameter, arakhnoid, dan durameter." },
            { id: 9, q: "Bagian sel saraf yang berfungsi membawa impuls menjauhi badan sel menuju neuron lain atau efektor adalah...", opt: ["A. Akson (Neurit)", "B. Dendrit", "C. Nodus Ranvier", "D. Badan Sel"], ans: 0, type: "LOTS", bahas: "Akson atau neurit adalah juluran panjang yang berfungsi menghantarkan impuls keluar atau menjauhi badan sel saraf menuju sel saraf lainnya." },
            { id: 10, q: "Perbedaan utama antara mekanisme gerak sadar dan gerak refleks terletak pada...", opt: ["A. Jenis reseptor yang menerima rangsangan pertama kali", "B. Pusat pengolahan impuls sarafnya", "C. Kecepatan hantaran impuls saraf motoriknya", "D. Jenis efektor otot yang memberikan tanggapan"], ans: 1, type: "MOTS", bahas: "Pusat pengolah gerak sadar berada di otak (serebrum), sedangkan gerak refleks diproses di sumsum tulang belakang secara otomatis tanpa disadari." },
            { id: 11, q: "Fungsi utama dari selubung mielin yang melapisi akson pada sel saraf adalah...", opt: ["A. Menerima rangsangan dari lingkungan luar", "B. Memberi nutrisi dan mempercepat hantaran impuls", "C. Mengolah informasi di dalam otak", "D. Menghasilkan zat neurotransmiter"], ans: 1, type: "MOTS", bahas: "Selubung mielin berfungsi sebagai isolator untuk melindungi akson, memberikan nutrisi bagi sel saraf, dan mempercepat jalannya impuls." },
            { id: 12, q: "Pusat penglihatan pada otak besar (serebrum) manusia terletak di bagian lobus...", opt: ["A. Frontal (Depan)", "B. Parietal (Ubun-ubun)", "C. Temporal (Samping)", "D. Oksipital (Belakang)"], ans: 3, type: "LOTS", bahas: "Lobus oksipital yang terletak di bagian belakang otak besar merupakan pusat pemrosesan informasi visual (penglihatan)." },
            { id: 13, q: "Sistem saraf tepi kranial (saraf otak) pada manusia berjumlah...", opt: ["A. 12 pasang", "B. 31 pasang", "C. 33 pasang", "D. 10 pasang"], ans: 0, type: "LOTS", bahas: "Saraf kranial yang keluar langsung dari otak berjumlah 12 pasang, sedangkan saraf spinal yang keluar dari tulang belakang berjumlah 31 pasang." },
            { id: 14, q: "Sistem saraf otonom terdiri dari saraf simpatis dan parasimpatis. Sifat kerja kedua saraf tersebut pada organ tubuh umumnya adalah...", opt: ["A. Sinergis (saling mendukung satu sama lain)", "B. Antagonis (berlawanan secara fungsi)", "C. Bergantian sesuai dengan usia manusia", "D. Tidak saling mempengaruhi satu sama lain"], ans: 1, type: "MOTS", bahas: "Kerja saraf simpatis dan parasimpatis selalu berlawanan (antagonis). Contoh: Simpatis mempercepat detak jantung, sedangkan parasimpatis memperlambatnya." },
            { id: 15, q: "Zat kimia yang berfungsi menghantarkan impuls saraf melintasi celah sinapsis menuju neuron berikutnya disebut...", opt: ["A. Hormon adrenalin", "B. Enzim ptialin", "C. Neurotransmiter", "D. Asam amino"], ans: 2, type: "LOTS", bahas: "Neurotransmiter (seperti asetilkolin dan dopamin) adalah zat kimia pembawa pesan yang dilepaskan di celah sinapsis." },

            // SISTEM INDRA
            { id: 16, q: "Bagian mata yang berfungsi mengatur jumlah cahaya yang masuk ke dalam mata dengan cara menyempitkan atau melebarkan pupil adalah...", opt: ["A. Kornea", "B. Retina", "C. Lensa", "D. Iris"], ans: 3, type: "LOTS", bahas: "Iris (selaput pelangi) adalah otot berwarna pada mata yang mengatur ukuran pupil sesuai intensitas cahaya." },
            { id: 17, q: "Pada penderita miopi (rabun jauh), bayangan benda jatuh di depan retina. Untuk membantu penderita miopi agar dapat melihat normal, dibutuhkan kacamata berlensa...", opt: ["A. Cembung (Positif)", "B. Cekung (Negatif)", "C. Silindris", "D. Ganda (Bifokal)"], ans: 1, type: "MOTS", bahas: "Lensa cekung (divergen) akan memencarkan cahaya sebelum masuk ke mata, sehingga bayangan yang awalnya jatuh di depan retina dapat mundur pas ke retina." },
            { id: 18, q: "Sel fotoreseptor pada retina yang peka terhadap cahaya redup dan tidak dapat membedakan warna disebut...", opt: ["A. Sel kerucut (Cone)", "B. Sel batang (Rod)", "C. Bintik kuning", "D. Saraf optik"], ans: 1, type: "LOTS", bahas: "Sel batang berfungsi dalam penglihatan pada kondisi cahaya redup/gelap, sedangkan sel kerucut untuk kondisi terang dan pengenalan warna." },
            { id: 19, q: "Ketika kita berpindah dari tempat terang terik ke dalam ruangan yang redup, awalnya penglihatan menjadi gelap sesaat. Secara fisiologis, hal ini terjadi karena...", opt: ["A. Otot siliaris sedang memipihkan lensa mata", "B. Iris membutuhkan waktu untuk melebarkan pupil", "C. Sel kerucut tiba-tiba mati sementara", "D. Retina kekurangan suplai darah sesaat"], ans: 1, type: "MOTS", bahas: "Di tempat terang pupil mengecil. Saat tiba di tempat redup, iris butuh beberapa detik untuk relaksasi dan melebarkan pupil agar lebih banyak cahaya masuk." },
            { id: 20, q: "Tulang-tulang pendengaran yang berada di telinga bagian tengah secara berurutan dari luar ke dalam adalah...", opt: ["A. Martil - Landasan - Sanggurdi", "B. Sanggurdi - Landasan - Martil", "C. Landasan - Martil - Sanggurdi", "D. Martil - Sanggurdi - Landasan"], ans: 0, type: "LOTS", bahas: "Urutan tulang pendengaran (Osikula) dari membran timpani ke dalam adalah Malleus (Martil), Inkus (Landasan), Stapes (Sanggurdi)." },
            { id: 21, q: "Saluran Eustachius merupakan saluran yang menghubungkan...", opt: ["A. Telinga luar dengan telinga tengah", "B. Telinga tengah dengan rongga mulut/faring", "C. Telinga dalam dengan otak", "D. Koklea dengan saluran gelang"], ans: 1, type: "LOTS", bahas: "Saluran Eustachius menghubungkan rongga telinga tengah dengan faring (kerongkongan) untuk menyeimbangkan tekanan udara." },
            { id: 22, q: "Saat pesawat lepas landas, telinga kadang terasa berdengung dan sakit. Tindakan menelan ludah atau menguap dapat menghilangkan keluhan tersebut karena...", opt: ["A. Membuka saluran Eustachius sehingga tekanan udara di telinga tengah dan luar seimbang", "B. Menggerakkan tulang pendengaran agar lebih fleksibel", "C. Menarik gendang telinga agar lebih kencang", "D. Mencegah cairan masuk ke dalam koklea"], ans: 0, type: "MOTS", bahas: "Gerakan menelan membuka katup saluran Eustachius, memungkinkan udara masuk atau keluar dari telinga tengah agar tekanan sama dengan lingkungan luar." },
            { id: 23, q: "Reseptor pendengaran (Organ Korti) yang berfungsi mengubah getaran mekanik menjadi impuls saraf terletak di bagian...", opt: ["A. Membran timpani", "B. Saluran setengah lingkaran", "C. Rumah siput (Koklea)", "D. Tingkap jorong"], ans: 2, type: "LOTS", bahas: "Di dalam koklea (rumah siput) terdapat organ Korti yang berisi sel-sel rambut sebagai reseptor suara sejati." },
            { id: 24, q: "Reseptor pembau pada rongga hidung berupa ujung-ujung saraf olfaktori. Agar zat bau dapat merangsang saraf tersebut, syarat utamanya adalah...", opt: ["A. Zat bau harus berupa partikel gas dan padat", "B. Zat tersebut memiliki suhu yang tinggi", "C. Zat bau harus dapat larut dalam lendir hidung", "D. Zat bau masuk melalui rongga mulut"], ans: 2, type: "MOTS", bahas: "Partikel gas zat kimia (kemoreseptor) harus larut terlebih dahulu dalam selaput lendir (mukus) di hidung agar dapat dideteksi oleh ujung saraf olfaktori." },
            { id: 25, q: "Bintil-bintil kecil pada permukaan lidah yang di dalamnya terdapat puting pengecap disebut...", opt: ["A. Papila", "B. Tonsil", "C. Epiglotis", "D. Mukosa"], ans: 0, type: "LOTS", bahas: "Papila adalah tonjolan-tonjolan kecil di permukaan lidah tempat berkumpulnya tunas pengecap." },
            { id: 26, q: "Saat seseorang sedang pilek parah, makanan seringkali terasa hambar. Hubungan fisiologis yang tepat menjelaskan hal ini adalah...", opt: ["A. Reseptor pengecap lidah diserang oleh virus influenza", "B. Cita rasa makanan merupakan kombinasi antara rangsangan pengecap di lidah dan pembau di hidung", "C. Lendir mematikan fungsi enzim amilase di mulut", "D. Hidung tersumbat membuat otot mengunyah melemah"], ans: 1, type: "MOTS", bahas: "Rasa makanan yang kita persepsikan (flavour) sebenarnya adalah gabungan stimulasi dari papila lidah dan reseptor olfaktori di hidung yang sedang tersumbat saat pilek." },
            { id: 27, q: "Walaupun seluruh permukaan lidah mampu mengecap rasa, area yang memiliki kepekaan paling tinggi terhadap rasa pahit terletak di bagian...", opt: ["A. Ujung lidah", "B. Samping depan lidah", "C. Samping belakang lidah", "D. Pangkal lidah (belakang)"], ans: 3, type: "LOTS", bahas: "Pangkal lidah (bagian paling belakang dekat tenggorokan) memiliki kepekaan tertinggi terhadap zat yang rasanya pahit." },
            { id: 28, q: "Reseptor pada kulit yang peka terhadap rangsangan tekanan kuat (misalnya saat kita memijat bahu secara keras) adalah...", opt: ["A. Korpuskula Pacini", "B. Korpuskula Meissner", "C. Korpuskula Ruffini", "D. Korpuskula Krause"], ans: 0, type: "LOTS", bahas: "Korpuskula Pacini berada di lapisan kulit dalam dan peka terhadap rangsangan tekanan kuat. Meissner untuk sentuhan, Ruffini untuk panas, Krause untuk dingin." },
            { id: 29, q: "Bintik buta (blind spot) pada mata manusia tidak dapat mendeteksi cahaya karena pada bagian tersebut...", opt: ["A. Tertutup oleh selaput pelindung sklera", "B. Tidak memiliki sel-sel fotoreseptor (batang dan kerucut)", "C. Terhalang oleh pembuluh darah vena besar", "D. Merupakan tempat melekatnya otot penggerak bola mata"], ans: 1, type: "MOTS", bahas: "Bintik buta adalah area keluarnya saraf optik dari retina. Di titik tersebut sama sekali tidak ada sel batang maupun kerucut, sehingga bayangan yang jatuh di sana tidak akan terlihat." },
            { id: 30, q: "Telinga tidak hanya berfungsi sebagai indra pendengar, tetapi juga sebagai alat keseimbangan tubuh. Bagian telinga yang menjalankan fungsi keseimbangan ini adalah...", opt: ["A. Tiga saluran setengah lingkaran (Kanalis semisirkularis)", "B. Membran timpani bagian dalam", "C. Susunan tulang sanggurdi dan landasan", "D. Rumah siput (Koklea)"], ans: 0, type: "MOTS", bahas: "Kanalis semisirkularis yang terletak di telinga dalam berisi cairan endolimfa yang akan merangsang saraf saat posisi kepala berubah untuk mengatur keseimbangan tubuh." }
        ];

        // --- VARIABEL GLOBAL ---
        let namaSiswa = "";
        let emailSiswa = "";
        let totalTime = 45 * 60; // 45 Menit
        let timerInterval;
        let isExamActive = false;
        let cheatCount = 0;
        let currentIndex = 0;
        let answers = new Array(bankSoal.length).fill(null);

        // --- FUNGSI ACAK (RANDOMIZER) ---
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }

        function acakSoalDanOpsi() {
            shuffleArray(bankSoal);
            bankSoal.forEach(q => {
                let correctAnswerText = q.opt[q.ans]; 
                shuffleArray(q.opt); 
                q.ans = q.opt.indexOf(correctAnswerText); 
            });
        }

        // --- FUNGSI UTAMA ---
        function mulaiUjian() {
            namaSiswa = document.getElementById("nama").value.trim();
            emailSiswa = document.getElementById("email").value.trim();
            
            if (!namaSiswa || !emailSiswa) {
                alert("Harap isi Nama dan Email dengan lengkap!");
                return;
            }

            acakSoalDanOpsi();

            // Memaksa mode Fullscreen dengan try-catch agar aman untuk perangkat iOS
            try {
                let elem = document.documentElement;
                if (elem.requestFullscreen) { 
                    elem.requestFullscreen().catch(err => console.warn("Fullscreen diabaikan oleh browser", err)); 
                } else if (elem.webkitRequestFullscreen) { 
                    elem.webkitRequestFullscreen(); 
                } else if (elem.msRequestFullscreen) { 
                    elem.msRequestFullscreen(); 
                }
            } catch (e) {
                console.log("Perangkat ini tidak mendukung API Fullscreen (Biasa terjadi pada iOS/iPhone).");
            }

            document.getElementById("loginPage").classList.add("hidden");
            document.getElementById("examPage").classList.remove("hidden");
            document.getElementById("identitasSiswa").innerText = `${namaSiswa} | ${emailSiswa}`;
            
            isExamActive = true;
            buatPanelNavigasi();
            tampilkanSoal(0);
            
            timerInterval = setInterval(updateTimer, 1000);
        }

        // --- NAVIGASI SOAL ---
        function buatPanelNavigasi() {
            const panel = document.getElementById("panelGrid");
            panel.innerHTML = "";
            for (let i = 0; i < bankSoal.length; i++) {
                const btn = document.createElement("div");
                btn.className = "btn-nav";
                btn.innerText = i + 1;
                btn.id = "navBtn_" + i;
                btn.onclick = () => tampilkanSoal(i);
                panel.appendChild(btn);
            }
        }

        function tampilkanSoal(index) {
            document.querySelectorAll(".btn-nav").forEach(el => el.classList.remove("current"));
            document.getElementById("navBtn_" + index).classList.add("current");
            
            currentIndex = index;
            const qData = bankSoal[index];
            
            const badge = document.getElementById("badgeDiff");
            badge.innerText = qData.type;
            badge.className = `badge-diff ${qData.type === 'LOTS' ? 'badge-lots' : 'badge-mots'}`;
            
            document.getElementById("questionText").innerHTML = `<b>Soal No ${index + 1}.</b><br>${qData.q}`;
            
            const optsContainer = document.getElementById("optionsContainer");
            optsContainer.innerHTML = "";
            
            qData.opt.forEach((opsi, i) => {
                const lbl = document.createElement("label");
                lbl.className = "option-label";
                if (answers[index] === i) lbl.classList.add("selected");
                
                const inp = document.createElement("input");
                inp.type = "radio";
                inp.name = "radioOpsi";
                inp.value = i;
                if (answers[index] === i) inp.checked = true;
                inp.onchange = () => pilihJawaban(index, i, lbl);
                
                let teksBersih = opsi.replace(/^[A-D]\.\s*/, "");
                let abjadBaru = String.fromCharCode(65 + i); 
                
                lbl.appendChild(inp);
                lbl.appendChild(document.createTextNode(abjadBaru + ". " + teksBersih));
                optsContainer.appendChild(lbl);
            });

            document.getElementById("btnPrev").style.visibility = (index === 0) ? "hidden" : "visible";
            document.getElementById("btnNext").style.visibility = (index === bankSoal.length - 1) ? "hidden" : "visible";
        }

        function pilihJawaban(qIndex, optIndex, labelElement) {
            answers[qIndex] = optIndex;
            document.querySelectorAll(".option-label").forEach(el => el.classList.remove("selected"));
            labelElement.classList.add("selected");
            document.getElementById("navBtn_" + qIndex).classList.add("answered");
        }

        function changeQuestion(step) {
            let nextIndex = currentIndex + step;
            if (nextIndex >= 0 && nextIndex < bankSoal.length) tampilkanSoal(nextIndex);
        }

        function skipQuestion() {
            let found = false;
            for (let i = currentIndex + 1; i < bankSoal.length; i++) {
                if (answers[i] === null) {
                    tampilkanSoal(i);
                    found = true; break;
                }
            }
            if(!found) {
                for(let i = 0; i < bankSoal.length; i++){
                    if (answers[i] === null) {
                        tampilkanSoal(i);
                        found = true; break;
                    }
                }
            }
            if(!found) alert("Semua soal sudah dijawab! Silakan tekan tombol Selesai di bawah panel nomor.");
        }

        // --- TIMER ---
        function updateTimer() {
            if (totalTime <= 0) {
                kalkulasiDanKirim("Selesai Waktu Habis");
                return;
            }
            totalTime--;
            let m = Math.floor(totalTime / 60);
            let s = totalTime % 60;
            document.getElementById("timerDisplay").innerText = (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
        }

        // --- ANTI CHEAT (Diperbarui untuk dukungan iOS) ---
        function deteksiKecurangan() {
            if (isExamActive) {
                cheatCount++;
                alert(`PELANGGARAN! Anda terdeteksi keluar dari layar ujian. Peringatan ke: ${cheatCount}/2`);
                if (cheatCount >= 2) {
                    alert("Anda Dikeluarkan dari Ujian (Diskualifikasi).");
                    kalkulasiDanKirim("Diskualifikasi");
                }
            }
        }

        document.addEventListener("visibilitychange", () => {
            if (document.hidden) deteksiKecurangan();
        });
        
        // Tambahan untuk dukungan Safari/iOS yang terkadang tidak membaca visibilitychange dengan baik
        window.addEventListener("pagehide", () => {
            deteksiKecurangan();
        });

        // Cegah back button
        history.pushState(null, null, location.href);
        window.addEventListener('popstate', function () {
            history.pushState(null, null, location.href);
        });

        // --- PENYELESAIAN ---
        function konfirmasiSelesai() {
            const blmDijawab = answers.filter(a => a === null).length;
            if (blmDijawab > 0) {
                if(!confirm(`Ada ${blmDijawab} soal belum dijawab! Yakin ingin menyelesaikan ujian?`)) return;
            } else {
                if(!confirm("Yakin ingin menyelesaikan ujian dan mengirim jawaban?")) return;
            }
            kalkulasiDanKirim("Selesai Normal");
        }

        function kalkulasiDanKirim(statusUjian) {
            isExamActive = false;
            clearInterval(timerInterval);
            
            let benar = 0;
            
            let stringJawabanSiswa = answers.map((ans, idx) => {
                let qData = bankSoal[idx];
                let isBenar = (ans === qData.ans);
                if (isBenar) benar++;
                
                let statusJwb = isBenar ? "Benar" : "Salah";
                let teksPilihan = ans !== null ? qData.opt[ans].replace(/^[A-D]\.\s*/, "") : "Kosong";
                
                return `ID${qData.id}:${teksPilihan}(${statusJwb})`;
            }).join(" | ");
            
            let nilai = Math.round((benar / bankSoal.length) * 100);

            let payload = {
                nama: namaSiswa,
                email: emailSiswa,
                skor: statusUjian === "Diskualifikasi" ? 0 : nilai,
                status: statusUjian,
                detailJawaban: stringJawabanSiswa
            };

            // =========================================================================
            // GANTI URL DI BAWAH INI DENGAN URL WEB APP GOOGLE SCRIPT ANDA!
            let gasURL = "https://www.appsheet.com/start/72b144b3-9524-4965-9649-7f9aea672ee2?platform=desktop#appName=PenilaianSistemSaraf-377285758&vss=H4sIAAAAAAAAA7WQuw7CMAxFfyXy3C_IipCoeCxFLITBNI6ISJMqSYEqyr-T8hArA4w-ls69doKLpmsTsT0D36fPtKQROCQB27EnAVzAzNnonRFQCdhg94QLDNqwFUZ9QssaHSJ1rEGPiskCais9CsiQD9XbHSkAT79T8_-1rkBLslErTX7KmazF_3KW9WQs4Bsf5Aq6IeLR0OMJxZdzYcq1QyC5Kyf8uHqo7fzWo5VrJ0ucQhMo3wH1YYoO8QEAAA==&view=Hasil%20Latihan%20Sistem%20Saraf%20dan%20Indra"; 
            // =========================================================================

            document.body.style.cursor = 'wait';
            tampilkanHasilDanPembahasan(nilai);

            fetch(gasURL, {
                method: "POST",
                mode: "no-cors",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(payload)
            }).then(() => {
                document.body.style.cursor = 'default';
            }).catch(e => {
                document.body.style.cursor = 'default';
            });
        }

        function tampilkanHasilDanPembahasan(skorAkhir) {
            // Keluar dari fullscreen dengan try-catch agar tidak menyebabkan error di iOS
            try {
                if (document.fullscreenElement && document.exitFullscreen) { 
                    document.exitFullscreen().catch(err => console.warn(err)); 
                } else if (document.webkitFullscreenElement && document.webkitExitFullscreen) { 
                    document.webkitExitFullscreen(); 
                }
            } catch (e) {
                console.log("Exit fullscreen tidak didukung atau sedang tidak dalam fullscreen.");
            }

            document.getElementById("examPage").classList.add("hidden");
            document.getElementById("resultPage").classList.remove("hidden");
            
            document.getElementById("resNama").innerText = namaSiswa;
            document.getElementById("resSkor").innerText = skorAkhir;

            const box = document.getElementById("discussionContainer");
            box.innerHTML = "";

            bankSoal.forEach((q, i) => {
                const jwbSiswa = answers[i];
                const isBenar = jwbSiswa === q.ans;
                
                let jwbTeks = jwbSiswa !== null ? q.opt[jwbSiswa].replace(/^[A-D]\.\s*/, "") : "<i>Tidak Dijawab</i>";
                let kunciTeks = q.opt[q.ans].replace(/^[A-D]\.\s*/, "");
                
                const item = document.createElement("div");
                item.className = `result-item ${isBenar ? 'correct-ans' : 'wrong-ans'}`;
                
                item.innerHTML = `
                    <b>Soal No ${i + 1} (${q.type}) - <small style="color:#666;">ID Soal Asli: ${q.id}</small></b>
                    <p>${q.q}</p>
                    <p>Jawaban Anda: <b>${jwbTeks}</b> ${isBenar ? '✅' : '❌'}</p>
                    <p>Kunci Jawaban: <b>${kunciTeks}</b></p>
                    <div class="discussion"><b>Pembahasan:</b> ${q.bahas}</div>
                `;
                box.appendChild(item);
            });
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Panel Admin: Ujian IPA Kelas 9</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #18bc9c;
            --danger: #e74c3c;
            --light: #ecf0f1;
        }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f8f9fa; margin: 0; padding: 20px; }
        .container { max-width: 1000px; margin: auto; background: white; padding: 30px; border-radius: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); }
        h2 { color: var(--primary); border-bottom: 2px solid var(--light); padding-bottom: 10px; margin-top: 0; }
        .hidden { display: none !important; }
        
        /* Form Login */
        .login-box { max-width: 400px; margin: 50px auto; text-align: center; }
        input[type="password"] { width: 100%; padding: 12px; margin: 15px 0; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; }
        
        button { padding: 10px 20px; border: none; border-radius: 5px; cursor: pointer; font-weight: bold; background: var(--secondary); color: white; transition: 0.2s; }
        button:hover { opacity: 0.9; }
        
        /* Tabel Data */
        .controls { display: flex; justify-content: space-between; margin-bottom: 20px; align-items: center; }
        .stat-box { background: var(--light); padding: 15px; border-radius: 5px; font-weight: bold; color: var(--primary); }
        
        table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 0.9em; }
        th, td { padding: 12px; text-align: left; border-bottom: 1px solid #ddd; }
        th { background-color: var(--primary); color: white; }
        tr:hover { background-color: #f1f1f1; }
        
        .status-diskualifikasi { color: var(--danger); font-weight: bold; }
        .status-selesai { color: var(--secondary); font-weight: bold; }
        .loading { text-align: center; padding: 20px; font-style: italic; color: #666; }
    </style>
</head>
<body>

    <!-- Panel Login Admin -->
    <div id="loginPanel" class="container login-box">
        <h2>Akses Administrator</h2>
        <p>Silakan masukkan PIN untuk melihat rekapitulasi nilai IPA.</p>
        <input type="password" id="adminPin" placeholder="Masukkan PIN" onkeypress="if(event.key === 'Enter') cekPin()">
        <button style="width: 100%;" onclick="cekPin()">Masuk</button>
    </div>

    <!-- Dasbor Utama -->
    <div id="dashboardPanel" class="container hidden">
        <h2>Rekapitulasi Hasil Ujian</h2>
        
        <div class="controls">
            <button onclick="muatData()">🔄 Perbarui Data</button>
            <div class="stat-box" id="totalSiswa">Total Peserta: 0</div>
        </div>

        <div style="overflow-x: auto;">
            <table id="tabelNilai">
                <thead>
                    <tr>
                        <th>Waktu Submit</th>
                        <th>Nama Siswa</th>
                        <th>Email</th>
                        <th>Skor</th>
                        <th>Status</th>
                        <th>Aksi</th>
                    </tr>
                </thead>
                <tbody id="badanTabel">
                    <tr><td colspan="6" class="loading">Menunggu otorisasi...</td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- Modal Detail Jawaban (Opsional jika ingin melihat butir soal) -->
    <div id="detailModal" class="container hidden" style="margin-top: 20px; background: #fff3cd; border-left: 4px solid #ffc107;">
        <div style="display: flex; justify-content: space-between;">
            <h3 style="margin-top: 0;">Detail Jawaban: <span id="namaDetail"></span></h3>
            <button onclick="document.getElementById('detailModal').classList.add('hidden')" style="background: var(--danger); padding: 5px 10px;">Tutup</button>
        </div>
        <p id="teksDetail" style="word-break: break-word; font-family: monospace; font-size: 0.9em;"></p>
    </div>

    <script>
        // =========================================================
        // 1. GANTI URL INI DENGAN URL WEB APP GOOGLE SCRIPT YANG BARU
        const gasURL = "URL_GOOGLE_APPS_SCRIPT_ANDA_DISINI";
        
        // 2. ATUR PIN ADMIN DI SINI
        const PIN_ADMIN = "ipa123";
        // =========================================================

        let dataGlobal = [];

        function cekPin() {
            const input = document.getElementById("adminPin").value;
            if (input === PIN_ADMIN) {
                document.getElementById("loginPanel").classList.add("hidden");
                document.getElementById("dashboardPanel").classList.remove("hidden");
                muatData();
            } else {
                alert("PIN Salah!");
            }
        }

        function muatData() {
            const tbody = document.getElementById("badanTabel");
            tbody.innerHTML = '<tr><td colspan="6" class="loading">Mengambil data dari server...</td></tr>';
            
            fetch(gasURL)
                .then(response => response.json())
                .then(data => {
                    dataGlobal = data.reverse(); // Balik urutan agar yang terbaru di atas
                    tampilkanTabel();
                })
                .catch(error => {
                    tbody.innerHTML = '<tr><td colspan="6" class="loading" style="color:red;">Gagal memuat data. Periksa koneksi atau URL Script.</td></tr>';
                    console.error("Error fetching data:", error);
                });
        }

        function tampilkanTabel() {
            const tbody = document.getElementById("badanTabel");
            document.getElementById("totalSiswa").innerText = "Total Peserta: " + dataGlobal.length;
            tbody.innerHTML = "";

            if (dataGlobal.length === 0) {
                tbody.innerHTML = '<tr><td colspan="6" class="loading">Belum ada data ujian yang masuk.</td></tr>';
                return;
            }

            dataGlobal.forEach((baris, index) => {
                const tr = document.createElement("tr");
                
                // Format Status
                let statusClass = baris.status.toLowerCase().includes("diskualifikasi") ? "status-diskualifikasi" : "status-selesai";

                tr.innerHTML = `
                    <td>${baris.waktu}</td>
                    <td><b>${baris.nama}</b></td>
                    <td>${baris.email}</td>
                    <td style="font-size: 1.2em; font-weight: bold;">${baris.skor}</td>
                    <td class="${statusClass}">${baris.status}</td>
                    <td><button style="padding: 5px 10px; font-size: 0.8em;" onclick="lihatDetail(${index})">Detail</button></td>
                `;
                tbody.appendChild(tr);
            });
        }

        function lihatDetail(index) {
            const data = dataGlobal[index];
            document.getElementById("namaDetail").innerText = data.nama;
            
            // Format ulang teks detail agar lebih rapi
            let detailRapih = data.detail.replace(/ \| /g, "<br>• ");
            document.getElementById("teksDetail").innerHTML = "• " + detailRapih;
            
            document.getElementById("detailModal").classList.remove("hidden");
            // Scroll ke bagian detail
            document.getElementById("detailModal").scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
