<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>README — Vibe Coder Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;700;800&family=Space+Grotesk:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080c10;
    --bg2: #0d1117;
    --bg3: #111820;
    --accent: #00ffe0;
    --accent2: #ff4af0;
    --accent3: #ffe84d;
    --text: #cdd9e5;
    --muted: #636e7b;
    --border: rgba(0,255,224,0.15);
    --glow: 0 0 20px rgba(0,255,224,0.3);
    --glow2: 0 0 20px rgba(255,74,240,0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Grotesk', sans-serif;
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* GRID BACKGROUND */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,255,224,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,224,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* SCANLINE */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.05) 2px,
      rgba(0,0,0,0.05) 4px
    );
    pointer-events: none;
    z-index: 1;
  }

  .wrapper { max-width: 860px; margin: 0 auto; padding: 2rem 1.5rem 6rem; position: relative; z-index: 2; }

  /* ──────────── HERO ──────────── */
  .hero {
    text-align: center;
    padding: 5rem 0 3rem;
    position: relative;
  }

  .badge-row {
    display: flex;
    justify-content: center;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 2rem;
  }

  .badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 12px;
    border-radius: 20px;
    border: 1px solid;
    animation: pulseIn 0.6s ease both;
  }

  .badge-cyan  { color: var(--accent);  border-color: rgba(0,255,224,0.4);  background: rgba(0,255,224,0.06); }
  .badge-pink  { color: var(--accent2); border-color: rgba(255,74,240,0.4); background: rgba(255,74,240,0.06); }
  .badge-yellow{ color: var(--accent3); border-color: rgba(255,232,77,0.4); background: rgba(255,232,77,0.06); }

  .hero-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(2.2rem, 6vw, 4.5rem);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -0.02em;
    color: #fff;
    position: relative;
    display: inline-block;
    margin-bottom: 0.5rem;
  }

  .hero-name .glitch-text { position: relative; }

  .hero-name .glitch-text::before,
  .hero-name .glitch-text::after {
    content: attr(data-text);
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    opacity: 0;
  }

  .hero-name .glitch-text::before {
    color: var(--accent);
    animation: glitch1 4s infinite;
    clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  }

  .hero-name .glitch-text::after {
    color: var(--accent2);
    animation: glitch2 4s infinite;
    clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
  }

  .hero-tagline {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.85rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    margin-bottom: 1.5rem;
  }

  .hero-tagline span { color: var(--accent); }

  .typing-line {
    font-family: 'JetBrains Mono', monospace;
    font-size: 1.05rem;
    color: var(--accent);
    min-height: 1.6em;
    margin-bottom: 2.5rem;
  }

  .typing-line::after {
    content: '|';
    animation: blink 0.8s step-end infinite;
    color: var(--accent);
  }

  /* ──────────── STATS BAR ──────────── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    margin-bottom: 3.5rem;
  }

  .stat-card {
    background: var(--bg2);
    padding: 1.5rem 1rem;
    text-align: center;
    transition: background 0.3s;
    cursor: default;
  }

  .stat-card:hover { background: var(--bg3); }

  .stat-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 2.2rem;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 0.3rem;
  }

  .stat-label {
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .c-cyan   { color: var(--accent); }
  .c-pink   { color: var(--accent2); }
  .c-yellow { color: var(--accent3); }
  .c-white  { color: #fff; }

  /* ──────────── SECTIONS ──────────── */
  .section { margin-bottom: 3.5rem; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 1.5rem;
  }

  .section-icon {
    width: 32px;
    height: 32px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
    flex-shrink: 0;
  }

  .icon-cyan   { background: rgba(0,255,224,0.1); border: 1px solid rgba(0,255,224,0.3); }
  .icon-pink   { background: rgba(255,74,240,0.1); border: 1px solid rgba(255,74,240,0.3); }
  .icon-yellow { background: rgba(255,232,77,0.1); border: 1px solid rgba(255,232,77,0.3); }

  .section-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .section-title strong {
    display: block;
    font-size: 1.15rem;
    font-family: 'Space Grotesk', sans-serif;
    letter-spacing: 0;
    color: #fff;
    font-weight: 700;
    text-transform: none;
  }

  /* ──────────── TIMELINE ──────────── */
  .timeline { position: relative; padding-left: 1.5rem; }

  .timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 6px;
    bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent), var(--accent2), transparent);
  }

  .tl-item {
    position: relative;
    margin-bottom: 1.5rem;
    opacity: 0;
    transform: translateX(-10px);
    transition: all 0.5s ease;
  }

  .tl-item.visible { opacity: 1; transform: translateX(0); }

  .tl-dot {
    position: absolute;
    left: -1.75rem;
    top: 5px;
    width: 9px;
    height: 9px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 8px var(--accent);
  }

  .tl-content {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1rem 1.25rem;
    transition: border-color 0.3s, box-shadow 0.3s;
  }

  .tl-content:hover {
    border-color: rgba(0,255,224,0.35);
    box-shadow: var(--glow);
  }

  .tl-year {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent);
    font-weight: 700;
    letter-spacing: 0.1em;
    margin-bottom: 0.3rem;
  }

  .tl-title { font-weight: 700; color: #fff; font-size: 0.95rem; }
  .tl-desc  { font-size: 0.85rem; color: var(--muted); margin-top: 0.3rem; line-height: 1.5; }

  /* ──────────── SKILL BARS ──────────── */
  .skill-list { display: flex; flex-direction: column; gap: 1rem; }

  .skill-row { }

  .skill-meta {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin-bottom: 6px;
  }

  .skill-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--text);
    letter-spacing: 0.05em;
  }

  .skill-pct {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
  }

  .skill-track {
    height: 5px;
    background: rgba(255,255,255,0.05);
    border-radius: 10px;
    overflow: hidden;
  }

  .skill-fill {
    height: 100%;
    border-radius: 10px;
    width: 0;
    transition: width 1.4s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .fill-cyan   { background: linear-gradient(90deg, var(--accent), rgba(0,255,224,0.5)); box-shadow: 0 0 8px rgba(0,255,224,0.5); }
  .fill-pink   { background: linear-gradient(90deg, var(--accent2), rgba(255,74,240,0.5)); box-shadow: 0 0 8px rgba(255,74,240,0.5); }
  .fill-yellow { background: linear-gradient(90deg, var(--accent3), rgba(255,232,77,0.5)); box-shadow: 0 0 8px rgba(255,232,77,0.5); }

  /* ──────────── TOOL GRID ──────────── */
  .tool-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tool-chip {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.06em;
    padding: 6px 14px;
    border-radius: 6px;
    border: 1px solid;
    cursor: default;
    transition: transform 0.2s, box-shadow 0.2s, background 0.2s;
    opacity: 0;
    transform: scale(0.85);
    animation: chipIn 0.4s ease forwards;
  }

  .tool-chip:hover {
    transform: translateY(-2px) scale(1.04);
  }

  .chip-cyan {
    color: var(--accent);
    border-color: rgba(0,255,224,0.3);
    background: rgba(0,255,224,0.05);
  }
  .chip-cyan:hover { background: rgba(0,255,224,0.12); box-shadow: 0 4px 16px rgba(0,255,224,0.2); }

  .chip-pink {
    color: var(--accent2);
    border-color: rgba(255,74,240,0.3);
    background: rgba(255,74,240,0.05);
  }
  .chip-pink:hover { background: rgba(255,74,240,0.12); box-shadow: 0 4px 16px rgba(255,74,240,0.2); }

  .chip-yellow {
    color: var(--accent3);
    border-color: rgba(255,232,77,0.3);
    background: rgba(255,232,77,0.05);
  }
  .chip-yellow:hover { background: rgba(255,232,77,0.12); box-shadow: 0 4px 16px rgba(255,232,77,0.2); }

  .chip-white {
    color: #fff;
    border-color: rgba(255,255,255,0.15);
    background: rgba(255,255,255,0.04);
  }
  .chip-white:hover { background: rgba(255,255,255,0.1); box-shadow: 0 4px 16px rgba(255,255,255,0.1); }

  /* ──────────── WEAKNESS CARD ──────────── */
  .weakness-card {
    background: linear-gradient(135deg, rgba(255,74,240,0.06), rgba(255,74,240,0.02));
    border: 1px solid rgba(255,74,240,0.2);
    border-radius: 12px;
    padding: 1.5rem 1.75rem;
    position: relative;
    overflow: hidden;
  }

  .weakness-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 4px; height: 100%;
    background: var(--accent2);
  }

  .weakness-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    color: var(--accent2);
    text-transform: uppercase;
    font-weight: 700;
    margin-bottom: 1rem;
  }

  .weakness-row {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    margin-bottom: 0.6rem;
    font-size: 0.88rem;
    color: var(--text);
  }

  .weakness-row .bullet {
    color: var(--accent2);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    margin-top: 3px;
    flex-shrink: 0;
  }

  /* ──────────── STRENGTH CARD ──────────── */
  .strength-card {
    background: linear-gradient(135deg, rgba(0,255,224,0.06), rgba(0,255,224,0.02));
    border: 1px solid rgba(0,255,224,0.2);
    border-radius: 12px;
    padding: 1.5rem 1.75rem;
    position: relative;
    overflow: hidden;
  }

  .strength-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 4px; height: 100%;
    background: var(--accent);
  }

  .strength-row {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    margin-bottom: 0.6rem;
    font-size: 0.88rem;
    color: var(--text);
  }

  .strength-row .bullet { color: var(--accent); font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; margin-top: 3px; flex-shrink: 0; }

  /* ──────────── FOOTER ──────────── */
  .footer {
    text-align: center;
    padding-top: 4rem;
    border-top: 1px solid var(--border);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.08em;
  }

  .footer span { color: var(--accent); }

  /* ──────────── ANIMATIONS ──────────── */
  @keyframes glitch1 {
    0%, 90%, 100% { opacity: 0; transform: translate(0); }
    92% { opacity: 0.8; transform: translate(-3px, 1px) skewX(-5deg); }
    94% { opacity: 0; }
    96% { opacity: 0.6; transform: translate(3px, -1px) skewX(3deg); }
  }

  @keyframes glitch2 {
    0%, 93%, 100% { opacity: 0; transform: translate(0); }
    95% { opacity: 0.7; transform: translate(3px, 2px) skewX(5deg); }
    97% { opacity: 0; }
    99% { opacity: 0.5; transform: translate(-2px, -1px); }
  }

  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  @keyframes pulseIn {
    from { opacity: 0; transform: scale(0.8) translateY(4px); }
    to   { opacity: 1; transform: scale(1) translateY(0); }
  }

  @keyframes chipIn {
    to { opacity: 1; transform: scale(1); }
  }

  /* Particle canvas */
  #particles {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  /* ──────────── RESPONSIVE ──────────── */
  @media (max-width: 500px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .hero-name  { font-size: 2rem; }
  }
