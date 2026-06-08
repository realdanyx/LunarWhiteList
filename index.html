<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de Whitelist</title>
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #121214;
            color: #e1e1e6;
        }
        .box {
            background: #202024;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
            text-align: center;
        }
        input[type="text"] {
            padding: 12px;
            width: 240px;
            background: #121214;
            border: 2px solid #29292e;
            border-radius: 6px;
            color: white;
            font-size: 16px;
            outline: none;
        }
        input[type="text"]:focus {
            border-color: #00b37e;
        }
        button {
            padding: 12px 24px;
            background-color: #00b37e;
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            margin-left: 10px;
            transition: background 0.2s;
        }
        button:hover {
            background-color: #00875f;
        }
        #message {
            margin-top: 20px;
            font-size: 14px;
        }
    </style>
</head>
<body>

<div class="box">
    <input type="text" id="playerName" placeholder="Tu Gamertag">
    <button id="readyBtn">Ready</button>
    <div id="message"></div>
</div>

<script>
    // CONFIGURACIÓN DE GITHUB
    const GITHUB_USER = 'TU_USUARIO_DE_GITHUB';
    const GITHUB_REPO = 'NOMBRE_DE_TU_REPOSITORIO';
    const GITHUB_TOKEN = 'TU_FINE_GRAINED_TOKEN_AQUÍ'; 

    document.getElementById('readyBtn').addEventListener('click', async () => {
        const player = document.getElementById('playerName').value.trim();
        const messageDiv = document.getElementById('message');

        if (!player) {
            messageDiv.style.color = "#f75a68";
            messageDiv.innerText = "Escribe un Gamertag.";
            return;
        }

        // Limpiar espacios extraños o caracteres no permitidos en sistemas de archivos si es necesario
        const cleanName = player.replace(/[^a-zA-Z0-9_-]/g, '');
        
        messageDiv.style.color = "#8d8d99";
        messageDiv.innerText = "Conectando con la lista...";

        const url = `https://api.github.com/repos/${GITHUB_USER}/${GITHUB_REPO}/contents/WhiteListPlayers/Players.txt`;

        let currentContent = "";
        let fileSha = null;

        // PASO 1: Intentar leer el archivo existente para obtener su contenido y su SHA
        try {
            const getResponse = await fetch(url, {
                method: 'GET',
                headers: {
                    'Authorization': `token ${GITHUB_TOKEN}`,
                    'Accept': 'application/vnd.github.v3+json'
                }
            });

            if (getResponse.status === 200) {
                const fileData = await getResponse.json();
                fileSha = fileData.sha; // Guardamos el SHA para poder editarlo luego
                // Decodificar el contenido actual que viene en Base64
                currentContent = decodeURIComponent(escape(atob(fileData.content)));
            } else if (getResponse.status !== 404) {
                // Si da un error que no sea "No encontrado (404)", detenemos el proceso
                messageDiv.style.color = "#f75a68";
                messageDiv.innerText = "Error al obtener la lista actual.";
                return;
            }
        } catch (error) {
            messageDiv.style.color = "#f75a68";
            messageDiv.innerText = "Error de conexión al leer el archivo.";
            return;
        }

        // Verificar si el jugador ya está en el archivo text (evitar duplicados)
        const jugadoresExistentes = currentContent.split('\n').map(name => name.trim().toLowerCase());
        if (jugadoresExistentes.includes(cleanName.toLowerCase())) {
            messageDiv.style.color = "#ffb84d";
            messageDiv.innerText = `¡${cleanName} ya está registrado en la Whitelist!`;
            return;
        }

        messageDiv.innerText = "Actualizando lista...";

        // Añadir el nuevo jugador en una nueva línea limpia
        let updatedContent = currentContent;
        if (updatedContent.length > 0 && !updatedContent.endsWith('\n')) {
            updatedContent += '\n';
        }
        updatedContent += cleanName;

        // Convertir el texto final a Base64 (requerido por la API de GitHub)
        const base64Content = btoa(unescape(encodeURIComponent(updatedContent)));

        // PASO 2: Guardar el archivo modificado de vuelta en GitHub
        try {
            const putResponse = await fetch(url, {
                method: 'PUT',
                headers: {
                    'Authorization': `token ${GITHUB_TOKEN}`,
                    'Content-Type': 'application/json',
                    'Accept': 'application/vnd.github.v3+json'
                },
                body: JSON.stringify({
                    message: `Añadido el jugador ${cleanName} a la whitelist`,
                    content: base64Content,
                    sha: fileSha // Si el archivo no existía, esto es null y GitHub lo creará de cero. Si existía, lo edita usando el SHA.
                })
            });

            if (putResponse.status === 200 || putResponse.status === 201) {
                messageDiv.style.color = "#00b37e";
                messageDiv.innerText = `¡${cleanName} ha sido agregado con éxito!`;
                document.getElementById('playerName').value = "";
            } else {
                messageDiv.style.color = "#f75a68";
                messageDiv.innerText = "Error al guardar los cambios en GitHub.";
            }
        } catch (error) {
            messageDiv.style.color = "#f75a68";
            messageDiv.innerText = "Error de conexión al guardar.";
        }
    });
</script>

</body>
</html>
