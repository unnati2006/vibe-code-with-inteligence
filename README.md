# ⚡ Vibe Code IDE

A browser-based AI Code Editor (similar to StackBlitz & Replit) powered by Next.js 15, WebContainers API, Monaco Editor, Xterm.js, MongoDB + Prisma ORM, and local Ollama LLMs.

---

## ✨ Features

- **In-Browser Node.js Runtime**: Full interactive development runtime powered by `@webcontainer/api` and `jsh`.
- **Dynamic File Tree & Virtual FS**: Create, rename, delete files and folders; real-time sync with `container.fs` and `container.mount()`.
- **Interactive Terminal**: Real-time bidirectional streaming terminal via `xterm.js` and `xterm-addon-fit`.
- **Monaco Code Editor**: VS Code-grade editing experience with automatic language detection and cursor context extraction.
- **Dynamic Port Preview**: Real-time dev server detection (`server-ready` event) rendering in an isolated iframe.
- **Local AI Code Assistant**: Connects to local Ollama (`http://localhost:11434`) via streaming API route (`/api/generate`) for context-aware code completion, bug fixing, and refactoring.
- **Template Support**: Ready-to-run templates for **React (Vite)**, **Express**, **Hono**, and **Node.js**.
- **Auth & Persistence**: MongoDB storage for project templates and user accounts via Prisma ORM & NextAuth.js.

---

## 🛠️ Tech Stack

- **Framework**: Next.js 15 (App Router), React 19, TypeScript
- **Execution Engine**: `@webcontainer/api`
- **Editor**: `@monaco-editor/react`
- **Terminal**: `xterm`, `xterm-addon-fit`
- **Database & Auth**: MongoDB, Prisma ORM, NextAuth.js
- **Local AI**: Ollama (`codellama`, `llama3`, `qwen2.5-coder`)
- **Styling**: Tailwind CSS & Lucide Icons

---

## 🚀 Quick Start

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure Environment Variables
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```
Ensure your `DATABASE_URL` is set to your MongoDB database.

### 3. Generate Prisma Client
```bash
npx prisma generate
```

### 4. Start Local Ollama
Ensure you have Ollama installed with your preferred coding model:
```bash
# Pull model
ollama pull codellama

# Run Ollama with CORS origins enabled
# Windows PowerShell:
$env:OLLAMA_ORIGINS="*"
ollama serve

# Linux / macOS:
OLLAMA_ORIGINS="*" ollama serve
```

### 5. Run the IDE
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🔒 Cross-Origin Isolation Note
WebContainers require `SharedArrayBuffer` which requires Cross-Origin Isolation headers:
```
Cross-Origin-Embedder-Policy: require-corp
Cross-Origin-Opener-Policy: same-origin
```
These are pre-configured in `next.config.ts`.