</style>
</head>
<body>

<canvas id="particles"></canvas>

<div class="wrapper">

  <!-- ── HERO ── -->
  <section class="hero">
    <div class="badge-row">
      <span class="badge badge-cyan">🧠 Vibe Coder</span>
      <span class="badge badge-pink">⚡ AI Power User</span>
      <span class="badge badge-yellow">🛠 Tool Builder</span>
    </div>

    <h1 class="hero-name">
      <span class="glitch-text" data-text="VIBE.CODER()">VIBE.CODER()</span>
    </h1>

    <p class="hero-tagline">
      &lt;/ <span>không giỏi code</span> · nhưng giỏi <span>vibe coding</span> /&gt;
    </p>

    <div class="typing-line" id="typing"></div>
  </section>

  <!-- ── STATS ── -->
  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-num c-cyan" data-target="8">0</div>
      <div class="stat-label">Năm vọc code</div>
    </div>
    <div class="stat-card">
      <div class="stat-num c-pink" data-target="5">0</div>
      <div class="stat-label">AI Tools / ngày</div>
    </div>
    <div class="stat-card">
      <div class="stat-num c-yellow" data-target="4">0</div>
      <div class="stat-label">Ngôn ngữ dùng</div>
    </div>
    <div class="stat-card">
      <div class="stat-num c-white" data-target="∞">0</div>
      <div class="stat-label">Tò mò Level</div>
    </div>
  </div>

  <!-- ── TIMELINE ── -->
  <section class="section" id="timeline">
    <div class="section-header">
      <div class="section-icon icon-cyan">⏱</div>
      <div class="section-title">
        origin story
        <strong>Hành Trình Bắt Đầu</strong>
      </div>
    </div>
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-dot" style="background:var(--accent); box-shadow: 0 0 8px var(--accent)"></div>
        <div class="tl-content">
          <div class="tl-year">LỚP 8 · Khởi Nguồn</div>
          <div class="tl-title">Lần đầu vọc code</div>
          <div class="tl-desc">Tò mò cực kỳ cao — tự mày mò HTML/CSS đầu tiên, cảm giác như vừa tìm ra một siêu năng lực ẩn.</div>
        </div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background:var(--accent3); box-shadow: 0 0 8px var(--accent3)"></div>
        <div class="tl-content">
          <div class="tl-year">TIẾP THEO · Mở Rộng</div>
          <div class="tl-title">Python · PHP · Logic Systems</div>
          <div class="tl-desc">Bắt đầu hiểu database, API, JWT. Không cần viết code đẹp — chỉ cần hiểu hệ thống vận hành thế nào.</div>
        </div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background:var(--accent2); box-shadow: 0 0 8px var(--accent2)"></div>
        <div class="tl-content">
          <div class="tl-year">HIỆN TẠI · Era of AI</div>
          <div class="tl-title">Vibe Coding + AI Stack</div>
          <div class="tl-desc">GPT, Claude, Copilot, DeepSeek, Gemini... Cursor, Antigravity. Tận dụng AI để build tools nhanh — check logic, test bug, tìm lỗ hổng.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── SKILLS ── -->
  <section class="section" id="skills">
    <div class="section-header">
      <div class="section-icon icon-yellow">⚡</div>
      <div class="section-title">
        tech stack
        <strong>Kỹ Năng & Hiểu Biết</strong>
      </div>
    </div>
    <div class="skill-list">
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">Python / NodeJS / Go / .NET</span><span class="skill-pct c-yellow">Vọc tạo tools</span></div>
        <div class="skill-track"><div class="skill-fill fill-yellow" data-pct="70"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">HTML / CSS / PHP</span><span class="skill-pct c-cyan">Cơ bản</span></div>
        <div class="skill-track"><div class="skill-fill fill-cyan" data-pct="65"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">Hiểu Logic Hệ Thống</span><span class="skill-pct c-cyan">Nắm vững</span></div>
        <div class="skill-track"><div class="skill-fill fill-cyan" data-pct="82"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">Database · API · JWT</span><span class="skill-pct c-cyan">Hiểu rõ flow</span></div>
        <div class="skill-track"><div class="skill-fill fill-cyan" data-pct="75"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">AI Prompting & Vibe Coding</span><span class="skill-pct c-pink">Main skill 💀</span></div>
        <div class="skill-track"><div class="skill-fill fill-pink" data-pct="95"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-meta"><span class="skill-name">Bug Testing · Security Logic Check</span><span class="skill-pct">Cơ bản</span></div>
        <div class="skill-track"><div class="skill-fill fill-yellow" data-pct="60"></div></div>
      </div>
    </div>
  </section>

  <!-- ── STRENGTHS / WEAKNESSES ── -->
  <section class="section">
    <div class="section-header">
      <div class="section-icon icon-pink">⚖️</div>
      <div class="section-title">
        self analysis
        <strong>Điểm Mạnh & Điểm Yếu</strong>
      </div>
    </div>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
      <div class="strength-card">
        <div class="weakness-title" style="color: var(--accent);">// điểm mạnh</div>
        <div class="strength-row"><span class="bullet">▶</span><span>Tò mò không giới hạn</span></div>
        <div class="strength-row"><span class="bullet">▶</span><span>Hiểu flow & logic hệ thống</span></div>
        <div class="strength-row"><span class="bullet">▶</span><span>Vibe Coding cực kỳ linh hoạt</span></div>
        <div class="strength-row"><span class="bullet">▶</span><span>Dùng AI như một superpower</span></div>
        <div class="strength-row"><span class="bullet">▶</span><span>Check bug & test lỗ hổng cơ bản</span></div>
      </div>
      <div class="weakness-card">
        <div class="weakness-title">// điểm yếu</div>
        <div class="weakness-row"><span class="bullet">▶</span><span>Không giỏi code thuần tay</span></div>
        <div class="weakness-row"><span class="bullet">▶</span><span>Phụ thuộc AI để generate code</span></div>
        <div class="weakness-row"><span class="bullet">▶</span><span>Debug sâu vẫn còn giới hạn</span></div>
        <div class="weakness-row"><span class="bullet">▶</span><span>Security check chỉ ở mức basic</span></div>
      </div>
    </div>
  </section>

  <!-- ── AI TOOLS ── -->
  <section class="section">
    <div class="section-header">
      <div class="section-icon icon-pink">🤖</div>
      <div class="section-title">
        ai arsenal
        <strong>AI Tools Thường Dùng</strong>
      </div>
    </div>
    <div class="tool-grid" id="ai-tools">
      <span class="tool-chip chip-cyan" style="animation-delay:0.05s">ChatGPT</span>
      <span class="tool-chip chip-pink" style="animation-delay:0.10s">Claude</span>
      <span class="tool-chip chip-yellow" style="animation-delay:0.15s">Gemini</span>
      <span class="tool-chip chip-white" style="animation-delay:0.20s">Copilot</span>
      <span class="tool-chip chip-cyan" style="animation-delay:0.25s">DeepSeek</span>
      <span class="tool-chip chip-pink" style="animation-delay:0.30s">Cursor</span>
      <span class="tool-chip chip-yellow" style="animation-delay:0.35s">Antigravity</span>
      <span class="tool-chip chip-white" style="animation-delay:0.40s">+ nhiều tool AI khác</span>
    </div>
  </section>

  <!-- ── LANGUAGES ── -->
  <section class="section">
    <div class="section-header">
      <div class="section-icon icon-yellow">🔧</div>
      <div class="section-title">
        languages used
        <strong>Ngôn Ngữ Thường Vọc</strong>
      </div>
    </div>
    <div class="tool-grid">
      <span class="tool-chip chip-yellow" style="animation-delay:0.05s">Python</span>
      <span class="tool-chip chip-cyan" style="animation-delay:0.10s">Node.js</span>
      <span class="tool-chip chip-pink" style="animation-delay:0.15s">Go (Golang)</span>
      <span class="tool-chip chip-white" style="animation-delay:0.20s">.NET / C#</span>
      <span class="tool-chip chip-cyan" style="animation-delay:0.25s">HTML/CSS</span>
      <span class="tool-chip chip-yellow" style="animation-delay:0.30s">PHP</span>
    </div>
  </section>

  <!-- ── FOOTER ── -->
  <footer class="footer">
    <p>// built with <span>vibe coding</span> + <span>AI magic</span> + không ngủ đủ giấc //</p>
    <p style="margin-top:0.5rem; font-size:0.65rem;">README.md · Powered by curiosity since lớp 8</p>
  </footer>

