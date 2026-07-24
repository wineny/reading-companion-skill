# 📖 Reading Companion — a Claude Code / Agent Skill

*[한국어 README](./README.ko.md)*

A skill that **reads a book with you across multiple sessions.** While you read a PDF or physical book yourself, Claude takes on three roles:

1. **Archivist** — saves the quotes you love, verbatim, into an archive.
2. **Tutor** — when you ask about a confusing passage, it explains *and* logs that learning point.
3. **Review coach** — quizzes you on what you read that day and builds **spaced-repetition review cards**.

> What sets it apart: highlight apps review *the quotes you picked*. This skill reviews ***the things you didn't understand and asked about.*** It closes the "confusion → explanation → future review" loop.

## What it produces

Inside the folder of the book you're reading, it creates and keeps updating two things:

- **`독서아카이브.md` (reading archive)** — ① a dated reading log (range read · favorite quotes · your notes), ② a running collection of all quotes, ③ a table-of-contents progress checklist.
- **`복습/YYYY-MM-DD_복습.md` (review cards)** — one spaced-repetition card per day (score summary · weak spots · questions+answers · review schedule: tomorrow → 3 days → 1 week).

> Note: the templates are written in Korean. Swap the wording in `assets/` for any language you like — the workflow is language-agnostic.

## Install

Copy it into your Claude Code personal skills folder.

```bash
git clone https://github.com/wineny/reading-companion-skill.git
mkdir -p ~/.claude/skills/reading-companion
cp -R reading-companion-skill/SKILL.md reading-companion-skill/assets ~/.claude/skills/reading-companion/
```

Once `SKILL.md` and `assets/` sit under `~/.claude/skills/reading-companion/`, you're ready.

## How to use

Start a conversation from the folder of the book you're reading, and just talk naturally:

- **Start** — "let's read this book together" / "start reading" → if no archive exists, it extracts the table of contents and creates one; if it does, it picks up from where you left off.
- **Save a quote** — hand it a sentence and it stores it verbatim in the archive.
- **Ask** — "what does this part mean?" → it explains and logs the point into your notes.
- **Review** — "quiz me on today's reading" / "let's review" → 5–8 questions, one at a time, graded, then a review card.
- **Re-review** — another day, "let's do the review cards" → it re-runs an old card with answers hidden and records your progress.

## Structure

```
reading-companion/
├── SKILL.md                 # workflow definition (frontmatter + procedure)
└── assets/
    ├── 독서아카이브.md         # log / quote-collection / TOC template
    └── 복습카드.md             # score / weak-spot / spaced-repetition template
```

## Why it exists

A good reading routine — collect quotes, ask questions, then quiz yourself with spaced repetition — is easy to do by hand but tedious to keep up across a whole book. This skill turns that routine into something Claude runs for you, session after session. I looked hard across the ecosystem (Claude skill marketplaces, Readwise, RemNote, custom GPTs, and more) and found no single tool that combines quote archiving + a log of what confused you + a daily quiz on that day's pages + spaced repetition. This fills that gap.

## License

MIT
