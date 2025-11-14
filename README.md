<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>2° Aniversario — Nuestra Historia</title>

  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700&family=Dancing+Script:wght@400;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg1:#fff1f5; --bg2:#ffe8ef;
      --card:rgba(255,255,255,0.95);
      --accent:#ff8fa3;
      --text:#5e4a52;
      --shadow:0 8px 28px rgba(0,0,0,0.08);
      --radius:20px;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    body{
      background:linear-gradient(135deg,var(--bg1),var(--bg2));
      font-family:Montserrat,Arial,sans-serif;
      color:var(--text);
      padding-bottom:60px;
    }
    .wrap{max-width:1100px;margin:auto;padding:30px}

    header{text-align:center;margin-bottom:30px}
    h1{font-family:'Dancing Script',cursive;font-size:48px;color:#3b2b2f}
    .sub{margin-top:8px;font-size:15px;opacity:0.8}

    .section{background:var(--card);padding:22px;border-radius:var(--radius);box-shadow:var(--shadow);margin-top:22px}
    .section h2{font-family:'Dancing Script',cursive;font-size:32px;margin-bottom:10px;color:#3b2b2f}

    /* historia */
    .story{font-size:15px;line-height:1.55;white-space:pre-line}

    /* galería */
    .gallery{margin-top:14px;display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:10px}
    .gallery img{width:100%;border-radius:14px;object-fit:cover;height:140px;cursor:pointer;box-shadow:0 6px 18px rgba(0,0,0,0.08)}

    /* canción */
    .music{display:flex;align-items:center;justify-content:space-between}
    .music button{background:var(--accent);border:0;padding:10px 16px;border-radius:10px;color:white;font-weight:700;cursor:pointer;box-shadow:var(--shadow)}

    /* animaciones suaves */
    .fade{opacity:0;transform:translateY(10px);transition:all .6s ease}
    .fade.show{opacity:1;transform:translateY(0)}

    /* lightbox */
    #lightbox{position:fixed;inset:0;background:rgba(0,0,0,0.75);display:none;align-items:center;justify-content:center;z-index:99}
    #lightbox img{max-width:90%;max-height:85%;border-radius:14px;box-shadow:0 0 20px rgba(255,255,255,0.3)}

    /* mensajes */
    #mensajeMostrado{transition:opacity .3s ease;opacity:0.6}

    @keyframes flotar{
      0%{transform:translateY(0);opacity:0.7}
      100%{transform:translateY(-150px);opacity:0}
    }

    /* responsive tweaks */
    @media (max-width:600px){ h1{font-size:36px} .gallery img{height:120px} }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <h1>Nuestro 2° Aniversario</h1>
      <div class="sub">Un pequeño rincón para recordar cada paso de nuestro viaje juntos ✨</div>
    </header>

    <div class="section">
      <h2>Nuestra historia</h2>
      <div class="story">
Conocí a la mujer más hermosa en 2022, aunque realmente nuestra historia comenzó en 2023.
Pasamos alrededor de tres meses hablándonos, conociéndonos poco a poco, conectando de una forma que jamás había sentido.

El 18 de noviembre del 2023 reuní el valor para pedirle que fuera mi novia. Y dijo que sí.

Desde ese día todo cambió. Ella es perfecta para mí: mi primer y último amor.
Morena, delgada, hermosa, con unos ojos negros que brillan de una forma que hace que cada canción de amor tenga sentido.

Es mi ser de luz, mi vida entera.

Cada día a su lado ha sido un regalo: desde los mensajes tímidos del principio, hasta las risas que ahora llenan todos nuestros recuerdos. Dos años después, sigo mirándola con la misma admiración de la primera vez… y con un amor aún más grande.

Gracias por dos años que han sido los mejores capítulos de mi vida, y por todos los que aún nos quedan por escribir juntos.
      </div>
    </div>

    <!-- lightbox para fotos -->
    <div id="lightbox"><img src="" alt="foto"></div>

    <div class="section">
      <h2>Momentos importantes</h2>
      <p style="font-size:14px;opacity:0.85">Añade aquí tus fotos reemplazando las rutas dentro de /images</p>

      <div class="gallery" id="gallery">
        <img src="images/taekwondo.jpg" alt="Taekwondo" data-full="images/tkw.jpg">
        <img src="images/pichilemu.jpg" alt="Pichilemu" data-full="images/playa.jpg">
        <img src="images/chocolate.jpg" alt="Casa de chocolate" data-full="images/cajon.jpg">
        <img src="images/baile.jpg" alt="Baile nacional" data-full="images/baile.jpg">
        <img src="images/gala.jpg" alt="Gala" data-full="images/gala.jpg">
        <img src="images/amigos.jpg" alt="Cuando solo éramos amigos" data-full="images/amigos.jpg">
      </div>
    </div>

    <div class="section">
      <h2>Nuestra canción</h2>
      <div class="music">
        <div>
          <div style="font-weight:600">Canción especial</div>
          <div style="font-size:13px;opacity:0.7">Haz clic para reproducir</div>
        </div>
        <button id="playBtn">▶</button>
      </div>
      <!-- Mantén el src apuntando a tu archivo si lo subes a /audio -->
      <audio id="track" src="audio/cancion.mp3"></audio>
    </div>

    <!-- sección de mensajes interactivos -->
    <div class="section" id="mensajes">
      <h2>Mensajitos para ti 💌</h2>
      <p style="font-size:14px;opacity:0.7">Haz clic en los corazones para ver mis mensajes.</p>
      <div id="hearts" style="display:flex;gap:14px;flex-wrap:wrap;margin-top:12px"></div>
      <div id="mensajeMostrado" style="margin-top:18px;font-size:18px;font-weight:600;text-align:center;min-height:30px"></div>
    </div>

  </div>

  <script>
    // animación al aparecer
    document.addEventListener('DOMContentLoaded',()=>{
      document.querySelectorAll('.section').forEach((sec,i)=>{
        sec.classList.add('fade');
        setTimeout(()=>sec.classList.add('show'),200*i);
      });

      // inicializar corazones mensajitos
      initMensajes();

      // iniciar lightbox listeners
      initLightbox();

      // preparar reproductor
      initPlayer();

    });

    // LIGHTBOX
    function initLightbox(){
      const lb=document.getElementById('lightbox');
      const lbImg=lb.querySelector('img');
      document.querySelectorAll('.gallery img').forEach(img=>{
        img.addEventListener('click',()=>{
          lbImg.src=img.dataset.full || img.src;
          lb.style.display='flex';
        });
      });
      lb.addEventListener('click',()=>lb.style.display='none');
    }

    // PLAYER
    function initPlayer(){
      const playBtn = document.getElementById('playBtn');
      const track = document.getElementById('track');
      if(!playBtn || !track) return;

      // pequeño efecto al presionar
      playBtn.style.transition='transform .12s ease';
      playBtn.addEventListener('mousedown',()=>playBtn.style.transform='scale(0.95)');
      playBtn.addEventListener('mouseup',()=>playBtn.style.transform='scale(1)');

      playBtn.addEventListener('click',()=>{
        if(track.paused){
          track.play();
          playBtn.textContent='⏸';
        } else {
          track.pause();
          playBtn.textContent='▶';
        }
      });

      // cuando termine la canción, volver al icono play
      track.addEventListener('ended',()=>playBtn.textContent='▶');
    }

    // MENSAJES
    function initMensajes(){
      const mensajes=[
        "Eres la princesa de mis sueños",
        "Tan radiante que el sol te tiene envidia",
        "Eres el amor de mi vida, monita"
      ];

      const hearts=document.getElementById('hearts');
      const msgBox=document.getElementById('mensajeMostrado');

      mensajes.forEach(m=>{
        const h=document.createElement('div');
        h.textContent='❤';
        h.style.fontSize='30px';
        h.style.cursor='pointer';
        h.style.transition='transform .2s';
        h.addEventListener('mouseover',()=>h.style.transform='scale(1.3)');
        h.addEventListener('mouseout',()=>h.style.transform='scale(1)');
        h.addEventListener('click',()=>{
          msgBox.textContent=m;
          msgBox.style.opacity='1';
          setTimeout(()=>msgBox.style.opacity='0.5',2500);
        });
        hearts.appendChild(h);
      });

      // corazones flotando
      function crearCorazon(){
        const c=document.createElement('div');
        c.textContent='❤';
        c.style.position='fixed';
        c.style.left=Math.random()*100+'vw';
        c.style.bottom='0px';
        c.style.fontSize=(20+Math.random()*20)+'px';
        c.style.opacity='0.7';
        c.style.pointerEvents='none';
        c.style.animation='flotar 4s linear forwards';
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),4000);
      }
      setInterval(crearCorazon,1200);
    }

  </script>

  <style>
  /* styling para animación de corazones (se deja al final por simplicidad) */
  @keyframes flotar{ 0%{transform:translateY(0);opacity:0.7} 100%{transform:translateY(-150px);opacity:0} }
  </style>

</body>
</html>
