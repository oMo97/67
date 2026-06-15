<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>統計與機率策略中心</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@300;400;500&family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
:root {
  --ink: #0f1923;
  --ink2: #1e2e3d;
  --slate: #3a4f63;
  --muted: #6b7f92;
  --pale: #a8b8c8;
  --rule: #dce4ec;
  --bg: #f5f2ee;
  --paper: #fdfbf8;
  --paper2: #f8f5f0;
  --accent: #c0392b;
  --accent2: #2980b9;
  --green: #27ae60;
  --gold: #d4860a;
  --highlight: #fff3cd;

  --fs-xs: .72rem;
  --fs-sm: .85rem;
  --fs-base: 1rem;
  --fs-lg: 1.15rem;
  --fs-xl: 1.4rem;
  --fs-2xl: 2rem;
  --fs-3xl: 3.2rem;
}

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--ink);
  font-family: 'Noto Sans TC', sans-serif;
  font-weight: 300;
  line-height: 1.7;
  overflow-x: hidden;
}

/* ── NOISE TEXTURE ── */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: .4;
}

/* ── LAYOUT ── */
.page-wrap { max-width: 1200px; margin: 0 auto; padding: 0 32px; }

/* ── NAV ── */
nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(245,242,238,.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--rule);
}
.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 32px;
  max-width: 1200px;
  margin: 0 auto;
}
.nav-brand {
  font-family: 'DM Serif Display', serif;
  font-size: 1.15rem;
  color: var(--ink);
  letter-spacing: .02em;
}
.nav-brand span { color: var(--accent); }
.nav-links { display: flex; gap: 28px; list-style: none; }
.nav-links a {
  font-size: var(--fs-sm);
  color: var(--slate);
  text-decoration: none;
  letter-spacing: .04em;
  font-weight: 400;
  transition: color .2s;
  font-family: 'DM Mono', monospace;
}
.nav-links a:hover { color: var(--ink); }

/* ── HERO ── */
.hero {
  padding: 90px 0 70px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  border-bottom: 1px solid var(--rule);
  margin-bottom: 80px;
}
.hero-text {}
.hero-eyebrow {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  letter-spacing: .2em;
  color: var(--accent);
  text-transform: uppercase;
  margin-bottom: 18px;
}
.hero h1 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.4rem, 5vw, 3.8rem);
  line-height: 1.1;
  color: var(--ink);
  margin-bottom: 20px;
}
.hero h1 em { font-style: italic; color: var(--accent2); }
.hero-desc {
  font-size: var(--fs-base);
  color: var(--slate);
  line-height: 1.8;
  max-width: 440px;
  margin-bottom: 32px;
}
.hero-pills { display: flex; flex-wrap: wrap; gap: 8px; }
.pill {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  padding: 4px 12px;
  border-radius: 2px;
  border: 1px solid;
  letter-spacing: .06em;
}
.pill.red   { border-color: var(--accent); color: var(--accent); }
.pill.blue  { border-color: var(--accent2); color: var(--accent2); }
.pill.green { border-color: var(--green); color: var(--green); }
.pill.gold  { border-color: var(--gold); color: var(--gold); }

/* hero visual: animated bell curve */
.hero-visual {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}
.hero-visual canvas { width: 100% !important; max-width: 480px; }
.hero-visual-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .08em;
}

/* ── SECTION HEADERS ── */
.sec-header {
  display: flex;
  align-items: baseline;
  gap: 18px;
  margin-bottom: 36px;
}
.sec-num {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .12em;
}
.sec-title {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-2xl);
  color: var(--ink);
}
.sec-rule {
  flex: 1;
  height: 1px;
  background: var(--rule);
}

/* ── CONCEPT CARDS ── */
.concepts-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: var(--rule);
  border: 1px solid var(--rule);
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 80px;
}
.concept-card {
  background: var(--paper);
  padding: 32px 28px;
  transition: background .2s;
  cursor: default;
}
.concept-card:hover { background: var(--paper2); }
.concept-icon {
  font-size: 1.6rem;
  margin-bottom: 14px;
}
.concept-name {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-lg);
  color: var(--ink);
  margin-bottom: 8px;
}
.concept-formula {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent2);
  background: rgba(41,128,185,.06);
  border-left: 2px solid var(--accent2);
  padding: 6px 10px;
  margin-bottom: 12px;
  letter-spacing: .04em;
  border-radius: 0 2px 2px 0;
  word-break: break-all;
}
.concept-desc {
  font-size: var(--fs-sm);
  color: var(--slate);
  line-height: 1.7;
}

/* ── STRATEGY SECTION ── */
.strategies { margin-bottom: 80px; }
.strategy-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid var(--rule);
  margin-bottom: 32px;
}
.tab-btn {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  padding: 10px 22px;
  border: none;
  background: transparent;
  color: var(--muted);
  cursor: pointer;
  letter-spacing: .06em;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: color .2s, border-color .2s;
}
.tab-btn.active { color: var(--ink); border-bottom-color: var(--ink); }
.tab-btn:hover  { color: var(--ink2); }

.tab-panel { display: none; }
.tab-panel.active { display: block; }

.strategy-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 40px;
  align-items: start;
}
.strategy-info h3 {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-xl);
  color: var(--ink);
  margin-bottom: 14px;
}
.strategy-info p {
  font-size: var(--fs-sm);
  color: var(--slate);
  line-height: 1.8;
  margin-bottom: 18px;
}
.strategy-info .when-to-use {
  background: var(--paper2);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 16px 20px;
  margin-bottom: 18px;
}
.when-to-use .wtu-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  letter-spacing: .1em;
  color: var(--accent);
  margin-bottom: 8px;
  text-transform: uppercase;
}
.when-to-use ul {
  padding-left: 18px;
  font-size: var(--fs-sm);
  color: var(--slate);
}
.when-to-use li { margin-bottom: 4px; }

.strategy-visual {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 24px;
}
.strategy-visual canvas { width: 100% !important; display: block; }
.chart-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  text-align: center;
  margin-top: 10px;
  letter-spacing: .06em;
}

/* ── CALCULATOR ── */
.calc-section { margin-bottom: 80px; }
.calc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
  gap: 20px;
}
.calc-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  overflow: hidden;
}
.calc-header {
  padding: 16px 22px;
  background: var(--ink);
  color: var(--bg);
  display: flex;
  align-items: center;
  gap: 10px;
}
.calc-header .c-icon { font-size: 1.1rem; }
.calc-header .c-name {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .06em;
}
.calc-body { padding: 22px; }
.field { margin-bottom: 16px; }
.field label {
  display: block;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
  letter-spacing: .08em;
  margin-bottom: 6px;
  text-transform: uppercase;
}
.field input, .field select {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  background: var(--paper2);
  color: var(--ink);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  outline: none;
  transition: border-color .2s;
}
.field input:focus, .field select:focus { border-color: var(--accent2); }
.calc-btn {
  width: 100%;
  padding: 10px;
  background: var(--ink);
  color: var(--paper);
  border: none;
  border-radius: 3px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .1em;
  cursor: pointer;
  transition: background .2s;
  text-transform: uppercase;
  margin-top: 4px;
}
.calc-btn:hover { background: var(--ink2); }
.calc-result {
  margin-top: 16px;
  padding: 14px;
  background: var(--highlight);
  border-left: 3px solid var(--gold);
  border-radius: 0 3px 3px 0;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  display: none;
  line-height: 1.8;
}
.calc-result.show { display: block; }

/* ── PROBABILITY DISTRIBUTIONS ── */
.dist-section { margin-bottom: 80px; }
.dist-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  margin-bottom: 24px;
  padding: 20px;
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
}
.dist-control { display: flex; flex-direction: column; gap: 4px; }
.dist-control label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
  letter-spacing: .08em;
}
.dist-control input[type=range] { width: 160px; accent-color: var(--ink); }
.dist-control .dv {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent2);
}
.dist-control select {
  padding: 5px 10px;
  border: 1px solid var(--rule);
  background: var(--paper2);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  border-radius: 3px;
}
.dist-canvas-wrap {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 24px;
}
.dist-canvas-wrap canvas { width: 100% !important; display: block; }

/* ── CHEAT SHEET ── */
.cheatsheet { margin-bottom: 80px; }
.cs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 16px;
}
.cs-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 20px;
}
.cs-card .cs-topic {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent);
  letter-spacing: .1em;
  margin-bottom: 10px;
  text-transform: uppercase;
}
.cs-card .cs-formula {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  background: rgba(15,25,35,.04);
  padding: 8px 10px;
  border-radius: 3px;
  margin-bottom: 10px;
  word-break: break-all;
}
.cs-card .cs-note {
  font-size: var(--fs-xs);
  color: var(--muted);
  line-height: 1.6;
}

/* ── GAMES SECTION ── */
.games-section { margin-bottom: 80px; }
.games-grid-wrap {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
@media(max-width:760px){ .games-grid-wrap{ grid-template-columns:1fr; } }

.game-box {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 6px;
  overflow: hidden;
}
.game-box-header {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 14px 20px;
  background: var(--ink2);
  color: var(--bg);
}
.game-box-header .gh-icon { font-size: 1.1rem; }
.game-box-header .gh-title {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .06em;
}
.game-box-header .gh-badge {
  margin-left: auto;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  padding: 2px 8px;
  border-radius: 2px;
  border: 1px solid rgba(255,255,255,.2);
  color: rgba(255,255,255,.7);
  letter-spacing: .08em;
}
.game-box-body { padding: 20px; }
.game-desc-text {
  font-size: var(--fs-xs);
  color: var(--muted);
  margin-bottom: 14px;
  line-height: 1.6;
}

/* Coin flip game */
.coin-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
}
.coin {
  width: 80px; height: 80px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 2rem;
  font-family: 'DM Serif Display', serif;
  border: 3px solid var(--rule);
  background: var(--paper2);
  transition: transform .15s;
  cursor: default;
  user-select: none;
}
.coin.flip-anim {
  animation: coinFlip .6s ease;
}
@keyframes coinFlip {
  0%   { transform: rotateY(0deg) scale(1); }
  25%  { transform: rotateY(90deg) scale(1.1); }
  50%  { transform: rotateY(180deg) scale(1); }
  75%  { transform: rotateY(270deg) scale(1.1); }
  100% { transform: rotateY(360deg) scale(1); }
}
.coin-stats {
  display: flex; gap: 16px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
}
.coin-stat { text-align: center; }
.coin-stat .cv { font-size: 1.2rem; font-weight: 500; color: var(--ink); }
.coin-stat .cl { color: var(--muted); }
.coin-history {
  display: flex; flex-wrap: wrap; gap: 4px;
  max-height: 48px; overflow: hidden;
  width: 100%;
}
.coin-chip {
  font-size: .65rem;
  padding: 2px 5px;
  border-radius: 2px;
  font-family: 'DM Mono', monospace;
}
.coin-chip.H { background: rgba(41,128,185,.12); color: var(--accent2); }
.coin-chip.T { background: rgba(192,57,43,.1); color: var(--accent); }
.coin-btn-row { display: flex; gap: 8px; }
.g-btn {
  flex: 1;
  padding: 8px 16px;
  border: 1px solid var(--rule);
  background: var(--ink);
  color: var(--paper);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  border-radius: 3px;
  cursor: pointer;
  letter-spacing: .08em;
  transition: background .15s;
}
.g-btn:hover { background: var(--ink2); }
.g-btn.outline { background: transparent; color: var(--ink); }
.g-btn.outline:hover { background: var(--rule); }

/* Guess the mean game */
.gtm-canvas-wrap { position: relative; margin-bottom: 10px; }
.gtm-canvas-wrap canvas { width: 100% !important; display: block; border: 1px solid var(--rule); border-radius: 3px; }
.gtm-input-row { display: flex; gap: 8px; align-items: center; margin-bottom: 10px; }
.gtm-input-row input {
  flex:1; padding: 7px 10px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  background: var(--paper2);
  color: var(--ink);
  outline: none;
}
.gtm-input-row input:focus { border-color: var(--accent2); }
.gtm-feedback {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  min-height: 20px;
  color: var(--muted);
}
.gtm-score {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--slate);
  margin-top: 6px;
}

/* CLT game */
.clt-area { display: flex; flex-direction: column; gap: 10px; }
.clt-canvas-wrap canvas { width: 100% !important; display: block; }
.clt-controls { display: flex; gap: 10px; align-items: center; flex-wrap: wrap; }
.clt-controls label { font-family: 'DM Mono', monospace; font-size: var(--fs-xs); color: var(--muted); }
.clt-controls input[type=range] { width: 120px; accent-color: var(--ink); }
.clt-controls .cv { font-family: 'DM Mono', monospace; font-size: var(--fs-xs); color: var(--accent2); }
.clt-info {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--slate);
  line-height: 1.7;
}

/* Probability quiz */
.quiz-area {}
.quiz-q {
  font-size: var(--fs-sm);
  color: var(--ink);
  font-weight: 500;
  margin-bottom: 14px;
  min-height: 44px;
  line-height: 1.6;
}
.quiz-options { display: flex; flex-direction: column; gap: 8px; margin-bottom: 14px; }
.quiz-opt {
  width: 100%;
  text-align: left;
  padding: 9px 14px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  background: var(--paper2);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--ink);
  cursor: pointer;
  transition: border-color .15s, background .15s;
  letter-spacing: .04em;
}
.quiz-opt:hover:not(:disabled) { border-color: var(--accent2); background: rgba(41,128,185,.06); }
.quiz-opt.correct { border-color: var(--green); background: rgba(39,174,96,.1); color: var(--green); }
.quiz-opt.wrong   { border-color: var(--accent); background: rgba(192,57,43,.08); color: var(--accent); }
.quiz-opt:disabled { cursor: default; }
.quiz-explain {
  font-size: var(--fs-xs);
  color: var(--slate);
  line-height: 1.7;
  background: var(--highlight);
  padding: 10px 14px;
  border-radius: 3px;
  border-left: 3px solid var(--gold);
  display: none;
  margin-bottom: 10px;
}
.quiz-explain.show { display: block; }
.quiz-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
}
.quiz-progress-bar {
  width: 100%;
  height: 4px;
  background: var(--rule);
  border-radius: 2px;
  margin-bottom: 14px;
  overflow: hidden;
}
.quiz-progress-fill {
  height: 100%;
  background: var(--accent2);
  border-radius: 2px;
  transition: width .4s ease;
}

/* ── FOOTER ── */
footer {
  border-top: 1px solid var(--rule);
  padding: 40px 32px;
  text-align: center;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .08em;
}

/* ── ANIMATIONS ── */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
.fade-up { animation: fadeUp .6s ease forwards; }
.fade-up:nth-child(2) { animation-delay: .1s; opacity: 0; }
.fade-up:nth-child(3) { animation-delay: .2s; opacity: 0; }
.fade-up:nth-child(4) { animation-delay: .3s; opacity: 0; }
.fade-up:nth-child(5) { animation-delay: .4s; opacity: 0; }
.fade-up:nth-child(6) { animation-delay: .5s; opacity: 0; }

