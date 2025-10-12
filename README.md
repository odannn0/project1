<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Kata Romantis untuk Enji</title>
  <style>
    :root{
      --bg1: #ffecd2;
      --bg2: #fcb69f;
      --card: rgba(255,255,255,0.9);
      --accent: #ff5577;
      --shadow: 0 10px 30px rgba(0,0,0,0.12);
      font-family: "Helvetica Neue", Arial, sans-serif;
    }
    html,body{
      height:100%;
      margin:0;
    }
    body{
      display:flex;
      align-items:center;
      justify-content:center;
      background: linear-gradient(135deg,var(--bg1),var(--bg2));
      padding:24px;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
    }

    .card{
      width:100%;
      max-width:820px;
      background:var(--card);
      border-radius:18px;
      box-shadow:var(--shadow);
      padding:32px;
      display:grid;
      grid-template-columns: 1fr 360px;
      gap:24px;
      align-items:center;
    }

    .left{
      padding:12px 8px;
    }

    h1{
      margin:0 0 8px 0;
      font-size:28px;
      color:#333;
      letter-spacing:0.2px;
    }
    p.lead{
      margin:0 0 18px 0;
      color:#555;
    }

    .quote-box{
      background: linear-gradient(180deg, rgba(255,255,255,0.95), rgba(255,249,250,0.95));
      border-radius:12px;
      padding:20px;
      min-height:160px;
      display:flex;
      align-items:center;
      justify-content:center;
      text-align:center;
      font-size:20px;
      color:#222;
      line-height:1.45;
      box-shadow: 0 6px 18px rgba(0,0,0,0.06);
    }

    .controls{
      margin-top:16px;
      display:flex;
      gap:12px;
      flex-wrap:wrap;
    }

    button{
      appearance:none;
      border:0;
      padding:10px 14px;
      border-radius:10px;
      font-weight:600;
      cursor:pointer;
      box-shadow: 0 6px 12px rgba(0,0,0,0.06);
    }

    .btn-primary{
      background:linear-gradient(90deg,var(--accent),#ff7a9a);
      color:white;
    }
    .btn-ghost{
      background:transparent;
      border:1px solid rgba(0,0,0,0.06);
      color:#444;
    }

    .right{
      display:flex;
      flex-direction:column;
      align-items:center;
      gap:18px;
      padding:8px;
    }

    .heart{
      width:170px;
      height:170px;
      display:flex;
      align-items:center;
      justify-content:center;
      position:relative;
      transform:translateY(-6px);
    }

    /* heart shape */
    .heart-shape{
      width:90px;
      height:90px;
      background:var(--accent);
      position:relative;
      transform: rotate(-45deg);
      border-radius:20px 20px 0 0;
      box-shadow: 0 8px 20px rgba(255,85,119,0.18);
      animation: beat 1s infinite ease-in-out;
    }
    .heart-shape::before,
    .heart-shape::after{
      content:"";
      width:90px;
      height:90px;
      background:var(--accent);
      position:absolute;
      border-radius:50%;
    }
    .heart-shape::before{ top:-45px; left:0; }
    .heart-shape::after{ left:45px; top:0; }

    @keyframes beat{
      0% { transform: rotate(-45deg) scale(1); }
      25%{ transform: rotate(-45deg) scale(1.05); }
      50%{ transform: rotate(-45deg) scale(1); }
      75%{ transform: rotate(-45deg) scale(1.05); }
      100%{ transform: rotate(-45deg) scale(1); }
    }

    .note{
      font-size:13px;
      color:#555;
      text-align:center;
    }

    footer{
      grid-column:1 / -1;
      margin-top:8px;
      text-align:center;
      font-size:13px;
      color:#666;
    }

    @media(max-width:880px){
      .card{ grid-template-columns: 1fr; padding:20px; }
      .right{ flex-direction:row; justify-content:space-between; }
      .heart{ transform: translateY(0); }
    }
  </style>
</head>
<body>
  <div class="card" role="main" aria-label="Kata romantis untuk enji">
    <div class="left">
      <h1>Untukmu, sayang 💌</h1>
      <p class="lead">Salin atau kirimkan ini ke pacarmu. Tekan <strong>Acak</strong> untuk lihat kata-kata lain.</p>

      <div class="quote-box" id="quoteBox">
        "Kamu bukan hanya milikku — kamu adalah rumah yang selalu kurindukan."
      </div>

      <div class="controls" aria-hidden="false">
        <button class="btn-primary" id="shuffleBtn">Acak Kata</button>
        <button class="btn-ghost" id="copyBtn">Salin ke Clipboard</button>
        <button class="btn-ghost" id="downloadBtn">Unduh (TXT)</button>
      </div>
    </div>

    <div class="right">
      <div class="heart" aria-hidden="true">
        <div class="heart-shape"></div>
      </div>

      <div class="note">
        Kamu bisa pakai kata-kata ini buat caption, pesan, atau cetak di kartu kecil.
      </div>
    </div>

    <footer>Made with ❤️ — kirim ke dia, dan lihat senyumnya.</footer>
  </div>

  <script>
    const quotes = [
      "Kamu bukan hanya milikku — kamu adalah rumah yang selalu kurindukan.",
      "Setiap hari bersamamu terasa seperti lagu favorit yang tak pernah bosan kudengar.",
      "Aku jatuh cinta pada caramu membuat hal-hal kecil terasa berarti.",
      "Di antara jutaan bintang, kamu tetap pilihan hatiku.",
      "Kalau cinta itu perjalanan, aku mau terus jalan bersamamu sampai tua.",
      "Kau tu orang yang bikin hari-hariku jadi terang. (Manado style: 'Kau yang bikin hariku jadi terang tomohon!')",
      "Pelukanmu adalah tempat paling aman yang pernah aku tahu.",
      "Darimu aku belajar arti sabar, percaya, dan setia. Terima kasih sudah ada.",
      "Setiap pesan darimu selalu bikin jantungku loncat—dalam arti yang baik.",
      "Aku pilih kamu, sekarang, nanti, dan selamanya."
    ];

    const quoteBox = document.getElementById('quoteBox');
    const shuffleBtn = document.getElementById('shuffleBtn');
    const copyBtn = document.getElementById('copyBtn');
    const downloadBtn = document.getElementById('downloadBtn');

    function pickRandom(){
      const i = Math.floor(Math.random() * quotes.length);
      return quotes[i];
    }

    shuffleBtn.addEventListener('click', () => {
      const q = pickRandom();
      quoteBox.textContent = q;
    });

    copyBtn.addEventListener('click', async () => {
      const text = quoteBox.textContent.trim();
      try{
        await navigator.clipboard.writeText(text);
        copyBtn.textContent = 'Tersalin!';
        setTimeout(()=> copyBtn.textContent = 'Salin ke Clipboard', 1500);
      }catch(e){
        // fallback
        const ta = document.createElement('textarea');
        ta.value = text;
        document.body.appendChild(ta);
        ta.select();
        try{ document.execCommand('copy'); copyBtn.textContent = 'Tersalin!'; }
        catch(e){ alert('Salin manual: ' + text); }
        document.body.removeChild(ta);
        setTimeout(()=> copyBtn.textContent = 'Salin ke Clipboard', 1500);
      }
    });

    downloadBtn.addEventListener('click', () => {
      const text = quoteBox.textContent.trim();
      const blob = new Blob([text], { type: 'text/plain' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'kata-romantis.txt';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
      downloadBtn.textContent = 'Diunduh!';
      setTimeout(()=> downloadBtn.textContent = 'Unduh (TXT)', 1500);
    });

    // Optional: tampilkan acak pada load
    document.addEventListener('DOMContentLoaded', () => {
      quoteBox.textContent = pickRandom();
    });
  </script>
</body>
</html>
