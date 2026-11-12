<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>অফলাইন গেম হাব - Offline Game Hub</title>
  <style>
    :root {
      --bg-dark: #0f172a;
      --bg-card: #1e293b;
      --bg-hover: #334155;
      --primary: #3b82f6;
      --primary-hover: #2563eb;
      --accent: #10b981;
      --accent-hover: #059669;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --border: #334155;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: var(--bg-dark);
      color: var(--text-main);
      line-height: 1.6;
    }

    /* Header & Navbar */
    header {
      background-color: rgba(15, 23, 42, 0.95);
      border-bottom: 1px solid var(--border);
      padding: 1rem 5%;
      position: sticky;
      top: 0;
      z-index: 100;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
    }

    .logo {
      font-size: 1.5rem;
      font-weight: bold;
      color: var(--primary);
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .logo span {
      color: var(--text-main);
    }

    .nav-actions {
      display: flex;
      gap: 1rem;
      align-items: center;
      flex-wrap: wrap;
    }

    .search-box {
      padding: 0.5rem 1rem;
      border-radius: 8px;
      border: 1px solid var(--border);
      background: var(--bg-card);
      color: var(--text-main);
      outline: none;
      min-width: 220px;
    }

    .search-box:focus {
      border-color: var(--primary);
    }

    .btn {
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      font-size: 0.9rem;
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }
    .btn-primary:hover {
      background: var(--primary-hover);
    }

    .btn-accent {
      background: var(--accent);
      color: white;
    }
    .btn-accent:hover {
      background: var(--accent-hover);
    }

    .btn-outline {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-main);
    }
    .btn-outline:hover {
      background: var(--bg-hover);
    }

    /* Hero Banner */
    .hero {
      text-align: center;
      padding: 3rem 5% 2rem;
      background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
      border-bottom: 1px solid var(--border);
    }

    .hero h1 {
      font-size: 2.2rem;
      margin-bottom: 0.5rem;
    }

    .hero p {
      color: var(--text-muted);
      max-width: 650px;
      margin: 0 auto 1.5rem;
    }

    /* Categories */
    .categories {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 0.6rem;
      padding: 1.5rem 5%;
    }

    .cat-btn {
      padding: 0.45rem 1.1rem;
      border-radius: 20px;
      border: 1px solid var(--border);
      background: var(--bg-card);
      color: var(--text-muted);
      cursor: pointer;
      font-weight: 600;
      transition: 0.2s;
    }

    .cat-btn.active, .cat-btn:hover {
      background: var(--primary);
      color: white;
      border-color: var(--primary);
    }

    /* Game Grid */
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem 5% 4rem;
    }

    .section-title {
      margin-bottom: 1.2rem;
      font-size: 1.3rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .game-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
      gap: 1.5rem;
    }

    .game-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      overflow: hidden;
      transition: transform 0.2s, box-shadow 0.2s;
      display: flex;
      flex-direction: column;
    }

    .game-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.3);
      border-color: var(--primary);
    }

    .game-banner {
      height: 140px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 4rem;
      background: linear-gradient(45deg, #1e3a8a, #312e81);
      position: relative;
    }

    .badge {
      position: absolute;
      top: 10px;
      right: 10px;
      background: rgba(15, 23, 42, 0.85);
      color: var(--accent);
      padding: 0.2rem 0.6rem;
      border-radius: 6px;
      font-size: 0.75rem;
      font-weight: bold;
      border: 1px solid var(--accent);
    }

    .game-info {
      padding: 1.2rem;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .game-meta {
      display: flex;
      justify-content: space-between;
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-bottom: 0.4rem;
    }

    .game-title {
      font-size: 1.15rem;
      font-weight: bold;
      margin-bottom: 0.5rem;
    }

    .game-desc {
      font-size: 0.88rem;
      color: var(--text-muted);
      margin-bottom: 1.2rem;
      flex: 1;
    }

    .card-actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 0.6rem;
    }

    /* Modal for Playing Game & Downloads */
    .modal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.85);
      z-index: 200;
      align-items: center;
      justify-content: center;
      padding: 1rem;
    }

    .modal.open {
      display: flex;
    }

    .modal-content {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 14px;
      width: 100%;
      max-width: 650px;
      max-height: 90vh;
      overflow-y: auto;
      padding: 1.5rem;
      position: relative;
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid var(--border);
      padding-bottom: 0.8rem;
      margin-bottom: 1rem;
    }

    .close-btn {
      background: #ef4444;
      color: white;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      font-weight: bold;
    }

    /* Game Canvas / Play Area */
    #gameStage {
      background: #090d16;
      border: 2px solid var(--border);
      border-radius: 10px;
      min-height: 340px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 1rem;
      text-align: center;
    }

    canvas {
      background: #000;
      border: 1px solid #334155;
      max-width: 100%;
    }

    /* Tic Tac Toe & Memory Grid */
    .ttt-grid {
      display: grid;
      grid-template-columns: repeat(3, 80px);
      gap: 8px;
      margin: 1rem auto;
    }
    .ttt-cell {
      width: 80px;
      height: 80px;
      background: var(--bg-card);
      border: 2px solid var(--primary);
      font-size: 2rem;
      font-weight: bold;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      border-radius: 8px;
    }

    .mem-grid {
      display: grid;
      grid-template-columns: repeat(4, 65px);
      gap: 8px;
      margin: 1rem auto;
    }
    .mem-card {
      width: 65px;
      height: 65px;
      background: var(--primary);
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.6rem;
      cursor: pointer;
      user-select: none;
    }
    .mem-card.flipped {
      background: var(--bg-card);
      border: 2px solid var(--accent);
    }

    .download-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.8rem;
      border-bottom: 1px solid var(--border);
    }

    footer {
      text-align: center;
      padding: 1
