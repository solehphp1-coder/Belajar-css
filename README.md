# Belajar-css
Skdr bljr
<!-- Simpan sebagai index.html -->
<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Belajar CSS - Single File</title>

  <!-- CSS internal -->
  <style>
    :root{
      --bg:#f6f8fc;
      --card:#ffffff;
      --accent:#0b84ff;
      --text:#111827;
      --muted:#6b7280;
      --radius:12px;
    }

    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:linear-gradient(180deg, var(--bg), #e6eefc);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding:32px;
    }

    .wrap{
      max-width:920px;
      margin:0 auto;
    }

    header{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:24px;
    }

    .brand{
      display:flex;
      align-items:center;
      gap:12px;
    }
    .logo{
      width:52px;
      height:52px;
      background:linear-gradient(135deg,#0b84ff,#5eead4);
      border-radius:10px;
      display:flex;
      align-items:center;
      justify-content:center;
      color:white;
      font-weight:700;
      box-shadow:0 6px 18px rgba(11,132,255,0.18);
    }
    h1{font-size:20px;margin:0}
    p.lead{margin:0;color:var(--muted);font-size:13px}

    /* main grid */
    .grid{
      display:grid;
      grid-template-columns: 1fr 360px;
      gap:20px;
      align-items:start;
    }

    /* card */
    .card{
      background:var(--card);
      border-radius:var(--radius);
      padding:18px;
      box-shadow:0 8px 24px rgba(16,24,40,0.06);
    }

    .example{
      padding:28px;
      border-radius:10px;
      text-align:center;
      background:linear-gradient(180deg, rgba(11,132,255,0.06), rgba(94,234,212,0.03));
      margin-bottom:18px;
    }

    .example h2{margin:0 0 8px 0}
    .example p{margin:0;color:var(--muted)}

    button{
      background:var(--accent);
      color:white;
      border:0;
      padding:10px 14px;
      border-radius:10px;
      cursor:pointer;
      font-weight:600;
      transition:transform .12s ease, box-shadow .12s ease;
    }
    button:active{transform:translateY(1px)}
    .btn-ghost{
      background:transparent;
      color:var(--accent);
      border:1px solid rgba(11,132,255,0.12);
    }

    /* right column */
    .controls h3{margin-top:0}
    label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}
    input[type="color"], input[type="text"], select, textarea{
      width:100%;
      padding:8px 10px;
      border-radius:8px;
      border:1px solid #e6eefc;
      margin-bottom:12px;
      background:#fbfdff;
    }

    pre{
      background:#0b1220;
      color:#dbeafe;
      border-radius:10px;
      padding:12px;
      overflow:auto;
      font-size:13px;
      line-height:1.5;
    }

    footer{margin-top:18px;color:var(--muted);font-size:13px;text-align:center}
    @media (max-width:900px){
      .grid{grid-template-columns:1fr; padding-bottom:60px}
      header{flex-direction:column;align-items:flex-start;gap:10px}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo">CSS</div>
        <div>
          <h1>Belajar CSS (Single file)</h1>
          <p class="lead">Contoh HTML + CSS + JS jadi satu. Edit, simpan, upload ke GitHub.</p>
        </div>
      </div>

      <div style="display:flex;gap:8px;align-items:center">
        <button id="themeBtn" title="Ganti tema">Ganti Tema</button>
        <button id="downloadBtn" class="btn-ghost" title="Download HTML">Download</button>
      </div>
    </header>

    <main class="grid">
      <!-- LEFT: preview & contoh -->
      <section>
        <div class="card">
          <div class="example" id="preview">
            <h2>Contoh Judul</h2>
            <p>Ini contoh blok, gunakan tombol di kanan untuk mengubah warna dan teks.</p>
            <div style="margin-top:14px">
              <button onclick="alert('Halo!')">Alert</button>
              <button class="btn-ghost" onclick="document.getElementById('liveText').textContent='Teks diubah!'">Ubah Teks</button>
            </div>
          </div>

          <div style="margin-top:14px;">
            <label style="font-size:13px;color:var(--muted)">Teks yang bisa diedit (preview):</label>
            <input id="liveTextInput" type="text" placeholder="Tulis sesuatu..." oninput="updatePreviewText()" />
            <p style="color:var(--muted);font-size:13px;margin-top:8px"><strong>Preview live:</strong> <span id="liveText">Ini contoh blok</span></p>
          </div>

        </div>

        <div class="card" style="margin-top:18px">
          <h3>Penjelasan singkat</h3>
          <p style="color:var(--muted)">File ini sudah include style (di &lt;style&gt;) dan script (di &lt;script&gt;). Kamu bisa ubah warna, radius, dan lihat perubahan langsung pada area preview.</p>
        </div>
      </section>

      <!-- RIGHT: controls -->
      <aside class="controls">
        <div class="card">
          <h3>Kontrol CSS</h3>

          <label>Warna Accent</label>
          <input id="accentColor" type="color" value="#0b84ff" />

          <label>Background Gradient (awal)</label>
          <input id="bgColor1" type="color" value="#f6f8fc" />

          <label>Background Gradient (akhir)</label>
          <input id="bgColor2" type="color" value="#e6eefc" />

          <label>Radius (px)</label>
          <input id="radius" type="text" value="12px" />

          <button onclick="applyStyles()">Terapkan</button>

          <hr style="margin:16px 0;border:none;border-top:1px solid #f1f5f9">

          <h3>Sample CSS</h3>
          <pre id="cssSample">
:root{
  --accent: #0b84ff;
  --bg: #f6f8fc;
  --card: #ffffff;
  --radius: 12px;
}
          </pre>

          <hr style="margin:16px 0;border:none;border-top:1px solid #f1f5f9">

          <h3>Export / Simpan</h3>
          <p style="color:var(--muted);font-size:13px">Klik download untuk menyimpan file HTML ini ke HP/Laptop.</p>
        </div>
      </aside>
    </main>

    <footer>Created for <strong>Belajar-css</strong> • Copy & edit sesuka hati</footer>
  </div>

  <!-- JS internal -->
  <script>
    // fungsi update preview text
    function updatePreviewText(){
      var v = document.getElementById('liveTextInput').value || 'Ini contoh blok';
      document.getElementById('liveText').textContent = v;
      document.querySelector('#preview h2').textContent = v.length ? v : 'Contoh Judul';
    }

    // terapkan style dari kontrol ke :root
    function applyStyles(){
      var a = document.getElementById('accentColor').value;
      var b1 = document.getElementById('bgColor1').value;
      var b2 = document.getElementById('bgColor2').value;
      var r = document.getElementById('radius').value || '12px';

      document.documentElement.style.setProperty('--accent', a);
      // ubah box gradient
      document.body.style.background = 'linear-gradient(180deg, '+b1+', '+b2+')';
      document.documentElement.style.setProperty('--radius', r);

      // update contoh sample teks CSS
      document.getElementById('cssSample').textContent =
`:root{
  --accent: ${a};
  --bg: ${b1};
  --card: #ffffff;
  --radius: ${r};
}`;
    }

    // ganti tema (gelap / terang)
    var dark=false;
    document.getElementById('themeBtn').addEventListener('click', function(){
      if(!dark){
        document.documentElement.style.setProperty('--bg','#0b1220');
        document.documentElement.style.setProperty('--card','#071027');
        document.documentElement.style.setProperty('--text','#e6eefc');
        document.documentElement.style.setProperty('--muted','#94a3b8');
        dark=true;
      } else {
        document.documentElement.style.setProperty('--bg','#f6f8fc');
        document.documentElement.style.setProperty('--card','#ffffff');
        document.documentElement.style.setProperty('--text','#111827');
        document.documentElement.style.setProperty('--muted','#6b7280');
        dark=false;
      }
    });

    // download HTML current page as file
    document.getElementById('downloadBtn').addEventListener('click', function(){
      var doc = '<!doctype html>\\n' + document.documentElement.outerHTML;
      var blob = new Blob([doc], {type:'text/html'});
      var url = URL.createObjectURL(blob);
      var a = document.createElement('a');
      a.href = url;
      a.download = 'index.html';
      document.body.appendChild(a);
      a.click();
      a.remove();
      URL.revokeObjectURL(url);
    });

    // inisialisasi sample css
    applyStyles();
  </script>
</body>
</html>