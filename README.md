<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Girlfriend? 🍍</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        pineapple: {
                            50: '#fffbeb',
                            100: '#fef3c7',
                            200: '#fde68a',
                            300: '#fcd34d',
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                            700: '#b45309',
                        }
                    },
                    fontFamily: {
                        fredoka: ['Fredoka', 'sans-serif'],
                        nunito: ['Nunito', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(135deg, #fffbeb 0%, #fef3c7 50%, #fde68a 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        h1, h2, h3, .font-heading {
            font-family: 'Fredoka', cursive;
        }

        .perspective-1000 {
            perspective: 1000px;
        }

        .transform-style-3d {
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .backface-hidden {
            backface-visibility: hidden;
        }

        .rotate-y-180 {
            transform: rotateY(180deg);
        }

        .card-flipped .transform-style-3d {
            transform: rotateY(180deg);
        }

        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-16px) rotate(8deg); }
        }

        .animate-float {
            animation: floatSlow 4s ease-in-out infinite;
        }

        .bg-particle {
            position: fixed;
            pointer-events: none;
            z-index: 0;
            opacity: 0.25;
            user-select: none;
            animation: floatSlow linear infinite;
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 15px rgba(245, 158, 11, 0.4); }
            50% { box-shadow: 0 0 30px rgba(245, 158, 11, 0.8); }
        }

        .glow-active {
            animation: pulseGlow 2s infinite;
        }

        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #fffbeb;
        }
        ::-webkit-scrollbar-thumb {
            background: #fcd34d;
            border-radius: 4px;
        }
    </style>