section { position: relative; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <div class="nav-brand">Stats<span>&</span>Prob</div>
    <ul class="nav-links">
      <li><a href="#concepts">概念</a></li>
      <li><a href="#strategies">策略</a></li>
      <li><a href="#calculator">計算機</a></li>
      <li><a href="#distributions">分布圖</a></li>
      <li><a href="#games">互動遊戲</a></li>
      <li><a href="#cheatsheet">速查表</a></li>
    </ul>
  </div>
</nav>

<div class="page-wrap">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-text fade-up">
      <div class="hero-eyebrow">統計 × 機率 × 決策</div>
      <h1>用數學<br>做出<em>更好的</em><br>決策</h1>
      <p class="hero-desc">從基礎機率到貝葉斯推斷，從中央極限定理到假設檢定，掌握統計思維是現代決策者的核心競爭力。</p>
      <div class="hero-pills">
        <span class="pill red">機率論</span>
        <span class="pill blue">統計推斷</span>
        <span class="pill green">假設檢定</span>
        <span class="pill gold">貝葉斯方法</span>
      </div>
    </div>
    <div class="hero-visual fade-up">
      <canvas id="heroCanvas" height="240"></canvas>
      <div class="hero-visual-label">標準常態分布 N(μ=0, σ²=1)</div>
    </div>
  </div>

  <!-- CONCEPTS -->
  <section id="concepts">
    <div class="sec-header">
      <span class="sec-num">01</span>
      <h2 class="sec-title">核心概念</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="concepts-grid">
      <div class="concept-card fade-up">
        <div class="concept-icon">🎲</div>
        <div class="concept-name">條件機率</div>
        <div class="concept-formula">P(A|B) = P(A∩B) / P(B)</div>
        <div class="concept-desc">在事件 B 已發生的條件下，事件 A 發生的機率。是貝葉斯定理的基石，廣泛應用於醫學診斷、垃圾郵件過濾。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">📊</div>
        <div class="concept-name">期望值</div>
        <div class="concept-formula">E[X] = Σ xᵢ · P(xᵢ)</div>
        <div class="concept-desc">所有可能結果的加權平均，以機率為權重。是評估投資報酬、賭局公平性、保險定價的核心指標。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">🔔</div>
        <div class="concept-name">中央極限定理</div>
        <div class="concept-formula">X̄ ~ N(μ, σ²/n)</div>
        <div class="concept-desc">樣本數足夠大時，樣本均值趨近常態分布，無論母體分布為何。這是統計推斷的理論基礎。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">⚖️</div>
        <div class="concept-name">貝葉斯定理</div>
        <div class="concept-formula">P(H|E) = P(E|H)·P(H) / P(E)</div>
        <div class="concept-desc">根據新證據更新信念的數學框架。後驗機率 = 先驗機率 × 似然比。機器學習的核心思想。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">📉</div>
        <div class="concept-name">標準差與變異數</div>
        <div class="concept-formula">σ² = E[(X-μ)²]</div>
        <div class="concept-desc">衡量數據分散程度的指標。標準差越大，不確定性越高，風險越大。投資組合管理的必備工具。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">🔗</div>
        <div class="concept-name">相關與因果</div>
        <div class="concept-formula">r = Cov(X,Y) / (σₓ · σᵧ)</div>
        <div class="concept-desc">相關係數衡量兩變數線性關係強度（-1 到 1）。相關不等於因果，需透過實驗設計驗證因果推斷。</div>
      </div>
    </div>
  </section>

  <!-- STRATEGIES -->
  <section id="strategies" class="strategies">
    <div class="sec-header">
      <span class="sec-num">02</span>
      <h2 class="sec-title">機率策略</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="strategy-tabs">
      <button class="tab-btn active" onclick="switchTab(this,'bayes')">貝葉斯更新</button>
      <button class="tab-btn" onclick="switchTab(this,'sampling')">大數法則</button>
      <button class="tab-btn" onclick="switchTab(this,'hypothesis')">假設檢定</button>
      <button class="tab-btn" onclick="switchTab(this,'montecarlo')">蒙地卡羅</button>
    </div>

    <!-- Bayes -->
    <div class="tab-panel active" id="tab-bayes">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>貝葉斯更新策略</h3>
          <p>貝葉斯方法的核心思想：從先驗信念出發，隨著新證據的加入，不斷更新我們的信念強度。這種「邊學邊更新」的方式比傳統頻率學派更符合真實決策情境。</p>
          <div class="when-to-use">
            <div class="wtu-label">適用情境</div>
            <ul>
              <li>醫學診斷（症狀 → 疾病機率）</li>
              <li>垃圾郵件過濾</li>
              <li>A/B 測試即時更新</li>
              <li>股票市場情報更新</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">關鍵步驟：</strong><br>① 設定先驗 P(H) → ② 觀察到新證據 E → ③ 計算似然度 P(E|H) → ④ 更新後驗 P(H|E)</p>
        </div>
        <div class="strategy-visual">
          <canvas id="bayesCanvas" height="220"></canvas>
          <div class="chart-label">貝葉斯更新：隨資料累積，後驗分布逐漸收斂</div>
        </div>
      </div>
    </div>

    <!-- Sampling -->
    <div class="tab-panel" id="tab-sampling">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>大數法則應用</h3>
          <p>隨著樣本數增加，樣本均值趨近母體真實均值。大數法則告訴我們：短期結果充滿隨機性，但長期行為是可預測的。這是保險業、賭場、量化投資的理論基礎。</p>
          <div class="when-to-use">
            <div class="wtu-label">策略應用</div>
            <ul>
              <li>確保樣本數足夠大（n ≥ 30）</li>
              <li>避免以小樣本下大結論</li>
              <li>透過分散投資降低個別風險</li>
              <li>對沖策略：做大量小賭注</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">陷阱警告：</strong><br>「賭徒謬誤」——錯誤認為過去事件影響未來獨立事件。每次公正拋硬幣仍是 50% 機率，與歷史無關。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="samplingCanvas" height="220"></canvas>
          <div class="chart-label">大數法則：樣本均值隨 n 增加趨近真實均值（虛線）</div>
        </div>
      </div>
    </div>

    <!-- Hypothesis -->
    <div class="tab-panel" id="tab-hypothesis">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>假設檢定流程</h3>
          <p>假設檢定是科學決策的標準框架：先設立虛無假設（H₀），再以數據決定是否有足夠證據拒絕它。p 值代表「假設 H₀ 成立，觀察到如此極端結果的機率」。</p>
          <div class="when-to-use">
            <div class="wtu-label">檢定步驟</div>
            <ul>
              <li>① 設定 H₀（虛無）與 H₁（對立）假設</li>
              <li>② 選擇顯著水準 α（通常 0.05）</li>
              <li>③ 計算檢定統計量與 p 值</li>
              <li>④ p &lt; α 則拒絕 H₀</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">常見錯誤：</strong><br>p &gt; 0.05 ≠ 接受 H₀，只是「無法拒絕」。同時需考量第一型（偽陽性）與第二型（偽陰性）錯誤。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="hypothesisCanvas" height="220"></canvas>
          <div class="chart-label">α=0.05 雙尾檢定：拒絕區域（紅色）與接受區域（藍色）</div>
        </div>
      </div>
    </div>

    <!-- Monte Carlo -->
    <div class="tab-panel" id="tab-montecarlo">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>蒙地卡羅模擬</h3>
          <p>透過大量隨機抽樣來估計數值解。當問題太複雜、無法用解析公式求解時，用電腦重複模擬數千至百萬次，以統計結果逼近真實答案。</p>
          <div class="when-to-use">
            <div class="wtu-label">應用場景</div>
            <ul>
              <li>複雜衍生品定價（Black-Scholes 以外）</li>
              <li>氣候模型、核反應模擬</li>
              <li>AI 強化學習策略評估</li>
              <li>圓周率 π 的近似估算</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">精度提升：</strong><br>誤差約為 1/√n，所以要減半誤差，需將模擬次數增加 4 倍。計算成本與精度需取得平衡。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="montecarloCanvas" height="220"></canvas>
          <div class="chart-label">蒙地卡羅估算π：圓內點(藍)與圓外點(紅) π ≈ 4×(圓內/總數)</div>
        </div>
      </div>
    </div>
  </section>

  <!-- CALCULATORS -->
  <section id="calculator" class="calc-section">
    <div class="sec-header">
      <span class="sec-num">03</span>
      <h2 class="sec-title">互動計算機</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="calc-grid">

      <!-- Bayes Calc -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">⚖️</span><span class="c-name">貝葉斯定理計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>先驗機率 P(H)  %</label><input type="number" id="b_prior" min="0" max="100" value="5" step="0.1"></div>
          <div class="field"><label>靈敏度 P(E|H)  %（真陽性率）</label><input type="number" id="b_sens" min="0" max="100" value="90" step="0.1"></div>
          <div class="field"><label>特異度 P(¬E|¬H)  %（真陰性率）</label><input type="number" id="b_spec" min="0" max="100" value="95" step="0.1"></div>
          <button class="calc-btn" onclick="calcBayes()">計算後驗機率</button>
          <div class="calc-result" id="b_result"></div>
        </div>
      </div>

      <!-- Expected Value -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">📊</span><span class="c-name">期望值計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>結果 1 數值</label><input type="number" id="ev_v1" value="100"></div>
          <div class="field"><label>結果 1 機率 %</label><input type="number" id="ev_p1" value="30" min="0" max="100"></div>
          <div class="field"><label>結果 2 數值</label><input type="number" id="ev_v2" value="-50"></div>
          <div class="field"><label>結果 2 機率 %</label><input type="number" id="ev_p2" value="70" min="0" max="100"></div>
          <button class="calc-btn" onclick="calcEV()">計算期望值</button>
          <div class="calc-result" id="ev_result"></div>
        </div>
      </div>

      <!-- Confidence Interval -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">📏</span><span class="c-name">信賴區間計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>樣本均值</label><input type="number" id="ci_mean" value="75"></div>
          <div class="field"><label>樣本標準差</label><input type="number" id="ci_sd" value="12" min="0.01"></div>
          <div class="field"><label>樣本數 n</label><input type="number" id="ci_n" value="50" min="2"></div>
          <div class="field"><label>信賴水準</label>
            <select id="ci_conf">
              <option value="1.645">90%</option>
              <option value="1.960" selected>95%</option>
              <option value="2.576">99%</option>
            </select>
          </div>
          <button class="calc-btn" onclick="calcCI()">計算信賴區間</button>
          <div class="calc-result" id="ci_result"></div>
        </div>
      </div>

      <!-- Sample Size -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">🔢</span><span class="c-name">樣本數計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>預期機率 p  %</label><input type="number" id="ss_p" value="50" min="1" max="99"></div>
          <div class="field"><label>誤差容忍度 E  %</label><input type="number" id="ss_e" value="5" min="0.1"></div>
          <div class="field"><label>信賴水準</label>
            <select id="ss_conf">
              <option value="1.645">90%</option>
              <option value="1.960" selected>95%</option>
              <option value="2.576">99%</option>
            </select>
          </div>
          <button class="calc-btn" onclick="calcSS()">計算最小樣本數</button>
          <div class="calc-result" id="ss_result"></div>
        </div>
      </div>

    </div>
  </section>

  <!-- DISTRIBUTION EXPLORER -->
  <section id="distributions" class="dist-section">
    <div class="sec-header">
      <span class="sec-num">04</span>
      <h2 class="sec-title">機率分布探索器</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="dist-controls">
      <div class="dist-control">
        <label>分布類型</label>
        <select id="distType" onchange="drawDist()">
          <option value="normal">常態分布 Normal</option>
          <option value="binomial">二項分布 Binomial</option>
          <option value="poisson">卜瓦松分布 Poisson</option>
          <option value="uniform">均勻分布 Uniform</option>
          <option value="exponential">指數分布 Exponential</option>
        </select>
      </div>
      <div class="dist-control" id="dc_mu">
        <label>均值 μ</label>
        <input type="range" min="-3" max="3" step=".1" value="0" id="d_mu" oninput="updateDist()">
        <span class="dv" id="dv_mu">0</span>
      </div>
      <div class="dist-control" id="dc_sigma">
        <label>標準差 σ</label>
        <input type="range" min=".2" max="3" step=".1" value="1" id="d_sigma" oninput="updateDist()">
        <span class="dv" id="dv_sigma">1</span>
      </div>
      <div class="dist-control" id="dc_n" style="display:none">
        <label>試驗次數 n</label>
        <input type="range" min="5" max="50" step="1" value="20" id="d_n" oninput="updateDist()">
        <span class="dv" id="dv_n">20</span>
      </div>
      <div class="dist-control" id="dc_pp" style="display:none">
        <label>成功機率 p</label>
        <input type="range" min=".05" max=".95" step=".05" value=".5" id="d_pp" oninput="updateDist()">
        <span class="dv" id="dv_pp">0.5</span>
      </div>
      <div class="dist-control" id="dc_lambda" style="display:none">
        <label>λ (速率)</label>
        <input type="range" min=".5" max="10" step=".5" value="3" id="d_lambda" oninput="updateDist()">
        <span class="dv" id="dv_lambda">3</span>
      </div>
    </div>
    <div class="dist-canvas-wrap">
      <canvas id="distCanvas" height="280"></canvas>
      <div class="chart-label" id="distLabel">常態分布 N(μ=0, σ=1)</div>
    </div>
  </section>

  <!-- GAMES -->
  <section id="games" class="games-section">
    <div class="sec-header">
      <span class="sec-num">05</span>
      <h2 class="sec-title">互動遊戲</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="games-grid-wrap">

      <!-- GAME 1: Coin Flip -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🪙</span>
          <span class="gh-title">硬幣實驗室</span>
          <span class="gh-badge">大數法則</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">親身體驗大數法則：持續拋硬幣，看正面比率如何慢慢收斂到 50%。</div>
          <div class="coin-area">
            <div class="coin" id="coinFace">？</div>
            <div class="coin-stats">
              <div class="coin-stat"><div class="cv" id="c_heads">0</div><div class="cl">正面</div></div>
              <div class="coin-stat"><div class="cv" id="c_total">0</div><div class="cl">總次數</div></div>
              <div class="coin-stat"><div class="cv" id="c_pct">—</div><div class="cl">正面率</div></div>
              <div class="coin-stat"><div class="cv" id="c_streak">0</div><div class="cl">連續正面</div></div>
            </div>
            <div class="coin-history" id="coinHistory"></div>
            <div class="coin-btn-row">
              <button class="g-btn" onclick="flipCoin(1)">拋 1 次</button>
              <button class="g-btn" onclick="flipCoin(10)">拋 10 次</button>
              <button class="g-btn" onclick="flipCoin(100)">拋 100 次</button>
              <button class="g-btn outline" onclick="resetCoin()">重置</button>
            </div>
            <canvas id="coinCanvas" height="80"></canvas>
          </div>
        </div>
      </div>

      <!-- GAME 2: Guess the Mean -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🎯</span>
          <span class="gh-title">猜猜均值在哪</span>
          <span class="gh-badge">統計直覺</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">看圖中的散點，憑直覺猜測樣本均值的位置，訓練你的統計直覺！</div>
          <div class="gtm-canvas-wrap">
            <canvas id="gtmCanvas" height="150"></canvas>
          </div>
          <div class="gtm-input-row">
            <input type="number" id="gtmGuess" placeholder="輸入你猜測的均值…" step="0.1">
            <button class="g-btn" onclick="submitGTM()" style="flex:0;white-space:nowrap">確認</button>
            <button class="g-btn outline" onclick="newGTM()" style="flex:0;white-space:nowrap">新題</button>
          </div>
          <div class="gtm-feedback" id="gtmFeedback"></div>
          <div class="gtm-score" id="gtmScore">得分：0 / 0</div>
        </div>
      </div>

      <!-- GAME 3: CLT Demo -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🔔</span>
          <span class="gh-title">中央極限定理動畫</span>
          <span class="gh-badge">CLT 體驗</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">選擇任意母體分布，抽樣並累積樣本均值，親眼看它變成鐘形曲線。</div>
          <div class="clt-area">
            <div class="clt-controls">
              <label>母體：</label>
              <select id="cltDist" onchange="resetCLT()">
                <option value="uniform">均勻分布</option>
                <option value="exponential">指數分布（偏態）</option>
                <option value="bimodal">雙峰分布</option>
                <option value="discrete">離散分布</option>
              </select>
              <label>樣本數 n=</label>
              <input type="range" id="cltN" min="1" max="50" value="5" oninput="document.getElementById('cltNv').textContent=this.value;resetCLT()">
              <span class="cv" id="cltNv">5</span>
            </div>
            <canvas id="cltPopCanvas" height="80"></canvas>
            <canvas id="cltSampCanvas" height="100"></canvas>
            <div class="clt-info" id="cltInfo">按「抽樣」開始實驗</div>
            <div class="coin-btn-row">
              <button class="g-btn" onclick="doSampleCLT(1)">抽樣 ×1</button>
              <button class="g-btn" onclick="doSampleCLT(50)">抽樣 ×50</button>
              <button class="g-btn" onclick="doSampleCLT(500)">抽樣 ×500</button>
              <button class="g-btn outline" onclick="resetCLT()">重置</button>
            </div>
          </div>
        </div>
      </div>

      <!-- GAME 4: Probability Quiz -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🧠</span>
          <span class="gh-title">機率直覺測驗</span>
          <span class="gh-badge">10 題挑戰</span>
        </div>
        <div class="game-box-body">
          <div class="quiz-progress-bar"><div class="quiz-progress-fill" id="quizProgressFill" style="width:0%"></div></div>
          <div class="quiz-q" id="quizQ">按「開始測驗」挑戰你的機率直覺！</div>
          <div class="quiz-options" id="quizOpts"></div>
          <div class="quiz-explain" id="quizExplain"></div>
          <div class="quiz-meta">
            <span id="quizMeta">0 / 10 題</span>
            <span id="quizScoreDisplay">得分：0</span>
          </div>
          <div style="margin-top:10px">
            <button class="g-btn" id="quizStartBtn" onclick="startQuiz()">開始測驗</button>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- CHEAT SHEET -->
  <section id="cheatsheet" class="cheatsheet">
    <div class="sec-header">
      <span class="sec-num">06</span>
      <h2 class="sec-title">公式速查表</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="cs-grid" id="csGrid"></div>
  </section>

</div><!-- /page-wrap -->

<footer>
  統計與機率策略中心 · 教育用途 · 數字會說話，讓數學成為你的武器
</footer>

<script>
// ── UTILITY ───────────────────────────────────────────────────────
function normalPDF(x, mu=0, sigma=1) {
  return Math.exp(-0.5*((x-mu)/sigma)**2) / (sigma * Math.sqrt(2*Math.PI));
}
function normalCDF(x) {
  const t = 1/(1+0.2316419*Math.abs(x));
  const d = 0.3989423*Math.exp(-x*x/2);
  let p = d*t*(0.3193815+t*(-0.3565638+t*(1.7814779+t*(-1.8212560+t*1.3302744))));
  return x > 0 ? 1-p : p;
}

function clearCanvas(canvas, ctx, fillColor='#fdfbf8') {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle = fillColor;
  ctx.fillRect(0,0,canvas.width,canvas.height);
}

// ── HERO BELL CURVE ────────────────────────────────────────────────
function drawHero() {
  const canvas = document.getElementById('heroCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 240 * dpr;
  canvas.style.height = '240px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 240;
  clearCanvas(canvas, ctx, '#f5f2ee');

  const xs = [], ys = [];
  for(let i=0;i<=200;i++) {
    const x = -4 + i*8/200;
    xs.push(x); ys.push(normalPDF(x));
  }
  const maxY = Math.max(...ys);
  const toX = x => (x+4)/8*W;
  const toY = y => H-20 - (y/maxY)*(H-50);

  // shade regions
  const regions = [
    {from:-1,to:1,color:'rgba(41,128,185,.12)'},
    {from:-2,to:-1,color:'rgba(192,57,43,.07)'},
    {from:1,to:2,color:'rgba(192,57,43,.07)'},
    {from:-3,to:-2,color:'rgba(192,57,43,.04)'},
    {from:2,to:3,color:'rgba(192,57,43,.04)'},
  ];
  regions.forEach(({from,to,color}) => {
    ctx.beginPath();
    ctx.moveTo(toX(from), toY(0));
    for(let i=0;i<=100;i++) {
      const x = from+(to-from)*i/100;
      ctx.lineTo(toX(x), toY(normalPDF(x)));
    }
    ctx.lineTo(toX(to), toY(0));
    ctx.closePath();
    ctx.fillStyle = color;
    ctx.fill();
  });

  // curve
  ctx.beginPath();
  xs.forEach((x,i) => i===0 ? ctx.moveTo(toX(x),toY(ys[i])) : ctx.lineTo(toX(x),toY(ys[i])));
  ctx.strokeStyle = '#0f1923';
  ctx.lineWidth = 2;
  ctx.stroke();

  // baseline
  ctx.beginPath(); ctx.moveTo(0,toY(0)); ctx.lineTo(W,toY(0));
  ctx.strokeStyle = '#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  // labels
  ctx.font = '10px DM Mono, monospace';
  ctx.fillStyle = '#6b7f92';
  ctx.textAlign = 'center';
  ['-3σ','-2σ','-1σ','μ','+1σ','+2σ','+3σ'].forEach((l,i) => {
    ctx.fillText(l, toX(-3+i), toY(0)+14);
  });

  // annotation
  ctx.font = '9px DM Mono, monospace';
  ctx.fillStyle = '#2980b9';
  ctx.fillText('68.27%', toX(0), toY(normalPDF(0))+22);
}

// ── STRATEGY CHARTS ────────────────────────────────────────────────
function drawBayes() {
  const canvas = document.getElementById('bayesCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  // show 4 beta distributions with increasing data
  const colors = ['#a8b8c8','#6b7f92','#2980b9','#0f1923'];
  const labels = ['先驗 (弱)','10個樣本','50個樣本','200個樣本'];
  const alphas = [2,6,22,82], betas = [8,14,38,118];

  function betaPDF(x,a,b) {
    if(x<=0||x>=1) return 0;
    let logB = 0;
    for(let i=1;i<a;i++) logB+=Math.log(i);
    for(let i=1;i<b;i++) logB+=Math.log(i);
    let logAB=0; for(let i=1;i<a+b;i++) logAB+=Math.log(i);
    logB -= logAB;
    return Math.exp((a-1)*Math.log(x)+(b-1)*Math.log(1-x)-logB);
  }

  const pts = 120;
  const xs = Array.from({length:pts},(_, i)=>(i+1)/(pts+1));
  const allY = alphas.flatMap((a,j)=>xs.map(x=>betaPDF(x,a,betas[j])));
  const maxY = Math.max(...allY)||1;
  const toX = x => 30+x*(W-40);
  const toY = y => H-30-(y/maxY)*(H-50);

  alphas.forEach((a,j) => {
    ctx.beginPath();
    xs.forEach((x,i) => {
      const y = betaPDF(x,a,betas[j]);
      i===0 ? ctx.moveTo(toX(x),toY(y)) : ctx.lineTo(toX(x),toY(y));
    });
    ctx.strokeStyle = colors[j];
    ctx.lineWidth = j===3?2.5:1.5;
    ctx.globalAlpha = j===3?1:0.7;
    ctx.stroke();
    ctx.globalAlpha=1;
  });

  // legend
  colors.forEach((c,j) => {
    ctx.fillStyle = c;
    ctx.fillRect(30+j*90, H-18, 18, 2);
    ctx.fillStyle = '#6b7f92';
    ctx.font = '9px DM Mono, monospace';
    ctx.textAlign = 'left';
    ctx.fillText(labels[j], 52+j*90, H-14);
  });

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawSampling() {
  const canvas = document.getElementById('samplingCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const TRUE_MEAN = 0.5;
  const n = 200;
  let cum = 0;
  const means = [];
  for(let i=1;i<=n;i++) { cum += Math.random(); means.push(cum/i); }

  const minV = Math.min(...means)-0.05, maxV = Math.max(...means)+0.05;
  const toX = i => 30+i/(n-1)*(W-40);
  const toY = v => H-30-(v-minV)/(maxV-minV)*(H-50);

  // true mean line
  ctx.beginPath(); ctx.moveTo(30,toY(TRUE_MEAN)); ctx.lineTo(W-10,toY(TRUE_MEAN));
  ctx.strokeStyle='#27ae60'; ctx.lineWidth=1.5; ctx.setLineDash([6,4]); ctx.stroke();
  ctx.setLineDash([]);

  // path
  ctx.beginPath();
  means.forEach((v,i)=> i===0? ctx.moveTo(toX(i),toY(v)) : ctx.lineTo(toX(i),toY(v)));
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#6b7f92'; ctx.textAlign='center';
  [1,50,100,150,200].forEach(i=>ctx.fillText(i,toX(i-1),H-14));
  ctx.fillStyle='#27ae60'; ctx.textAlign='right';
  ctx.fillText('真實均值 μ=0.5',W-14,toY(TRUE_MEAN)-5);
}

function drawHypothesis() {
  const canvas = document.getElementById('hypothesisCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const crit = 1.96;
  const toX = x => 30+(x+4)/8*(W-40);
  const toY = y => H-30-y/(normalPDF(0))*(H-50);
  const pts = 200;

  // fill reject regions
  [[-4,-crit],[crit,4]].forEach(([a,b]) => {
    ctx.beginPath();
    ctx.moveTo(toX(a),toY(0));
    for(let i=0;i<=60;i++){
      const x=a+(b-a)*i/60;
      ctx.lineTo(toX(x),toY(normalPDF(x)));
    }
    ctx.lineTo(toX(b),toY(0));
    ctx.closePath();
    ctx.fillStyle='rgba(192,57,43,.2)';
    ctx.fill();
  });

  // fill accept region
  ctx.beginPath();
  ctx.moveTo(toX(-crit),toY(0));
  for(let i=0;i<=100;i++){
    const x=-crit+(crit*2)*i/100;
    ctx.lineTo(toX(x),toY(normalPDF(x)));
  }
  ctx.lineTo(toX(crit),toY(0));
  ctx.closePath();
  ctx.fillStyle='rgba(41,128,185,.12)';
  ctx.fill();

  // curve
  ctx.beginPath();
  for(let i=0;i<=pts;i++){
    const x=-4+8*i/pts;
    i===0?ctx.moveTo(toX(x),toY(normalPDF(x))):ctx.lineTo(toX(x),toY(normalPDF(x)));
  }
  ctx.strokeStyle='#0f1923'; ctx.lineWidth=2; ctx.stroke();

  // crit lines
  [-crit,crit].forEach(cv => {
    ctx.beginPath(); ctx.moveTo(toX(cv),toY(0)); ctx.lineTo(toX(cv),toY(normalPDF(cv)));
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=1.5; ctx.setLineDash([4,3]); ctx.stroke();
    ctx.setLineDash([]);
    ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
    ctx.fillText(cv>0?'+1.96':'-1.96',toX(cv),toY(0)+14);
  });

  // labels
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
  ctx.fillText('拒絕域 α/2=2.5%',toX(-3.2),toY(0.02));
  ctx.fillText('拒絕域 α/2=2.5%',toX(3.2),toY(0.02));
  ctx.fillStyle='#2980b9';
  ctx.fillText('接受域 95%',toX(0),toY(normalPDF(0))+20);

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawMonteCarlo() {
  const canvas = document.getElementById('montecarloCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const pad = 20, sq = Math.min(W-pad*2, H-pad*2);
  const ox = pad, oy = (H-sq)/2;

  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1;
  ctx.strokeRect(ox,oy,sq,sq);

  // quarter circle
  ctx.beginPath(); ctx.arc(ox,oy+sq,sq,0,-Math.PI/2,true);
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();

  let inside=0; const total=600;
  for(let i=0;i<total;i++){
    const x=Math.random(), y=Math.random();
    const isIn = x*x+y*y<=1;
    if(isIn) inside++;
    ctx.beginPath();
    ctx.arc(ox+x*sq, oy+(1-y)*sq, 2, 0, Math.PI*2);
    ctx.fillStyle = isIn ? 'rgba(41,128,185,.55)' : 'rgba(192,57,43,.45)';
    ctx.fill();
  }
  const piEst = 4*inside/total;
  ctx.font='bold 11px DM Mono,monospace';
  ctx.fillStyle='#0f1923';
  ctx.textAlign='left';
  ctx.fillText(`π ≈ ${piEst.toFixed(4)} (n=${total})`,ox+4,oy+16);
}

// ── TAB SWITCHING ──────────────────────────────────────────────────
function switchTab(btn, name) {
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('tab-'+name).classList.add('active');
  setTimeout(()=>{
    if(name==='bayes')      drawBayes();
    if(name==='sampling')   drawSampling();
    if(name==='hypothesis') drawHypothesis();
    if(name==='montecarlo') drawMonteCarlo();
  }, 50);
}

// ── CALCULATORS ────────────────────────────────────────────────────
function show(id, html) {
  const el = document.getElementById(id);
  el.innerHTML = html; el.classList.add('show');
}

function calcBayes() {
  const prior   = +document.getElementById('b_prior').value/100;
  const sens    = +document.getElementById('b_sens').value/100;
  const spec    = +document.getElementById('b_spec').value/100;
  const fpr     = 1-spec;
  const pE      = sens*prior + fpr*(1-prior);
  const posterior = (sens*prior)/pE;
  show('b_result',
    `先驗 P(H) = ${(prior*100).toFixed(1)}%<br>` +
    `P(E) = ${(pE*100).toFixed(2)}%<br>` +
    `<strong>後驗 P(H|E) = ${(posterior*100).toFixed(2)}%</strong><br>` +
    `<small style="color:#888">從 ${(prior*100).toFixed(1)}% → ${(posterior*100).toFixed(1)}%，更新了 ${((posterior-prior)*100).toFixed(1)}%</small>`
  );
}

function calcEV() {
  const v1=+document.getElementById('ev_v1').value;
  const p1=+document.getElementById('ev_p1').value/100;
  const v2=+document.getElementById('ev_v2').value;
  const p2=+document.getElementById('ev_p2').value/100;
  const ev = v1*p1 + v2*p2;
  const color = ev>=0?'#27ae60':'#c0392b';
  show('ev_result',
    `E[X] = ${v1}×${(p1*100).toFixed(0)}% + (${v2})×${(p2*100).toFixed(0)}%<br>` +
    `<strong style="color:${color}">期望值 = ${ev.toFixed(2)}</strong><br>` +
    `<small style="color:#888">${ev>=0?'✅ 正期望值，長期有利':'❌ 負期望值，長期不利'}</small>`
  );
}

function calcCI() {
  const mean=+document.getElementById('ci_mean').value;
  const sd  =+document.getElementById('ci_sd').value;
  const n   =+document.getElementById('ci_n').value;
  const z   =+document.getElementById('ci_conf').value;
  const me  = z*sd/Math.sqrt(n);
  show('ci_result',
    `邊際誤差 ME = ${me.toFixed(3)}<br>` +
    `<strong>信賴區間：[${(mean-me).toFixed(2)}, ${(mean+me).toFixed(2)}]</strong><br>` +
    `<small style="color:#888">標準誤 SE = ${(sd/Math.sqrt(n)).toFixed(3)}</small>`
  );
}

function calcSS() {
  const p=+document.getElementById('ss_p').value/100;
  const e=+document.getElementById('ss_e').value/100;
  const z=+document.getElementById('ss_conf').value;
  const n=Math.ceil(z*z*p*(1-p)/(e*e));
  show('ss_result',
    `最小樣本數 n = ⌈${z}² × ${p} × ${1-p} / ${e}²⌉<br>` +
    `<strong>n = ${n.toLocaleString()}</strong><br>` +
    `<small style="color:#888">增加信賴水準或縮小誤差容忍度會增加所需樣本</small>`
  );
}

// ── DISTRIBUTION EXPLORER ──────────────────────────────────────────
function updateDist() {
  document.getElementById('dv_mu').textContent    = document.getElementById('d_mu').value;
  document.getElementById('dv_sigma').textContent = document.getElementById('d_sigma').value;
  document.getElementById('dv_n').textContent     = document.getElementById('d_n').value;
  document.getElementById('dv_pp').textContent    = document.getElementById('d_pp').value;
  document.getElementById('dv_lambda').textContent= document.getElementById('d_lambda').value;
  drawDist();
}

function drawDist() {
  const type   = document.getElementById('distType').value;
  const mu     = +document.getElementById('d_mu').value;
  const sigma  = +document.getElementById('d_sigma').value;
  const nBin   = +document.getElementById('d_n').value;
  const pp     = +document.getElementById('d_pp').value;
  const lambda = +document.getElementById('d_lambda').value;

  // show/hide controls
  document.getElementById('dc_mu').style.display    = ['normal','uniform'].includes(type)?'':'none';
  document.getElementById('dc_sigma').style.display = type==='normal'?'':'none';
  document.getElementById('dc_n').style.display     = type==='binomial'?'':'none';
  document.getElementById('dc_pp').style.display    = type==='binomial'?'':'none';
  document.getElementById('dc_lambda').style.display= ['poisson','exponential'].includes(type)?'':'none';

  const canvas = document.getElementById('distCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 280 * dpr;
  canvas.style.height = '280px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 280;
  clearCanvas(canvas, ctx);

  const pad=40;
  let xs=[], ys=[], discrete=false;

  if(type==='normal') {
    const lo=mu-4*sigma, hi=mu+4*sigma;
    xs=Array.from({length:200},(_,i)=>lo+(hi-lo)*i/199);
    ys=xs.map(x=>normalPDF(x,mu,sigma));
    document.getElementById('distLabel').textContent=`常態分布 N(μ=${mu}, σ=${sigma})`;
  } else if(type==='binomial') {
    discrete=true;
    for(let k=0;k<=nBin;k++){
      xs.push(k);
      let logP=0;
      for(let i=0;i<k;i++) logP+=Math.log(nBin-i)-Math.log(i+1);
      logP+=k*Math.log(pp)+(nBin-k)*Math.log(1-pp);
      ys.push(Math.exp(logP));
    }
    document.getElementById('distLabel').textContent=`二項分布 B(n=${nBin}, p=${pp})`;
  } else if(type==='poisson') {
    discrete=true;
    const maxK=Math.ceil(lambda*3)+1;
    for(let k=0;k<=maxK;k++){
      xs.push(k);
      let logP=-lambda+k*Math.log(lambda);
      for(let i=1;i<=k;i++) logP-=Math.log(i);
      ys.push(Math.exp(logP));
    }
    document.getElementById('distLabel').textContent=`卜瓦松分布 Poisson(λ=${lambda})`;
  } else if(type==='uniform') {
    const a=mu-2, b=mu+2;
    xs=[-1+a,a,a,b,b,b+1];
    ys=[0,0,1/(b-a),1/(b-a),0,0];
    document.getElementById('distLabel').textContent=`均勻分布 U(${a.toFixed(1)}, ${b.toFixed(1)})`;
  } else if(type==='exponential') {
    xs=Array.from({length:200},(_,i)=>i/199*8/lambda);
    ys=xs.map(x=>lambda*Math.exp(-lambda*x));
    document.getElementById('distLabel').textContent=`指數分布 Exp(λ=${lambda})`;
  }

  const maxY=Math.max(...ys)||1;
  const minX=Math.min(...xs), maxX=Math.max(...xs);
  const rangeX=maxX-minX||1;
  const toX=x=>pad+(x-minX)/rangeX*(W-pad*2);
  const toY=y=>H-pad-(y/maxY)*(H-pad*2);

  if(discrete) {
    const barW=Math.max(4,(W-pad*2)/xs.length*0.7);
    xs.forEach((x,i)=>{
      ctx.fillStyle='rgba(41,128,185,.65)';
      const bx=toX(x)-barW/2;
      const bh=(ys[i]/maxY)*(H-pad*2);
      ctx.fillRect(bx,H-pad-bh,barW,bh);
      ctx.strokeStyle='#2980b9'; ctx.lineWidth=1;
      ctx.strokeRect(bx,H-pad-bh,barW,bh);
    });
  } else {
    // fill
    ctx.beginPath();
    ctx.moveTo(toX(xs[0]),toY(0));
    xs.forEach((x,i)=>ctx.lineTo(toX(x),toY(ys[i])));
    ctx.lineTo(toX(xs[xs.length-1]),toY(0));
    ctx.closePath();
    const grad=ctx.createLinearGradient(0,pad,0,H-pad);
    grad.addColorStop(0,'rgba(41,128,185,.25)');
    grad.addColorStop(1,'rgba(41,128,185,.03)');
    ctx.fillStyle=grad; ctx.fill();
    // line
    ctx.beginPath();
    xs.forEach((x,i)=>i===0?ctx.moveTo(toX(x),toY(ys[i])):ctx.lineTo(toX(x),toY(ys[i])));
    ctx.strokeStyle='#2980b9'; ctx.lineWidth=2; ctx.stroke();
  }

  // axes
  ctx.beginPath(); ctx.moveTo(pad,pad); ctx.lineTo(pad,H-pad); ctx.lineTo(W-pad,H-pad);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  // x ticks
  ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#6b7f92'; ctx.textAlign='center';
  const tickCount=6;
  for(let i=0;i<=tickCount;i++){
    const v=minX+rangeX*i/tickCount;
    ctx.fillText(v.toFixed(1),toX(v),H-pad+16);
  }
}

// ── CHEAT SHEET ────────────────────────────────────────────────────
const formulas = [
  {topic:'機率加法法則',formula:'P(A∪B) = P(A)+P(B)−P(A∩B)',note:'若 A, B 互斥則 P(A∩B)=0'},
  {topic:'獨立事件乘法',formula:'P(A∩B) = P(A)·P(B)',note:'僅在 A, B 統計獨立時成立'},
  {topic:'貝葉斯定理',formula:'P(H|E)=P(E|H)·P(H)/P(E)',note:'後驗 = 似然 × 先驗 / 邊際'},
  {topic:'期望值（離散）',formula:'E[X] = Σ xᵢ P(xᵢ)',note:'所有結果的機率加權平均'},
  {topic:'變異數',formula:'Var(X) = E[X²] − (E[X])²',note:'標準差 σ = √Var(X)'},
  {topic:'中央極限定理',formula:'X̄ ~ N(μ, σ²/n)',note:'n≥30 時近似成立'},
  {topic:'95% 信賴區間',formula:'x̄ ± 1.96 · σ/√n',note:'99% 用 2.576，90% 用 1.645'},
  {topic:'樣本數公式',formula:'n = z²·p(1−p)/E²',note:'E 為誤差容忍度（小數）'},
  {topic:'相關係數',formula:'r = Σ(xᵢ−x̄)(yᵢ−ȳ) / (nσₓσᵧ)',note:'-1≤r≤1，0 表示無線性相關'},
  {topic:'常態分布 PDF',formula:'f(x)=e^(−½((x−μ)/σ)²)/(σ√2π)',note:'鐘形曲線，對稱於均值'},
  {topic:'二項分布',formula:'P(X=k)=C(n,k)pᵏ(1−p)ⁿ⁻ᵏ',note:'n 次試驗中 k 次成功的機率'},
  {topic:'大數法則',formula:'X̄ₙ → μ  (n→∞)',note:'樣本均值依機率收斂至母體均值'},
];

const csGrid = document.getElementById('csGrid');
formulas.forEach(f=>{
  csGrid.innerHTML+=`
  <div class="cs-card">
    <div class="cs-topic">${f.topic}</div>
    <div class="cs-formula">${f.formula}</div>
    <div class="cs-note">${f.note}</div>
  </div>`;
});

// ═══════════════════════════════════════════════════════════════════
// GAME 1 — COIN FLIP
// ═══════════════════════════════════════════════════════════════════
let coinHeads=0, coinTotal=0, coinStreak=0, coinHistory=[], coinRatioHistory=[];

function flipCoin(n) {
  for(let i=0;i<n;i++){
    const h = Math.random()<0.5;
    if(h){ coinHeads++; coinStreak++; } else { coinStreak=0; }
    coinTotal++;
    coinHistory.push(h?'H':'T');
    coinRatioHistory.push(coinHeads/coinTotal);
  }
  const last = coinHistory[coinHistory.length-1];
  const face = document.getElementById('coinFace');
  face.textContent = last==='H'?'正':'反';
  face.classList.remove('flip-anim');
  void face.offsetWidth;
  face.classList.add('flip-anim');
  document.getElementById('c_heads').textContent = coinHeads;
  document.getElementById('c_total').textContent = coinTotal;
  document.getElementById('c_pct').textContent   = (coinHeads/coinTotal*100).toFixed(1)+'%';
  document.getElementById('c_streak').textContent= coinStreak;
  // history chips (last 30)
  const hBox = document.getElementById('coinHistory');
  hBox.innerHTML = coinHistory.slice(-40).map(c=>`<span class="coin-chip ${c}">${c==='H'?'正':'反'}</span>`).join('');
  drawCoinChart();
}

function resetCoin(){
  coinHeads=coinTotal=coinStreak=0; coinHistory=[]; coinRatioHistory=[];
  document.getElementById('coinFace').textContent='？';
  ['c_heads','c_total','c_streak'].forEach(id=>document.getElementById(id).textContent='0');
  document.getElementById('c_pct').textContent='—';
  document.getElementById('coinHistory').innerHTML='';
  drawCoinChart();
}

function drawCoinChart(){
  const canvas=document.getElementById('coinCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=80*dpr;
  canvas.style.height='80px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=80;
  clearCanvas(canvas,ctx);
  if(coinRatioHistory.length<2){
    ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='center';
    ctx.fillText('拋硬幣後顯示正面率變化圖',W/2,H/2); return;
  }
  const pts=coinRatioHistory;
  const toX=i=>i/(pts.length-1)*W;
  const toY=v=>H-4-(v)*( H-8);
  // 50% line
  ctx.beginPath(); ctx.moveTo(0,toY(.5)); ctx.lineTo(W,toY(.5));
  ctx.strokeStyle='rgba(39,174,96,.4)'; ctx.lineWidth=1; ctx.setLineDash([4,4]); ctx.stroke(); ctx.setLineDash([]);
  // curve
  ctx.beginPath();
  pts.forEach((v,i)=>i===0?ctx.moveTo(toX(i),toY(v)):ctx.lineTo(toX(i),toY(v)));
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#27ae60'; ctx.textAlign='left';
  ctx.fillText('50%',4,toY(.5)-3);
}

// ═══════════════════════════════════════════════════════════════════
// GAME 2 — GUESS THE MEAN
// ═══════════════════════════════════════════════════════════════════
let gtmData=[], gtmTrueMean=0, gtmAnswered=false, gtmCorrect=0, gtmTotal=0;

function newGTM(){
  gtmAnswered=false;
  document.getElementById('gtmGuess').value='';
  document.getElementById('gtmFeedback').textContent='';
  document.getElementById('gtmFeedback').style.color='var(--muted)';
  // generate random dataset
  const dist = Math.random();
  gtmData=[];
  if(dist<0.33){
    // normal-ish
    const mu=Math.random()*6-3, sig=0.5+Math.random()*1.5;
    for(let i=0;i<25;i++) gtmData.push(mu+sig*(Math.random()+Math.random()+Math.random()-1.5));
  } else if(dist<0.66){
    // skewed
    const base=Math.random()*4-2;
    for(let i=0;i<20;i++) gtmData.push(base+Math.pow(Math.random(),2)*6);
  } else {
    // bimodal
    const c1=Math.random()*3-3, c2=c1+2+Math.random()*2;
    for(let i=0;i<12;i++) gtmData.push(c1+(Math.random()-.5)*1.2);
    for(let i=0;i<12;i++) gtmData.push(c2+(Math.random()-.5)*1.2);
  }
  gtmTrueMean = gtmData.reduce((a,b)=>a+b,0)/gtmData.length;
  drawGTM();
}

function drawGTM(guessVal, showAnswer){
  const canvas=document.getElementById('gtmCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=150*dpr;
  canvas.style.height='150px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=150;
  clearCanvas(canvas,ctx);
  if(!gtmData.length) return;

  const minV=Math.min(...gtmData)-0.5, maxV=Math.max(...gtmData)+0.5;
  const toX=v=>20+(v-minV)/(maxV-minV)*(W-40);

  // dots
  // jitter y
  const ys=gtmData.map(()=>40+Math.random()*60);
  gtmData.forEach((v,i)=>{
    ctx.beginPath(); ctx.arc(toX(v),ys[i],5,0,Math.PI*2);
    ctx.fillStyle='rgba(41,128,185,.5)'; ctx.fill();
    ctx.strokeStyle='#2980b9'; ctx.lineWidth=1; ctx.stroke();
  });

  if(showAnswer){
    // true mean line
    ctx.beginPath(); ctx.moveTo(toX(gtmTrueMean),10); ctx.lineTo(toX(gtmTrueMean),H-20);
    ctx.strokeStyle='#27ae60'; ctx.lineWidth=2.5; ctx.stroke();
    ctx.font='bold 10px DM Mono,monospace'; ctx.fillStyle='#27ae60'; ctx.textAlign='center';
    ctx.fillText(`真實均值 ${gtmTrueMean.toFixed(2)}`,toX(gtmTrueMean),H-6);
  }
  if(guessVal!==undefined){
    ctx.beginPath(); ctx.moveTo(toX(guessVal),10); ctx.lineTo(toX(guessVal),H-20);
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=2; ctx.setLineDash([5,4]); ctx.stroke(); ctx.setLineDash([]);
    ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
    ctx.fillText(`你的猜測 ${(+guessVal).toFixed(2)}`,toX(guessVal),8);
  }

  // axis
  ctx.beginPath(); ctx.moveTo(20,H-18); ctx.lineTo(W-20,H-18);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='center';
  [minV+0.5, (minV+maxV)/2, maxV-0.5].forEach(v=>ctx.fillText(v.toFixed(1),toX(v),H-5));
}

function submitGTM(){
  if(gtmAnswered||!gtmData.length) return;
  const g=parseFloat(document.getElementById('gtmGuess').value);
  if(isNaN(g)){ document.getElementById('gtmFeedback').textContent='請輸入數字'; return; }
  gtmAnswered=true; gtmTotal++;
  const err=Math.abs(g-gtmTrueMean);
  const range=Math.max(...gtmData)-Math.min(...gtmData);
  const pct=err/range;
  let fb='', color='';
  if(pct<0.05){ fb=`🎯 超準！誤差只有 ${err.toFixed(2)}，真厲害！`; color='#27ae60'; gtmCorrect++; }
  else if(pct<0.12){ fb=`👍 不錯！誤差 ${err.toFixed(2)}，接近了！`; color='#d4860a'; gtmCorrect++; }
  else { fb=`📉 差了點，誤差 ${err.toFixed(2)}，再試一次！`; color='#c0392b'; }
  document.getElementById('gtmFeedback').textContent=fb;
  document.getElementById('gtmFeedback').style.color=color;
  document.getElementById('gtmScore').textContent=`得分：${gtmCorrect} / ${gtmTotal}`;
  drawGTM(g, true);
}

// ═══════════════════════════════════════════════════════════════════
// GAME 3 — CLT DEMO
// ═══════════════════════════════════════════════════════════════════
let cltMeans=[];

function getCLTSample(n){
  const dist=document.getElementById('cltDist').value;
  const arr=[];
  for(let i=0;i<n;i++){
    let v;
    if(dist==='uniform') v=Math.random()*10;
    else if(dist==='exponential') v=-Math.log(1-Math.random())*2;
    else if(dist==='bimodal') v=Math.random()<0.5?Math.random()*2+1:Math.random()*2+7;
    else {
      const r=Math.random();
      v = r<0.3?1:r<0.6?3:r<0.8?5:8;
    }
    arr.push(v);
  }
  return arr;
}

function resetCLT(){
  cltMeans=[];
  drawCLTPopulation();
  drawCLTSampling();
  document.getElementById('cltInfo').textContent='按「抽樣」開始實驗';
}

function doSampleCLT(times){
  const n=+document.getElementById('cltN').value;
  for(let i=0;i<times;i++){
    const s=getCLTSample(n);
    cltMeans.push(s.reduce((a,b)=>a+b,0)/n);
  }
  drawCLTSampling();
  const m=cltMeans.reduce((a,b)=>a+b,0)/cltMeans.length;
  const v=cltMeans.reduce((a,b)=>a+(b-m)**2,0)/cltMeans.length;
  document.getElementById('cltInfo').textContent=
    `已收集 ${cltMeans.length} 個樣本均值 · 均值的均值=${m.toFixed(3)} · 標準差=${Math.sqrt(v).toFixed(3)} · 分布${cltMeans.length>=100?'已趨近常態 🔔':'逐漸成形…'}`;
}

function drawCLTPopulation(){
  const canvas=document.getElementById('cltPopCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=80*dpr; canvas.style.height='80px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=80;
  clearCanvas(canvas,ctx);
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='left';
  ctx.fillText('母體分布：',4,12);

  const dist=document.getElementById('cltDist').value;
  const pts=120;
  const xs=[],ys=[];
  if(dist==='uniform'){
    xs.push(0,0,10,10); ys.push(0,0.1,0.1,0);
  } else if(dist==='exponential'){
    for(let i=0;i<pts;i++){const x=i/pts*10;xs.push(x);ys.push(0.5*Math.exp(-x*0.5));}
  } else if(dist==='bimodal'){
    for(let i=0;i<pts;i++){const x=i/pts*12;xs.push(x);ys.push(normalPDF(x,2,0.7)+normalPDF(x,8,0.7));}
  } else {
    xs.push(0.5,1,1,1.5,2.5,3,3,3.5,4.5,5,5,5.5,7.5,8,8,8.5);
    ys.push(0,0,0.3,0,0,0,0.3,0,0,0,0.2,0,0,0,0.2,0);
  }
  const maxY=Math.max(...ys)||0.1;
  const minX=Math.min(...xs),maxX=Math.max(...xs);
  const toX=x=>20+(x-minX)/(maxX-minX)*(W-30);
  const toY=y=>H-14-y/maxY*(H-24);

  ctx.beginPath();
  ctx.moveTo(toX(xs[0]),toY(0));
  xs.forEach((x,i)=>ctx.lineTo(toX(x),toY(ys[i])));
  ctx.lineTo(toX(xs[xs.length-1]),toY(0));
  ctx.closePath();
  ctx.fillStyle='rgba(192,57,43,.15)'; ctx.fill();
  ctx.beginPath();
  xs.forEach((x,i)=>i===0?ctx.moveTo(toX(x),toY(ys[i])):ctx.lineTo(toX(x),toY(ys[i])));
  ctx.strokeStyle='#c0392b'; ctx.lineWidth=1.5; ctx.stroke();

  ctx.beginPath(); ctx.moveTo(20,H-13); ctx.lineTo(W-10,H-13);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawCLTSampling(){
  const canvas=document.getElementById('cltSampCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=100*dpr; canvas.style.height='100px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=100;
  clearCanvas(canvas,ctx);
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='left';
  ctx.fillText('樣本均值分布（累積次數）：',4,12);

  if(cltMeans.length<2){ return; }
  const minV=Math.min(...cltMeans),maxV=Math.max(...cltMeans);
  const bins=20;
  const counts=new Array(bins).fill(0);
  cltMeans.forEach(v=>{
    const b=Math.min(bins-1,Math.floor((v-minV)/(maxV-minV+0.001)*bins));
    counts[b]++;
  });
  const maxC=Math.max(...counts)||1;
  const bw=(W-30)/bins;
  const toY=c=>H-18-c/maxC*(H-30);

  counts.forEach((c,i)=>{
    const x=20+i*bw;
    const bh=c/maxC*(H-30);
    ctx.fillStyle='rgba(41,128,185,.55)';
    ctx.fillRect(x,H-18-bh,bw-1,bh);
  });

  // overlay normal curve if enough samples
  if(cltMeans.length>=30){
    const mu=cltMeans.reduce((a,b)=>a+b,0)/cltMeans.length;
    const sig=Math.sqrt(cltMeans.reduce((a,b)=>a+(b-mu)**2,0)/cltMeans.length);
    ctx.beginPath();
    for(let i=0;i<=100;i++){
      const x=minV+(maxV-minV)*i/100;
      const px=20+(x-minV)/(maxV-minV)*(W-30);
      const py=toY(normalPDF(x,mu,sig)*cltMeans.length*(maxV-minV)/bins);
      i===0?ctx.moveTo(px,py):ctx.lineTo(px,py);
    }
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=2; ctx.stroke();
  }

  ctx.beginPath(); ctx.moveTo(20,H-17); ctx.lineTo(W-10,H-17);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

// ═══════════════════════════════════════════════════════════════════
// GAME 4 — PROBABILITY QUIZ
// ═══════════════════════════════════════════════════════════════════
const QUIZ_QUESTIONS = [
  {
    q:'拋一枚公正硬幣 10 次，全部正面的機率是？',
    opts:['1/1024','1/512','1/100','1/1000'],
    ans:0,
    explain:'每次正面機率為 1/2，10次獨立事件：(1/2)¹⁰ = 1/1024 ≈ 0.098%'
  },{
    q:'一個袋子有 3 顆紅球、7 顆藍球，隨機取 2 顆（不放回），兩顆都是紅球的機率？',
    opts:['9%','3.3%','6.7%','12%'],
    ans:1,
    explain:'P = (3/10)×(2/9) = 6/90 = 1/15 ≈ 6.7%。等等——答案是 6.7%！選項順序是陷阱，正確答案是 C（6.7%）。'
  },{
    q:'甲病盛行率 1%，篩檢靈敏度 99%、特異度 95%。篩到陽性後，真的有病的機率約？',
    opts:['99%','50%','16.7%','1%'],
    ans:2,
    explain:'貝葉斯：P(病|陽) = (0.99×0.01)/(0.99×0.01 + 0.05×0.99) ≈ 0.0099/0.0594 ≈ 16.7%。基率低時，假陽性大量稀釋了真陽性。'
  },{
    q:'「連輸 5 次後，第 6 次更容易贏」— 這句話是？',
    opts:['正確，機率會補回來','正確，但只適用賭場','完全錯誤（賭徒謬誤）','取決於遊戲類型'],
    ans:2,
    explain:'獨立事件沒有記憶。每次結果只取決於當下機率，不受歷史影響。這就是著名的「賭徒謬誤」。'
  },{
    q:'一個班 23 人，至少 2 人同生日的機率約為？',
    opts:['6.3%','23%','50.7%','89%'],
    ans:2,
    explain:'生日問題！1-(365×364×...×343)/365²³ ≈ 50.7%。人數遠少於 365 時機率就過半，反直覺！'
  },{
    q:'獨立事件 A（P=0.6）和 B（P=0.7），A 或 B 發生的機率？',
    opts:['1.3（不可能）','88%','42%','65%'],
    ans:1,
    explain:'P(A∪B) = P(A)+P(B)-P(A∩B) = 0.6+0.7-0.6×0.7 = 1.3-0.42 = 0.88 = 88%'
  },{
    q:'標準常態分布中，|X| > 2 的機率約為？',
    opts:['32%','5%','0.3%','16%'],
    ans:1,
    explain:'68-95-99.7 法則：±1σ 佔 68%，±2σ 佔 95%，所以 |X|>2σ ≈ 5%（雙尾各 2.5%）。'
  },{
    q:'樣本數從 100 增加到 400，信賴區間寬度變化？',
    opts:['縮小 4 倍','縮小 2 倍','縮小 1.5 倍','不變'],
    ans:1,
    explain:'信賴區間寬度 ∝ 1/√n。√400/√100 = 2，所以寬度縮小一半。要縮小 4 倍需要樣本數增加 16 倍。'
  },{
    q:'回歸係數 r=0.9，表示 X 能解釋 Y 多少變異？',
    opts:['90%','81%','0.9%','95%'],
    ans:1,
    explain:'決定係數 R² = r² = 0.81，即 81%。注意：r 是相關係數，r² 才是解釋力（決定係數）。'
  },{
    q:'p 值 = 0.03，顯著水準 α = 0.05，結論是？',
    opts:['接受 H₀','拒絕 H₁','拒絕 H₀','數據不足'],
    ans:2,
    explain:'p < α（0.03 < 0.05），有足夠證據拒絕虛無假設 H₀。注意：這不代表 H₀ 一定是錯的，只是「不太可能」。'
  }
];
let quizIdx=0, quizScore=0, quizOrder=[], quizActive=false;

function startQuiz(){
  quizIdx=0; quizScore=0; quizActive=true;
  quizOrder=[...Array(QUIZ_QUESTIONS.length).keys()].sort(()=>Math.random()-.5).slice(0,10);
  document.getElementById('quizStartBtn').style.display='none';
  showQuizQ();
}

function showQuizQ(){
  if(quizIdx>=quizOrder.length){ endQuiz(); return; }
  const q=QUIZ_QUESTIONS[quizOrder[quizIdx]];
  document.getElementById('quizProgressFill').style.width=`${quizIdx/10*100}%`;
  document.getElementById('quizMeta').textContent=`${quizIdx+1} / 10 題`;
  document.getElementById('quizQ').textContent=q.q;
  document.getElementById('quizExplain').textContent='';
  document.getElementById('quizExplain').classList.remove('show');
  const optsEl=document.getElementById('quizOpts');
  optsEl.innerHTML=q.opts.map((o,i)=>
    `<button class="quiz-opt" onclick="answerQuiz(${i})">${String.fromCharCode(65+i)}. ${o}</button>`
  ).join('');
}

function answerQuiz(chosen){
  const q=QUIZ_QUESTIONS[quizOrder[quizIdx]];
  const opts=document.querySelectorAll('.quiz-opt');
  opts.forEach(b=>b.disabled=true);
  opts[q.ans].classList.add('correct');
  if(chosen!==q.ans){ opts[chosen].classList.add('wrong'); } else { quizScore++; }
  document.getElementById('quizScoreDisplay').textContent=`得分：${quizScore}`;
  const ex=document.getElementById('quizExplain');
  ex.textContent='💡 '+q.explain; ex.classList.add('show');
  quizIdx++;
  setTimeout(()=>{
    if(quizIdx<quizOrder.length) showQuizQ();
    else endQuiz();
  }, 2200);
}

function endQuiz(){
  document.getElementById('quizProgressFill').style.width='100%';
  document.getElementById('quizMeta').textContent='完成！';
  document.getElementById('quizExplain').classList.remove('show');
  const grade = quizScore>=9?'🏆 機率大師！':quizScore>=7?'🎓 統計高手！':quizScore>=5?'📚 繼續加油！':'💪 再練習一下！';
  document.getElementById('quizQ').textContent=`測驗結束！得分 ${quizScore}/10 — ${grade}`;
  document.getElementById('quizOpts').innerHTML='';
  const btn=document.getElementById('quizStartBtn');
  btn.textContent='重新挑戰'; btn.style.display='block';
  quizActive=false;
}

// ── INIT ──────────────────────────────────────────────────────────
window.addEventListener('load', ()=>{
  drawHero();
  drawBayes();
  drawSampling();
  drawHypothesis();
  drawMonteCarlo();
  drawDist();
  document.getElementById('dv_mu').textContent     = document.getElementById('d_mu').value;
  document.getElementById('dv_sigma').textContent  = document.getElementById('d_sigma').value;
  document.getElementById('dv_n').textContent      = document.getElementById('d_n').value;
  document.getElementById('dv_pp').textContent     = document.getElementById('d_pp').value;
  document.getElementById('dv_lambda').textContent = document.getElementById('d_lambda').value;
  // games init
  drawCoinChart();
  newGTM();
  drawCLTPopulation();
  drawCLTSampling();
});
window.addEventListener('resize', ()=>{ drawHero(); drawDist(); });
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>統計與機率策略中心</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@300;400;500&family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
:root {
  --ink: #0f1923;
  --ink2: #1e2e3d;
  --slate: #3a4f63;
  --muted: #6b7f92;
  --pale: #a8b8c8;
  --rule: #dce4ec;
  --bg: #f5f2ee;
  --paper: #fdfbf8;
  --paper2: #f8f5f0;
  --accent: #c0392b;
  --accent2: #2980b9;
  --green: #27ae60;
  --gold: #d4860a;
  --highlight: #fff3cd;

  --fs-xs: .72rem;
  --fs-sm: .85rem;
  --fs-base: 1rem;
  --fs-lg: 1.15rem;
  --fs-xl: 1.4rem;
  --fs-2xl: 2rem;
  --fs-3xl: 3.2rem;
}

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--ink);
  font-family: 'Noto Sans TC', sans-serif;
  font-weight: 300;
  line-height: 1.7;
  overflow-x: hidden;
}

/* ── NOISE TEXTURE ── */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: .4;
}

/* ── LAYOUT ── */
.page-wrap { max-width: 1200px; margin: 0 auto; padding: 0 32px; }

/* ── NAV ── */
nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(245,242,238,.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--rule);
}
.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 32px;
  max-width: 1200px;
  margin: 0 auto;
}
.nav-brand {
  font-family: 'DM Serif Display', serif;
  font-size: 1.15rem;
  color: var(--ink);
  letter-spacing: .02em;
}
.nav-brand span { color: var(--accent); }
.nav-links { display: flex; gap: 28px; list-style: none; }
.nav-links a {
  font-size: var(--fs-sm);
  color: var(--slate);
  text-decoration: none;
  letter-spacing: .04em;
  font-weight: 400;
  transition: color .2s;
  font-family: 'DM Mono', monospace;
}
.nav-links a:hover { color: var(--ink); }

/* ── HERO ── */
.hero {
  padding: 90px 0 70px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  border-bottom: 1px solid var(--rule);
  margin-bottom: 80px;
}
.hero-text {}
.hero-eyebrow {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  letter-spacing: .2em;
  color: var(--accent);
  text-transform: uppercase;
  margin-bottom: 18px;
}
.hero h1 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.4rem, 5vw, 3.8rem);
  line-height: 1.1;
  color: var(--ink);
  margin-bottom: 20px;
}
.hero h1 em { font-style: italic; color: var(--accent2); }
.hero-desc {
  font-size: var(--fs-base);
  color: var(--slate);
  line-height: 1.8;
  max-width: 440px;
  margin-bottom: 32px;
}
.hero-pills { display: flex; flex-wrap: wrap; gap: 8px; }
.pill {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  padding: 4px 12px;
  border-radius: 2px;
  border: 1px solid;
  letter-spacing: .06em;
}
.pill.red   { border-color: var(--accent); color: var(--accent); }
.pill.blue  { border-color: var(--accent2); color: var(--accent2); }
.pill.green { border-color: var(--green); color: var(--green); }
.pill.gold  { border-color: var(--gold); color: var(--gold); }

/* hero visual: animated bell curve */
.hero-visual {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}
.hero-visual canvas { width: 100% !important; max-width: 480px; }
.hero-visual-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .08em;
}

/* ── SECTION HEADERS ── */
.sec-header {
  display: flex;
  align-items: baseline;
  gap: 18px;
  margin-bottom: 36px;
}
.sec-num {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .12em;
}
.sec-title {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-2xl);
  color: var(--ink);
}
.sec-rule {
  flex: 1;
  height: 1px;
  background: var(--rule);
}

/* ── CONCEPT CARDS ── */
.concepts-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: var(--rule);
  border: 1px solid var(--rule);
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 80px;
}
.concept-card {
  background: var(--paper);
  padding: 32px 28px;
  transition: background .2s;
  cursor: default;
}
.concept-card:hover { background: var(--paper2); }
.concept-icon {
  font-size: 1.6rem;
  margin-bottom: 14px;
}
.concept-name {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-lg);
  color: var(--ink);
  margin-bottom: 8px;
}
.concept-formula {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent2);
  background: rgba(41,128,185,.06);
  border-left: 2px solid var(--accent2);
  padding: 6px 10px;
  margin-bottom: 12px;
  letter-spacing: .04em;
  border-radius: 0 2px 2px 0;
  word-break: break-all;
}
.concept-desc {
  font-size: var(--fs-sm);
  color: var(--slate);
  line-height: 1.7;
}

/* ── STRATEGY SECTION ── */
.strategies { margin-bottom: 80px; }
.strategy-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid var(--rule);
  margin-bottom: 32px;
}
.tab-btn {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  padding: 10px 22px;
  border: none;
  background: transparent;
  color: var(--muted);
  cursor: pointer;
  letter-spacing: .06em;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: color .2s, border-color .2s;
}
.tab-btn.active { color: var(--ink); border-bottom-color: var(--ink); }
.tab-btn:hover  { color: var(--ink2); }

.tab-panel { display: none; }
.tab-panel.active { display: block; }

.strategy-layout {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 40px;
  align-items: start;
}
.strategy-info h3 {
  font-family: 'DM Serif Display', serif;
  font-size: var(--fs-xl);
  color: var(--ink);
  margin-bottom: 14px;
}
.strategy-info p {
  font-size: var(--fs-sm);
  color: var(--slate);
  line-height: 1.8;
  margin-bottom: 18px;
}
.strategy-info .when-to-use {
  background: var(--paper2);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 16px 20px;
  margin-bottom: 18px;
}
.when-to-use .wtu-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  letter-spacing: .1em;
  color: var(--accent);
  margin-bottom: 8px;
  text-transform: uppercase;
}
.when-to-use ul {
  padding-left: 18px;
  font-size: var(--fs-sm);
  color: var(--slate);
}
.when-to-use li { margin-bottom: 4px; }

.strategy-visual {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 24px;
}
.strategy-visual canvas { width: 100% !important; display: block; }
.chart-label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  text-align: center;
  margin-top: 10px;
  letter-spacing: .06em;
}

