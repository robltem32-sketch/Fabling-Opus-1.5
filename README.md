# Fabling Opus 1.5

**Бесплатный локальный AI-помощник (чат + редактор + терминал + Git + vision) под Windows — без подписок и телеметрии.**

Fabling Opus 1.5 — открытый и полностью бесплатный десктоп‑клиент, который работает
с локальными моделями через [Ollama](https://ollama.com) (qwen2.5-coder, Llama 3.2, llava/qwen2.5-vl и др.).
Всё вычисление происходит на вашей машине: никаких платных API, никакой отправки кода в облако.

## Возможности (v1)
- Чат с Markdown/код-блоками, режимы **Ask / Plan / Code**
- Редактор с подсветкой синтаксиса (Monaco) + показ diff и применение патчей из ответов ИИ
- Встроенный терминал (xterm.js) с командами из чата (на подтверждении)
- Git-панель: статус, diff, commit
- Vision: загрузка картинок (включая screenshots низкого качества) → base64 + лёгкая предобработка (контраст/резкость) → Ollama vision‑модель
- CI-ready: локальный build под Windows (`.exe`)

## Архитектура
- UI: **Tauri 2 + React + Vite + TypeScript**
- Бэкенд: **Rust** (команды файловой системы, shell, Git)
- ИИ: **Ollama HTTP API** (`http://127.0.0.1:11434/api/chat`) — потоковые ответы
- Vision: предобработка на canvas + передача base64 в `images`

## Требования
- Windows 10/11 (x64) **или** macOS/Linux (кроссплатформенный, основной тест — Windows)
- [Ollama](https://ollama.com/download) установлен и запущен
- Модели (примеры):
  ```bash
  ollama pull qwen2.5-coder:7b
  ollama pull qwen2.5-vl:7b       # для vision
  ```
- Rust toolchain + Node LTS 20+ для сборки из исходников

## Быстрый старт (разработчик)
```bash
git clone <repo>
cd fabling-opus-1.5
npm install
npm run tauri dev
```

## Сборка .exe
```bash
npm run tauri build
# результат в src-tauri/target/release/bundle/nsis/*.exe
```

## Лицензия
MIT — свободно используйте, форкайте, модифицируйте. Без навязанных подписок и данных.
