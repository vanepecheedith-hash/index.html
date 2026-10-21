
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Queque Clicker 🎂</title>
  <style>
    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: linear-gradient(#ffe1ec, #fff3cc);
      font-family: Arial, sans-serif;
      text-align: center;
      color: #793c51;
    }

    h1 { font-size: 34px; }

    #puntos {
      font-size: 28px;
      font-weight: bold;
      margin: 15px;
    }

    #queque {
      font-size: 130px;
      border: none;
      background: transparent;
      cursor: pointer;
      transition: transform 0.1s;
      -webkit-tap-highlight-color: transparent;
    }

    #queque:active {
      transform: scale(0.85) rotate(-5deg);
    }

    #mensaje {
      font-size: 20px;
      min-height: 28px;
    }

    button {
      font-size: 18px;
      padding: 12px 22px;
      border: none;
      border-radius: 15px;
      background: #ff9ebc;
      color: #57253a;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>🎂 Queque Clicker 🎂</h1>
  <p>¡Tocá el queque para ganar puntos!</p>

  <div id="puntos">Puntos: 0</div>

  <button id="queque" aria-label="Hacer clic en el queque">
    🎂
  </button>

  <p id="mensaje">¡Dale un mordisco! 😋</p>

  <button id="mejora">Mejora: 25 puntos 🍰</button>

  <script>
    let puntos = 0;
    let porClic = 1;
    let precio = 25;

    const queque = document.getElementById("queque");
    const marcador = document.getElementById("puntos");
    const mensaje = document.getElementById("mensaje");
    const mejora = document.getElementById("mejora");

    queque.addEventListener("click", () => {
      puntos += porClic;
      marcador.textContent = "Puntos: " + puntos;

      if (puntos >= 100) {
        mensaje.textContent = "¡Sos el rey del queque! 👑🎂";
      } else {
        mensaje.textContent = "¡ÑAM! 😋 +" + porClic;
      }
    });

    mejora.addEventListener("click", () => {
      if (puntos >= precio) {
        puntos -= precio;
        porClic *= 2;
        precio *= 2;

        marcador.textContent = "Puntos: " + puntos;
        mejora.textContent = "Mejora: " + precio + " puntos 🍰";
        mensaje.textContent = "¡Ahora ganás el doble por clic! 🚀";
      } else {
        mensaje.textContent = "¡Te faltan puntos! Seguí clickeando 😋";
      }
    });
  </script>

</body>
</html>