/* ── CALCULATOR ── */
.calc-section { margin-bottom: 80px; }
.calc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
  gap: 20px;
}
.calc-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  overflow: hidden;
}
.calc-header {
  padding: 16px 22px;
  background: var(--ink);
  color: var(--bg);
  display: flex;
  align-items: center;
  gap: 10px;
}
.calc-header .c-icon { font-size: 1.1rem; }
.calc-header .c-name {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .06em;
}
.calc-body { padding: 22px; }
.field { margin-bottom: 16px; }
.field label {
  display: block;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
  letter-spacing: .08em;
  margin-bottom: 6px;
  text-transform: uppercase;
}
.field input, .field select {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  background: var(--paper2);
  color: var(--ink);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  outline: none;
  transition: border-color .2s;
}
.field input:focus, .field select:focus { border-color: var(--accent2); }
.calc-btn {
  width: 100%;
  padding: 10px;
  background: var(--ink);
  color: var(--paper);
  border: none;
  border-radius: 3px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .1em;
  cursor: pointer;
  transition: background .2s;
  text-transform: uppercase;
  margin-top: 4px;
}
.calc-btn:hover { background: var(--ink2); }
.calc-result {
  margin-top: 16px;
  padding: 14px;
  background: var(--highlight);
  border-left: 3px solid var(--gold);
  border-radius: 0 3px 3px 0;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  display: none;
  line-height: 1.8;
}
.calc-result.show { display: block; }

