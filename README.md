# The Reading Room · 词汇索引
<span style="font-size: 0.75em; color: #888;">个人词汇索引网站 — 由 Skill 4 自动填充</span>

A personal vocabulary index, built from words encountered during academic reading. Each entry is treated as a catalog card, not a flashcard — meant for reference, not drill.

<span style="font-size: 0.75em; color: #888;">学术阅读中遇到的词汇个人索引。每个词条按目录卡处理，不是抽认卡——为查阅而设，非为刷题。</span>

---

## Live URL · 网址

After publishing to GitHub Pages: **https://serena967wmq.github.io/vocab/**

<span style="font-size: 0.75em; color: #888;">发布到 GitHub Pages 后的访问地址（见上）</span>

---

## How to Deploy (One-Time Setup) · 首次部署

1. Open **GitHub Desktop**. Confirm the `vocab` repository is open.
2. Drag `index.html`, `vocab.json`, and `README.md` into the repo folder (`/Users/serena967/Documents/GitHub/vocab/`).
3. In GitHub Desktop, you'll see the three files appear under "Changes".
4. At the bottom-left, write a commit summary: `Initial scaffold`. Click **Commit to main**.
5. Top-right, click **Publish repository** (this pushes to GitHub.com for the first time). Untick "Keep this code private" if you want the site publicly accessible — required for free GitHub Pages.
6. Once published, go to **github.com → your `vocab` repo → Settings → Pages**.
7. Under "Build and deployment", set:
   - Source: **Deploy from a branch**
   - Branch: **main** · folder: **/ (root)**
   - Click **Save**.
8. Wait 1–2 minutes. Visit the Live URL above. The site should load with one demo entry (the word "ubiquitous").

<span style="font-size: 0.75em; color: #888;">**首次部署步骤**：1. 打开 GitHub Desktop，确认 `vocab` repo 已打开 · 2. 把 `index.html`、`vocab.json`、`README.md` 三个文件拖到 repo 文件夹 · 3. GitHub Desktop 的 "Changes" 区域会显示这三个文件 · 4. 左下方写 commit 描述 `Initial scaffold`，点 **Commit to main** · 5. 右上点 **Publish repository**（首次推送到 GitHub.com）。取消勾选 "Keep this code private" 才能用免费的 GitHub Pages · 6. 发布后到 github.com → 你的 `vocab` repo → Settings → Pages · 7. "Build and deployment" 设置：Source: Deploy from a branch · Branch: main · folder: / (root) · 点 Save · 8. 等 1–2 分钟，访问上面的网址，应该能看到一个演示词条 "ubiquitous"</span>

---

## How to Update (Each Time Skill 4 Adds Words) · 日常更新

1. Skill 4 (in Claude) generates a new `vocab.json` (or an updated version).
2. You replace `vocab.json` in `/Users/serena967/Documents/GitHub/vocab/` with the new file.
3. In GitHub Desktop, you'll see `vocab.json` under "Changes".
4. Write a commit summary like `Add 12 words from McKee 2010`. Click **Commit to main**.
5. Top-right, click **Push origin**.
6. Wait ~1 minute. Refresh the Live URL. New words appear.

<span style="font-size: 0.75em; color: #888;">**日常更新步骤**：1. Skill 4 生成新版 `vocab.json` · 2. 用新文件替换 repo 里旧的 `vocab.json` · 3. GitHub Desktop 的 Changes 会看到 vocab.json · 4. 写 commit 描述（如 "Add 12 words from McKee 2010"），点 Commit to main · 5. 右上点 Push origin · 6. 等约 1 分钟，刷新网址，新词出现</span>

---

## File Structure · 文件结构

```
vocab/
├── index.html      ← the website itself · 网站本体
├── vocab.json      ← all word data · 全部词汇数据
└── README.md       ← this file · 本文件
```

Three files total. No build step, no framework, no dependencies. Everything runs in the browser.

<span style="font-size: 0.75em; color: #888;">共三个文件。无构建步骤、无框架、无依赖。一切在浏览器中运行。</span>

---

## vocab.json Schema · 数据格式

Each entry in the JSON array follows this shape:

```json
{
  "id": "string — unique identifier, e.g. 'word-source-page'",
  "word": "string — the English word or phrase",
  "ipa_uk": "string — British IPA, e.g. '/juːˈbɪk.wɪ.təs/' (optional)",
  "part_of_speech": "string — one of: n, v, adj, adv, phr (optional)",
  "meaning_zh": "string — Chinese meaning",
  "color": "string — 'blue' (general academic) or 'purple' (domain term)",
  "audio_url": "string or null — Cambridge Dictionary MP3 URL (falls back to dictionary page lookup if null)",
  "source": {
    "id": "string — matches the source's id in Obsidian",
    "title": "string — source title (book, article, etc.)",
    "author": "string or null",
    "year": "number or null"
  },
  "example": {
    "text": "string — the exact sentence from the source where this word appears",
    "page": "number or null",
    "paragraph": "number or null"
  },
  "obsidian_uri": "string or null — Advanced URI link to open this word's location in Obsidian",
  "date_added": "string — ISO date YYYY-MM-DD",
  "notes": "string — optional free-text notes"
}
```

<span style="font-size: 0.75em; color: #888;">**vocab.json 数据格式**：JSON 数组中每个词条遵循上述结构。`id` 唯一标识符 · `word` 英文词或短语 · `ipa_uk` 英式音标（可选）· `part_of_speech` 词性（n/v/adj/adv/phr，可选）· `meaning_zh` 中文释义 · `color` 颜色标签（blue 一般学术 / purple 专业术语）· `audio_url` 剑桥词典 MP3 URL（为 null 时回退到词典页面查询）· `source` 来源信息 · `example` 原文例句和位置 · `obsidian_uri` 跳转到 Obsidian 对应位置的链接 · `date_added` 加入日期 · `notes` 备注</span>

---

## Design · 设计说明

The aesthetic is a digital library card catalog — warm paper tones, serif typography (Cormorant Garamond for display, Spectral for body, Noto Serif SC for Chinese), subtle ruled lines on each card. The intention is a reference object meant to be returned to over years, not a gamified language-learning app.

Colour coding follows Skill 4's logic: blue dot for general academic words above the user's CEFR threshold; purple dot for domain-specific terminology within a given source.

<span style="font-size: 0.75em; color: #888;">**设计说明**：美学风格为数字图书馆目录卡——温润纸色、衬线字体（Cormorant Garamond 用于标题，Spectral 用于正文，Noto Serif SC 用于中文）、每张卡片有细微的横纹线。意图是做一个可以多年回访的参考对象，而非游戏化的语言学习 app。颜色编码沿用 Skill 4 的逻辑：蓝点 = 超过用户 CEFR 阈值的一般学术词；紫点 = 某来源内的专业术语。</span>

---

*Built on Skills 1–4 in the Research Lab project. See `_Hub/skill4-handoff.md` in the Obsidian vault for full design context.*

<span style="font-size: 0.75em; color: #888;">建立在 Research Lab 项目的 Skills 1–4 之上。完整设计上下文见 Obsidian 资料库的 `_Hub/skill4-handoff.md`。</span>
