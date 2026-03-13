<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sri Prasath | Fullstack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #22223a;
    --accent: #7c3aed;
    --accent2: #06b6d4;
    --accent3: #f59e0b;
    --text: #e8e8f0;
    --muted: #6b6b8a;
    --white: #ffffff;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9999;
    opacity: 0.4;
  }

  /* GRID BG */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(124,58,237,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,58,237,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.2rem 4rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.2rem;
    letter-spacing: -0.02em;
    color: var(--white);
  }

  .nav-logo span { color: var(--accent); }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem;
    color: var(--muted);
    text-decoration: none;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent2); }

  /* HERO */
  #hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 0 4rem;
    z-index: 1;
    overflow: hidden;
  }

  .hero-blob {
    position: absolute;
    width: 700px; height: 700px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(124,58,237,0.18) 0%, transparent 70%);
    top: -100px; right: -100px;
    animation: blobFloat 8s ease-in-out infinite;
    pointer-events: none;
  }

  .hero-blob2 {
    position: absolute;
    width: 400px; height: 400px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(6,182,212,0.12) 0%, transparent 70%);
    bottom: 0px; left: 200px;
    animation: blobFloat 10s ease-in-out infinite reverse;
    pointer-events: none;
  }

  @keyframes blobFloat {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  .hero-content {
    max-width: 800px;
    animation: fadeUp 0.9s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(40px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.4rem 1rem;
    background: rgba(124,58,237,0.12);
    border: 1px solid rgba(124,58,237,0.3);
    border-radius: 100px;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.08em;
    margin-bottom: 2rem;
    animation: fadeUp 0.9s 0.1s ease both;
  }

  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.4); }
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(3rem, 7vw, 5.5rem);
    line-height: 1;
    letter-spacing: -0.04em;
    color: var(--white);
    animation: fadeUp 0.9s 0.2s ease both;
    margin-bottom: 0.5rem;
  }

  .hero-name .highlight {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-title {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: clamp(1.2rem, 2.5vw, 1.8rem);
    color: var(--muted);
    letter-spacing: -0.01em;
    animation: fadeUp 0.9s 0.3s ease both;
    margin-bottom: 1.5rem;
  }

  .hero-desc {
    font-size: 1.05rem;
    color: var(--muted);
    max-width: 520px;
    animation: fadeUp 0.9s 0.4s ease both;
    margin-bottom: 2.5rem;
    line-height: 1.8;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    animation: fadeUp 0.9s 0.5s ease both;
  }

  .btn-primary {
    padding: 0.85rem 2rem;
    background: linear-gradient(135deg, var(--accent), #5b21b6);
    border: none;
    border-radius: 8px;
    color: white;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: pointer;
    text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 30px rgba(124,58,237,0.4);
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 40px rgba(124,58,237,0.6);
  }

  .btn-outline {
    padding: 0.85rem 2rem;
    background: transparent;
    border: 1px solid var(--border);
    border-radius: 8px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: pointer;
    text-decoration: none;
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
  }

  .btn-outline:hover {
    border-color: var(--accent2);
    color: var(--accent2);
    transform: translateY(-2px);
  }

  /* SECTIONS */
  section {
    position: relative;
    z-index: 1;
    padding: 6rem 4rem;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin-bottom: 0.8rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }

  .section-label::after {
    content: '';
    height: 1px;
    width: 40px;
    background: var(--accent);
    opacity: 0.5;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    letter-spacing: -0.03em;
    color: var(--white);
    margin-bottom: 1rem;
  }

  .section-sub {
    color: var(--muted);
    font-size: 1rem;
    max-width: 500px;
    margin-bottom: 3.5rem;
    line-height: 1.8;
  }

  /* ABOUT */
  #about {
    border-top: 1px solid var(--border);
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
  }

  .about-text p {
    color: var(--muted);
    font-size: 1.02rem;
    line-height: 1.9;
    margin-bottom: 1rem;
  }

  .about-text p strong { color: var(--text); font-weight: 500; }

  .stats-row {
    display: flex;
    gap: 2.5rem;
    margin-top: 2.5rem;
  }

  .stat {
    text-align: left;
  }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2.5rem;
    font-weight: 800;
    letter-spacing: -0.04em;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .stat-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-top: 0.2rem;
  }

  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2.5rem;
    position: relative;
    overflow: hidden;
  }

  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
  }

  .card-line {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.9rem 0;
    border-bottom: 1px solid var(--border);
  }

  .card-line:last-child { border-bottom: none; }

  .card-key {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.06em;
  }

  .card-val {
    font-size: 0.9rem;
    color: var(--text);
    font-weight: 400;
  }

  .badge-chip {
    display: inline-block;
    padding: 0.25rem 0.75rem;
    border-radius: 100px;
    font-size: 0.75rem;
    font-family: 'DM Mono', monospace;
  }

  .chip-green {
    background: rgba(16,185,129,0.12);
    color: #10b981;
    border: 1px solid rgba(16,185,129,0.25);
  }

  /* SKILLS */
  #skills {
    border-top: 1px solid var(--border);
    background: var(--surface);
  }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .skill-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.8rem;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
    cursor: default;
  }

  .skill-card:hover {
    transform: translateY(-6px);
    border-color: var(--accent);
    box-shadow: 0 20px 40px rgba(124,58,237,0.15);
  }

  .skill-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    margin-bottom: 1.2rem;
  }

  .icon-purple { background: rgba(124,58,237,0.15); }
  .icon-cyan { background: rgba(6,182,212,0.15); }
  .icon-amber { background: rgba(245,158,11,0.15); }
  .icon-green { background: rgba(16,185,129,0.15); }
  .icon-rose { background: rgba(244,63,94,0.15); }
  .icon-blue { background: rgba(59,130,246,0.15); }

  .skill-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1rem;
    color: var(--white);
    margin-bottom: 0.4rem;
  }

  .skill-desc {
    font-size: 0.83rem;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 1.2rem;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .tag {
    padding: 0.2rem 0.6rem;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 4px;
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
  }

  /* PROJECTS */
  #projects {
    border-top: 1px solid var(--border);
  }

  .projects-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 2rem;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
  }

  .project-card:hover {
    transform: translateY(-5px);
    border-color: var(--accent2);
    box-shadow: 0 20px 40px rgba(6,182,212,0.1);
  }

  .project-card.featured {
    grid-column: 1 / -1;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    align-items: center;
  }

  .project-number {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 1rem;
  }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1.25rem;
    color: var(--white);
    margin-bottom: 0.6rem;
  }

  .project-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 1.5rem;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin-bottom: 1.5rem;
  }

  .stack-tag {
    padding: 0.2rem 0.65rem;
    border-radius: 4px;
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.04em;
  }

  .stack-purple { background: rgba(124,58,237,0.15); color: #a78bfa; border: 1px solid rgba(124,58,237,0.2); }
  .stack-cyan { background: rgba(6,182,212,0.12); color: #67e8f9; border: 1px solid rgba(6,182,212,0.2); }
  .stack-amber { background: rgba(245,158,11,0.12); color: #fcd34d; border: 1px solid rgba(245,158,11,0.2); }
  .stack-green { background: rgba(16,185,129,0.12); color: #6ee7b7; border: 1px solid rgba(16,185,129,0.2); }

  .project-link {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent2);
    text-decoration: none;
    letter-spacing: 0.05em;
    transition: gap 0.2s;
  }

  .project-link:hover { gap: 0.8rem; }

  .project-mockup {
    background: linear-gradient(135deg, rgba(124,58,237,0.1), rgba(6,182,212,0.05));
    border: 1px solid var(--border);
    border-radius: 10px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
  }

  /* CONTACT */
  #contact {
    border-top: 1px solid var(--border);
    background: var(--surface);
  }

  .contact-wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: start;
  }

  .contact-info h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 2.5rem;
    letter-spacing: -0.04em;
    color: var(--white);
    margin-bottom: 1rem;
  }

  .contact-info p {
    color: var(--muted);
    font-size: 1rem;
    line-height: 1.8;
    margin-bottom: 2rem;
  }

  .contact-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.2rem;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    transition: border-color 0.2s;
  }

  .contact-item:hover { border-color: var(--accent); }

  .contact-icon {
    width: 38px; height: 38px;
    border-radius: 8px;
    background: rgba(124,58,237,0.12);
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem;
    flex-shrink: 0;
  }

  .contact-detail { font-size: 0.88rem; color: var(--text); }
  .contact-label { font-family: 'DM Mono', monospace; font-size: 0.68rem; color: var(--muted); letter-spacing: 0.06em; text-transform: uppercase; margin-bottom: 0.1rem; }

  /* FORM */
  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 1.2rem;
  }

  .form-group { display: flex; flex-direction: column; gap: 0.5rem; }

  .form-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .form-input, .form-textarea {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 0.9rem 1.1rem;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  .form-input:focus, .form-textarea:focus {
    border-color: var(--accent);
    box-shadow: 0 0 0 3px rgba(124,58,237,0.1);
  }

  .form-textarea { resize: vertical; min-height: 130px; }

  /* FOOTER */
  footer {
    position: relative;
    z-index: 1;
    padding: 2rem 4rem;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-copy {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .footer-links {
    display: flex;
    gap: 1.5rem;
    list-style: none;
  }

  .footer-links a {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-links a:hover { color: var(--accent2); }

  /* SCROLL INDICATOR */
  .scroll-line {
    position: absolute;
    bottom: 2.5rem;
    left: 4rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
    animation: fadeUp 0.9s 0.7s ease both;
  }

  .scroll-line span {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.12em;
    writing-mode: vertical-rl;
  }

  .scroll-line::before {
    content: '';
    height: 60px;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--muted));
    animation: scrollPulse 2s ease-in-out infinite;
  }

  @keyframes scrollPulse {
    0%, 100% { opacity: 0.3; }
    50% { opacity: 1; }
  }

  @media (max-width: 900px) {
    nav { padding: 1rem 2rem; }
    section { padding: 4rem 2rem; }
    #hero { padding: 0 2rem; }
    .about-grid, .contact-wrapper { grid-template-columns: 1fr; gap: 2.5rem; }
    .skills-grid { grid-template-columns: repeat(2, 1fr); }
    .projects-grid { grid-template-columns: 1fr; }
    .project-card.featured { grid-column: auto; grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Sri<span>.</span>Prasath</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-blob"></div>
  <div class="hero-blob2"></div>

  <div class="hero-content">
    <div class="hero-badge">Available for Opportunities</div>
    <h1 class="hero-name">
      Sri<br/><span class="highlight">Prasath</span>
    </h1>
    <p class="hero-title">Fullstack Developer · India</p>
    <p class="hero-desc">
      Crafting responsive web applications with clean code and thoughtful design.
      Specialised in Angular, PHP, MySQL — bridging the gap between UI and logic.
    </p>
    <div class="hero-cta">
      <a href="#projects" class="btn-primary">View My Work</a>
      <a href="#contact" class="btn-outline">Get In Touch</a>
    </div>
  </div>

  <div class="scroll-line">
    <span>Scroll</span>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">About Me</div>
  <div class="about-grid">
    <div class="about-text">
      <h2 class="section-title">Fullstack Dev<br/>from India 🇮🇳</h2>
      <p>
        I'm <strong>Sri Prasath</strong>, a passionate Fullstack Developer with hands-on experience in building
        modern, scalable web applications from scratch. I enjoy solving complex problems with clean, readable code.
      </p>
      <p>
        With a strong foundation in both frontend and backend development, I specialise in creating
        <strong>responsive interfaces</strong> powered by robust server-side logic and efficient databases.
      </p>
      <div class="stats-row">
        <div class="stat">
          <div class="stat-num">2+</div>
          <div class="stat-label">Years Exp.</div>
        </div>
        <div class="stat">
          <div class="stat-num">10+</div>
          <div class="stat-label">Projects</div>
        </div>
        <div class="stat">
          <div class="stat-num">5+</div>
          <div class="stat-label">Technologies</div>
        </div>
      </div>
    </div>

    <div class="about-card">
      <div class="card-line">
        <span class="card-key">Role</span>
        <span class="card-val">Fullstack Developer</span>
      </div>
      <div class="card-line">
        <span class="card-key">Location</span>
        <span class="card-val">India 🇮🇳</span>
      </div>
      <div class="card-line">
        <span class="card-key">Specialisation</span>
        <span class="card-val">Angular · PHP · MySQL</span>
      </div>
      <div class="card-line">
        <span class="card-key">Frontend</span>
        <span class="card-val">HTML · CSS · JS · Angular</span>
      </div>
      <div class="card-line">
        <span class="card-key">Backend</span>
        <span class="card-val">PHP · Node.js</span>
      </div>
      <div class="card-line">
        <span class="card-key">Database</span>
        <span class="card-val">MySQL</span>
      </div>
      <div class="card-line">
        <span class="card-key">Status</span>
        <span class="badge-chip chip-green">Open to Work</span>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">Tech Stack</div>
  <h2 class="section-title">Skills & Technologies</h2>
  <p class="section-sub">A well-rounded toolkit for building complete web solutions — from pixel-perfect UIs to performant backend systems.</p>

  <div class="skills-grid">
    <div class="skill-card">
      <div class="skill-icon icon-purple">🅰️</div>
      <div class="skill-name">Angular</div>
      <div class="skill-desc">Building dynamic SPAs with component-based architecture and powerful CLI tooling.</div>
      <div class="skill-tags">
        <span class="tag">TypeScript</span>
        <span class="tag">RxJS</span>
        <span class="tag">NgRx</span>
        <span class="tag">Routing</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon icon-cyan">🌐</div>
      <div class="skill-name">HTML5 & CSS3</div>
      <div class="skill-desc">Crafting semantic, accessible markup with modern layouts using Flexbox and Grid.</div>
      <div class="skill-tags">
        <span class="tag">Flexbox</span>
        <span class="tag">Grid</span>
        <span class="tag">Animations</span>
        <span class="tag">Responsive</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon icon-amber">⚡</div>
      <div class="skill-name">JavaScript</div>
      <div class="skill-desc">Writing clean, modern ES6+ JavaScript for interactive and data-driven interfaces.</div>
      <div class="skill-tags">
        <span class="tag">ES6+</span>
        <span class="tag">DOM</span>
        <span class="tag">Fetch API</span>
        <span class="tag">Async/Await</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon icon-blue">🐘</div>
      <div class="skill-name">PHP</div>
      <div class="skill-desc">Server-side development with PHP — REST APIs, authentication, and MVC patterns.</div>
      <div class="skill-tags">
        <span class="tag">REST API</span>
        <span class="tag">MVC</span>
        <span class="tag">Auth</span>
        <span class="tag">CRUD</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon icon-green">🗄️</div>
      <div class="skill-name">MySQL</div>
      <div class="skill-desc">Designing normalised schemas, writing optimised queries, and managing relational databases.</div>
      <div class="skill-tags">
        <span class="tag">Schema Design</span>
        <span class="tag">Joins</span>
        <span class="tag">Indexing</span>
        <span class="tag">Stored Procs</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon icon-rose">🛠️</div>
      <div class="skill-name">Tools & Others</div>
      <div class="skill-desc">Version control, runtime environments, and additional languages for a complete dev workflow.</div>
      <div class="skill-tags">
        <span class="tag">Git</span>
        <span class="tag">Node.js</span>
        <span class="tag">Bootstrap</span>
        <span class="tag">Python</span>
        <span class="tag">Java</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">Portfolio</div>
  <h2 class="section-title">Featured Projects</h2>
  <p class="section-sub">A selection of real-world projects that showcase my fullstack capabilities.</p>

  <div class="projects-grid">
    <div class="project-card featured">
      <div>
        <div class="project-number">PROJECT 01 · FEATURED</div>
        <h3 class="project-title">E-Commerce Web Application</h3>
        <p class="project-desc">
          A full-featured e-commerce platform with product listings, cart management, user authentication,
          admin dashboard, and order tracking. Built with Angular frontend and PHP REST API backend.
        </p>
        <div class="project-stack">
          <span class="stack-tag stack-purple">Angular</span>
          <span class="stack-tag stack-cyan">TypeScript</span>
          <span class="stack-tag stack-amber">PHP</span>
          <span class="stack-tag stack-green">MySQL</span>
        </div>
        <a href="#" class="project-link">View Project → </a>
      </div>
      <div class="project-mockup">🛒</div>
    </div>

    <div class="project-card">
      <div class="project-number">PROJECT 02</div>
      <h3 class="project-title">Student Management System</h3>
      <p class="project-desc">
        A comprehensive portal for managing students, courses, grades, and attendance with role-based access control.
      </p>
      <div class="project-stack">
        <span class="stack-tag stack-purple">Angular</span>
        <span class="stack-tag stack-amber">PHP</span>
        <span class="stack-tag stack-green">MySQL</span>
      </div>
      <a href="#" class="project-link">View Project →</a>
    </div>

    <div class="project-card">
      <div class="project-number">PROJECT 03</div>
      <h3 class="project-title">Hospital Appointment System</h3>
      <p class="project-desc">
        Online appointment booking system with doctor scheduling, patient records, and automated email reminders.
      </p>
      <div class="project-stack">
        <span class="stack-tag stack-cyan">Node.js</span>
        <span class="stack-tag stack-purple">Angular</span>
        <span class="stack-tag stack-green">MySQL</span>
      </div>
      <a href="#" class="project-link">View Project →</a>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-wrapper">
    <div class="contact-info">
      <div class="section-label">Contact</div>
      <h2>Let's Build<br/>Something Great</h2>
      <p>
        I'm open to freelance projects, full-time opportunities, and collaborations.
        Drop a message and I'll get back to you soon!
      </p>
      <ul class="contact-list">
        <li class="contact-item">
          <div class="contact-icon">📧</div>
          <div>
            <div class="contact-label">Email</div>
            <div class="contact-detail">sriprasath@email.com</div>
          </div>
        </li>
        <li class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <div class="contact-label">Location</div>
            <div class="contact-detail">India</div>
          </div>
        </li>
        <li class="contact-item">
          <div class="contact-icon">💼</div>
          <div>
            <div class="contact-label">GitHub</div>
            <div class="contact-detail">github.com/sathish0205</div>
          </div>
        </li>
      </ul>
    </div>

    <form class="contact-form" onsubmit="return false;">
      <div class="form-group">
        <label class="form-label">Your Name</label>
        <input type="text" class="form-input" placeholder="John Doe" />
      </div>
      <div class="form-group">
        <label class="form-label">Email Address</label>
        <input type="email" class="form-input" placeholder="john@email.com" />
      </div>
      <div class="form-group">
        <label class="form-label">Message</label>
        <textarea class="form-textarea" placeholder="Hey Sri, I'd like to discuss a project..."></textarea>
      </div>
      <button type="submit" class="btn-primary" style="width:100%;text-align:center;">Send Message →</button>
    </form>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-copy">© 2024 Sri Prasath · Fullstack Developer · India</div>
  <ul class="footer-links">
    <li><a href="#">GitHub</a></li>
    <li><a href="#">LinkedIn</a></li>
    <li><a href="#">Twitter</a></li>
  </ul>
</footer>

</body>
</html>