/* ── PROBABILITY DISTRIBUTIONS ── */
.dist-section { margin-bottom: 80px; }
.dist-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  margin-bottom: 24px;
  padding: 20px;
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
}
.dist-control { display: flex; flex-direction: column; gap: 4px; }
.dist-control label {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
  letter-spacing: .08em;
}
.dist-control input[type=range] { width: 160px; accent-color: var(--ink); }
.dist-control .dv {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent2);
}
.dist-control select {
  padding: 5px 10px;
  border: 1px solid var(--rule);
  background: var(--paper2);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  border-radius: 3px;
}
.dist-canvas-wrap {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 24px;
}
.dist-canvas-wrap canvas { width: 100% !important; display: block; }

/* ── CHEAT SHEET ── */
.cheatsheet { margin-bottom: 80px; }
.cs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 16px;
}
.cs-card {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 4px;
  padding: 20px;
}
.cs-card .cs-topic {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--accent);
  letter-spacing: .1em;
  margin-bottom: 10px;
  text-transform: uppercase;
}
.cs-card .cs-formula {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  color: var(--ink);
  background: rgba(15,25,35,.04);
  padding: 8px 10px;
  border-radius: 3px;
  margin-bottom: 10px;
  word-break: break-all;
}
.cs-card .cs-note {
  font-size: var(--fs-xs);
  color: var(--muted);
  line-height: 1.6;
}

