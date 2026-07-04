# sanish
a very well trained and profensional  coder
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chips & Beats | My Space</title>
    <style>
        /* --- Global Resets & Theme --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #2e2e36;
            color: #f0f0f5;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* --- Intro Animation Overlay --- */
        #intro-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #1c1c21;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.8s ease;
        }

        /* Animated Poker Joker Elements */
        .joker-table {
            position: relative;
            width: 200px;
            height: 200px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* The Joker's floating mask/presence */
        .joker-face {
            width: 60px;
            height: 60px;
            background: #ff2a5f;
            clip-path: polygon(50% 0%, 80% 20%, 100% 50%, 80% 80%, 50% 100%, 20% 80%, 0% 50%, 20% 20%);
            box-shadow: 0 0 30px #ff2a5f;
            animation: floatJoker 2s infinite ease-in-out;
            position: absolute;
            z-index: 2;
        }

        /* Eyes pulsing with card suit shapes */
        .joker-face::before, .joker-face::after {
            content: '♠';
            position: absolute;
            top: 35%;
            color: #1c1c21;
            font-size: 1.2rem;
            font-weight: bold;
        }
        .joker-face::before { left: 20%; transform: rotate(-15deg); }
        .joker-face::after { right: 20%; transform: rotate(15deg); }

        /* Rapidly dealing/shuffling digital cards */
        .poker-card-anim {
            position: absolute;
            width: 45px;
            height: 65px;
            background: #00f0ff;
            border: 2px solid #fff;
            border-radius: 5px;
            box-shadow: 0 0 15px #00f0ff;
            opacity: 0;
            transform-origin: bottom center;
        }

        .card-1 { animation: dealCard 1.2s infinite 0s linear; }
        .card-2 { animation: dealCard 1.2s infinite 0.3s linear; }
        .card-3 { animation: dealCard 1.2s infinite 0.6s linear; }
        .card-4 { animation: dealCard 1.2s infinite 0.9s linear; }

        @keyframes floatJoker {
            0%, 100% { transform: translateY(0) scale(1); filter: drop-shadow(0 0 15px #ff2a5f); }
            50% { transform: translateY(-15px) scale(1.05); filter: drop-shadow(0 0 30px #ff2a5f); }
        }

        @keyframes dealCard {
            0% {
                transform: translate(0, 0) rotate(0deg) scale(0.3);
                opacity: 0;
            }
            30% {
                opacity: 1;
            }
            100% {
                transform: translate(var(--tx, 80px), var(--ty, 50px)) rotate(var(--rot, 45deg)) scale(1);
                opacity: 0;
            }
        }

        /* Setting specific dealing directions for each card */
        .card-1 { --tx: -90px; --ty: 40px; --rot: -60deg; }
        .card-2 { --tx: -40px; --ty: 80px; --rot: -20deg; }
        .card-3 { --tx: 40px; --ty: 80px; --rot: 20deg; }
        .card-4 { --tx: 90px; --ty: 40px; --rot: 60deg; }

        .intro-text {
            margin-top: 25px;
            font-size: 1.5rem;
            letter-spacing: 3px;
            color: #00f0ff;
            text-shadow: 0 0 10px #00f0ff;
            font-weight: bold;
            text-transform: uppercase;
            animation: pulse 1.5s infinite alternate;
        }

        @keyframes pulse {
            0% { opacity: 0.4; }
            100% { opacity: 1; }
        }

        /* --- Main Content --- */
        #main-content {
            opacity: 0;
            transition: opacity 1s ease-in;
            padding-bottom: 60px;
        }

        /* --- Header / Navigation --- */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(36, 36, 43, 0.9);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid #444;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff2a5f, #00f0ff);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        nav a {
            color: #ccc;
            text-decoration: none;
            margin-left: 20px;
            transition: color 0.3s;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        nav a:hover {
            color: #00f0ff;
        }

        /* --- Hero Section --- */
        .hero {
            height: 75vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: radial-gradient(circle at center, #3e324d 0%, #2e2e36 70%);
            padding: 0 20px;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 10px;
            letter-spacing: 2px;
            color: #ffffff;
        }

        .hero p {
            color: #bbb;
            font-size: 1.2rem;
            max-width: 600px;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .hero-accent {
            color: #ff2a5f;
        }

        /* Dynamic Pop-up Button Styling */
        .thanks-btn {
            background: linear-gradient(45deg, #ff2a5f, #00f0ff);
            color: #ffffff;
            border: none;
            padding: 12px 30px;
            font-size: 1rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            border-radius: 30px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 240, 255, 0.3);
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .thanks-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 20px rgba(255, 42, 95, 0.5);
        }

        .thanks-btn:active {
            transform: scale(0.98);
        }

        /* --- Grid Section --- */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .card {
            background: #222229;
            border: 1px solid #444;
            border-radius: 12px;
            padding: 25px;
            transition: transform 0.3s, border-color 0.3s;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: #00f0ff;
        }

        .card h2 {
            font-size: 1.4rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .poker-card h2 { color: #ff2a5f; }
        .music-card h2 { color: #00f0ff; }

        /* --- Custom Styling Elements --- */
        .poker-badge {
            background: #3d1b29;
            color: #ff2a5f;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
            display: inline-block;
            margin-bottom: 10px;
        }

        .track-list {
            list-style: none;
            margin-top: 15px;
        }

        .track-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #333;
            font-size: 0.9rem;
        }

        .track-item span {
            color: #aaa;
        }

        .audio-placeholder {
            background: #2e2e38;
            height: 45px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.85rem;
            color: #aaa;
            margin-top: 15px;
            border: 1px dashed #555;
        }
    </style>
</head>
<body>

    <div id="intro-overlay">
        <div class="joker-table">
            <div class="joker-face"></div>
            <div class="poker-card-anim card-1"></div>
            <div class="poker-card-anim card-2"></div>
            <div class="poker-card-anim card-3"></div>
            <div class="poker-card-anim card-4"></div>
        </div>
        <div class="intro-text">The Joker is Dealing...</div>
    </div>

    <div id="main-content">
        <header>
            <div class="logo">♠️ CHIPS & BEATS 🎧</div>
            <nav>
                <a href="#poker">Poker</a>
                <a href="#music">Music</a>
            </nav>
        </header>

        <section class="hero">
            <h1>High Stakes & <span class="hero-accent">Lo-Fi Breaks</span></h1>
            <p>Welcome to my corner of the web. This is where strategic bluffs meet deep baselines. Read the room, ride the rhythm.</p>
            <button class="thanks-btn" id="pop-btn">Say Thanks ⚡</button>
        </section>

        <main class="container">
            <div class="grid">
                
                <div class="card poker-card" id="poker">
                    <span class="poker-badge">Favorite Variant</span>
                    <h2>Texas Hold'em</h2>
                    <p>Nothing beats the rush of table dynamics, calculated risks, and pulling off the perfect bluff when the pot is locked tight.</p>
                </div>

                <div class="card music-card" id="music">
                    <h2>Current Rotation</h2>
                    <p>My go-to genres while grinding out a session or analyzing past hands:</p>
                    <ul class="track-list">
                        <li class="track-item">Synthwave / Cyberpunk <span>Concentration</span></li>
                        <li class="track-item">Deep House <span>Grinding</span></li>
                        <li class="track-item">Lo-Fi Hip Hop <span>Chill Review</span></li>
                    </ul>
                </div>

                <div class="card poker-card">
                    <span class="poker-badge">Latest Win</span>
                    <h2>The Pocket Rockets</h2>
                    <p>Held pocket Aces [A♦ A♠], slow-played pre-flop, and trapped a heavy bettor on a clean board. Pure satisfaction.</p>
                </div>

                <div class="card music-card">
                    <h2>Now Playing</h2>
                    <p>Keeping the focus sharp and the heart rate steady.</p>
                    <div class="audio-placeholder">
                        ▶️ Ambient Focus Mix - 02:14 / 45:00
                    </div>
                </div>

            </div>
        </main>
    </div>

    <script>
        // Intro Animation controller
        window.addEventListener('DOMContentLoaded', () => {
            setTimeout(() => {
                const overlay = document.getElementById('intro-overlay');
                const mainContent = document.getElementById('main-content');
                
                overlay.style.opacity = '0';
                mainContent.style.opacity = '1';

                setTimeout(() => {
                    overlay.style.display = 'none';
                }, 800);

            }, 2500); 
        });

        // Functional click popup behavior
        const popBtn = document.getElementById('pop-btn');
        popBtn.addEventListener('click', () => {
            alert('thank u');
        });
    </script>
</body>
</html>