</head>
<body class="relative text-gray-800 pb-20">

    <div id="particle-container" class="fixed inset-0 pointer-events-none overflow-hidden z-0"></div>

    <!-- FLOATING MUSIC PLAYER WIDGET -->
    <div class="fixed top-4 right-4 z-50 bg-white/90 backdrop-blur-md border-2 border-amber-300 shadow-xl rounded-full px-4 py-2 flex items-center gap-3">
        <button id="music-toggle-btn" onclick="toggleMusic()" class="w-10 h-10 bg-amber-500 hover:bg-amber-600 text-white rounded-full flex items-center justify-center font-bold text-lg shadow transition-all transform active:scale-95">
            ▶
        </button>
        <div class="text-xs pr-2">
            <p class="font-bold text-amber-800 font-heading leading-tight">Fool — Djo 🎵</p>
            <p id="music-status" class="text-amber-600/80 font-semibold text-[10px]">Click to play background vibe</p>
        </div>
        <!-- Audio element playing Djo - Fool -->
        <audio id="bg-music" loop preload="auto">
            <source src="https://ia801509.us.archive.org/24/items/djo-fool/Djo%20-%20Fool.mp3" type="audio/mpeg">
            Your browser does not support audio elements.
        </audio>
    </div>

    <!-- MAIN CONTAINER -->
    <main class="relative z-10 max-w-4xl mx-auto px-4 py-8 sm:px-6 lg:px-8">
        
        <header class="text-center my-6 sm:my-8">
            <div class="inline-block relative">
                <div class="text-8xl sm:text-9xl animate-float cursor-pointer transform hover:scale-110 transition-transform duration-300 select-none" id="hero-pineapple">
                    🍍
                </div>
                <span class="absolute -top-2 -right-2 text-3xl animate-bounce">🎸</span>
                <span class="absolute bottom-2 -left-4 text-3xl animate-pulse">💛</span>
            </div>

            <h1 class="text-4xl sm:text-6xl font-bold text-amber-800 mt-4 tracking-wide drop-shadow-sm font-heading">
                Hey You... Yea Yea, You! 🍍
            </h1>
            
            <p class="text-lg sm:text-xl text-amber-900/80 mt-3 max-w-xl mx-auto font-bold italic">
                "I Have A Very Khrayzzee Questions For You, Will You *Officially* Be My Girlfriend??" 
            </p>
        </header>

        <!-- SARCASTIC REASONS SECTION -->
        <section class="my-12">
            <h2 class="text-2xl sm:text-3xl font-bold text-center text-amber-800 mb-2 font-heading">
                😏 4 Completely Irresistible Reasons Why You Should Say Yes 😏
            </h2>
            <p class="text-center text-amber-900/70 text-sm mb-8 font-semibold">Tap each card to reveal the indisputable facts:</p>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 px-2">
                
                <!-- Card 1 -->
                <div class="perspective-1000 h-48 cursor-pointer group" onclick="flipCard(this)">
                    <div class="transform-style-3d relative w-full h-full rounded-2xl shadow-md hover:shadow-xl transition-shadow duration-300">
                        <div class="backface-hidden absolute inset-0 bg-white border-2 border-amber-200 rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-4xl mb-2">👨‍🍳</span>
                            <h3 class="text-xl font-bold text-amber-700 font-heading">1. Personal Private Chef</h3>
                            <p class="text-xs text-amber-900/60 mt-1 font-semibold">Tap to flip 🔄</p>
                        </div>
                        <div class="backface-hidden rotate-y-180 absolute inset-0 bg-gradient-to-br from-amber-400 to-amber-500 text-white rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <p class="font-bold text-lg font-heading">Gourmet Cooking & Cheesecake 🍳🧀</p>
                            <p class="text-sm mt-2 font-medium">I will cook or bake for you on command. You are officially set for life.</p>
                        </div>
                    </div>
                </div>

                <!-- Card 2 -->
                <div class="perspective-1000 h-48 cursor-pointer group" onclick="flipCard(this)">
                    <div class="transform-style-3d relative w-full h-full rounded-2xl shadow-md hover:shadow-xl transition-shadow duration-300">
                        <div class="backface-hidden absolute inset-0 bg-white border-2 border-amber-200 rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-4xl mb-2">🎸</span>
                            <h3 class="text-xl font-bold text-amber-700 font-heading">2. Guitar Lessons & Jams</h3>
                            <p class="text-xs text-amber-900/60 mt-1 font-semibold">Tap to flip 🔄</p>
                        </div>
                        <div class="backface-hidden rotate-y-180 absolute inset-0 bg-gradient-to-br from-emerald-500 to-teal-600 text-white rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <p class="font-bold text-lg font-heading">Guitar Instructor 🎶</p>
                            <p class="text-sm mt-2 font-medium">Your personal instructor ready to teach you any song you wish, just like velvet rings.</p>
                        </div>
                    </div>
                </div>

                <!-- Card 3 -->
                <div class="perspective-1000 h-48 cursor-pointer group" onclick="flipCard(this)">
                    <div class="transform-style-3d relative w-full h-full rounded-2xl shadow-md hover:shadow-xl transition-shadow duration-300">
                        <div class="backface-hidden absolute inset-0 bg-white border-2 border-amber-200 rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-4xl mb-2">🦸‍♂️</span>
                            <h3 class="text-xl font-bold text-amber-700 font-heading">3. Certified Marvel Nerd</h3>
                            <p class="text-xs text-amber-900/60 mt-1 font-semibold">Tap to flip 🔄</p>
                        </div>
                        <div class="backface-hidden rotate-y-180 absolute inset-0 bg-gradient-to-br from-amber-500 to-orange-500 text-white rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <p class="font-bold text-lg font-heading">MCU Multiverse Duo ⚡</p>
                            <p class="text-sm mt-2 font-medium">We are huge Marvel nerds. Who else is going to debate MCU timelines, theories, and easter eggs with you for hours?</p>
                        </div>
                    </div>
                </div>

                <!-- Card 4 -->
                <div class="perspective-1000 h-48 cursor-pointer group" onclick="flipCard(this)">
                    <div class="transform-style-3d relative w-full h-full rounded-2xl shadow-md hover:shadow-xl transition-shadow duration-300">
                        <div class="backface-hidden absolute inset-0 bg-white border-2 border-amber-200 rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-4xl mb-2">🗣️</span>
                            <h3 class="text-xl font-bold text-amber-700 font-heading">4. Professional Gossip Duo</h3>
                            <p class="text-xs text-amber-900/60 mt-1 font-semibold">Tap to flip 🔄</p>
                        </div>
                        <div class="backface-hidden rotate-y-180 absolute inset-0 bg-gradient-to-br from-amber-400 to-yellow-500 text-white rounded-2xl p-6 flex flex-col justify-center items-center text-center">
                            <p class="font-bold text-lg font-heading">Bonded Over Bitching 🤫</p>
                            <p class="text-sm mt-2 font-medium">We literally started talking over Sausage Party & bitching about Riaan. If that's not the foundation of true love, what is?</p>
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <!-- MEMORY ESCAPE ROOM SECTION -->
        <section id="escape-room" class="my-12 bg-white/90 backdrop-blur-md rounded-3xl p-6 sm:p-10 border-4 border-amber-300 shadow-2xl relative">
            <div class="text-center mb-8">
                <span class="bg-amber-100 text-amber-800 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider">Interactive Vault Challenge</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-amber-800 mt-2 font-heading">
                    🔐 The Shared Memory Escape Room 🔐
                </h2>
                <p class="text-sm text-gray-600 mt-1 font-semibold">
                    Solve all 4 memory stages below to unlock the final question box!
                </p>
            </div>

            <!-- Progress Tracker -->
            <div class="flex items-center justify-between max-w-xs mx-auto mb-8 relative">
                <div class="absolute top-1/2 left-0 right-0 h-1 bg-amber-200 -translate-y-1/2 z-0"></div>
                <div id="progress-bar-fill" class="absolute top-1/2 left-0 h-1 bg-emerald-500 -translate-y-1/2 z-0 transition-all duration-500" style="width: 0%;"></div>
                
                <div id="step-dot-1" class="w-8 h-8 rounded-full bg-amber-500 text-white font-bold flex items-center justify-center relative z-10 font-heading">1</div>
                <div id="step-dot-2" class="w-8 h-8 rounded-full bg-amber-200 text-amber-800 font-bold flex items-center justify-center relative z-10 font-heading">2</div>
                <div id="step-dot-3" class="w-8 h-8 rounded-full bg-amber-200 text-amber-800 font-bold flex items-center justify-center relative z-10 font-heading">3</div>
                <div id="step-dot-4" class="w-8 h-8 rounded-full bg-amber-200 text-amber-800 font-bold flex items-center justify-center relative z-10 font-heading">4</div>
            </div>

            <!-- PUZZLE STAGE 1 -->
            <div id="puzzle-stage-1" class="puzzle-stage space-y-4">
                <div class="bg-amber-50 border-2 border-amber-200 rounded-2xl p-5 text-center">
                    <span class="text-4xl">🎪</span>
                    <h3 class="text-xl font-bold text-amber-800 font-heading mt-2">Stage 1: Where did our story first begin?</h3>
                    <p class="text-sm text-amber-900/70 font-semibold mt-1">Select where we first met:</p>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <button onclick="checkStage1('Coachella')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">A) Aujla Concert</button>
                    <button onclick="checkStage1('Rhapsody')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">B) Art Studio</button>
                    <button onclick="checkStage1('Woodstock')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">C) Recording Room</button>
                    <button onclick="checkStage1('Superbowl')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">D) Rhapsody</button>
                </div>
            </div>

            <!-- PUZZLE STAGE 2 -->
            <div id="puzzle-stage-2" class="puzzle-stage hidden space-y-4">
                <div class="bg-amber-50 border-2 border-amber-200 rounded-2xl p-5 text-center">
                    <span class="text-4xl">🎼</span>
                    <h3 class="text-xl font-bold text-amber-800 font-heading mt-2">Stage 2: Guitar Masterclass</h3>
                    <p class="text-sm text-amber-900/70 font-semibold mt-1">What was the very first song I taught you on guitar?</p>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <button onclick="checkStage2('Wonderwall')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">A) Wonderwall</button>
                    <button onclick="checkStage2('Velvet Rings')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">B) Velvet Rings 💍</button>
                    <button onclick="checkStage2('Hotel California')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">C) Hotel California</button>
                    <button onclick="checkStage2('Fool')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">D) Fool by Djo</button>
                </div>
            </div>

            <!-- PUZZLE STAGE 3 -->
            <div id="puzzle-stage-3" class="puzzle-stage hidden space-y-4">
                <div class="bg-amber-50 border-2 border-amber-200 rounded-2xl p-5 text-center">
                    <span class="text-4xl">🍿</span>
                    <h3 class="text-xl font-bold text-amber-800 font-heading mt-2">Stage 3: Movie Night Trivia</h3>
                    <p class="text-sm text-amber-900/70 font-semibold mt-1">Which was the very first movie we watched together?</p>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <button onclick="checkStage3('To All the Boys I have loved before')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">A) To All The Boys I Have Loved Before 💌</button>
                    <button onclick="checkStage3('Sausage Party')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">B) Sausage Party</button>
                    <button onclick="checkStage3('Titanic')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">C) Kim's Convenience</button>
                    <button onclick="checkStage3('Shrek 2')" class="p-4 bg-white hover:bg-amber-100 border-2 border-amber-200 rounded-xl font-bold text-amber-800 transition">D) Dune</button>
                </div>
            </div>

            <!-- PUZZLE STAGE 4 -->
            <div id="puzzle-stage-4" class="puzzle-stage hidden space-y-4">
                <div class="bg-amber-50 border-2 border-amber-200 rounded-2xl p-5 text-center">
                    <span class="text-4xl">🗣️</span>
                    <h3 class="text-xl font-bold text-amber-800 font-heading mt-2">Stage 4: Inside Joke Cipher</h3>
                    <p class="text-sm text-amber-900/70 font-semibold mt-1">Complete our mandatory daily vocabulary catchphrases:</p>
                </div>
                <div class="space-y-3 max-w-md mx-auto">
                    <div class="flex items-center gap-2">
                        <span class="font-bold text-amber-800 font-heading">Phrase 1:</span>
                        <input type="text" id="catchphrase-1" placeholder="Type: yea yea" class="w-full px-4 py-2 border-2 border-amber-300 rounded-xl font-bold text-amber-900 focus:outline-none focus:border-amber-500">
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="font-bold text-amber-800 font-heading">Phrase 2:</span>
                        <input type="text" id="catchphrase-2" placeholder="Type: khrayzzee" class="w-full px-4 py-2 border-2 border-amber-300 rounded-xl font-bold text-amber-900 focus:outline-none focus:border-amber-500">
                    </div>
                    <button onclick="checkStage4()" class="w-full py-3 bg-amber-500 hover:bg-amber-600 text-white font-extrabold rounded-xl shadow-lg font-heading text-lg transition">
                        Unlock Proposal Vault 🔓
                    </button>
                </div>
            </div>

            <!-- PUZZLE FEEDBACK MESSAGE -->
            <div id="puzzle-feedback" class="mt-4 text-center font-bold text-sm min-h-[24px]"></div>
            
        </section>

        <!-- PROPOSAL SECTION (LOCKED INITIALLY) -->
        <section id="proposal-section" class="my-16 text-center relative min-h-[300px] flex flex-col items-center justify-center bg-gradient-to-b from-amber-100/80 to-amber-200/60 p-8 rounded-3xl border-4 border-amber-300 shadow-xl opacity-50 pointer-events-none transition-all duration-700">
            
            <div id="lock-overlay" class="absolute inset-0 bg-amber-900/10 backdrop-blur-sm rounded-3xl flex flex-col items-center justify-center z-20 transition-opacity">
                <span class="text-6xl mb-2 animate-bounce">🔒</span>
                <p class="font-extrabold text-amber-900 text-xl font-heading bg-white/90 px-6 py-2 rounded-full shadow-lg">
                    Complete the Escape Room above to unlock this box!
                </p>
            </div>

            <h2 class="text-3xl sm:text-5xl font-extrabold text-amber-800 mb-8 font-heading">
                So... What Do You Say? 🍍
            </h2>

            <div class="flex flex-col sm:flex-row items-center justify-center gap-6 w-full max-w-lg relative min-h-[100px]" id="button-container">
                
                <!-- YES BUTTON -->
                <button id="yes-btn" onclick="handleYesClick()" class="w-full sm:w-auto px-10 py-5 bg-gradient-to-r from-emerald-500 to-emerald-600 hover:from-emerald-600 hover:to-emerald-700 text-white font-extrabold text-2xl rounded-2xl shadow-xl hover:shadow-2xl transform hover:-translate-y-1 transition-all duration-200 font-heading border-b-4 border-emerald-700 active:translate-y-0 cursor-pointer">
                    YES! 💛
                </button>

                <!-- NO BUTTON (EVASIVE) -->
                <button id="no-btn" onmouseover="dodgeNoButton()" onclick="dodgeNoButton()" class="w-full sm:w-auto px-8 py-4 bg-gray-200 hover:bg-gray-300 text-gray-700 font-bold text-lg rounded-2xl shadow transition-all duration-200 font-heading border-b-4 border-gray-400 cursor-pointer">
                    No 😅
                </button>

            </div>
            
            <p id="no-hint" class="text-xs text-amber-800/80 mt-6 hidden font-bold">Hint: The "No" button seems to be very afraid of commitment!</p>
        </section>

    </main>

    <!-- SUCCESS MODAL -->
    <div id="success-modal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden opacity-0 transition-opacity duration-300">
        <div class="bg-white border-4 border-amber-300 rounded-3xl p-8 max-w-md w-full text-center shadow-2xl transform scale-90 transition-transform duration-300" id="modal-card">
            <div class="text-7xl mb-4 animate-bounce">🎉 🍍 🎉</div>
            <h3 class="text-3xl font-extrabold text-amber-700 font-heading mb-2">YES! Yea Yea! Khrayzzee!</h3>
            <p class="text-gray-700 text-lg mb-6 font-semibold leading-relaxed">
                You passed the memory test & said YES! More cheesecake, Late nights, Watching movies together, and always being there for each other! ✨
            </p>
            
            <a id="text-link" href="#" target="_blank" class="inline-block w-full py-4 bg-emerald-500 hover:bg-emerald-600 text-white font-bold text-lg rounded-xl shadow-lg transition-colors font-heading mb-3">
                Send Me A Text 📱
            </a>

            <button onclick="closeModal()" class="text-xs text-amber-800/60 hover:underline font-semibold">
                Close
            </button>
        </div>
    </div>

    <script>
        /* 1. Global Card Flip Handler */
        function flipCard(card) {
            if (card) {
                card.classList.toggle('card-flipped');
            }
        }

        /* 2. Audio Control for "Fool - Djo" */
        let isPlaying = false;
        function toggleMusic() {
            const music = document.getElementById('bg-music');
            const btn = document.getElementById('music-toggle-btn');
            const status = document.getElementById('music-status');

            if (isPlaying) {
                music.pause();
                btn.innerText = '▶';
                status.innerText = 'Click to play background vibe';
                isPlaying = false;
            } else {
                music.play().then(() => {
                    btn.innerText = '⏸';
                    status.innerText = 'Playing: Fool — Djo 🎵';
                    isPlaying = true;
                }).catch(e => {
                    status.innerText = 'Tap again to allow audio playback';
                });
            }
        }

        /* 3. Floating Background Particles */
        function createParticles() {
            const container = document.getElementById('particle-container');
            const items = ['🍍', '🎸', '💛', '🧀', '🍿', '👑'];
            for (let i = 0; i < 20; i++) {
                const el = document.createElement('div');
                el.className = 'bg-particle';
                el.innerText = items[Math.floor(Math.random() * items.length)];
                el.style.left = Math.random() * 100 + 'vw';
                el.style.top = Math.random() * 100 + 'vh';
                el.style.fontSize = (Math.random() * 20 + 20) + 'px';
                el.style.animationDuration = (Math.random() * 5 + 4) + 's';
                el.style.animationDelay = (Math.random() * 3) + 's';
                container.appendChild(el);
            }
        }

        /* 4. Memory Escape Room Logic */
        let currentStage = 1;

        function setPuzzleFeedback(msg, isError = false) {
            const fb = document.getElementById('puzzle-feedback');
            fb.innerText = msg;
            fb.className = `mt-4 text-center font-bold text-sm min-h-[24px] ${isError ? 'text-red-500' : 'text-emerald-600'}`;
        }

        function checkStage1(answer) {
            if (answer === 'Rhapsody') {
                setPuzzleFeedback('✨ Correct! We first met in the art studio! Stage 1 cleared.');
                advanceStage(2, '25%');
            } else {
                setPuzzleFeedback('❌ Nope! Try remembering our absolute first encounter!', true);
            }
        }

        function checkStage2(answer) {
            if (answer === 'Velvet Rings') {
                setPuzzleFeedback('✨ Correct! Velvet Rings on guitar! Stage 2 cleared.');
                advanceStage(3, '50%');
            } else {
                setPuzzleFeedback('❌ Nope! Though Djo is playing, that was not the first guitar song!', true);
            }
        }

        function checkStage3(answer) {
            if (answer === 'To All the Boys I have loved before') {
                setPuzzleFeedback('✨ Correct! To All The Boys I Have Loved Before! Stage 3 cleared.');
                advanceStage(4, '75%');
            } else {
                setPuzzleFeedback('❌ Wrong movie choice! Hint: It involves letters and high school romance.', true);
            }
        }

        function checkStage4() {
            const p1 = document.getElementById('catchphrase-1').value.trim().toLowerCase();
            const p2 = document.getElementById('catchphrase-2').value.trim().toLowerCase();

            if ((p1.includes('yea') || p1.includes('yeah')) && (p2.includes('khrayzzee') || p2.includes('crazy') || p2.includes('khrayzee'))) {
                setPuzzleFeedback('🎉 ALL STAGES CLEARED! Vault Unlocked!');
                document.getElementById('progress-bar-fill').style.width = '100%';
                document.getElementById('step-dot-4').className = 'w-8 h-8 rounded-full bg-emerald-500 text-white font-bold flex items-center justify-center relative z-10 font-heading';
                
                // Unlock Proposal Section
                setTimeout(() => {
                    const overlay = document.getElementById('lock-overlay');
                    const propSec = document.getElementById('proposal-section');
                    overlay.classList.add('opacity-0');
                    setTimeout(() => { overlay.remove(); }, 400);
                    propSec.classList.remove('opacity-50', 'pointer-events-none');
                    propSec.classList.add('glow-active');
                    propSec.scrollIntoView({ behavior: 'smooth' });
                }, 600);
            } else {
                setPuzzleFeedback('❌ Make sure you spell "yea yea" and "khrayzzee" properly!', true);
            }
        }

        function advanceStage(nextStage, progressWidth) {
            document.getElementById(`puzzle-stage-${currentStage}`).classList.add('hidden');
            document.getElementById(`puzzle-stage-${nextStage}`).classList.remove('hidden');
            
            document.getElementById(`step-dot-${currentStage}`).className = 'w-8 h-8 rounded-full bg-emerald-500 text-white font-bold flex items-center justify-center relative z-10 font-heading';
            document.getElementById(`step-dot-${nextStage}`).className = 'w-8 h-8 rounded-full bg-amber-500 text-white font-bold flex items-center justify-center relative z-10 font-heading';
            document.getElementById('progress-bar-fill').style.width = progressWidth;
            
            currentStage = nextStage;
        }

        /* 5. Evasive "NO" Button Handler */
        let dodgeCount = 0;
        const noPhrases = [
            "Are you sure?",
            "Think again!",
            "Try again 😉",
            "Almost got it!",
            "Nice try!",
            "Definitely YES!"
        ];

        function dodgeNoButton() {
            const noBtn = document.getElementById('no-btn');
            const yesBtn = document.getElementById('yes-btn');
            const hint = document.getElementById('no-hint');

            dodgeCount++;
            hint.classList.remove('hidden');

            // Make YES button grow larger each time
            const currentScale = 1 + (dodgeCount * 0.12);
            yesBtn.style.transform = `scale(${Math.min(currentScale, 1.6)})`;

            // Make NO button shrink & jump position
            const shrinkScale = Math.max(0.85 - (dodgeCount * 0.08), 0.4);
            const randomX = (Math.random() - 0.5) * 240;
            const randomY = (Math.random() - 0.5) * 160;

            noBtn.style.transform = `translate(${randomX}px, ${randomY}px) scale(${shrinkScale})`;
            noBtn.innerText = noPhrases[Math.min(dodgeCount - 1, noPhrases.length - 1)];
        }

        /* 6. Sound Chime using Web Audio API */
        function playJoyfulTone() {
            try {
                const AudioCtx = window.AudioContext || window.webkitAudioContext;
                if (!AudioCtx) return;
                const ctx = new AudioCtx();
                
                const notes = [523.25, 659.25, 783.99, 1046.50]; // C5, E5, G5, C6
                notes.forEach((freq, i) => {
                    const osc = ctx.createOscillator();
                    const gain = ctx.createGain();
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(freq, ctx.currentTime + i * 0.12);
                    
                    gain.gain.setValueAtTime(0.2, ctx.currentTime + i * 0.12);
                    gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + i * 0.12 + 0.4);
                    
                    osc.connect(gain);
                    gain.connect(ctx.destination);
                    
                    osc.start(ctx.currentTime + i * 0.12);
                    osc.stop(ctx.currentTime + i * 0.12 + 0.45);
                });
            } catch(e) {
                console.log('Audio Context error ignored');
            }
        }

        /* 7. Celebratory Confetti and Modal Trigger */
        function handleYesClick() {
            playJoyfulTone();

            // Trigger Confetti explosion
            if (window.confetti) {
                confetti({
                    particleCount: 120,
                    spread: 80,
                    origin: { y: 0.6 },
                    colors: ['#f59e0b', '#10b981', '#fcd34d', '#ffffff', '#fbbf24']
                });

                setTimeout(() => {
                    confetti({
                        particleCount: 60,
                        angle: 60,
                        spread: 55,
                        origin: { x: 0 }
                    });
                    confetti({
                        particleCount: 60,
                        angle: 120,
                        spread: 55,
                        origin: { x: 1 }
                    });
                }, 250);
            }

            // Setup WhatsApp / SMS message link
            const message = encodeURIComponent("I passed the escape room and I said YES! Yea yea khrayzzee! 🍍💛✨");
            const textLink = document.getElementById('text-link');
            textLink.href = `https://wa.me/?text=${message}`;

            // Show Modal
            const modal = document.getElementById('success-modal');
            const modalCard = document.getElementById('modal-card');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modalCard.classList.remove('scale-90');
                modalCard.classList.add('scale-100');
            }, 20);
        }

        function closeModal() {
            const modal = document.getElementById('success-modal');
            const modalCard = document.getElementById('modal-card');
            modal.classList.add('opacity-0');
            modalCard.classList.remove('scale-100');
            modalCard.classList.add('scale-90');
            setTimeout(() => {
                modal.classList.add('hidden');
            }, 300);
        }

        // Initialize particles on load
        window.onload = function() {
            createParticles();
        };
    </script>
</body>
</html>