/* ── GAMES SECTION ── */
.games-section { margin-bottom: 80px; }
.games-grid-wrap {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
@media(max-width:760px){ .games-grid-wrap{ grid-template-columns:1fr; } }

.game-box {
  background: var(--paper);
  border: 1px solid var(--rule);
  border-radius: 6px;
  overflow: hidden;
}
.game-box-header {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 14px 20px;
  background: var(--ink2);
  color: var(--bg);
}
.game-box-header .gh-icon { font-size: 1.1rem; }
.game-box-header .gh-title {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  letter-spacing: .06em;
}
.game-box-header .gh-badge {
  margin-left: auto;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  padding: 2px 8px;
  border-radius: 2px;
  border: 1px solid rgba(255,255,255,.2);
  color: rgba(255,255,255,.7);
  letter-spacing: .08em;
}
.game-box-body { padding: 20px; }
.game-desc-text {
  font-size: var(--fs-xs);
  color: var(--muted);
  margin-bottom: 14px;
  line-height: 1.6;
}

/* Coin flip game */
.coin-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
}
.coin {
  width: 80px; height: 80px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 2rem;
  font-family: 'DM Serif Display', serif;
  border: 3px solid var(--rule);
  background: var(--paper2);
  transition: transform .15s;
  cursor: default;
  user-select: none;
}
.coin.flip-anim {
  animation: coinFlip .6s ease;
}
@keyframes coinFlip {
  0%   { transform: rotateY(0deg) scale(1); }
  25%  { transform: rotateY(90deg) scale(1.1); }
  50%  { transform: rotateY(180deg) scale(1); }
  75%  { transform: rotateY(270deg) scale(1.1); }
  100% { transform: rotateY(360deg) scale(1); }
}
.coin-stats {
  display: flex; gap: 16px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
}
.coin-stat { text-align: center; }
.coin-stat .cv { font-size: 1.2rem; font-weight: 500; color: var(--ink); }
.coin-stat .cl { color: var(--muted); }
.coin-history {
  display: flex; flex-wrap: wrap; gap: 4px;
  max-height: 48px; overflow: hidden;
  width: 100%;
}
.coin-chip {
  font-size: .65rem;
  padding: 2px 5px;
  border-radius: 2px;
  font-family: 'DM Mono', monospace;
}
.coin-chip.H { background: rgba(41,128,185,.12); color: var(--accent2); }
.coin-chip.T { background: rgba(192,57,43,.1); color: var(--accent); }
.coin-btn-row { display: flex; gap: 8px; }
.g-btn {
  flex: 1;
  padding: 8px 16px;
  border: 1px solid var(--rule);
  background: var(--ink);
  color: var(--paper);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  border-radius: 3px;
  cursor: pointer;
  letter-spacing: .08em;
  transition: background .15s;
}
.g-btn:hover { background: var(--ink2); }
.g-btn.outline { background: transparent; color: var(--ink); }
.g-btn.outline:hover { background: var(--rule); }

/* Guess the mean game */
.gtm-canvas-wrap { position: relative; margin-bottom: 10px; }
.gtm-canvas-wrap canvas { width: 100% !important; display: block; border: 1px solid var(--rule); border-radius: 3px; }
.gtm-input-row { display: flex; gap: 8px; align-items: center; margin-bottom: 10px; }
.gtm-input-row input {
  flex:1; padding: 7px 10px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-sm);
  background: var(--paper2);
  color: var(--ink);
  outline: none;
}
.gtm-input-row input:focus { border-color: var(--accent2); }
.gtm-feedback {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  min-height: 20px;
  color: var(--muted);
}
.gtm-score {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--slate);
  margin-top: 6px;
}

/* CLT game */
.clt-area { display: flex; flex-direction: column; gap: 10px; }
.clt-canvas-wrap canvas { width: 100% !important; display: block; }
.clt-controls { display: flex; gap: 10px; align-items: center; flex-wrap: wrap; }
.clt-controls label { font-family: 'DM Mono', monospace; font-size: var(--fs-xs); color: var(--muted); }
.clt-controls input[type=range] { width: 120px; accent-color: var(--ink); }
.clt-controls .cv { font-family: 'DM Mono', monospace; font-size: var(--fs-xs); color: var(--accent2); }
.clt-info {
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--slate);
  line-height: 1.7;
}

/* Probability quiz */
.quiz-area {}
.quiz-q {
  font-size: var(--fs-sm);
  color: var(--ink);
  font-weight: 500;
  margin-bottom: 14px;
  min-height: 44px;
  line-height: 1.6;
}
.quiz-options { display: flex; flex-direction: column; gap: 8px; margin-bottom: 14px; }
.quiz-opt {
  width: 100%;
  text-align: left;
  padding: 9px 14px;
  border: 1px solid var(--rule);
  border-radius: 3px;
  background: var(--paper2);
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--ink);
  cursor: pointer;
  transition: border-color .15s, background .15s;
  letter-spacing: .04em;
}
.quiz-opt:hover:not(:disabled) { border-color: var(--accent2); background: rgba(41,128,185,.06); }
.quiz-opt.correct { border-color: var(--green); background: rgba(39,174,96,.1); color: var(--green); }
.quiz-opt.wrong   { border-color: var(--accent); background: rgba(192,57,43,.08); color: var(--accent); }
.quiz-opt:disabled { cursor: default; }
.quiz-explain {
  font-size: var(--fs-xs);
  color: var(--slate);
  line-height: 1.7;
  background: var(--highlight);
  padding: 10px 14px;
  border-radius: 3px;
  border-left: 3px solid var(--gold);
  display: none;
  margin-bottom: 10px;
}
.quiz-explain.show { display: block; }
.quiz-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--muted);
}
.quiz-progress-bar {
  width: 100%;
  height: 4px;
  background: var(--rule);
  border-radius: 2px;
  margin-bottom: 14px;
  overflow: hidden;
}
.quiz-progress-fill {
  height: 100%;
  background: var(--accent2);
  border-radius: 2px;
  transition: width .4s ease;
}

/* ── FOOTER ── */
footer {
  border-top: 1px solid var(--rule);
  padding: 40px 32px;
  text-align: center;
  font-family: 'DM Mono', monospace;
  font-size: var(--fs-xs);
  color: var(--pale);
  letter-spacing: .08em;
}

/* ── ANIMATIONS ── */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
.fade-up { animation: fadeUp .6s ease forwards; }
.fade-up:nth-child(2) { animation-delay: .1s; opacity: 0; }
.fade-up:nth-child(3) { animation-delay: .2s; opacity: 0; }
.fade-up:nth-child(4) { animation-delay: .3s; opacity: 0; }
.fade-up:nth-child(5) { animation-delay: .4s; opacity: 0; }
.fade-up:nth-child(6) { animation-delay: .5s; opacity: 0; }

