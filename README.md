<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Ecosistema Digital de Aprendizaje Autogestivo - UnADM</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --menu-bg: #DDC9A3;
            --menu-hover: #235B4E;
            --footer-bg: #691C32;
            --accent: #235B4E;
            --gray-mid: #98989A;
            --white: #fff;
            --text-dark: #333;
            --shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
            --shadow-hover: 0 6px 18px rgba(0, 0, 0, 0.12);
            --border-radius: 10px;
            --max-width: 1200px;
            --transition: 0.25s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f9f9f9;
            color: var(--text-dark);
            line-height: 1.5;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
            width: 100%;
        }

        /* HEADER */
        .header-pre,
        .header-post {
            background: #fff;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.06);
            position: sticky;
            top: 0;
            z-index: 1000;
            width: 100%;
        }
        .header-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
            max-width: var(--max-width);
            margin: 0 auto;
            padding: 10px 20px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .header-logo img {
            height: 50px;
            width: auto;
        }
        .header-title {
            font-size: 1.4rem;
            font-weight: 700;
            color: #1a1a2e;
            text-align: center;
            flex: 1;
            min-width: 200px;
        }
        .header-social {
            display: flex;
            gap: 10px;
        }
        .header-social a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: #f0f0f0;
            color: #333;
            text-decoration: none;
            transition: var(--transition);
            font-size: 1rem;
        }
        .header-social a:hover {
            background: var(--accent);
            color: #fff;
            transform: scale(1.1);
        }

        /* MENÚ (siempre visible, sin hamburguesa) */
        .nav-pre,
        .nav-post {
            background: var(--menu-bg);
            width: 100%;
            padding: 4px 0;
        }
        .nav-pre-inner,
        .nav-post-inner {
            max-width: var(--max-width);
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
            gap: 2px;
        }
        .nav-pre a,
        .nav-pre button,
        .nav-post a,
        .nav-post button {
            display: inline-block;
            padding: 8px 18px;
            color: #333;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.9rem;
            transition: var(--transition);
            border: none;
            background: none;
            cursor: pointer;
            font-family: inherit;
            border-radius: 4px;
            white-space: nowrap;
        }
        .nav-pre a:hover,
        .nav-pre button:hover,
        .nav-post a:hover,
        .nav-post button:hover {
            background: var(--menu-hover);
            color: #fff;
        }
        /* Clase active solo temporal */
        .nav-pre a.active,
        .nav-pre button.active,
        .nav-post a.active,
        .nav-post button.active {
            background: var(--menu-hover);
            color: #fff;
        }
        .dropdown {
            position: relative;
            display: inline-block;
        }
        .dropdown-content {
            display: none;
            position: absolute;
            top: 100%;
            left: 0;
            background: #fff;
            min-width: 240px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
            border-radius: 8px;
            z-index: 1001;
            flex-direction: column;
            overflow: hidden;
        }
        .dropdown-content a {
            display: block;
            padding: 10px 16px;
            color: #333;
            text-decoration: none;
            font-weight: 500;
            border-bottom: 1px solid #eee;
            white-space: normal;
            font-size: 0.85rem;
        }
        .dropdown-content a:hover {
            background: #e8f5e9;
            color: var(--accent);
        }
        .dropdown:hover .dropdown-content,
        .dropdown.show .dropdown-content {
            display: flex;
        }

        /* MAIN CONTENT */
        .main-content {
            flex: 1;
            max-width: var(--max-width);
            margin: 0 auto;
            width: 100%;
            padding: 16px 20px;
            box-sizing: border-box;
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }

        /* FOOTER */
        .footer {
            background: var(--footer-bg);
            color: #fff;
            padding: 14px 20px;
            text-align: center;
            width: 100%;
            position: sticky;
            bottom: 0;
            z-index: 999;
        }
        .footer-inner {
            max-width: var(--max-width);
            margin: 0 auto;
        }
        .footer-links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 14px;
            margin-bottom: 6px;
        }
        .footer-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.85rem;
        }
        .footer-links a:hover {
            text-decoration: underline;
        }
        .footer-legend {
            font-size: 0.75rem;
            opacity: 0.9;
        }

        /* BOTONES Y TARJETAS */
        .btn {
            display: inline-block;
            padding: 10px 20px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.95rem;
            transition: var(--transition);
            text-decoration: none;
            text-align: center;
            font-family: inherit;
        }
        .btn-primary {
            background: var(--accent);
            color: #fff;
        }
        .btn-primary:hover {
            background: #1a4a3e;
            transform: translateY(-1px);
            box-shadow: var(--shadow-hover);
        }
        .btn-outline {
            background: #fff;
            color: var(--accent);
            border: 2px solid var(--accent);
        }
        .btn-outline:hover {
            background: var(--accent);
            color: #fff;
        }
        .btn-lg {
            padding: 14px 28px;
            font-size: 1.05rem;
        }
        .btn-sm {
            padding: 6px 14px;
            font-size: 0.8rem;
        }

        .card {
            background: #fff;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            overflow: hidden;
            transition: var(--transition);
            flex: 0 0 auto;
            width: 200px;
            min-width: 180px;
        }
        .card:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-hover);
        }
        .card img {
            width: 100%;
            height: 110px;
            object-fit: cover;
            display: block;
        }
        .card-body {
            padding: 10px;
            text-align: center;
        }
        .card-body h4 {
            font-size: 0.85rem;
            margin-bottom: 6px;
            color: #333;
            min-height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .card-body .btn {
            font-size: 0.75rem;
            padding: 6px 14px;
        }
        .card-footer {
            padding: 8px;
            text-align: center;
            border-top: 1px solid #eee;
        }

        /* CARRUSEL */
        .carousel-container {
            position: relative;
            overflow: hidden;
            width: 100%;
        }
        .carousel-track {
            display: flex;
            gap: 14px;
            transition: transform 0.4s ease;
            padding: 6px 2px;
        }
        .carousel-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: #fff;
            border: none;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            box-shadow: var(--shadow);
            cursor: pointer;
            z-index: 10;
            font-size: 1rem;
            color: #333;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .carousel-btn:hover {
            background: var(--accent);
            color: #fff;
        }
        .carousel-btn.prev {
            left: 2px;
        }
        .carousel-btn.next {
            right: 2px;
        }
        .carousel-wrapper {
            position: relative;
            overflow: hidden;
        }

        .section-title {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--accent);
            margin: 16px 0 8px;
            cursor: pointer;
            display: inline-block;
        }
        .section-title:hover {
            text-decoration: underline;
        }

        /* FORMULARIOS */
        .form-group {
            margin-bottom: 12px;
            text-align: left;
        }
        .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 4px;
            color: #555;
            font-size: 0.9rem;
        }
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 8px 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 0.95rem;
            transition: var(--transition);
            font-family: inherit;
        }
        .form-group input:focus,
        .form-group textarea:focus {
            border-color: var(--accent);
            outline: none;
            box-shadow: 0 0 0 3px rgba(35, 91, 78, 0.1);
        }

        .stars {
            color: #f0c040;
            font-size: 1.3rem;
            letter-spacing: 1px;
        }
        .stars .far {
            color: #ccc;
        }

        .search-box {
            display: flex;
            align-items: center;
            background: #fff;
            border: 2px solid #ddd;
            border-radius: 25px;
            padding: 6px 14px;
            gap: 6px;
            transition: var(--transition);
            max-width: 280px;
        }
        .search-box:focus-within {
            border-color: var(--accent);
        }
        .search-box input {
            border: none;
            outline: none;
            flex: 1;
            font-size: 0.9rem;
            background: transparent;
        }
        .search-box i {
            color: #888;
        }
        .search-suggestions {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 0 0 8px 8px;
            z-index: 20;
            display: none;
            box-shadow: var(--shadow);
            max-height: 200px;
            overflow-y: auto;
        }
        .search-suggestions .suggestion-item {
            padding: 8px 14px;
            cursor: pointer;
            font-size: 0.85rem;
            border-bottom: 1px solid #f0f0f0;
        }
        .search-suggestions .suggestion-item:hover {
            background: #e8f5e9;
        }

        /* UTILIDADES */
        .text-center {
            text-align: center;
        }
        .mt-2 {
            margin-top: 14px;
        }
        .mb-2 {
            margin-bottom: 14px;
        }
        .d-flex {
            display: flex;
        }
        .flex-wrap {
            flex-wrap: wrap;
        }
        .align-center {
            align-items: center;
        }
        .justify-center {
            justify-content: center;
        }
        .flex-col {
            flex-direction: column;
        }
        .sidebar-left {
            flex: 0 0 260px;
            padding-right: 16px;
        }
        .content-right {
            flex: 1;
            min-width: 0;
        }
        .divider {
            border-top: 1px solid #e0e0e0;
            margin: 10px 0;
        }

        /* Ajustes para paneles completos */
        .detalle-layout {
            display: flex;
            gap: 20px;
            align-items: flex-start;
        }
        .detalle-left {
            flex: 0 0 55%;
            min-width: 0;
        }
        .detalle-right {
            flex: 0 0 45%;
            min-width: 0;
        }
        .detalle-left .card,
        .detalle-right .card {
            width: 100%;
            height: auto;
        }
        .evaluation-card {
            max-height: 300px;
            overflow-y: auto;
        }
        .visualizacion-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin-top: 10px;
        }

        /* Mi perfil centrado */
        .profile-panel {
            max-width: 500px;
            margin: 0 auto;
            width: 100%;
        }

        /* Menú horizontal tipo comunidad */
        .community-menu {
            display: flex;
            gap: 4px;
            flex-wrap: wrap;
            background: var(--gray-mid);
            padding: 5px;
            border-radius: 8px;
            margin: 12px 0;
        }
        .community-menu .btn {
            background: #fff;
            color: #333;
            flex: 1;
            min-width: 100px;
        }
        .community-menu .btn.active {
            background: var(--accent);
            color: #fff;
        }

        @media (max-width: 860px) {
            .header-title {
                font-size: 1.1rem;
            }
            .header-logo img {
                height: 38px;
            }
            .nav-pre a,
            .nav-post a,
            .nav-pre button,
            .nav-post button {
                padding: 8px 12px;
                font-size: 0.8rem;
            }
            .card {
                width: 160px;
                min-width: 140px;
            }
            .card img {
                height: 90px;
            }
            .carousel-btn {
                width: 30px;
                height: 30px;
                font-size: 0.9rem;
            }
            .d-flex.responsive-stack {
                flex-direction: column;
            }
            .sidebar-left {
                flex: auto;
                padding-right: 0;
                margin-bottom: 14px;
            }
            .detalle-layout {
                flex-direction: column;
            }
            .detalle-left,
            .detalle-right {
                flex: auto;
            }
            .community-menu .btn {
                font-size: 0.7rem;
                padding: 8px 6px;
            }
        }
        @media (max-width: 480px) {
            .card {
                width: 140px;
                min-width: 120px;
            }
            .card img {
                height: 80px;
            }
            .btn {
                padding: 8px 16px;
                font-size: 0.8rem;
            }
            .section-title {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- HEADER PRE-LOGIN -->
    <header class="header-pre" id="headerPre">
        <div class="header-top">
            <div class="header-logo">
                <img src="Imagen6.jpg" alt="Logo UnADM" style="border-radius:6px;">
            </div>
            <div class="header-title">Ecosistema digital de aprendizaje autogestivo</div>
            <div class="header-social">
                <a href="https://www.facebook.com/UnADM.Oficial/" target="_blank"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/momentosunadm" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="https://www.youtube.com/channel/UC5Oms5ZMLVkZx8xwx191qfg" target="_blank"><i class="fab fa-youtube"></i></a>
            </div>
        </div>
        <nav class="nav-pre">
            <div class="nav-pre-inner" id="navPreInner">
                <a href="#" onclick="showPage('bienvenida')" class="active" data-page="bienvenida">Bienvenida</a>
                <a href="#" onclick="showPage('preguntasFrecuentes')" data-page="preguntasFrecuentes">Preguntas frecuentes</a>
                <a href="#" onclick="showPage('login')" data-page="login">Inicio de sesión</a>
            </div>
        </nav>
    </header>

    <!-- HEADER POST-LOGIN -->
    <header class="header-post" id="headerPost" style="display:none;">
        <div class="header-top">
            <div class="header-logo">
                <img src="Imagen6.jpg" alt="Logo UnADM" style="border-radius:6px;">
            </div>
            <div class="header-title">Ecosistema digital de aprendizaje autogestivo</div>
            <div class="header-social">
                <a href="https://www.facebook.com/UnADM.Oficial/" target="_blank"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/momentosunadm" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="https://www.youtube.com/channel/UC5Oms5ZMLVkZx8xwx191qfg" target="_blank"><i class="fab fa-youtube"></i></a>
            </div>
        </div>
        <nav class="nav-post">
            <div class="nav-post-inner" id="navPostInner">
                <a href="#" onclick="showPage('inicioPost')" class="active" data-page="inicioPost">Inicio</a>
                <div class="dropdown" id="dropdownRecursos">
                    <a href="#" onclick="toggleDropdown(event,'dropdownRecursos')">Recursos académicos ▾</a>
                    <div class="dropdown-content">
                        <a href="https://unadmexico.knimbus.com/portal/v2/default/login" target="_blank">Biblioteca digital</a>
                        <a href="https://proyectoterminal.unadmexico.mx/" target="_blank">Repositorio de proyectos terminales</a>
                        <a href="https://cvl.unadmexico.mx/" target="_blank">Club virtual de lenguas</a>
                        <a href="https://cvaa.unadmexico.mx/" target="_blank">Club virtual de asistencia académica</a>
                        <a href="https://www.unadmexico.mx/nosotros/normatividad" target="_blank">Normatividad</a>
                    </div>
                </div>
                <div class="dropdown" id="dropdownServicios">
                    <a href="#" onclick="toggleDropdown(event,'dropdownServicios')">Servicios UnADM ▾</a>
                    <div class="dropdown-content">
                        <a href="https://www.unadmexico.mx/retos-ciudadanos/" target="_blank">Retos ciudadanos</a>
                        <a href="https://planalma.unadmexico.mx/" target="_blank">Plan alma</a>
                        <a href="https://unadmsaludable.unadmexico.mx/" target="_blank">UnADM saludable</a>
                        <a href="https://www.unadmexico.mx/podcast" target="_blank">Podcast UnADM</a>
                        <a href="http://gaceta.unadmexico.mx/" target="_blank">Gaceta</a>
                    </div>
                </div>
                <a href="#" onclick="showPage('accionesFormativas')" data-page="accionesFormativas">Acciones formativas</a>
                <a href="#" onclick="showPage('recursosDidacticos')" data-page="recursosDidacticos">Recursos didácticos</a>
                <a href="#" onclick="showPage('comunidades')" data-page="comunidades">Comunidades</a>
                <a href="#" onclick="showPage('miPerfil')" data-page="miPerfil"><i class="fas fa-user"></i> Mi perfil</a>
                <a href="#" onclick="logout()" style="color:#a00;">Cerrar sesión</a>
            </div>
        </nav>
    </header>

    <div class="main-content" id="mainContent">
        <!-- Páginas Pre‑login (sin cambios) -->
        <div class="page active" id="page-bienvenida">
            <h2 class="text-center" style="color:var(--accent);margin-bottom:20px;">Bienvenida al Ecosistema Digital</h2>
            <div style="display:flex;flex-direction:column;align-items:center;gap:14px;max-width:500px;margin:0 auto;">
                <button class="btn btn-primary btn-lg" style="width:100%;" onclick="showPage('queEsEcosistema')">¿Qué es el ecosistema digital de aprendizaje autogestivo?</button>
                <button class="btn btn-outline btn-lg" style="width:100%;" onclick="showPage('modalidadEstudio')">Modalidad de estudio</button>
                <button class="btn btn-outline btn-lg" style="width:100%;" onclick="showPage('ejesTematicos')">Ejes temáticos</button>
                <button class="btn btn-outline btn-lg" style="width:100%;" onclick="showPage('tiposContenidos')">Tipos de contenidos</button>
                <button class="btn btn-outline btn-lg" style="width:100%;" onclick="showPage('tiposPoblacion')">Tipos de población</button>
            </div>
        </div>
        <div class="page" id="page-queEsEcosistema">
            <h2 style="color:var(--accent);">¿Qué es el ecosistema digital de aprendizaje autogestivo?</h2>
            <p style="margin-top:14px;">Es un entorno virtual integral diseñado por la UnADM para facilitar el aprendizaje autogestivo, ofreciendo recursos, herramientas y comunidades.</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-modalidadEstudio">
            <h2 style="color:var(--accent);">Modalidad de estudio</h2>
            <p><strong>Aprendizaje autogestivo:</strong> El estudiante es responsable de su propio proceso.</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-ejesTematicos">
            <h2 style="color:var(--accent);">Ejes temáticos</h2><p>Inducción a la vida universitaria, Preparación para el aprendizaje autogestivo, Fortalecimiento académico...</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-tiposContenidos">
            <h2 style="color:var(--accent);">Tipos de contenidos</h2><p>Cursos, talleres, recursos didácticos digitales, guías, videos, podcasts...</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-tiposPoblacion">
            <h2 style="color:var(--accent);">Tipos de población</h2><p>Estudiantes UnADM, servidores públicos, público general.</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-preguntasFrecuentes">
            <h2 style="color:var(--accent);">Preguntas frecuentes</h2>
            <p><strong>¿Qué es el ecosistema digital?</strong><br>Es una plataforma de aprendizaje autogestivo de la UnADM.</p>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-login">
            <h2 class="text-center" style="color:var(--accent);">Inicio de sesión</h2>
            <div style="display:flex;flex-wrap:nowrap;gap:150px;justify-content:center;margin-top:30px;">
                <div style="text-align:center;cursor:pointer;" onclick="showPage('datosAcceso')">
                    <i class="fa fa-users fa-10x" aria-hidden="true"></i>
                    <br><button class="btn btn-primary mt-2">Comunidad UnADM</button>
                </div>
                <div style="text-align:center;">
                    <i class="fa fa-university fa-10x" aria-hidden="true"></i>
                    <br><button class="btn btn-outline mt-2">Servidores Públicos</button>
                </div>
                <div style="text-align:center;">
                    <i class="fa fa-globe fa-10x" aria-hidden="true"></i>
                    <br><button class="btn btn-outline mt-2">Público general</button>
                </div>
            </div>
            <button class="btn btn-primary mt-2" onclick="showPage('bienvenida')">Volver</button>
        </div>
        <div class="page" id="page-datosAcceso">
            <h2 class="text-center" style="color:var(--accent);">Datos de acceso</h2>
            <div style="max-width:400px;margin:16px auto;">
                <div class="form-group"><label>Usuario</label><input type="text" placeholder="Ingresa tu usuario"></div>
                <div class="form-group"><label>Contraseña</label><input type="password" placeholder="Ingresa tu contraseña"></div>
                <div class="form-group" style="display:flex;align-items:center;gap:8px;background:#f9f9f9;padding:10px;border-radius:8px;">
                    <input type="checkbox" id="recaptchaCheck" style="width:18px;height:18px;">
                    <label for="recaptchaCheck"><i class="fa fa-refresh"></i> No soy un robot</label>
                </div>
                <button class="btn btn-primary" style="width:100%;" onclick="doLogin()">Ingresar</button>
                <p class="text-center mt-2"><a href="#" style="color:var(--accent);">¿No tiene una cuenta? Regístrese aquí.</a></p>
            </div>
            <button class="btn btn-outline mt-2" onclick="showPage('login')">Volver</button>
        </div>

        <!-- Página Inicio (Post‑login) -->
        <div class="page" id="page-inicioPost">
            <img src="Imagen10.png" alt="Banner del Ecosistema" style="width: 100%; height: auto; max-height: 200px; object-fit: contain; border-radius: 10px; margin-bottom: 16px;">
            <h3 class="section-title" onclick="showPage('accionesFormativas')">Acciones formativas autogestivas</h3>
            <div class="carousel-wrapper" id="carouselInicioAF">
                <button class="carousel-btn prev" onclick="slideCarousel('carouselInicioAF',-1)">◀</button>
                <div class="carousel-container"><div class="carousel-track" id="trackInicioAF"></div></div>
                <button class="carousel-btn next" onclick="slideCarousel('carouselInicioAF',1)">▶</button>
            </div>
            <h3 class="section-title" onclick="showPage('recursosDidacticos')">Recursos didácticos digitales</h3>
            <div class="carousel-wrapper" id="carouselInicioRD">
                <button class="carousel-btn prev" onclick="slideCarousel('carouselInicioRD',-1)">◀</button>
                <div class="carousel-container"><div class="carousel-track" id="trackInicioRD"></div></div>
                <button class="carousel-btn next" onclick="slideCarousel('carouselInicioRD',1)">▶</button>
            </div>
            <h3 class="section-title" onclick="showPage('comunidades')">Comunidades de interacción</h3>
            <div class="carousel-wrapper" id="carouselInicioCOM">
                <button class="carousel-btn prev" onclick="slideCarousel('carouselInicioCOM',-1)">◀</button>
                <div class="carousel-container"><div class="carousel-track" id="trackInicioCOM"></div></div>
                <button class="carousel-btn next" onclick="slideCarousel('carouselInicioCOM',1)">▶</button>
            </div>
        </div>

        <!-- Acciones Formativas -->
        <div class="page" id="page-accionesFormativas">
            <h2 class="text-center" style="color:var(--accent);">Acciones formativas autogestivas</h2>
            <div class="d-flex responsive-stack" style="gap:16px;margin-top:12px;">
                <div class="sidebar-left">
                    <div class="search-box" style="position:relative;">
                        <i class="fas fa-search"></i><input type="text" placeholder="Buscar curso/taller..." id="searchAF">
                        <div class="search-suggestions" id="suggestionsAF"></div>
                    </div>
                    <div style="text-align:center;margin-top:16px;">
                        <i class="far fa-calendar-alt" style="font-size:2.5rem;color:var(--accent);"></i>
                        <p style="font-weight:600;">Consulta el calendario para inscribirte</p>
                        <button class="btn btn-primary">Ver calendario <i class="fas fa-hand-pointer"></i></button>
                    </div>
                </div>
                <div class="content-right" id="categoriasAF"></div>
            </div>
        </div>

        <!-- Detalle de curso (reorganizado) -->
        <div class="page" id="page-detalleCurso">
            <h2 id="detalleCursoTitulo" style="color:var(--accent);">Curso/Taller</h2>
            <div class="detalle-layout mt-2">
                <div class="detalle-left">
                    <img id="detalleCursoImg" src="" alt="Curso" style="width:100%;border-radius:10px;max-height:200px;object-fit:cover;">
                    <div class="card" style="padding:12px;margin-top:10px;">
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Objetivo</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Duración (4 sem, 20 h)</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Contenido temático</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Requerimientos técnicos</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Sugerencias de AF</button>
                    </div>
                </div>
                <div class="detalle-right">
                    <div class="card evaluation-card" style="padding:14px;">
                        <div style="display:flex;justify-content:space-between;align-items:center;">
                            <span><strong>Puntuación</strong></span>
                            <span class="stars">★★★★★</span>
                            <button class="btn btn-primary btn-sm">Inscribirse</button>
                        </div>
                        <div class="divider"></div>
                        <h4>Comentarios sobre la acción formativa</h4>
                        <div style="display:flex;align-items:center;gap:8px;padding:6px 0;"><i class="fas fa-user-circle fa-2x" style="color:#888;"></i><div><strong>@Vero</strong> Este curso me ayudó a mejorar mis habilidades</div><span style="margin-left:auto;font-size:0.75rem;">12/05/26</span></div>
                        <div class="divider"></div>
                        <div style="display:flex;align-items:center;gap:8px;padding:6px 0;"><i class="fas fa-user-circle fa-2x" style="color:#888;"></i><div><strong>@Pame</strong> Me gustaron las actividades, es muy recomendable.</div><span style="margin-left:auto;font-size:0.75rem;">10/05/26</span></div>
                        <div class="divider"></div>
                        <div style="display:flex;align-items:center;gap:8px;padding:6px 0;"><i class="fas fa-user-circle fa-2x" style="color:#888;"></i><div><strong>@Leon</strong> Le pongo 5 estrellas porque fue muy útil para mí.</div><span style="margin-left:auto;font-size:0.75rem;">08/05/26</span></div>
                        <div class="divider"></div>
                        <p style="cursor:pointer;color:var(--accent);"><i class="fas fa-plus-circle"></i> Agregar comentario</p>
                    </div>
                </div>
            </div>
            <button class="btn btn-primary mt-2" onclick="showPage('accionesFormativas')">Volver</button>
        </div>

        <!-- Recursos Didácticos -->
        <div class="page" id="page-recursosDidacticos">
            <h2 class="text-center" style="color:var(--accent);">Recursos didácticos digitales</h2>
            <div class="d-flex responsive-stack" style="gap:16px;margin-top:12px;">
                <div class="sidebar-left">
                    <div class="search-box" style="position:relative;">
                        <i class="fas fa-search"></i><input type="text" placeholder="Buscar recurso..." id="searchRD">
                        <div class="search-suggestions" id="suggestionsRD"></div>
                    </div>
                    <div style="margin-top:16px;">
                        <button class="btn btn-primary" style="width:100%;"><i class="fas fa-share-alt"></i> ¿Quieres compartir un recurso? Consulta las características y los requisitos con los que debe cumplir.</button>
                    </div>
                </div>
                <div class="content-right" id="categoriasRD"></div>
            </div>
        </div>

        <!-- Detalle de recurso (reorganizado) -->
        <div class="page" id="page-detalleRecurso">
            <h2 id="detalleRecursoTitulo" style="color:var(--accent);">Nombre del recurso</h2>
            <div class="detalle-layout mt-2">
                <div class="detalle-left">
                    <div class="card" style="padding:12px;">
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Objetivo</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Tiempo de revisión</button>
                        <button class="btn btn-outline btn-sm" style="width:100%;margin:3px 0;">Requerimientos técnicos</button>
                    </div>
                    <div class="card evaluation-card" style="padding:14px;margin-top:12px;">
                        <div style="display:flex;justify-content:space-between;align-items:center;">
                            <span><strong>Puntuación</strong></span>
                            <span class="stars">★★★★☆</span>
                            <button class="btn btn-outline btn-sm">Agregar a favoritos</button>
                        </div>
                        <div class="divider"></div>
                        <h4>Comentarios sobre el recurso</h4>
                        <div style="display:flex;align-items:center;gap:8px;padding:6px 0;"><i class="fas fa-user-circle fa-2x" style="color:#888;"></i><div><strong>@Vero</strong> Muy útil para mis trabajos.</div><span style="margin-left:auto;font-size:0.75rem;">15/05/26</span></div>
                        <div class="divider"></div>
                        <div style="display:flex;align-items:center;gap:8px;padding:6px 0;"><i class="fas fa-user-circle fa-2x" style="color:#888;"></i><div><strong>@Pame</strong> Claro y bien explicado.</div><span style="margin-left:auto;font-size:0.75rem;">11/05/26</span></div>
                        <div class="divider"></div>
                        <p style="cursor:pointer;color:var(--accent);"><i class="fas fa-plus-circle"></i> Agregar comentario</p>
                    </div>
                </div>
                <div class="detalle-right">
                    <div class="card" style="padding:16px;">
                        <h3 style="color:var(--accent);">Visualización del recurso</h3>
                        <div class="visualizacion-grid">
                            <div style="text-align:center;padding:12px;background:#f9f9f9;border-radius:8px;"><i class="far fa-file-pdf fa-2x" style="color:#d00;"></i><br>PDF</div>
                            <div style="text-align:center;padding:12px;background:#f9f9f9;border-radius:8px;"><i class="fas fa-video fa-2x" style="color:#00f;"></i><br>Video</div>
                            <div style="text-align:center;padding:12px;background:#f9f9f9;border-radius:8px;"><i class="fas fa-volume-up fa-2x" style="color:#f80;"></i><br>Audio</div>
                            <div style="text-align:center;padding:12px;background:#f9f9f9;border-radius:8px;"><i class="fab fa-html5 fa-2x" style="color:#e44;"></i><br>HTML</div>
                            <div style="text-align:center;padding:12px;background:#f9f9f9;border-radius:8px;"><i class="far fa-file-word fa-2x" style="color:#06c;"></i><br>Word</div>
                        </div>
                    </div>
                </div>
            </div>
            <button class="btn btn-primary mt-2" onclick="showPage('recursosDidacticos')">Volver</button>
        </div>

        <!-- Comunidades -->
        <div class="page" id="page-comunidades">
            <h2 class="text-center" style="color:var(--accent);">Comunidades de aprendizaje</h2>
            <div class="d-flex responsive-stack" style="gap:16px;margin-top:12px;">
                <div class="sidebar-left">
                    <div class="search-box"><i class="fas fa-search"></i><input type="text" placeholder="Buscar comunidad..."></div>
                    <div style="margin-top:16px;display:flex;flex-direction:column;gap:10px;">
                        <button class="btn btn-primary"><i class="fas fa-user-plus"></i> Quiero crear una comunidad</button>
                        <button class="btn btn-outline"><i class="fas fa-scroll"></i> Normas para participar</button>
                    </div>
                </div>
                <div class="content-right">
                    <div class="carousel-wrapper" id="carouselComunidades">
                        <button class="carousel-btn prev" onclick="slideCarousel('carouselComunidades',-1)">◀</button>
                        <div class="carousel-container"><div class="carousel-track" id="trackComunidades"></div></div>
                        <button class="carousel-btn next" onclick="slideCarousel('carouselComunidades',1)">▶</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="page" id="page-detalleComunidad">
            <h2 class="text-center" style="color:var(--accent);" id="comunidadNombre">Uso de TIC para el aprendizaje</h2>
            <div style="width:100%;height:120px;background:#e0e0e0;border-radius:10px;display:flex;align-items:center;justify-content:center;margin:10px 0;">Imagen de portada</div>
            <div class="d-flex responsive-stack" style="gap:12px;">
                <div class="form-group" style="flex:1;"><label>Nombre</label><input type="text" value="Uso de TIC" readonly></div>
                <div class="form-group" style="flex:2;"><label>Descripción</label><textarea rows="2" readonly>Comunidad enfocada en TIC para el aprendizaje autogestivo.</textarea></div>
                <button class="btn btn-primary" style="align-self:flex-end;">Unirse</button>
            </div>
            <div class="community-menu">
                <button class="btn" onclick="showPage('publicacionesRecientes')">Publicaciones recientes</button>
                <button class="btn">Miembros</button>
                <button class="btn">Documentos</button>
                <button class="btn">Enlaces</button>
                <button class="btn">Imágenes</button>
                <button class="btn">Normas</button>
            </div>
            <button class="btn btn-outline mt-2" onclick="showPage('comunidades')">Volver</button>
        </div>

        <!-- Publicaciones recientes (corregida) -->
        <div class="page" id="page-publicacionesRecientes">
            <h2 class="text-center" style="color:var(--accent);">Publicaciones recientes</h2>
            <div class="community-menu">
                <button class="btn active">Publicaciones recientes</button>
                <button class="btn">Miembros</button>
                <button class="btn">Documentos</button>
                <button class="btn">Enlaces</button>
                <button class="btn">Imágenes</button>
                <button class="btn">Normas</button>
            </div>
            <!-- Primer cuadro de texto con publicación de ejemplo -->
            <div style="background:#fff;padding:16px;border-radius:10px;box-shadow:var(--shadow);margin:12px 0;">
                <div style="display:flex;align-items:flex-start;gap:10px;">
                    <i class="fas fa-user-circle fa-2x" style="color:#888;margin-top:4px;"></i>
                    <div style="flex:1;">
                        <p>Hola compañeros, un gusto ser parte de este grupo, espero compartir y crear una comunidad.</p>
                        <div style="display:flex;justify-content:space-between;align-items:center;margin-top:8px;">
                            <span class="stars">★★★★<i class="far fa-star"></i></span>
                            <button class="btn btn-primary btn-sm">Comentar</button>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Segundo cuadro de texto vacío para nueva publicación -->
            <div style="background:#fff;padding:16px;border-radius:10px;box-shadow:var(--shadow);">
                <div style="display:flex;align-items:flex-start;gap:10px;">
                    <i class="fas fa-user-circle fa-2x" style="color:#888;margin-top:4px;"></i>
                    <div style="flex:1;">
                        <textarea placeholder="Escribe tu publicación..." style="width:100%;min-height:60px;padding:10px;border:1px solid #ddd;border-radius:8px;font-family:inherit;"></textarea>
                        <div style="text-align:right;margin-top:8px;">
                            <button class="btn btn-primary">Publicar</button>
                        </div>
                    </div>
                </div>
            </div>
            <button class="btn btn-outline mt-2" onclick="showPage('detalleComunidad')">Volver</button>
        </div>

        <!-- Mi Perfil (panel editable centrado) -->
        <div class="page" id="page-miPerfil">
            <h2 class="text-center" style="color:var(--accent);">Mi perfil</h2>
            <div class="d-flex responsive-stack" style="gap:16px;margin-top:10px;align-items:flex-start;">
                <div style="text-align:center;flex:0 0 180px;">
                    <i class="fas fa-user-circle" style="font-size:5rem;color:#888;"></i>
                    <div class="form-group mt-2">
                        <label>Sobre mí (objetivo académico)</label>
                        <textarea rows="3" style="font-size:0.85rem;">Apasionado por el aprendizaje continuo y la tecnología educativa.</textarea>
                    </div>
                    <button class="btn btn-outline btn-sm"><i class="fas fa-pen"></i> Editar</button>
                </div>
                <!-- Panel editable centrado -->
                <div class="profile-panel">
                     <div style="flex:1; min-width:300px; background:white; border-radius:16px; padding:25px; box-shadow:var(--sombra);">
                        <div class="form-group"><label>Nombre de usuario</label><input type="text" value="Usuario UnADM" readonly></div>
                        <div class="form-group"><label>Programa educativo / área</label><input type="text" value="Ingeniería en Desarrollo de Software" readonly></div>
                        <div class="form-group"><label>Ciudad de residencia</label><input type="text" value="Ciudad de México" readonly></div>
                        <div class="card-footer"><button class="btn btn-outline btn-sm"><i class="fas fa-pen"></i> Editar</button></div>
                    </div>
                    <div style="margin-top:14px;">
                        <h4 style="color:var(--accent);">Acciones formativas inscritas</h4>
                        <div class="carousel-wrapper" id="carouselPerfilAF">
                            <button class="carousel-btn prev" onclick="slideCarousel('carouselPerfilAF',-1)">◀</button>
                            <div class="carousel-container"><div class="carousel-track" id="trackPerfilAF"></div></div>
                            <button class="carousel-btn next" onclick="slideCarousel('carouselPerfilAF',1)">▶</button>
                        </div>
                    </div>
                </div>
                <div style="flex:0 0 180px; display:flex; flex-direction:column; gap: 8px;"></div>
                    <button class="btn btn-outline btn-sm"><i class="fas fa-heart"></i> Recursos favoritos</button>
                    <button class="btn btn-outline btn-sm"><i class="fas fa-file-alt"></i> Recursos creados</button>
                    <button class="btn btn-outline btn-sm"><i class="fas fa-users"></i> Comunidades</button>
                </div>
            </div>
            <button class="btn btn-primary mt-2" onclick="showPage('inicioPost')">Volver a Inicio</button>
        </div>
    </div>

    <footer class="footer">
        <div class="footer-inner">
            <div class="footer-links">
                <a href="#" onclick="showPage('bienvenida')">Aviso de privacidad</a>
                <a href="#" onclick="showPage('preguntasFrecuentes')">Preguntas frecuentes</a>
                <a href="#" onclick="showPage('queEsEcosistema')">¿Qué es el ecosistema?</a>
            </div>
            <div class="footer-legend">2026 UnADM - Ecosistema Digital de Aprendizaje Autogestivo</div>
        </div>
    </footer>

    <script>
        // Navegación corregida: remueve active de todos los menús y asigna solo al botón con data-page correspondiente
        let currentPage = 'bienvenida';
        let isLoggedIn = false;

        function showPage(pageName) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            const pageEl = document.getElementById('page-' + pageName);
            if (pageEl) {
                pageEl.classList.add('active');
                currentPage = pageName;
                // Limpiar active de ambos menús
                document.querySelectorAll('#navPreInner a, #navPostInner a, #navPreInner button, #navPostInner button').forEach(a => a.classList.remove('active'));
                // Asignar active al enlace con data-page correspondiente
                const activeLink = document.querySelector(`[data-page="${pageName}"]`);
                if (activeLink) activeLink.classList.add('active');
                window.scrollTo({ top: 0, behavior: 'smooth' });
                initCarruselesOnPage(pageName);
            }
        }

        function doLogin() {
            isLoggedIn = true;
            document.getElementById('headerPre').style.display = 'none';
            document.getElementById('headerPost').style.display = 'block';
            showPage('inicioPost');
            initAllCarruseles();
        }

        function logout() {
            isLoggedIn = false;
            document.getElementById('headerPre').style.display = 'block';
            document.getElementById('headerPost').style.display = 'none';
            showPage('bienvenida');
        }

        function toggleDropdown(e, dropdownId) {
            e.preventDefault();
            e.stopPropagation();
            const dropdown = document.getElementById(dropdownId);
            dropdown.classList.toggle('show');
            document.querySelectorAll('.dropdown.show').forEach(d => {
                if (d.id !== dropdownId) d.classList.remove('show');
            });
        }
        document.addEventListener('click', () => document.querySelectorAll('.dropdown.show').forEach(d => d.classList.remove('show')));

        // Carrusel genérico
        const carouselPositions = {};
        function slideCarousel(wrapperId, direction) {
            const wrapper = document.getElementById(wrapperId);
            if (!wrapper) return;
            const track = wrapper.querySelector('.carousel-track');
            if (!track) return;
            const cards = track.querySelectorAll('.card');
            if (cards.length === 0) return;
            const cardWidth = cards[0].offsetWidth + 14;
            const visibleWidth = wrapper.querySelector('.carousel-container').offsetWidth;
            const maxScroll = track.scrollWidth - visibleWidth;
            if (!carouselPositions[wrapperId]) carouselPositions[wrapperId] = 0;
            let newPos = carouselPositions[wrapperId] + direction * cardWidth * 2;
            newPos = Math.max(0, Math.min(newPos, maxScroll));
            carouselPositions[wrapperId] = newPos;
            track.style.transform = `translateX(-${newPos}px)`;
        }

// Mapa de imágenes representativas (NO íconos)
const imageMap = {
    'Estrategias de aprendizaje para el estudio dentro y fuera de línea': 'https://images.unsplash.com/photo-1434030216411-0b793f4b4173?w=200&h=120&fit=crop',
    'Administración del tiempo. El tiempo y yo': 'https://images.unsplash.com/photo-1506784983877-45594efa4cbe?w=200&h=120&fit=crop',
    'Educación financiera. Quiero ahorrar': 'https://images.unsplash.com/photo-1579621970588-a35d0e7ab9b6?w=200&h=120&fit=crop',
    'Gestión de emociones': 'https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?w=200&h=120&fit=crop',
    'Mis primeros pasos en la escritura académica': 'https://images.unsplash.com/photo-1455390582262-044cdead277a?w=200&h=120&fit=crop',
    'Introducción a las habilidades blandas': 'https://images.unsplash.com/photo-1524178232363-1fb2b075b655?w=200&h=120&fit=crop',
    'Mejora tu escritura. De la palabra al párrafo': 'https://images.unsplash.com/photo-1456735190827-d1262f71b8a3?w=200&h=120&fit=crop',
    'Comunicación efectiva en entornos virtuales': 'https://images.unsplash.com/photo-1516321318423-f06f85e504b3?w=200&h=120&fit=crop',
    'Pensamiento crítico y resolución de problemas': 'https://images.unsplash.com/photo-1501504905252-473c47e087f8?w=200&h=120&fit=crop',
    'Herramientas digitales para la productividad': 'https://images.unsplash.com/photo-1488190211105-8b0e65b80b4e?w=200&h=120&fit=crop',
    'Guía para elaborar documentos académicos': 'https://images.unsplash.com/photo-1434030216411-0b793f4b4173?w=200&h=120&fit=crop',
    'Guía: Cita con estilo APA 7ª ed': 'https://images.unsplash.com/photo-1554224155-6726b3ff858f?w=200&h=120&fit=crop',
    'Estrategias de lectura': 'https://images.unsplash.com/photo-1506880018603-1d42b66e6d1f?w=200&h=120&fit=crop',
    'Edición de PDF': 'https://images.unsplash.com/photo-1581291518633-83b4ebd1d83e?w=200&h=120&fit=crop',
    'Elaboración de organizadores gráficos': 'https://images.unsplash.com/photo-1544717305-38b9144f7f0a?w=200&h=120&fit=crop',
    'Elaboración de videos': 'https://images.unsplash.com/photo-1492691527719-9d1e07e534b4?w=200&h=120&fit=crop',
    'Comunicación escrita': 'https://images.unsplash.com/photo-1455390582262-044cdead277a?w=200&h=120&fit=crop'
};

// Imagen genérica para títulos no mapeados (por defecto)
const DEFAULT_IMAGE = 'https://images.unsplash.com/photo-1516979187457-637abb4f9353?w=200&h=120&fit=crop';

function getItemImage(title, type = 'course') {
    // Devuelve la imagen específica si existe, sino la genérica
    return imageMap[title] || DEFAULT_IMAGE;
}

// La función getIconUnicode ya no es necesaria y se elimina.

function createCard(title, type = 'course', onClick) {
    const card = document.createElement('div');
    card.className = 'card';
    const imgSrc = getItemImage(title, type);
    card.innerHTML = `<img src="${imgSrc}" alt="${title}"><div class="card-body"><h4>${title}</h4><button class="btn btn-primary btn-sm">Ver más</button></div>`;
    if (onClick) card.querySelector('button').addEventListener('click', onClick);
    return card;
}

        function createCommunityCard(title) {
            const card = document.createElement('div');
            card.className = 'card';
            card.style.textAlign = 'center';
            card.style.padding = '14px';
            card.innerHTML = `<div style="width:60px;height:60px;border-radius:50%;background:#e0e0e0;margin:0 auto;display:flex;align-items:center;justify-content:center;font-size:1.8rem;"><i class="fas fa-users" style="color:#555;"></i></div><div class="card-body"><h4>${title}</h4></div>`;
            return card;
        }

        const cursosAF = [
            'Estrategias de aprendizaje para el estudio dentro y fuera de línea',
            'Administración del tiempo. El tiempo y yo',
            'Educación financiera. Quiero ahorrar',
            'Gestión de emociones',
            'Mis primeros pasos en la escritura académica',
            'Introducción a las habilidades blandas',
            'Mejora tu escritura. De la palabra al párrafo',
            'Comunicación efectiva en entornos virtuales',
            'Pensamiento crítico y resolución de problemas',
            'Herramientas digitales para la productividad'
        ];
        const recursosRD = [
            'Guía para elaborar documentos académicos',
            'Guía: Cita con estilo APA 7ª ed',
            'Estrategias de lectura',
            'Edición de PDF',
            'Elaboración de organizadores gráficos',
            'Elaboración de videos',
            'Comunicación escrita'
        ];
        const categorias = [
            'Inducción a la vida universitaria',
            'Preparación para el aprendizaje autogestivo',
            'Fortalecimiento académico',
            'Desarrollo integral y personal',
            'Actualización figuras académicas',
            'Profesionalización de servidores públicos'
        ];

        function initAllCarruseles() {
            initCarruselInicioAF(); initCarruselInicioRD(); initCarruselInicioCOM();
            initCategoriasAF(); initCategoriasRD(); initCarruselComunidades(); initCarruselPerfilAF();
        }

        function initCarruselesOnPage(pageName) {
            if (pageName === 'inicioPost') initAllCarruseles();
            if (pageName === 'accionesFormativas') initCategoriasAF();
            if (pageName === 'recursosDidacticos') initCategoriasRD();
            if (pageName === 'comunidades') initCarruselComunidades();
            if (pageName === 'miPerfil') initCarruselPerfilAF();
        }

        function initCarruselInicioAF() {
            const track = document.getElementById('trackInicioAF');
            if (!track || track.children.length > 0) return;
            cursosAF.slice(0,7).forEach(nombre => {
                track.appendChild(createCard(nombre, 'course', () => {
                    document.getElementById('detalleCursoTitulo').textContent = nombre;
                    document.getElementById('detalleCursoImg').src = getItemImage(nombre, 'course');
                    showPage('detalleCurso');
                }));
            });
            track.style.transform = 'translateX(0)';
        }
        function initCarruselInicioRD() {
            const track = document.getElementById('trackInicioRD');
            if (!track || track.children.length > 0) return;
            recursosRD.slice(0,7).forEach(nombre => {
                track.appendChild(createCard(nombre, 'resource', () => {
                    document.getElementById('detalleRecursoTitulo').textContent = nombre;
                    showPage('detalleRecurso');
                }));
            });
            track.style.transform = 'translateX(0)';
        }
        function initCarruselInicioCOM() {
            const track = document.getElementById('trackInicioCOM');
            if (!track || track.children.length > 0) return;
            ['Uso de TIC para el aprendizaje','Proyectos terminales','Escritura académica','Grupo 1-R 2026 Nutrición','Lectores UnADM','Foro de dudas UnADM'].forEach(nombre => {
                const card = createCommunityCard(nombre);
                card.addEventListener('click', ()=>{ document.getElementById('comunidadNombre').textContent=nombre; showPage('detalleComunidad'); });
                track.appendChild(card);
            });
            track.style.transform = 'translateX(0)';
        }
        function initCategoriasAF() {
            const container = document.getElementById('categoriasAF');
            if (!container || container.children.length > 0) return;
            categorias.forEach((cat, idx) => {
                const section = document.createElement('div');
                section.innerHTML = `<h4 style="color:#333;margin:10px 0 4px;">${cat}</h4>`;
                const wrapper = document.createElement('div');
                wrapper.className = 'carousel-wrapper';
                wrapper.id = 'carouselAF_cat' + idx;
                const track = document.createElement('div');
                track.className = 'carousel-track';
                for (let i=0; i<5; i++) {
                    const nombre = cursosAF[(idx*5 + i) % cursosAF.length];
                    track.appendChild(createCard(nombre, 'course', () => {
                        document.getElementById('detalleCursoTitulo').textContent = nombre;
                        document.getElementById('detalleCursoImg').src = getItemImage(nombre, 'course');
                        showPage('detalleCurso');
                    }));
                }
                const prev = document.createElement('button'); prev.className='carousel-btn prev'; prev.textContent='◀'; prev.onclick=()=>slideCarousel('carouselAF_cat'+idx,-1);
                const next = document.createElement('button'); next.className='carousel-btn next'; next.textContent='▶'; next.onclick=()=>slideCarousel('carouselAF_cat'+idx,1);
                const carContainer = document.createElement('div'); carContainer.className='carousel-container'; carContainer.appendChild(track);
                wrapper.appendChild(prev); wrapper.appendChild(carContainer); wrapper.appendChild(next);
                section.appendChild(wrapper);
                container.appendChild(section);
            });
        }
        function initCategoriasRD() {
            const container = document.getElementById('categoriasRD');
            if (!container || container.children.length > 0) return;
            categorias.forEach((cat, idx) => {
                const section = document.createElement('div');
                section.innerHTML = `<h4 style="color:#333;margin:10px 0 4px;">${cat}</h4>`;
                const wrapper = document.createElement('div');
                wrapper.className = 'carousel-wrapper';
                wrapper.id = 'carouselRD_cat' + idx;
                const track = document.createElement('div');
                track.className = 'carousel-track';
                for (let i=0; i<5; i++) {
                    const nombre = recursosRD[(idx*5 + i) % recursosRD.length];
                    track.appendChild(createCard(nombre, 'resource', () => {
                        document.getElementById('detalleRecursoTitulo').textContent = nombre;
                        showPage('detalleRecurso');
                    }));
                }
                const prev = document.createElement('button'); prev.className='carousel-btn prev'; prev.textContent='◀'; prev.onclick=()=>slideCarousel('carouselRD_cat'+idx,-1);
                const next = document.createElement('button'); next.className='carousel-btn next'; next.textContent='▶'; next.onclick=()=>slideCarousel('carouselRD_cat'+idx,1);
                const carContainer = document.createElement('div'); carContainer.className='carousel-container'; carContainer.appendChild(track);
                wrapper.appendChild(prev); wrapper.appendChild(carContainer); wrapper.appendChild(next);
                section.appendChild(wrapper);
                container.appendChild(section);
            });
        }
        function initCarruselComunidades() {
            const track = document.getElementById('trackComunidades');
            if (!track || track.children.length > 0) return;
            ['Uso de TIC para el aprendizaje','Proyectos terminales','Escritura académica','Grupo 1-R 2026 Nutrición','Lectores UnADM','Foro de dudas UnADM'].forEach(nombre => {
                const card = createCommunityCard(nombre);
                card.addEventListener('click', ()=>{ document.getElementById('comunidadNombre').textContent=nombre; showPage('detalleComunidad'); });
                track.appendChild(card);
            });
            track.style.transform = 'translateX(0)';
        }
        function initCarruselPerfilAF() {
            const track = document.getElementById('trackPerfilAF');
            if (!track || track.children.length > 0) return;
            cursosAF.slice(0,3).forEach(nombre => {
                track.appendChild(createCard(nombre, 'course', () => {
                    document.getElementById('detalleCursoTitulo').textContent = nombre;
                    document.getElementById('detalleCursoImg').src = getItemImage(nombre, 'course');
                    showPage('detalleCurso');
                }));
            });
            track.style.transform = 'translateX(0)';
        }

        function setupSearch(inputId, suggestionsId, dataArray) {
            const input = document.getElementById(inputId);
            const suggestions = document.getElementById(suggestionsId);
            if(!input||!suggestions) return;
            input.addEventListener('input', function(){
                const val = this.value.toLowerCase().trim();
                suggestions.innerHTML = '';
                if(val.length<2){ suggestions.style.display='none'; return; }
                const matches = dataArray.filter(i=>i.toLowerCase().includes(val)).slice(0,8);
                if(matches.length){
                    suggestions.style.display='block';
                    matches.forEach(m=>{
                        const div = document.createElement('div');
                        div.className='suggestion-item';
                        div.textContent=m;
                        div.addEventListener('click',()=>{ input.value=m; suggestions.style.display='none'; });
                        suggestions.appendChild(div);
                    });
                } else { suggestions.style.display='none'; }
            });
            input.addEventListener('blur', ()=> setTimeout(()=> suggestions.style.display='none', 200));
        }
        setupSearch('searchAF','suggestionsAF', [...cursosAF,...categorias]);
        setupSearch('searchRD','suggestionsRD', [...recursosRD,...categorias]);

        document.addEventListener('DOMContentLoaded', ()=>{
            showPage('bienvenida');
            initCarruselInicioAF(); initCarruselInicioRD(); initCarruselInicioCOM();
        });
    </script>
</body>
</html>
