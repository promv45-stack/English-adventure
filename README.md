<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>English Adventure 🌟</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&family=Fredoka+One&display=swap');

  :root {
    --sky: #4FC3F7;
    --sun: #FFD54F;
    --grass: #66BB6A;
    --coral: #FF7043;
    --purple: #AB47BC;
    --white: #FFFFFF;
    --dark: #2D3436;
    --light-bg: #F0F9FF;
    --card-bg: #FFFFFF;
    --shadow: 0 4px 20px rgba(0,0,0,0.12);
    --radius: 20px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Nunito', sans-serif;
    background: linear-gradient(160deg, #e0f7fa 0%, #f3e5f5 100%);
    min-height: 100vh;
    color: var(--dark);
  }

  /* ── HEADER ── */
  .header {
    background: linear-gradient(135deg, #4FC3F7, #AB47BC);
    padding: 16px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 4px 15px rgba(79,195,247,0.4);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .header h1 {
    font-family: 'Fredoka One', cursive;
    font-size: 1.5rem;
    color: white;
    text-shadow: 2px 2px 0px rgba(0,0,0,0.15);
  }
  .stars-display {
    background: rgba(255,255,255,0.25);
    border-radius: 30px;
    padding: 6px 14px;
    color: white;
    font-weight: 800;
    font-size: 1rem;
    display: flex;
    align-items: center;
    gap: 5px;
  }

  /* ── NAV ── */
  .nav {
    display: flex;
    background: white;
    box-shadow: 0 2px 10px rgba(0,0,0,0.08);
    overflow-x: auto;
    scrollbar-width: none;
  }
  .nav::-webkit-scrollbar { display: none; }
  .nav-btn {
    flex: 1;
    min-width: 80px;
    padding: 12px 8px;
    border: none;
    background: transparent;
    font-family: 'Nunito', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    color: #999;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    transition: all 0.2s;
    border-bottom: 3px solid transparent;
  }
  .nav-btn.active {
    color: var(--purple);
    border-bottom-color: var(--purple);
  }
  .nav-btn span.icon { font-size: 1.3rem; }

  /* ── SCREENS ── */
  .screen { display: none; padding: 16px; animation: fadeIn 0.3s ease; }
  .screen.active { display: block; }
  @keyframes fadeIn { from { opacity:0; transform:translateY(8px); } to { opacity:1; transform:none; } }

  /* ── HOME ── */
  .welcome-card {
    background: linear-gradient(135deg, #4FC3F7, #0288D1);
    border-radius: var(--radius);
    padding: 24px 20px;
    color: white;
    margin-bottom: 20px;
    position: relative;
    overflow: hidden;
  }
  .welcome-card::after {
    content: '🌍';
    font-size: 5rem;
    position: absolute;
    right: -10px;
    top: -10px;
    opacity: 0.3;
  }
  .welcome-card h2 {
    font-family: 'Fredoka One', cursive;
    font-size: 1.6rem;
    margin-bottom: 6px;
  }
  .welcome-card p { font-size: 0.9rem; opacity: 0.9; }

  .section-title {
    font-family: 'Fredoka One', cursive;
    font-size: 1.1rem;
    color: var(--dark);
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .modules-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 20px;
  }
  .module-card {
    background: white;
    border-radius: var(--radius);
    padding: 16px 12px;
    text-align: center;
    box-shadow: var(--shadow);
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    border-bottom: 4px solid transparent;
    position: relative;
    overflow: hidden;
  }
  .module-card:active { transform: scale(0.97); }
  .module-card .emoji { font-size: 2.2rem; margin-bottom: 8px; }
  .module-card h3 { font-size: 0.85rem; font-weight: 800; color: var(--dark); margin-bottom: 4px; }
  .module-card .level-badge {
    font-size: 0.65rem;
    font-weight: 700;
    padding: 2px 8px;
    border-radius: 20px;
    color: white;
    display: inline-block;
  }
  .module-card .progress-bar-wrap {
    background: #eee;
    border-radius: 10px;
    height: 6px;
    margin-top: 8px;
    overflow: hidden;
  }
  .module-card .progress-fill {
    height: 100%;
    border-radius: 10px;
    transition: width 0.5s;
  }
  .m1 { border-bottom-color: #FF7043; }
  .m1 .level-badge { background: #FF7043; }
  .m1 .progress-fill { background: #FF7043; }
  .m2 { border-bottom-color: #66BB6A; }
  .m2 .level-badge { background: #66BB6A; }
  .m2 .progress-fill { background: #66BB6A; }
  .m3 { border-bottom-color: #4FC3F7; }
  .m3 .level-badge { background: #4FC3F7; }
  .m3 .progress-fill { background: #4FC3F7; }
  .m4 { border-bottom-color: #AB47BC; }
  .m4 .level-badge { background: #AB47BC; }
  .m4 .progress-fill { background: #AB47BC; }

  /* ── QUIZ ── */
  .quiz-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }
  .back-btn {
    background: white;
    border: none;
    width: 38px;
    height: 38px;
    border-radius: 50%;
    font-size: 1.1rem;
    cursor: pointer;
    box-shadow: var(--shadow);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .quiz-topic-title {
    font-family: 'Fredoka One', cursive;
    font-size: 1.2rem;
    color: var(--dark);
  }

  .progress-strip {
    background: #e0e0e0;
    border-radius: 10px;
    height: 10px;
    margin-bottom: 6px;
    overflow: hidden;
  }
  .progress-strip-fill {
    height: 100%;
    border-radius: 10px;
    background: linear-gradient(90deg, #4FC3F7, #AB47BC);
    transition: width 0.4s;
  }
  .progress-label {
    font-size: 0.75rem;
    color: #888;
    font-weight: 700;
    margin-bottom: 20px;
    text-align: right;
  }

  .question-card {
    background: white;
    border-radius: var(--radius);
    padding: 24px 20px;
    box-shadow: var(--shadow);
    margin-bottom: 18px;
    text-align: center;
  }
  .question-emoji { font-size: 3rem; margin-bottom: 10px; }
  .question-text {
    font-size: 1.1rem;
    font-weight: 800;
    color: var(--dark);
    line-height: 1.4;
  }
  .question-hint {
    font-size: 0.8rem;
    color: #aaa;
    margin-top: 8px;
  }

  .options-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 16px;
  }
  .option-btn {
    background: white;
    border: 3px solid #E0E0E0;
    border-radius: 16px;
    padding: 14px 10px;
    font-family: 'Nunito', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    color: var(--dark);
  }
  .option-btn:active { transform: scale(0.96); }
  .option-btn.correct { background: #E8F5E9; border-color: #66BB6A; color: #2E7D32; }
  .option-btn.wrong { background: #FFEBEE; border-color: #EF5350; color: #C62828; }
  .option-btn.disabled { pointer-events: none; opacity: 0.6; }

  .feedback-box {
    border-radius: 16px;
    padding: 14px 16px;
    text-align: center;
    font-weight: 800;
    font-size: 1rem;
    margin-bottom: 16px;
    display: none;
    animation: popIn 0.3s ease;
  }
  @keyframes popIn {
    from { transform: scale(0.8); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }
  .feedback-box.correct { background: #E8F5E9; color: #2E7D32; }
  .feedback-box.wrong { background: #FFEBEE; color: #C62828; }

  .next-btn {
    width: 100%;
    background: linear-gradient(135deg, #AB47BC, #7B1FA2);
    color: white;
    border: none;
    border-radius: 16px;
    padding: 16px;
    font-family: 'Fredoka One', cursive;
    font-size: 1.1rem;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(171,71,188,0.4);
    display: none;
    transition: transform 0.15s;
  }
  .next-btn:active { transform: scale(0.98); }

  /* ── RESULT ── */
  .result-screen {
    text-align: center;
    padding: 30px 20px;
  }
  .result-emoji { font-size: 4rem; margin-bottom: 16px; }
  .result-title {
    font-family: 'Fredoka One', cursive;
    font-size: 1.8rem;
    margin-bottom: 10px;
    color: var(--dark);
  }
  .result-score {
    font-size: 3rem;
    font-weight: 900;
    color: var(--purple);
    margin-bottom: 10px;
  }
  .result-msg { color: #666; font-size: 0.95rem; margin-bottom: 24px; }
  .stars-row { font-size: 2rem; margin-bottom: 24px; letter-spacing: 4px; }
  .result-btns { display: flex; flex-direction: column; gap: 10px; }
  .btn-primary {
    background: linear-gradient(135deg, #AB47BC, #7B1FA2);
    color: white;
    border: none;
    border-radius: 16px;
    padding: 15px;
    font-family: 'Fredoka One', cursive;
    font-size: 1rem;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(171,71,188,0.4);
  }
  .btn-secondary {
    background: white;
    color: var(--purple);
    border: 3px solid var(--purple);
    border-radius: 16px;
    padding: 14px;
    font-family: 'Fredoka One', cursive;
    font-size: 1rem;
    cursor: pointer;
  }

  /* ── PROGRESSION ── */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 10px;
    margin-bottom: 20px;
  }
  .stat-card {
    background: white;
    border-radius: 16px;
    padding: 14px 10px;
    text-align: center;
    box-shadow: var(--shadow);
  }
  .stat-card .stat-emoji { font-size: 1.5rem; margin-bottom: 4px; }
  .stat-card .stat-num {
    font-family: 'Fredoka One', cursive;
    font-size: 1.4rem;
    color: var(--purple);
  }
  .stat-card .stat-label { font-size: 0.65rem; color: #999; font-weight: 700; }

  .progress-module-list { display: flex; flex-direction: column; gap: 12px; }
  .progress-module-item {
    background: white;
    border-radius: 16px;
    padding: 14px 16px;
    box-shadow: var(--shadow);
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .pm-emoji { font-size: 1.8rem; }
  .pm-info { flex: 1; }
  .pm-name { font-weight: 800; font-size: 0.9rem; color: var(--dark); margin-bottom: 4px; }
  .pm-bar-wrap { background: #eee; border-radius: 10px; height: 8px; overflow: hidden; }
  .pm-bar { height: 100%; border-radius: 10px; transition: width 0.5s; }
  .pm-pct { font-size: 0.75rem; font-weight: 700; color: #888; white-space: nowrap; }

  /* ── BADGES ── */
  .badges-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 12px;
  }
  .badge-card {
    background: white;
    border-radius: 16px;
    padding: 16px 10px;
    text-align: center;
    box-shadow: var(--shadow);
    transition: transform 0.2s;
  }
  .badge-card.locked { opacity: 0.4; filter: grayscale(1); }
  .badge-card .badge-emoji { font-size: 2rem; margin-bottom: 6px; }
  .badge-card .badge-name { font-size: 0.7rem; font-weight: 800; color: var(--dark); }
  .badge-card .badge-desc { font-size: 0.6rem; color: #aaa; margin-top: 2px; }

  /* ── LEÇON ── */
  .lesson-card {
    background: white;
    border-radius: var(--radius);
    padding: 20px;
    box-shadow: var(--shadow);
    margin-bottom: 14px;
  }
  .lesson-card h3 {
    font-family: 'Fredoka One', cursive;
    font-size: 1.1rem;
    margin-bottom: 12px;
    color: var(--dark);
  }
  .vocab-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px;
    background: var(--light-bg);
    border-radius: 12px;
    margin-bottom: 8px;
    cursor: pointer;
    transition: transform 0.15s;
  }
  .vocab-item:active { transform: scale(0.98); }
  .vocab-emoji { font-size: 1.6rem; }
  .vocab-en { font-weight: 800; font-size: 0.95rem; color: var(--dark); }
  .vocab-fr { font-size: 0.8rem; color: #888; }
  .vocab-audio { margin-left: auto; font-size: 1.2rem; }

  /* Confetti */
  .confetti-container {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 999;
    overflow: hidden;
  }
  .confetti-piece {
    position: absolute;
    width: 10px;
    height: 10px;
    border-radius: 2px;
    animation: confettiFall linear forwards;
  }
  @keyframes confettiFall {
    0% { transform: translateY(-20px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
  }
</style>
</head>
<body>

<!-- Header -->
<div class="header">
  <h1>🌟 English Adventure</h1>
  <div class="stars-display">⭐ <span id="totalStars">0</span></div>
</div>

<!-- Nav -->
<nav class="nav">
  <button class="nav-btn active" onclick="showScreen('home')" id="nav-home">
    <span class="icon">🏠</span>Accueil
  </button>
  <button class="nav-btn" onclick="showScreen('lessons')" id="nav-lessons">
    <span class="icon">📚</span>Leçons
  </button>
  <button class="nav-btn" onclick="showScreen('quiz')" id="nav-quiz">
    <span class="icon">🎯</span>Quiz
  </button>
  <button class="nav-btn" onclick="showScreen('progress')" id="nav-progress">
    <span class="icon">📈</span>Progrès
  </button>
  <button class="nav-btn" onclick="showScreen('badges')" id="nav-badges">
    <span class="icon">🏆</span>Badges
  </button>
</nav>

<!-- Confetti -->
<div class="confetti-container" id="confettiContainer"></div>

<!-- ════ SCREEN: HOME ════ -->
<div class="screen active" id="screen-home">
  <div class="welcome-card">
    <h2>Hello, Champion ! 👋</h2>
    <p>Apprends l'anglais en t'amusant et prépare ton entrée au collège !</p>
  </div>

  <div class="section-title">🎮 Modules</div>
  <div class="modules-grid">
    <div class="module-card m1" onclick="startModule(0)">
      <div class="emoji">🐾</div>
      <h3>Les Animaux</h3>
      <span class="level-badge">Débutant</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-0" style="width:0%"></div>
      </div>
    </div>
    <div class="module-card m2" onclick="startModule(1)">
      <div class="emoji">🎨</div>
      <h3>Les Couleurs</h3>
      <span class="level-badge">Débutant</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-1" style="width:0%"></div>
      </div>
    </div>
    <div class="module-card m3" onclick="startModule(2)">
      <div class="emoji">🏫</div>
      <h3>L'École</h3>
      <span class="level-badge">Intermédiaire</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-2" style="width:0%"></div>
      </div>
    </div>
    <div class="module-card m4" onclick="startModule(3)">
      <div class="emoji">🔢</div>
      <h3>Les Nombres</h3>
      <span class="level-badge">Intermédiaire</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-3" style="width:0%"></div>
      </div>
    </div>
    <div class="module-card m1" onclick="startModule(4)">
      <div class="emoji">👨‍👩‍👧</div>
      <h3>La Famille</h3>
      <span class="level-badge">Intermédiaire</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-4" style="width:0%"></div>
      </div>
    </div>
    <div class="module-card m2" onclick="startModule(5)">
      <div class="emoji">📖</div>
      <h3>Grammaire</h3>
      <span class="level-badge">Collège</span>
      <div class="progress-bar-wrap">
        <div class="progress-fill" id="mod-prog-5" style="width:0%"></div>
      </div>
    </div>
  </div>
</div>

<!-- ════ SCREEN: LESSONS ════ -->
<div class="screen" id="screen-lessons">
  <div class="section-title">📚 Leçons du jour</div>
  <div class="lesson-card">
    <h3>🐾 Animaux — Animals</h3>
    <div class="vocab-item" onclick="speak('dog')">
      <span class="vocab-emoji">🐶</span>
      <div><div class="vocab-en">Dog</div><div class="vocab-fr">Un chien</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('cat')">
      <span class="vocab-emoji">🐱</span>
      <div><div class="vocab-en">Cat</div><div class="vocab-fr">Un chat</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('bird')">
      <span class="vocab-emoji">🐦</span>
      <div><div class="vocab-en">Bird</div><div class="vocab-fr">Un oiseau</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('horse')">
      <span class="vocab-emoji">🐴</span>
      <div><div class="vocab-en">Horse</div><div class="vocab-fr">Un cheval</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('elephant')">
      <span class="vocab-emoji">🐘</span>
      <div><div class="vocab-en">Elephant</div><div class="vocab-fr">Un éléphant</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
  </div>
  <div class="lesson-card">
    <h3>🎨 Couleurs — Colors</h3>
    <div class="vocab-item" onclick="speak('red')">
      <span class="vocab-emoji">🔴</span>
      <div><div class="vocab-en">Red</div><div class="vocab-fr">Rouge</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('blue')">
      <span class="vocab-emoji">🔵</span>
      <div><div class="vocab-en">Blue</div><div class="vocab-fr">Bleu</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('green')">
      <span class="vocab-emoji">🟢</span>
      <div><div class="vocab-en">Green</div><div class="vocab-fr">Vert</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('yellow')">
      <span class="vocab-emoji">🟡</span>
      <div><div class="vocab-en">Yellow</div><div class="vocab-fr">Jaune</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
  </div>
  <div class="lesson-card">
    <h3>🏫 À l'école — At School</h3>
    <div class="vocab-item" onclick="speak('pencil')">
      <span class="vocab-emoji">✏️</span>
      <div><div class="vocab-en">Pencil</div><div class="vocab-fr">Un crayon</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('book')">
      <span class="vocab-emoji">📚</span>
      <div><div class="vocab-en">Book</div><div class="vocab-fr">Un livre</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('teacher')">
      <span class="vocab-emoji">👩‍🏫</span>
      <div><div class="vocab-en">Teacher</div><div class="vocab-fr">Un professeur</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
    <div class="vocab-item" onclick="speak('classroom')">
      <span class="vocab-emoji">🏫</span>
      <div><div class="vocab-en">Classroom</div><div class="vocab-fr">Une salle de classe</div></div>
      <span class="vocab-audio">🔊</span>
    </div>
  </div>
</div>

<!-- ════ SCREEN: QUIZ ════ -->
<div class="screen" id="screen-quiz">
  <!-- Module Selector -->
  <div id="quiz-selector">
    <div class="section-title">🎯 Choisis un quiz !</div>
    <div class="modules-grid">
      <div class="module-card m1" onclick="startModule(0)">
        <div class="emoji">🐾</div><h3>Animaux</h3><span class="level-badge">5 questions</span>
      </div>
      <div class="module-card m2" onclick="startModule(1)">
        <div class="emoji">🎨</div><h3>Couleurs</h3><span class="level-badge">5 questions</span>
      </div>
      <div class="module-card m3" onclick="startModule(2)">
        <div class="emoji">🏫</div><h3>L'École</h3><span class="level-badge">5 questions</span>
      </div>
      <div class="module-card m4" onclick="startModule(3)">
        <div class="emoji">🔢</div><h3>Nombres</h3><span class="level-badge">5 questions</span>
      </div>
      <div class="module-card m1" onclick="startModule(4)">
        <div class="emoji">👨‍👩‍👧</div><h3>Famille</h3><span class="level-badge">5 questions</span>
      </div>
      <div class="module-card m2" onclick="startModule(5)">
        <div class="emoji">📖</div><h3>Grammaire</h3><span class="level-badge">5 questions</span>
      </div>
    </div>
  </div>

  <!-- Quiz Active -->
  <div id="quiz-active" style="display:none">
    <div class="quiz-header">
      <button class="back-btn" onclick="exitQuiz()">←</button>
      <div class="quiz-to