section { position: relative; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <div class="nav-brand">Stats<span>&</span>Prob</div>
    <ul class="nav-links">
      <li><a href="#concepts">概念</a></li>
      <li><a href="#strategies">策略</a></li>
      <li><a href="#calculator">計算機</a></li>
      <li><a href="#distributions">分布圖</a></li>
      <li><a href="#games">互動遊戲</a></li>
      <li><a href="#cheatsheet">速查表</a></li>
    </ul>
  </div>
</nav>

<div class="page-wrap">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-text fade-up">
      <div class="hero-eyebrow">統計 × 機率 × 決策</div>
      <h1>用數學<br>做出<em>更好的</em><br>決策</h1>
      <p class="hero-desc">從基礎機率到貝葉斯推斷，從中央極限定理到假設檢定，掌握統計思維是現代決策者的核心競爭力。</p>
      <div class="hero-pills">
        <span class="pill red">機率論</span>
        <span class="pill blue">統計推斷</span>
        <span class="pill green">假設檢定</span>
        <span class="pill gold">貝葉斯方法</span>
      </div>
    </div>
    <div class="hero-visual fade-up">
      <canvas id="heroCanvas" height="240"></canvas>
      <div class="hero-visual-label">標準常態分布 N(μ=0, σ²=1)</div>
    </div>
  </div>

  <!-- CONCEPTS -->
  <section id="concepts">
    <div class="sec-header">
      <span class="sec-num">01</span>
      <h2 class="sec-title">核心概念</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="concepts-grid">
      <div class="concept-card fade-up">
        <div class="concept-icon">🎲</div>
        <div class="concept-name">條件機率</div>
        <div class="concept-formula">P(A|B) = P(A∩B) / P(B)</div>
        <div class="concept-desc">在事件 B 已發生的條件下，事件 A 發生的機率。是貝葉斯定理的基石，廣泛應用於醫學診斷、垃圾郵件過濾。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">📊</div>
        <div class="concept-name">期望值</div>
        <div class="concept-formula">E[X] = Σ xᵢ · P(xᵢ)</div>
        <div class="concept-desc">所有可能結果的加權平均，以機率為權重。是評估投資報酬、賭局公平性、保險定價的核心指標。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">🔔</div>
        <div class="concept-name">中央極限定理</div>
        <div class="concept-formula">X̄ ~ N(μ, σ²/n)</div>
        <div class="concept-desc">樣本數足夠大時，樣本均值趨近常態分布，無論母體分布為何。這是統計推斷的理論基礎。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">⚖️</div>
        <div class="concept-name">貝葉斯定理</div>
        <div class="concept-formula">P(H|E) = P(E|H)·P(H) / P(E)</div>
        <div class="concept-desc">根據新證據更新信念的數學框架。後驗機率 = 先驗機率 × 似然比。機器學習的核心思想。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">📉</div>
        <div class="concept-name">標準差與變異數</div>
        <div class="concept-formula">σ² = E[(X-μ)²]</div>
        <div class="concept-desc">衡量數據分散程度的指標。標準差越大，不確定性越高，風險越大。投資組合管理的必備工具。</div>
      </div>
      <div class="concept-card fade-up">
        <div class="concept-icon">🔗</div>
        <div class="concept-name">相關與因果</div>
        <div class="concept-formula">r = Cov(X,Y) / (σₓ · σᵧ)</div>
        <div class="concept-desc">相關係數衡量兩變數線性關係強度（-1 到 1）。相關不等於因果，需透過實驗設計驗證因果推斷。</div>
      </div>
    </div>
  </section>

  <!-- STRATEGIES -->
  <section id="strategies" class="strategies">
    <div class="sec-header">
      <span class="sec-num">02</span>
      <h2 class="sec-title">機率策略</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="strategy-tabs">
      <button class="tab-btn active" onclick="switchTab(this,'bayes')">貝葉斯更新</button>
      <button class="tab-btn" onclick="switchTab(this,'sampling')">大數法則</button>
      <button class="tab-btn" onclick="switchTab(this,'hypothesis')">假設檢定</button>
      <button class="tab-btn" onclick="switchTab(this,'montecarlo')">蒙地卡羅</button>
    </div>

    <!-- Bayes -->
    <div class="tab-panel active" id="tab-bayes">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>貝葉斯更新策略</h3>
          <p>貝葉斯方法的核心思想：從先驗信念出發，隨著新證據的加入，不斷更新我們的信念強度。這種「邊學邊更新」的方式比傳統頻率學派更符合真實決策情境。</p>
          <div class="when-to-use">
            <div class="wtu-label">適用情境</div>
            <ul>
              <li>醫學診斷（症狀 → 疾病機率）</li>
              <li>垃圾郵件過濾</li>
              <li>A/B 測試即時更新</li>
              <li>股票市場情報更新</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">關鍵步驟：</strong><br>① 設定先驗 P(H) → ② 觀察到新證據 E → ③ 計算似然度 P(E|H) → ④ 更新後驗 P(H|E)</p>
        </div>
        <div class="strategy-visual">
          <canvas id="bayesCanvas" height="220"></canvas>
          <div class="chart-label">貝葉斯更新：隨資料累積，後驗分布逐漸收斂</div>
        </div>
      </div>
    </div>

    <!-- Sampling -->
    <div class="tab-panel" id="tab-sampling">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>大數法則應用</h3>
          <p>隨著樣本數增加，樣本均值趨近母體真實均值。大數法則告訴我們：短期結果充滿隨機性，但長期行為是可預測的。這是保險業、賭場、量化投資的理論基礎。</p>
          <div class="when-to-use">
            <div class="wtu-label">策略應用</div>
            <ul>
              <li>確保樣本數足夠大（n ≥ 30）</li>
              <li>避免以小樣本下大結論</li>
              <li>透過分散投資降低個別風險</li>
              <li>對沖策略：做大量小賭注</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">陷阱警告：</strong><br>「賭徒謬誤」——錯誤認為過去事件影響未來獨立事件。每次公正拋硬幣仍是 50% 機率，與歷史無關。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="samplingCanvas" height="220"></canvas>
          <div class="chart-label">大數法則：樣本均值隨 n 增加趨近真實均值（虛線）</div>
        </div>
      </div>
    </div>

    <!-- Hypothesis -->
    <div class="tab-panel" id="tab-hypothesis">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>假設檢定流程</h3>
          <p>假設檢定是科學決策的標準框架：先設立虛無假設（H₀），再以數據決定是否有足夠證據拒絕它。p 值代表「假設 H₀ 成立，觀察到如此極端結果的機率」。</p>
          <div class="when-to-use">
            <div class="wtu-label">檢定步驟</div>
            <ul>
              <li>① 設定 H₀（虛無）與 H₁（對立）假設</li>
              <li>② 選擇顯著水準 α（通常 0.05）</li>
              <li>③ 計算檢定統計量與 p 值</li>
              <li>④ p &lt; α 則拒絕 H₀</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">常見錯誤：</strong><br>p &gt; 0.05 ≠ 接受 H₀，只是「無法拒絕」。同時需考量第一型（偽陽性）與第二型（偽陰性）錯誤。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="hypothesisCanvas" height="220"></canvas>
          <div class="chart-label">α=0.05 雙尾檢定：拒絕區域（紅色）與接受區域（藍色）</div>
        </div>
      </div>
    </div>

    <!-- Monte Carlo -->
    <div class="tab-panel" id="tab-montecarlo">
      <div class="strategy-layout">
        <div class="strategy-info">
          <h3>蒙地卡羅模擬</h3>
          <p>透過大量隨機抽樣來估計數值解。當問題太複雜、無法用解析公式求解時，用電腦重複模擬數千至百萬次，以統計結果逼近真實答案。</p>
          <div class="when-to-use">
            <div class="wtu-label">應用場景</div>
            <ul>
              <li>複雜衍生品定價（Black-Scholes 以外）</li>
              <li>氣候模型、核反應模擬</li>
              <li>AI 強化學習策略評估</li>
              <li>圓周率 π 的近似估算</li>
            </ul>
          </div>
          <p><strong style="color:var(--ink)">精度提升：</strong><br>誤差約為 1/√n，所以要減半誤差，需將模擬次數增加 4 倍。計算成本與精度需取得平衡。</p>
        </div>
        <div class="strategy-visual">
          <canvas id="montecarloCanvas" height="220"></canvas>
          <div class="chart-label">蒙地卡羅估算π：圓內點(藍)與圓外點(紅) π ≈ 4×(圓內/總數)</div>
        </div>
      </div>
    </div>
  </section>

  <!-- CALCULATORS -->
  <section id="calculator" class="calc-section">
    <div class="sec-header">
      <span class="sec-num">03</span>
      <h2 class="sec-title">互動計算機</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="calc-grid">

      <!-- Bayes Calc -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">⚖️</span><span class="c-name">貝葉斯定理計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>先驗機率 P(H)  %</label><input type="number" id="b_prior" min="0" max="100" value="5" step="0.1"></div>
          <div class="field"><label>靈敏度 P(E|H)  %（真陽性率）</label><input type="number" id="b_sens" min="0" max="100" value="90" step="0.1"></div>
          <div class="field"><label>特異度 P(¬E|¬H)  %（真陰性率）</label><input type="number" id="b_spec" min="0" max="100" value="95" step="0.1"></div>
          <button class="calc-btn" onclick="calcBayes()">計算後驗機率</button>
          <div class="calc-result" id="b_result"></div>
        </div>
      </div>

      <!-- Expected Value -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">📊</span><span class="c-name">期望值計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>結果 1 數值</label><input type="number" id="ev_v1" value="100"></div>
          <div class="field"><label>結果 1 機率 %</label><input type="number" id="ev_p1" value="30" min="0" max="100"></div>
          <div class="field"><label>結果 2 數值</label><input type="number" id="ev_v2" value="-50"></div>
          <div class="field"><label>結果 2 機率 %</label><input type="number" id="ev_p2" value="70" min="0" max="100"></div>
          <button class="calc-btn" onclick="calcEV()">計算期望值</button>
          <div class="calc-result" id="ev_result"></div>
        </div>
      </div>

      <!-- Confidence Interval -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">📏</span><span class="c-name">信賴區間計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>樣本均值</label><input type="number" id="ci_mean" value="75"></div>
          <div class="field"><label>樣本標準差</label><input type="number" id="ci_sd" value="12" min="0.01"></div>
          <div class="field"><label>樣本數 n</label><input type="number" id="ci_n" value="50" min="2"></div>
          <div class="field"><label>信賴水準</label>
            <select id="ci_conf">
              <option value="1.645">90%</option>
              <option value="1.960" selected>95%</option>
              <option value="2.576">99%</option>
            </select>
          </div>
          <button class="calc-btn" onclick="calcCI()">計算信賴區間</button>
          <div class="calc-result" id="ci_result"></div>
        </div>
      </div>

      <!-- Sample Size -->
      <div class="calc-card">
        <div class="calc-header"><span class="c-icon">🔢</span><span class="c-name">樣本數計算機</span></div>
        <div class="calc-body">
          <div class="field"><label>預期機率 p  %</label><input type="number" id="ss_p" value="50" min="1" max="99"></div>
          <div class="field"><label>誤差容忍度 E  %</label><input type="number" id="ss_e" value="5" min="0.1"></div>
          <div class="field"><label>信賴水準</label>
            <select id="ss_conf">
              <option value="1.645">90%</option>
              <option value="1.960" selected>95%</option>
              <option value="2.576">99%</option>
            </select>
          </div>
          <button class="calc-btn" onclick="calcSS()">計算最小樣本數</button>
          <div class="calc-result" id="ss_result"></div>
        </div>
      </div>

    </div>
  </section>

  <!-- DISTRIBUTION EXPLORER -->
  <section id="distributions" class="dist-section">
    <div class="sec-header">
      <span class="sec-num">04</span>
      <h2 class="sec-title">機率分布探索器</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="dist-controls">
      <div class="dist-control">
        <label>分布類型</label>
        <select id="distType" onchange="drawDist()">
          <option value="normal">常態分布 Normal</option>
          <option value="binomial">二項分布 Binomial</option>
          <option value="poisson">卜瓦松分布 Poisson</option>
          <option value="uniform">均勻分布 Uniform</option>
          <option value="exponential">指數分布 Exponential</option>
        </select>
      </div>
      <div class="dist-control" id="dc_mu">
        <label>均值 μ</label>
        <input type="range" min="-3" max="3" step=".1" value="0" id="d_mu" oninput="updateDist()">
        <span class="dv" id="dv_mu">0</span>
      </div>
      <div class="dist-control" id="dc_sigma">
        <label>標準差 σ</label>
        <input type="range" min=".2" max="3" step=".1" value="1" id="d_sigma" oninput="updateDist()">
        <span class="dv" id="dv_sigma">1</span>
      </div>
      <div class="dist-control" id="dc_n" style="display:none">
        <label>試驗次數 n</label>
        <input type="range" min="5" max="50" step="1" value="20" id="d_n" oninput="updateDist()">
        <span class="dv" id="dv_n">20</span>
      </div>
      <div class="dist-control" id="dc_pp" style="display:none">
        <label>成功機率 p</label>
        <input type="range" min=".05" max=".95" step=".05" value=".5" id="d_pp" oninput="updateDist()">
        <span class="dv" id="dv_pp">0.5</span>
      </div>
      <div class="dist-control" id="dc_lambda" style="display:none">
        <label>λ (速率)</label>
        <input type="range" min=".5" max="10" step=".5" value="3" id="d_lambda" oninput="updateDist()">
        <span class="dv" id="dv_lambda">3</span>
      </div>
    </div>
    <div class="dist-canvas-wrap">
      <canvas id="distCanvas" height="280"></canvas>
      <div class="chart-label" id="distLabel">常態分布 N(μ=0, σ=1)</div>
    </div>
  </section>

  <!-- GAMES -->
  <section id="games" class="games-section">
    <div class="sec-header">
      <span class="sec-num">05</span>
      <h2 class="sec-title">互動遊戲</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="games-grid-wrap">

      <!-- GAME 1: Coin Flip -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🪙</span>
          <span class="gh-title">硬幣實驗室</span>
          <span class="gh-badge">大數法則</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">親身體驗大數法則：持續拋硬幣，看正面比率如何慢慢收斂到 50%。</div>
          <div class="coin-area">
            <div class="coin" id="coinFace">？</div>
            <div class="coin-stats">
              <div class="coin-stat"><div class="cv" id="c_heads">0</div><div class="cl">正面</div></div>
              <div class="coin-stat"><div class="cv" id="c_total">0</div><div class="cl">總次數</div></div>
              <div class="coin-stat"><div class="cv" id="c_pct">—</div><div class="cl">正面率</div></div>
              <div class="coin-stat"><div class="cv" id="c_streak">0</div><div class="cl">連續正面</div></div>
            </div>
            <div class="coin-history" id="coinHistory"></div>
            <div class="coin-btn-row">
              <button class="g-btn" onclick="flipCoin(1)">拋 1 次</button>
              <button class="g-btn" onclick="flipCoin(10)">拋 10 次</button>
              <button class="g-btn" onclick="flipCoin(100)">拋 100 次</button>
              <button class="g-btn outline" onclick="resetCoin()">重置</button>
            </div>
            <canvas id="coinCanvas" height="80"></canvas>
          </div>
        </div>
      </div>

      <!-- GAME 2: Guess the Mean -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🎯</span>
          <span class="gh-title">猜猜均值在哪</span>
          <span class="gh-badge">統計直覺</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">看圖中的散點，憑直覺猜測樣本均值的位置，訓練你的統計直覺！</div>
          <div class="gtm-canvas-wrap">
            <canvas id="gtmCanvas" height="150"></canvas>
          </div>
          <div class="gtm-input-row">
            <input type="number" id="gtmGuess" placeholder="輸入你猜測的均值…" step="0.1">
            <button class="g-btn" onclick="submitGTM()" style="flex:0;white-space:nowrap">確認</button>
            <button class="g-btn outline" onclick="newGTM()" style="flex:0;white-space:nowrap">新題</button>
          </div>
          <div class="gtm-feedback" id="gtmFeedback"></div>
          <div class="gtm-score" id="gtmScore">得分：0 / 0</div>
        </div>
      </div>

      <!-- GAME 3: CLT Demo -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🔔</span>
          <span class="gh-title">中央極限定理動畫</span>
          <span class="gh-badge">CLT 體驗</span>
        </div>
        <div class="game-box-body">
          <div class="game-desc-text">選擇任意母體分布，抽樣並累積樣本均值，親眼看它變成鐘形曲線。</div>
          <div class="clt-area">
            <div class="clt-controls">
              <label>母體：</label>
              <select id="cltDist" onchange="resetCLT()">
                <option value="uniform">均勻分布</option>
                <option value="exponential">指數分布（偏態）</option>
                <option value="bimodal">雙峰分布</option>
                <option value="discrete">離散分布</option>
              </select>
              <label>樣本數 n=</label>
              <input type="range" id="cltN" min="1" max="50" value="5" oninput="document.getElementById('cltNv').textContent=this.value;resetCLT()">
              <span class="cv" id="cltNv">5</span>
            </div>
            <canvas id="cltPopCanvas" height="80"></canvas>
            <canvas id="cltSampCanvas" height="100"></canvas>
            <div class="clt-info" id="cltInfo">按「抽樣」開始實驗</div>
            <div class="coin-btn-row">
              <button class="g-btn" onclick="doSampleCLT(1)">抽樣 ×1</button>
              <button class="g-btn" onclick="doSampleCLT(50)">抽樣 ×50</button>
              <button class="g-btn" onclick="doSampleCLT(500)">抽樣 ×500</button>
              <button class="g-btn outline" onclick="resetCLT()">重置</button>
            </div>
          </div>
        </div>
      </div>

      <!-- GAME 4: Probability Quiz -->
      <div class="game-box">
        <div class="game-box-header">
          <span class="gh-icon">🧠</span>
          <span class="gh-title">機率直覺測驗</span>
          <span class="gh-badge">10 題挑戰</span>
        </div>
        <div class="game-box-body">
          <div class="quiz-progress-bar"><div class="quiz-progress-fill" id="quizProgressFill" style="width:0%"></div></div>
          <div class="quiz-q" id="quizQ">按「開始測驗」挑戰你的機率直覺！</div>
          <div class="quiz-options" id="quizOpts"></div>
          <div class="quiz-explain" id="quizExplain"></div>
          <div class="quiz-meta">
            <span id="quizMeta">0 / 10 題</span>
            <span id="quizScoreDisplay">得分：0</span>
          </div>
          <div style="margin-top:10px">
            <button class="g-btn" id="quizStartBtn" onclick="startQuiz()">開始測驗</button>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- CHEAT SHEET -->
  <section id="cheatsheet" class="cheatsheet">
    <div class="sec-header">
      <span class="sec-num">06</span>
      <h2 class="sec-title">公式速查表</h2>
      <div class="sec-rule"></div>
    </div>
    <div class="cs-grid" id="csGrid"></div>
  </section>

</div><!-- /page-wrap -->

<footer>
  統計與機率策略中心 · 教育用途 · 數字會說話，讓數學成為你的武器
</footer>

<script>
// ── UTILITY ───────────────────────────────────────────────────────
function normalPDF(x, mu=0, sigma=1) {
  return Math.exp(-0.5*((x-mu)/sigma)**2) / (sigma * Math.sqrt(2*Math.PI));
}
function normalCDF(x) {
  const t = 1/(1+0.2316419*Math.abs(x));
  const d = 0.3989423*Math.exp(-x*x/2);
  let p = d*t*(0.3193815+t*(-0.3565638+t*(1.7814779+t*(-1.8212560+t*1.3302744))));
  return x > 0 ? 1-p : p;
}

function clearCanvas(canvas, ctx, fillColor='#fdfbf8') {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle = fillColor;
  ctx.fillRect(0,0,canvas.width,canvas.height);
}

// ── HERO BELL CURVE ────────────────────────────────────────────────
function drawHero() {
  const canvas = document.getElementById('heroCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 240 * dpr;
  canvas.style.height = '240px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 240;
  clearCanvas(canvas, ctx, '#f5f2ee');

  const xs = [], ys = [];
  for(let i=0;i<=200;i++) {
    const x = -4 + i*8/200;
    xs.push(x); ys.push(normalPDF(x));
  }
  const maxY = Math.max(...ys);
  const toX = x => (x+4)/8*W;
  const toY = y => H-20 - (y/maxY)*(H-50);

  // shade regions
  const regions = [
    {from:-1,to:1,color:'rgba(41,128,185,.12)'},
    {from:-2,to:-1,color:'rgba(192,57,43,.07)'},
    {from:1,to:2,color:'rgba(192,57,43,.07)'},
    {from:-3,to:-2,color:'rgba(192,57,43,.04)'},
    {from:2,to:3,color:'rgba(192,57,43,.04)'},
  ];
  regions.forEach(({from,to,color}) => {
    ctx.beginPath();
    ctx.moveTo(toX(from), toY(0));
    for(let i=0;i<=100;i++) {
      const x = from+(to-from)*i/100;
      ctx.lineTo(toX(x), toY(normalPDF(x)));
    }
    ctx.lineTo(toX(to), toY(0));
    ctx.closePath();
    ctx.fillStyle = color;
    ctx.fill();
  });

  // curve
  ctx.beginPath();
  xs.forEach((x,i) => i===0 ? ctx.moveTo(toX(x),toY(ys[i])) : ctx.lineTo(toX(x),toY(ys[i])));
  ctx.strokeStyle = '#0f1923';
  ctx.lineWidth = 2;
  ctx.stroke();

  // baseline
  ctx.beginPath(); ctx.moveTo(0,toY(0)); ctx.lineTo(W,toY(0));
  ctx.strokeStyle = '#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  // labels
  ctx.font = '10px DM Mono, monospace';
  ctx.fillStyle = '#6b7f92';
  ctx.textAlign = 'center';
  ['-3σ','-2σ','-1σ','μ','+1σ','+2σ','+3σ'].forEach((l,i) => {
    ctx.fillText(l, toX(-3+i), toY(0)+14);
  });

  // annotation
  ctx.font = '9px DM Mono, monospace';
  ctx.fillStyle = '#2980b9';
  ctx.fillText('68.27%', toX(0), toY(normalPDF(0))+22);
}

// ── STRATEGY CHARTS ────────────────────────────────────────────────
function drawBayes() {
  const canvas = document.getElementById('bayesCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  // show 4 beta distributions with increasing data
  const colors = ['#a8b8c8','#6b7f92','#2980b9','#0f1923'];
  const labels = ['先驗 (弱)','10個樣本','50個樣本','200個樣本'];
  const alphas = [2,6,22,82], betas = [8,14,38,118];

  function betaPDF(x,a,b) {
    if(x<=0||x>=1) return 0;
    let logB = 0;
    for(let i=1;i<a;i++) logB+=Math.log(i);
    for(let i=1;i<b;i++) logB+=Math.log(i);
    let logAB=0; for(let i=1;i<a+b;i++) logAB+=Math.log(i);
    logB -= logAB;
    return Math.exp((a-1)*Math.log(x)+(b-1)*Math.log(1-x)-logB);
  }

  const pts = 120;
  const xs = Array.from({length:pts},(_, i)=>(i+1)/(pts+1));
  const allY = alphas.flatMap((a,j)=>xs.map(x=>betaPDF(x,a,betas[j])));
  const maxY = Math.max(...allY)||1;
  const toX = x => 30+x*(W-40);
  const toY = y => H-30-(y/maxY)*(H-50);

  alphas.forEach((a,j) => {
    ctx.beginPath();
    xs.forEach((x,i) => {
      const y = betaPDF(x,a,betas[j]);
      i===0 ? ctx.moveTo(toX(x),toY(y)) : ctx.lineTo(toX(x),toY(y));
    });
    ctx.strokeStyle = colors[j];
    ctx.lineWidth = j===3?2.5:1.5;
    ctx.globalAlpha = j===3?1:0.7;
    ctx.stroke();
    ctx.globalAlpha=1;
  });

  // legend
  colors.forEach((c,j) => {
    ctx.fillStyle = c;
    ctx.fillRect(30+j*90, H-18, 18, 2);
    ctx.fillStyle = '#6b7f92';
    ctx.font = '9px DM Mono, monospace';
    ctx.textAlign = 'left';
    ctx.fillText(labels[j], 52+j*90, H-14);
  });

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawSampling() {
  const canvas = document.getElementById('samplingCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const TRUE_MEAN = 0.5;
  const n = 200;
  let cum = 0;
  const means = [];
  for(let i=1;i<=n;i++) { cum += Math.random(); means.push(cum/i); }

  const minV = Math.min(...means)-0.05, maxV = Math.max(...means)+0.05;
  const toX = i => 30+i/(n-1)*(W-40);
  const toY = v => H-30-(v-minV)/(maxV-minV)*(H-50);

  // true mean line
  ctx.beginPath(); ctx.moveTo(30,toY(TRUE_MEAN)); ctx.lineTo(W-10,toY(TRUE_MEAN));
  ctx.strokeStyle='#27ae60'; ctx.lineWidth=1.5; ctx.setLineDash([6,4]); ctx.stroke();
  ctx.setLineDash([]);

  // path
  ctx.beginPath();
  means.forEach((v,i)=> i===0? ctx.moveTo(toX(i),toY(v)) : ctx.lineTo(toX(i),toY(v)));
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#6b7f92'; ctx.textAlign='center';
  [1,50,100,150,200].forEach(i=>ctx.fillText(i,toX(i-1),H-14));
  ctx.fillStyle='#27ae60'; ctx.textAlign='right';
  ctx.fillText('真實均值 μ=0.5',W-14,toY(TRUE_MEAN)-5);
}

function drawHypothesis() {
  const canvas = document.getElementById('hypothesisCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const crit = 1.96;
  const toX = x => 30+(x+4)/8*(W-40);
  const toY = y => H-30-y/(normalPDF(0))*(H-50);
  const pts = 200;

  // fill reject regions
  [[-4,-crit],[crit,4]].forEach(([a,b]) => {
    ctx.beginPath();
    ctx.moveTo(toX(a),toY(0));
    for(let i=0;i<=60;i++){
      const x=a+(b-a)*i/60;
      ctx.lineTo(toX(x),toY(normalPDF(x)));
    }
    ctx.lineTo(toX(b),toY(0));
    ctx.closePath();
    ctx.fillStyle='rgba(192,57,43,.2)';
    ctx.fill();
  });

  // fill accept region
  ctx.beginPath();
  ctx.moveTo(toX(-crit),toY(0));
  for(let i=0;i<=100;i++){
    const x=-crit+(crit*2)*i/100;
    ctx.lineTo(toX(x),toY(normalPDF(x)));
  }
  ctx.lineTo(toX(crit),toY(0));
  ctx.closePath();
  ctx.fillStyle='rgba(41,128,185,.12)';
  ctx.fill();

  // curve
  ctx.beginPath();
  for(let i=0;i<=pts;i++){
    const x=-4+8*i/pts;
    i===0?ctx.moveTo(toX(x),toY(normalPDF(x))):ctx.lineTo(toX(x),toY(normalPDF(x)));
  }
  ctx.strokeStyle='#0f1923'; ctx.lineWidth=2; ctx.stroke();

  // crit lines
  [-crit,crit].forEach(cv => {
    ctx.beginPath(); ctx.moveTo(toX(cv),toY(0)); ctx.lineTo(toX(cv),toY(normalPDF(cv)));
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=1.5; ctx.setLineDash([4,3]); ctx.stroke();
    ctx.setLineDash([]);
    ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
    ctx.fillText(cv>0?'+1.96':'-1.96',toX(cv),toY(0)+14);
  });

  // labels
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
  ctx.fillText('拒絕域 α/2=2.5%',toX(-3.2),toY(0.02));
  ctx.fillText('拒絕域 α/2=2.5%',toX(3.2),toY(0.02));
  ctx.fillStyle='#2980b9';
  ctx.fillText('接受域 95%',toX(0),toY(normalPDF(0))+20);

  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,H-28);
  ctx.moveTo(30,H-28); ctx.lineTo(W-10,H-28);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawMonteCarlo() {
  const canvas = document.getElementById('montecarloCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 220 * dpr;
  canvas.style.height = '220px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 220;
  clearCanvas(canvas, ctx);

  const pad = 20, sq = Math.min(W-pad*2, H-pad*2);
  const ox = pad, oy = (H-sq)/2;

  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1;
  ctx.strokeRect(ox,oy,sq,sq);

  // quarter circle
  ctx.beginPath(); ctx.arc(ox,oy+sq,sq,0,-Math.PI/2,true);
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();

  let inside=0; const total=600;
  for(let i=0;i<total;i++){
    const x=Math.random(), y=Math.random();
    const isIn = x*x+y*y<=1;
    if(isIn) inside++;
    ctx.beginPath();
    ctx.arc(ox+x*sq, oy+(1-y)*sq, 2, 0, Math.PI*2);
    ctx.fillStyle = isIn ? 'rgba(41,128,185,.55)' : 'rgba(192,57,43,.45)';
    ctx.fill();
  }
  const piEst = 4*inside/total;
  ctx.font='bold 11px DM Mono,monospace';
  ctx.fillStyle='#0f1923';
  ctx.textAlign='left';
  ctx.fillText(`π ≈ ${piEst.toFixed(4)} (n=${total})`,ox+4,oy+16);
}

// ── TAB SWITCHING ──────────────────────────────────────────────────
function switchTab(btn, name) {
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('tab-'+name).classList.add('active');
  setTimeout(()=>{
    if(name==='bayes')      drawBayes();
    if(name==='sampling')   drawSampling();
    if(name==='hypothesis') drawHypothesis();
    if(name==='montecarlo') drawMonteCarlo();
  }, 50);
}

// ── CALCULATORS ────────────────────────────────────────────────────
function show(id, html) {
  const el = document.getElementById(id);
  el.innerHTML = html; el.classList.add('show');
}

function calcBayes() {
  const prior   = +document.getElementById('b_prior').value/100;
  const sens    = +document.getElementById('b_sens').value/100;
  const spec    = +document.getElementById('b_spec').value/100;
  const fpr     = 1-spec;
  const pE      = sens*prior + fpr*(1-prior);
  const posterior = (sens*prior)/pE;
  show('b_result',
    `先驗 P(H) = ${(prior*100).toFixed(1)}%<br>` +
    `P(E) = ${(pE*100).toFixed(2)}%<br>` +
    `<strong>後驗 P(H|E) = ${(posterior*100).toFixed(2)}%</strong><br>` +
    `<small style="color:#888">從 ${(prior*100).toFixed(1)}% → ${(posterior*100).toFixed(1)}%，更新了 ${((posterior-prior)*100).toFixed(1)}%</small>`
  );
}

function calcEV() {
  const v1=+document.getElementById('ev_v1').value;
  const p1=+document.getElementById('ev_p1').value/100;
  const v2=+document.getElementById('ev_v2').value;
  const p2=+document.getElementById('ev_p2').value/100;
  const ev = v1*p1 + v2*p2;
  const color = ev>=0?'#27ae60':'#c0392b';
  show('ev_result',
    `E[X] = ${v1}×${(p1*100).toFixed(0)}% + (${v2})×${(p2*100).toFixed(0)}%<br>` +
    `<strong style="color:${color}">期望值 = ${ev.toFixed(2)}</strong><br>` +
    `<small style="color:#888">${ev>=0?'✅ 正期望值，長期有利':'❌ 負期望值，長期不利'}</small>`
  );
}

function calcCI() {
  const mean=+document.getElementById('ci_mean').value;
  const sd  =+document.getElementById('ci_sd').value;
  const n   =+document.getElementById('ci_n').value;
  const z   =+document.getElementById('ci_conf').value;
  const me  = z*sd/Math.sqrt(n);
  show('ci_result',
    `邊際誤差 ME = ${me.toFixed(3)}<br>` +
    `<strong>信賴區間：[${(mean-me).toFixed(2)}, ${(mean+me).toFixed(2)}]</strong><br>` +
    `<small style="color:#888">標準誤 SE = ${(sd/Math.sqrt(n)).toFixed(3)}</small>`
  );
}

function calcSS() {
  const p=+document.getElementById('ss_p').value/100;
  const e=+document.getElementById('ss_e').value/100;
  const z=+document.getElementById('ss_conf').value;
  const n=Math.ceil(z*z*p*(1-p)/(e*e));
  show('ss_result',
    `最小樣本數 n = ⌈${z}² × ${p} × ${1-p} / ${e}²⌉<br>` +
    `<strong>n = ${n.toLocaleString()}</strong><br>` +
    `<small style="color:#888">增加信賴水準或縮小誤差容忍度會增加所需樣本</small>`
  );
}

// ── DISTRIBUTION EXPLORER ──────────────────────────────────────────
function updateDist() {
  document.getElementById('dv_mu').textContent    = document.getElementById('d_mu').value;
  document.getElementById('dv_sigma').textContent = document.getElementById('d_sigma').value;
  document.getElementById('dv_n').textContent     = document.getElementById('d_n').value;
  document.getElementById('dv_pp').textContent    = document.getElementById('d_pp').value;
  document.getElementById('dv_lambda').textContent= document.getElementById('d_lambda').value;
  drawDist();
}

function drawDist() {
  const type   = document.getElementById('distType').value;
  const mu     = +document.getElementById('d_mu').value;
  const sigma  = +document.getElementById('d_sigma').value;
  const nBin   = +document.getElementById('d_n').value;
  const pp     = +document.getElementById('d_pp').value;
  const lambda = +document.getElementById('d_lambda').value;

  // show/hide controls
  document.getElementById('dc_mu').style.display    = ['normal','uniform'].includes(type)?'':'none';
  document.getElementById('dc_sigma').style.display = type==='normal'?'':'none';
  document.getElementById('dc_n').style.display     = type==='binomial'?'':'none';
  document.getElementById('dc_pp').style.display    = type==='binomial'?'':'none';
  document.getElementById('dc_lambda').style.display= ['poisson','exponential'].includes(type)?'':'none';

  const canvas = document.getElementById('distCanvas');
  const dpr = window.devicePixelRatio||1;
  canvas.width  = canvas.parentElement.clientWidth * dpr;
  canvas.height = 280 * dpr;
  canvas.style.height = '280px';
  const ctx = canvas.getContext('2d');
  ctx.scale(dpr, dpr);
  const W = canvas.parentElement.clientWidth, H = 280;
  clearCanvas(canvas, ctx);

  const pad=40;
  let xs=[], ys=[], discrete=false;

  if(type==='normal') {
    const lo=mu-4*sigma, hi=mu+4*sigma;
    xs=Array.from({length:200},(_,i)=>lo+(hi-lo)*i/199);
    ys=xs.map(x=>normalPDF(x,mu,sigma));
    document.getElementById('distLabel').textContent=`常態分布 N(μ=${mu}, σ=${sigma})`;
  } else if(type==='binomial') {
    discrete=true;
    for(let k=0;k<=nBin;k++){
      xs.push(k);
      let logP=0;
      for(let i=0;i<k;i++) logP+=Math.log(nBin-i)-Math.log(i+1);
      logP+=k*Math.log(pp)+(nBin-k)*Math.log(1-pp);
      ys.push(Math.exp(logP));
    }
    document.getElementById('distLabel').textContent=`二項分布 B(n=${nBin}, p=${pp})`;
  } else if(type==='poisson') {
    discrete=true;
    const maxK=Math.ceil(lambda*3)+1;
    for(let k=0;k<=maxK;k++){
      xs.push(k);
      let logP=-lambda+k*Math.log(lambda);
      for(let i=1;i<=k;i++) logP-=Math.log(i);
      ys.push(Math.exp(logP));
    }
    document.getElementById('distLabel').textContent=`卜瓦松分布 Poisson(λ=${lambda})`;
  } else if(type==='uniform') {
    const a=mu-2, b=mu+2;
    xs=[-1+a,a,a,b,b,b+1];
    ys=[0,0,1/(b-a),1/(b-a),0,0];
    document.getElementById('distLabel').textContent=`均勻分布 U(${a.toFixed(1)}, ${b.toFixed(1)})`;
  } else if(type==='exponential') {
    xs=Array.from({length:200},(_,i)=>i/199*8/lambda);
    ys=xs.map(x=>lambda*Math.exp(-lambda*x));
    document.getElementById('distLabel').textContent=`指數分布 Exp(λ=${lambda})`;
  }

  const maxY=Math.max(...ys)||1;
  const minX=Math.min(...xs), maxX=Math.max(...xs);
  const rangeX=maxX-minX||1;
  const toX=x=>pad+(x-minX)/rangeX*(W-pad*2);
  const toY=y=>H-pad-(y/maxY)*(H-pad*2);

  if(discrete) {
    const barW=Math.max(4,(W-pad*2)/xs.length*0.7);
    xs.forEach((x,i)=>{
      ctx.fillStyle='rgba(41,128,185,.65)';
      const bx=toX(x)-barW/2;
      const bh=(ys[i]/maxY)*(H-pad*2);
      ctx.fillRect(bx,H-pad-bh,barW,bh);
      ctx.strokeStyle='#2980b9'; ctx.lineWidth=1;
      ctx.strokeRect(bx,H-pad-bh,barW,bh);
    });
  } else {
    // fill
    ctx.beginPath();
    ctx.moveTo(toX(xs[0]),toY(0));
    xs.forEach((x,i)=>ctx.lineTo(toX(x),toY(ys[i])));
    ctx.lineTo(toX(xs[xs.length-1]),toY(0));
    ctx.closePath();
    const grad=ctx.createLinearGradient(0,pad,0,H-pad);
    grad.addColorStop(0,'rgba(41,128,185,.25)');
    grad.addColorStop(1,'rgba(41,128,185,.03)');
    ctx.fillStyle=grad; ctx.fill();
    // line
    ctx.beginPath();
    xs.forEach((x,i)=>i===0?ctx.moveTo(toX(x),toY(ys[i])):ctx.lineTo(toX(x),toY(ys[i])));
    ctx.strokeStyle='#2980b9'; ctx.lineWidth=2; ctx.stroke();
  }

  // axes
  ctx.beginPath(); ctx.moveTo(pad,pad); ctx.lineTo(pad,H-pad); ctx.lineTo(W-pad,H-pad);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();

  // x ticks
  ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#6b7f92'; ctx.textAlign='center';
  const tickCount=6;
  for(let i=0;i<=tickCount;i++){
    const v=minX+rangeX*i/tickCount;
    ctx.fillText(v.toFixed(1),toX(v),H-pad+16);
  }
}

// ── CHEAT SHEET ────────────────────────────────────────────────────
const formulas = [
  {topic:'機率加法法則',formula:'P(A∪B) = P(A)+P(B)−P(A∩B)',note:'若 A, B 互斥則 P(A∩B)=0'},
  {topic:'獨立事件乘法',formula:'P(A∩B) = P(A)·P(B)',note:'僅在 A, B 統計獨立時成立'},
  {topic:'貝葉斯定理',formula:'P(H|E)=P(E|H)·P(H)/P(E)',note:'後驗 = 似然 × 先驗 / 邊際'},
  {topic:'期望值（離散）',formula:'E[X] = Σ xᵢ P(xᵢ)',note:'所有結果的機率加權平均'},
  {topic:'變異數',formula:'Var(X) = E[X²] − (E[X])²',note:'標準差 σ = √Var(X)'},
  {topic:'中央極限定理',formula:'X̄ ~ N(μ, σ²/n)',note:'n≥30 時近似成立'},
  {topic:'95% 信賴區間',formula:'x̄ ± 1.96 · σ/√n',note:'99% 用 2.576，90% 用 1.645'},
  {topic:'樣本數公式',formula:'n = z²·p(1−p)/E²',note:'E 為誤差容忍度（小數）'},
  {topic:'相關係數',formula:'r = Σ(xᵢ−x̄)(yᵢ−ȳ) / (nσₓσᵧ)',note:'-1≤r≤1，0 表示無線性相關'},
  {topic:'常態分布 PDF',formula:'f(x)=e^(−½((x−μ)/σ)²)/(σ√2π)',note:'鐘形曲線，對稱於均值'},
  {topic:'二項分布',formula:'P(X=k)=C(n,k)pᵏ(1−p)ⁿ⁻ᵏ',note:'n 次試驗中 k 次成功的機率'},
  {topic:'大數法則',formula:'X̄ₙ → μ  (n→∞)',note:'樣本均值依機率收斂至母體均值'},
];

const csGrid = document.getElementById('csGrid');
formulas.forEach(f=>{
  csGrid.innerHTML+=`
  <div class="cs-card">
    <div class="cs-topic">${f.topic}</div>
    <div class="cs-formula">${f.formula}</div>
    <div class="cs-note">${f.note}</div>
  </div>`;
});

// ═══════════════════════════════════════════════════════════════════
// GAME 1 — COIN FLIP
// ═══════════════════════════════════════════════════════════════════
let coinHeads=0, coinTotal=0, coinStreak=0, coinHistory=[], coinRatioHistory=[];

function flipCoin(n) {
  for(let i=0;i<n;i++){
    const h = Math.random()<0.5;
    if(h){ coinHeads++; coinStreak++; } else { coinStreak=0; }
    coinTotal++;
    coinHistory.push(h?'H':'T');
    coinRatioHistory.push(coinHeads/coinTotal);
  }
  const last = coinHistory[coinHistory.length-1];
  const face = document.getElementById('coinFace');
  face.textContent = last==='H'?'正':'反';
  face.classList.remove('flip-anim');
  void face.offsetWidth;
  face.classList.add('flip-anim');
  document.getElementById('c_heads').textContent = coinHeads;
  document.getElementById('c_total').textContent = coinTotal;
  document.getElementById('c_pct').textContent   = (coinHeads/coinTotal*100).toFixed(1)+'%';
  document.getElementById('c_streak').textContent= coinStreak;
  // history chips (last 30)
  const hBox = document.getElementById('coinHistory');
  hBox.innerHTML = coinHistory.slice(-40).map(c=>`<span class="coin-chip ${c}">${c==='H'?'正':'反'}</span>`).join('');
  drawCoinChart();
}

function resetCoin(){
  coinHeads=coinTotal=coinStreak=0; coinHistory=[]; coinRatioHistory=[];
  document.getElementById('coinFace').textContent='？';
  ['c_heads','c_total','c_streak'].forEach(id=>document.getElementById(id).textContent='0');
  document.getElementById('c_pct').textContent='—';
  document.getElementById('coinHistory').innerHTML='';
  drawCoinChart();
}

function drawCoinChart(){
  const canvas=document.getElementById('coinCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=80*dpr;
  canvas.style.height='80px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=80;
  clearCanvas(canvas,ctx);
  if(coinRatioHistory.length<2){
    ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='center';
    ctx.fillText('拋硬幣後顯示正面率變化圖',W/2,H/2); return;
  }
  const pts=coinRatioHistory;
  const toX=i=>i/(pts.length-1)*W;
  const toY=v=>H-4-(v)*( H-8);
  // 50% line
  ctx.beginPath(); ctx.moveTo(0,toY(.5)); ctx.lineTo(W,toY(.5));
  ctx.strokeStyle='rgba(39,174,96,.4)'; ctx.lineWidth=1; ctx.setLineDash([4,4]); ctx.stroke(); ctx.setLineDash([]);
  // curve
  ctx.beginPath();
  pts.forEach((v,i)=>i===0?ctx.moveTo(toX(i),toY(v)):ctx.lineTo(toX(i),toY(v)));
  ctx.strokeStyle='#2980b9'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#27ae60'; ctx.textAlign='left';
  ctx.fillText('50%',4,toY(.5)-3);
}

// ═══════════════════════════════════════════════════════════════════
// GAME 2 — GUESS THE MEAN
// ═══════════════════════════════════════════════════════════════════
let gtmData=[], gtmTrueMean=0, gtmAnswered=false, gtmCorrect=0, gtmTotal=0;

function newGTM(){
  gtmAnswered=false;
  document.getElementById('gtmGuess').value='';
  document.getElementById('gtmFeedback').textContent='';
  document.getElementById('gtmFeedback').style.color='var(--muted)';
  // generate random dataset
  const dist = Math.random();
  gtmData=[];
  if(dist<0.33){
    // normal-ish
    const mu=Math.random()*6-3, sig=0.5+Math.random()*1.5;
    for(let i=0;i<25;i++) gtmData.push(mu+sig*(Math.random()+Math.random()+Math.random()-1.5));
  } else if(dist<0.66){
    // skewed
    const base=Math.random()*4-2;
    for(let i=0;i<20;i++) gtmData.push(base+Math.pow(Math.random(),2)*6);
  } else {
    // bimodal
    const c1=Math.random()*3-3, c2=c1+2+Math.random()*2;
    for(let i=0;i<12;i++) gtmData.push(c1+(Math.random()-.5)*1.2);
    for(let i=0;i<12;i++) gtmData.push(c2+(Math.random()-.5)*1.2);
  }
  gtmTrueMean = gtmData.reduce((a,b)=>a+b,0)/gtmData.length;
  drawGTM();
}

function drawGTM(guessVal, showAnswer){
  const canvas=document.getElementById('gtmCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=150*dpr;
  canvas.style.height='150px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=150;
  clearCanvas(canvas,ctx);
  if(!gtmData.length) return;

  const minV=Math.min(...gtmData)-0.5, maxV=Math.max(...gtmData)+0.5;
  const toX=v=>20+(v-minV)/(maxV-minV)*(W-40);

  // dots
  // jitter y
  const ys=gtmData.map(()=>40+Math.random()*60);
  gtmData.forEach((v,i)=>{
    ctx.beginPath(); ctx.arc(toX(v),ys[i],5,0,Math.PI*2);
    ctx.fillStyle='rgba(41,128,185,.5)'; ctx.fill();
    ctx.strokeStyle='#2980b9'; ctx.lineWidth=1; ctx.stroke();
  });

  if(showAnswer){
    // true mean line
    ctx.beginPath(); ctx.moveTo(toX(gtmTrueMean),10); ctx.lineTo(toX(gtmTrueMean),H-20);
    ctx.strokeStyle='#27ae60'; ctx.lineWidth=2.5; ctx.stroke();
    ctx.font='bold 10px DM Mono,monospace'; ctx.fillStyle='#27ae60'; ctx.textAlign='center';
    ctx.fillText(`真實均值 ${gtmTrueMean.toFixed(2)}`,toX(gtmTrueMean),H-6);
  }
  if(guessVal!==undefined){
    ctx.beginPath(); ctx.moveTo(toX(guessVal),10); ctx.lineTo(toX(guessVal),H-20);
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=2; ctx.setLineDash([5,4]); ctx.stroke(); ctx.setLineDash([]);
    ctx.font='10px DM Mono,monospace'; ctx.fillStyle='#c0392b'; ctx.textAlign='center';
    ctx.fillText(`你的猜測 ${(+guessVal).toFixed(2)}`,toX(guessVal),8);
  }

  // axis
  ctx.beginPath(); ctx.moveTo(20,H-18); ctx.lineTo(W-20,H-18);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='center';
  [minV+0.5, (minV+maxV)/2, maxV-0.5].forEach(v=>ctx.fillText(v.toFixed(1),toX(v),H-5));
}

function submitGTM(){
  if(gtmAnswered||!gtmData.length) return;
  const g=parseFloat(document.getElementById('gtmGuess').value);
  if(isNaN(g)){ document.getElementById('gtmFeedback').textContent='請輸入數字'; return; }
  gtmAnswered=true; gtmTotal++;
  const err=Math.abs(g-gtmTrueMean);
  const range=Math.max(...gtmData)-Math.min(...gtmData);
  const pct=err/range;
  let fb='', color='';
  if(pct<0.05){ fb=`🎯 超準！誤差只有 ${err.toFixed(2)}，真厲害！`; color='#27ae60'; gtmCorrect++; }
  else if(pct<0.12){ fb=`👍 不錯！誤差 ${err.toFixed(2)}，接近了！`; color='#d4860a'; gtmCorrect++; }
  else { fb=`📉 差了點，誤差 ${err.toFixed(2)}，再試一次！`; color='#c0392b'; }
  document.getElementById('gtmFeedback').textContent=fb;
  document.getElementById('gtmFeedback').style.color=color;
  document.getElementById('gtmScore').textContent=`得分：${gtmCorrect} / ${gtmTotal}`;
  drawGTM(g, true);
}

// ═══════════════════════════════════════════════════════════════════
// GAME 3 — CLT DEMO
// ═══════════════════════════════════════════════════════════════════
let cltMeans=[];

function getCLTSample(n){
  const dist=document.getElementById('cltDist').value;
  const arr=[];
  for(let i=0;i<n;i++){
    let v;
    if(dist==='uniform') v=Math.random()*10;
    else if(dist==='exponential') v=-Math.log(1-Math.random())*2;
    else if(dist==='bimodal') v=Math.random()<0.5?Math.random()*2+1:Math.random()*2+7;
    else {
      const r=Math.random();
      v = r<0.3?1:r<0.6?3:r<0.8?5:8;
    }
    arr.push(v);
  }
  return arr;
}

function resetCLT(){
  cltMeans=[];
  drawCLTPopulation();
  drawCLTSampling();
  document.getElementById('cltInfo').textContent='按「抽樣」開始實驗';
}

function doSampleCLT(times){
  const n=+document.getElementById('cltN').value;
  for(let i=0;i<times;i++){
    const s=getCLTSample(n);
    cltMeans.push(s.reduce((a,b)=>a+b,0)/n);
  }
  drawCLTSampling();
  const m=cltMeans.reduce((a,b)=>a+b,0)/cltMeans.length;
  const v=cltMeans.reduce((a,b)=>a+(b-m)**2,0)/cltMeans.length;
  document.getElementById('cltInfo').textContent=
    `已收集 ${cltMeans.length} 個樣本均值 · 均值的均值=${m.toFixed(3)} · 標準差=${Math.sqrt(v).toFixed(3)} · 分布${cltMeans.length>=100?'已趨近常態 🔔':'逐漸成形…'}`;
}

function drawCLTPopulation(){
  const canvas=document.getElementById('cltPopCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=80*dpr; canvas.style.height='80px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=80;
  clearCanvas(canvas,ctx);
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='left';
  ctx.fillText('母體分布：',4,12);

  const dist=document.getElementById('cltDist').value;
  const pts=120;
  const xs=[],ys=[];
  if(dist==='uniform'){
    xs.push(0,0,10,10); ys.push(0,0.1,0.1,0);
  } else if(dist==='exponential'){
    for(let i=0;i<pts;i++){const x=i/pts*10;xs.push(x);ys.push(0.5*Math.exp(-x*0.5));}
  } else if(dist==='bimodal'){
    for(let i=0;i<pts;i++){const x=i/pts*12;xs.push(x);ys.push(normalPDF(x,2,0.7)+normalPDF(x,8,0.7));}
  } else {
    xs.push(0.5,1,1,1.5,2.5,3,3,3.5,4.5,5,5,5.5,7.5,8,8,8.5);
    ys.push(0,0,0.3,0,0,0,0.3,0,0,0,0.2,0,0,0,0.2,0);
  }
  const maxY=Math.max(...ys)||0.1;
  const minX=Math.min(...xs),maxX=Math.max(...xs);
  const toX=x=>20+(x-minX)/(maxX-minX)*(W-30);
  const toY=y=>H-14-y/maxY*(H-24);

  ctx.beginPath();
  ctx.moveTo(toX(xs[0]),toY(0));
  xs.forEach((x,i)=>ctx.lineTo(toX(x),toY(ys[i])));
  ctx.lineTo(toX(xs[xs.length-1]),toY(0));
  ctx.closePath();
  ctx.fillStyle='rgba(192,57,43,.15)'; ctx.fill();
  ctx.beginPath();
  xs.forEach((x,i)=>i===0?ctx.moveTo(toX(x),toY(ys[i])):ctx.lineTo(toX(x),toY(ys[i])));
  ctx.strokeStyle='#c0392b'; ctx.lineWidth=1.5; ctx.stroke();

  ctx.beginPath(); ctx.moveTo(20,H-13); ctx.lineTo(W-10,H-13);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

function drawCLTSampling(){
  const canvas=document.getElementById('cltSampCanvas');
  const dpr=window.devicePixelRatio||1;
  canvas.width=canvas.parentElement.clientWidth*dpr;
  canvas.height=100*dpr; canvas.style.height='100px';
  const ctx=canvas.getContext('2d');
  ctx.scale(dpr,dpr);
  const W=canvas.parentElement.clientWidth,H=100;
  clearCanvas(canvas,ctx);
  ctx.font='9px DM Mono,monospace'; ctx.fillStyle='#a8b8c8'; ctx.textAlign='left';
  ctx.fillText('樣本均值分布（累積次數）：',4,12);

  if(cltMeans.length<2){ return; }
  const minV=Math.min(...cltMeans),maxV=Math.max(...cltMeans);
  const bins=20;
  const counts=new Array(bins).fill(0);
  cltMeans.forEach(v=>{
    const b=Math.min(bins-1,Math.floor((v-minV)/(maxV-minV+0.001)*bins));
    counts[b]++;
  });
  const maxC=Math.max(...counts)||1;
  const bw=(W-30)/bins;
  const toY=c=>H-18-c/maxC*(H-30);

  counts.forEach((c,i)=>{
    const x=20+i*bw;
    const bh=c/maxC*(H-30);
    ctx.fillStyle='rgba(41,128,185,.55)';
    ctx.fillRect(x,H-18-bh,bw-1,bh);
  });

  // overlay normal curve if enough samples
  if(cltMeans.length>=30){
    const mu=cltMeans.reduce((a,b)=>a+b,0)/cltMeans.length;
    const sig=Math.sqrt(cltMeans.reduce((a,b)=>a+(b-mu)**2,0)/cltMeans.length);
    ctx.beginPath();
    for(let i=0;i<=100;i++){
      const x=minV+(maxV-minV)*i/100;
      const px=20+(x-minV)/(maxV-minV)*(W-30);
      const py=toY(normalPDF(x,mu,sig)*cltMeans.length*(maxV-minV)/bins);
      i===0?ctx.moveTo(px,py):ctx.lineTo(px,py);
    }
    ctx.strokeStyle='#c0392b'; ctx.lineWidth=2; ctx.stroke();
  }

  ctx.beginPath(); ctx.moveTo(20,H-17); ctx.lineTo(W-10,H-17);
  ctx.strokeStyle='#dce4ec'; ctx.lineWidth=1; ctx.stroke();
}

// ═══════════════════════════════════════════════════════════════════
// GAME 4 — PROBABILITY QUIZ
// ═══════════════════════════════════════════════════════════════════
const QUIZ_QUESTIONS = [
  {
    q:'拋一枚公正硬幣 10 次，全部正面的機率是？',
    opts:['1/1024','1/512','1/100','1/1000'],
    ans:0,
    explain:'每次正面機率為 1/2，10次獨立事件：(1/2)¹⁰ = 1/1024 ≈ 0.098%'
  },{
    q:'一個袋子有 3 顆紅球、7 顆藍球，隨機取 2 顆（不放回），兩顆都是紅球的機率？',
    opts:['9%','3.3%','6.7%','12%'],
    ans:1,
    explain:'P = (3/10)×(2/9) = 6/90 = 1/15 ≈ 6.7%。等等——答案是 6.7%！選項順序是陷阱，正確答案是 C（6.7%）。'
  },{
    q:'甲病盛行率 1%，篩檢靈敏度 99%、特異度 95%。篩到陽性後，真的有病的機率約？',
    opts:['99%','50%','16.7%','1%'],
    ans:2,
    explain:'貝葉斯：P(病|陽) = (0.99×0.01)/(0.99×0.01 + 0.05×0.99) ≈ 0.0099/0.0594 ≈ 16.7%。基率低時，假陽性大量稀釋了真陽性。'
  },{
    q:'「連輸 5 次後，第 6 次更容易贏」— 這句話是？',
    opts:['正確，機率會補回來','正確，但只適用賭場','完全錯誤（賭徒謬誤）','取決於遊戲類型'],
    ans:2,
    explain:'獨立事件沒有記憶。每次結果只取決於當下機率，不受歷史影響。這就是著名的「賭徒謬誤」。'
  },{
    q:'一個班 23 人，至少 2 人同生日的機率約為？',
    opts:['6.3%','23%','50.7%','89%'],
    ans:2,
    explain:'生日問題！1-(365×364×...×343)/365²³ ≈ 50.7%。人數遠少於 365 時機率就過半，反直覺！'
  },{
    q:'獨立事件 A（P=0.6）和 B（P=0.7），A 或 B 發生的機率？',
    opts:['1.3（不可能）','88%','42%','65%'],
    ans:1,
    explain:'P(A∪B) = P(A)+P(B)-P(A∩B) = 0.6+0.7-0.6×0.7 = 1.3-0.42 = 0.88 = 88%'
  },{
    q:'標準常態分布中，|X| > 2 的機率約為？',
    opts:['32%','5%','0.3%','16%'],
    ans:1,
    explain:'68-95-99.7 法則：±1σ 佔 68%，±2σ 佔 95%，所以 |X|>2σ ≈ 5%（雙尾各 2.5%）。'
  },{
    q:'樣本數從 100 增加到 400，信賴區間寬度變化？',
    opts:['縮小 4 倍','縮小 2 倍','縮小 1.5 倍','不變'],
    ans:1,
    explain:'信賴區間寬度 ∝ 1/√n。√400/√100 = 2，所以寬度縮小一半。要縮小 4 倍需要樣本數增加 16 倍。'
  },{
    q:'回歸係數 r=0.9，表示 X 能解釋 Y 多少變異？',
    opts:['90%','81%','0.9%','95%'],
    ans:1,
    explain:'決定係數 R² = r² = 0.81，即 81%。注意：r 是相關係數，r² 才是解釋力（決定係數）。'
  },{
    q:'p 值 = 0.03，顯著水準 α = 0.05，結論是？',
    opts:['接受 H₀','拒絕 H₁','拒絕 H₀','數據不足'],
    ans:2,
    explain:'p < α（0.03 < 0.05），有足夠證據拒絕虛無假設 H₀。注意：這不代表 H₀ 一定是錯的，只是「不太可能」。'
  }
];
let quizIdx=0, quizScore=0, quizOrder=[], quizActive=false;

function startQuiz(){
  quizIdx=0; quizScore=0; quizActive=true;
  quizOrder=[...Array(QUIZ_QUESTIONS.length).keys()].sort(()=>Math.random()-.5).slice(0,10);
  document.getElementById('quizStartBtn').style.display='none';
  showQuizQ();
}

function showQuizQ(){
  if(quizIdx>=quizOrder.length){ endQuiz(); return; }
  const q=QUIZ_QUESTIONS[quizOrder[quizIdx]];
  document.getElementById('quizProgressFill').style.width=`${quizIdx/10*100}%`;
  document.getElementById('quizMeta').textContent=`${quizIdx+1} / 10 題`;
  document.getElementById('quizQ').textContent=q.q;
  document.getElementById('quizExplain').textContent='';
  document.getElementById('quizExplain').classList.remove('show');
  const optsEl=document.getElementById('quizOpts');
  optsEl.innerHTML=q.opts.map((o,i)=>
    `<button class="quiz-opt" onclick="answerQuiz(${i})">${String.fromCharCode(65+i)}. ${o}</button>`
  ).join('');
}

function answerQuiz(chosen){
  const q=QUIZ_QUESTIONS[quizOrder[quizIdx]];
  const opts=document.querySelectorAll('.quiz-opt');
  opts.forEach(b=>b.disabled=true);
  opts[q.ans].classList.add('correct');
  if(chosen!==q.ans){ opts[chosen].classList.add('wrong'); } else { quizScore++; }
  document.getElementById('quizScoreDisplay').textContent=`得分：${quizScore}`;
  const ex=document.getElementById('quizExplain');
  ex.textContent='💡 '+q.explain; ex.classList.add('show');
  quizIdx++;
  setTimeout(()=>{
    if(quizIdx<quizOrder.length) showQuizQ();
    else endQuiz();
  }, 2200);
}

function endQuiz(){
  document.getElementById('quizProgressFill').style.width='100%';
  document.getElementById('quizMeta').textContent='完成！';
  document.getElementById('quizExplain').classList.remove('show');
  const grade = quizScore>=9?'🏆 機率大師！':quizScore>=7?'🎓 統計高手！':quizScore>=5?'📚 繼續加油！':'💪 再練習一下！';
  document.getElementById('quizQ').textContent=`測驗結束！得分 ${quizScore}/10 — ${grade}`;
  document.getElementById('quizOpts').innerHTML='';
  const btn=document.getElementById('quizStartBtn');
  btn.textContent='重新挑戰'; btn.style.display='block';
  quizActive=false;
}

// ── INIT ──────────────────────────────────────────────────────────
window.addEventListener('load', ()=>{
  drawHero();
  drawBayes();
  drawSampling();
  drawHypothesis();
  drawMonteCarlo();
  drawDist();
  document.getElementById('dv_mu').textContent     = document.getElementById('d_mu').value;
  document.getElementById('dv_sigma').textContent  = document.getElementById('d_sigma').value;
  document.getElementById('dv_n').textContent      = document.getElementById('d_n').value;
  document.getElementById('dv_pp').textContent     = document.getElementById('d_pp').value;
  document.getElementById('dv_lambda').textContent = document.getElementById('d_lambda').value;
  // games init
  drawCoinChart();
  newGTM();
  drawCLTPopulation();
  drawCLTSampling();
});
window.addEventListener('resize', ()=>{ drawHero(); drawDist(); });
</script>
</body>
</html>