</div>

<script>
// ── PARTICLES ──
const canvas = document.getElementById('particles');
const ctx = canvas.getContext('2d');
let W, H, dots = [];

function resize() {
  W = canvas.width  = window.innerWidth;
  H = canvas.height = window.innerHeight;
}

function initDots() {
  dots = Array.from({length: 55}, () => ({
    x: Math.random() * W,
    y: Math.random() * H,
    vx: (Math.random() - 0.5) * 0.3,
    vy: (Math.random() - 0.5) * 0.3,
    r: Math.random() * 1.5 + 0.5,
    alpha: Math.random() * 0.5 + 0.1
  }));
}

function drawParticles() {
  ctx.clearRect(0, 0, W, H);
  dots.forEach(d => {
    d.x += d.vx; d.y += d.vy;
    if (d.x < 0) d.x = W; if (d.x > W) d.x = 0;
    if (d.y < 0) d.y = H; if (d.y > H) d.y = 0;
    ctx.beginPath();
    ctx.arc(d.x, d.y, d.r, 0, Math.PI*2);
    ctx.fillStyle = `rgba(0,255,224,${d.alpha})`;
    ctx.fill();
  });
  // connect close dots
  for (let i = 0; i < dots.length; i++) {
    for (let j = i+1; j < dots.length; j++) {
      const dx = dots[i].x - dots[j].x;
      const dy = dots[i].y - dots[j].y;
      const dist = Math.sqrt(dx*dx + dy*dy);
      if (dist < 110) {
        ctx.beginPath();
        ctx.moveTo(dots[i].x, dots[i].y);
        ctx.lineTo(dots[j].x, dots[j].y);
        ctx.strokeStyle = `rgba(0,255,224,${0.07*(1-dist/110)})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }
  requestAnimationFrame(drawParticles);
}

window.addEventListener('resize', () => { resize(); initDots(); });
resize(); initDots(); drawParticles();

// ── TYPING EFFECT ──
const phrases = [
  'Bắt đầu vọc code từ lớp 8 🔥',
  'Không giỏi code nhưng GIỎI vibe coding 💀',
  'AI là cánh tay phải của tôi 🤖',
  'Python · NodeJS · Go · .NET',
  'Check logic. Test bug. Build tools.',
  'Curiosity = my main stat 📈',
];
let pi = 0, ci = 0, del = false;
const el = document.getElementById('typing');

(function type() {
  const txt = phrases[pi];
  el.textContent = del ? txt.slice(0,--ci) : txt.slice(0,++ci);
  if (!del && ci === txt.length) { del = true; setTimeout(type, 1800); return; }
  if (del && ci === 0) { del = false; pi = (pi+1) % phrases.length; setTimeout(type, 400); return; }
  setTimeout(type, del ? 30 : 60);
})();

// ── COUNTER ANIMATION ──
function animateCounters() {
  document.querySelectorAll('[data-target]').forEach(el => {
    const target = el.dataset.target;
    if (target === '∞') { setTimeout(() => el.textContent = '∞', 500); return; }
    const end = parseInt(target);
    let start = 0;
    const step = () => {
      start++;
      el.textContent = start;
      if (start < end) setTimeout(step, 120);
    };
    setTimeout(step, 200);
  });
}

// ── SKILL BAR ANIMATION ──
function animateSkills() {
  document.querySelectorAll('.skill-fill').forEach(bar => {
    setTimeout(() => { bar.style.width = bar.dataset.pct + '%'; }, 200);
  });
}

// ── SCROLL OBSERVER ──
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      if (e.target.id === 'timeline') {
        document.querySelectorAll('.tl-item').forEach((item, i) => {
          setTimeout(() => item.classList.add('visible'), i * 200);
        });
      }
      if (e.target.id === 'skills') animateSkills();
    }
  });
}, { threshold: 0.2 });

document.querySelectorAll('#timeline, #skills').forEach(el => observer.observe(el));

// Stats counter on load
window.addEventListener('load', () => {
  animateCounters();
  // chips stagger
  document.querySelectorAll('.tool-chip').forEach((c, i) => {
    c.style.animationDelay = (i * 0.06 + 0.1) + 's';
  });
});
</script>
</body>
</html>
