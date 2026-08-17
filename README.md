# Mon Parcours en Français 🇫🇷 — French Beginner Learning App

A complete **French learning app** for Bengali speakers (lessons explained in বাংলা with Bengali
pronunciation) built with **React + Vite**. All course content lives in **JSON data files** under
`src/data/` — you can add or edit content without touching any React code.

## Highlights

- 🗺️ **13-week / 3-month roadmap** — levels **A0 → A1 → A2 → B1 → B2**, 7 days per week, each day
  has structured task badges: `Learn · Sound · Rules · Grammar · Vocab · Flashcards · Reading ·
  Writing · Practice · Listen · Review`
- 🔊 **Play audio** on every French word, sentence, conjugation and full passage — built-in Web
  Speech API (`fr-FR`), no audio files needed
- 🀄 **Bengali pronunciation (বাংলা উচ্চারণ)** shown next to every French word/sentence
- 📘 **Grammar** — 27 lessons with conjugation tables, formulas, examples and tips
- 🔢 **Numbers & Time** — 0–999 number generator + time, days, months, seasons
- 🃏 **Flashcards** with spaced repetition (boxes + due dates)
- ✍️ **Practice** — 10 exercise chapters + 8 writing tasks
- 📖 **Reading** — 5 passages with Bengali pronunciation, translation, vocab & questions
- 💡 **Reference & Tips** — 12 cheat sheets, 14 memory tricks, confusables, sentence templates
- 🔍 **Dictionary** — 148 words with search + A–Z filter
- 🔎 **Search & filter** on every tab
- 📈 **Progress** — streaks, day completion, mastered words (saved in `localStorage`)

## Getting started

```bash
npm install
npm run dev        # start the dev server (Vite)
npm run build      # production build → dist/
npm run preview    # preview the production build
npm run check      # validate all JSON data files
```

## Project structure

```
├── index.html
├── package.json
├── vite.config.js
├── scripts/
│   └── check-data.cjs          # JSON data sanity check
└── src/
    ├── main.jsx
    ├── App.jsx                 # tabs + shared state + progress
    ├── styles.css
    ├── hooks/usePersistedState.js
    ├── lib/speak.js            # Web Speech API helper (fr-FR)
    ├── components/             # one component per tab + shared UI
    └── data/                   # ← ALL CONTENT (JSON)
        ├── roadmap.json        # 13 weeks × 7 days
        ├── sounds.json         # alphabet, accents, sound combos, liaison…
        ├── grammar.json        # 27 grammar lessons
        ├── vocabulary.json     # 21 themed categories (~212 words)
        ├── numbers.json        # numbers, time, days, months, seasons
        ├── flashcards.json     # 11 decks (~121 cards)
        ├── practice.json       # 10 exercise chapters + 8 writing tasks
        ├── reading.json        # 5 passages with comprehension
        ├── reference.json      # cheat sheets, tips, confusables, templates
        └── dictionary.json     # 148 A–Z words
```

## How to add content (no code changes needed)

- **Roadmap** — append a week object to `roadmap.json` (`week`, `level`, `title`, `theme`, `goal`,
  `days[].title/tasks[]/tip`). Task `type` picks the badge; `ref` makes a jump-button to another tab.
- **Vocabulary** — add a category `{category, level, emoji, items:[{fr,bn,en}]}`. The same list is
  searchable and filterable automatically.
- **Flashcards** — add a deck `{id, name, emoji, cards:[{fr,bn,en}]}`.
- **Grammar** — append a lesson `{id, category, level, emoji, title, intro, formula, header, rows,
  examples, tips}`. The category filter fills itself.
- **Everything else** — same pattern: JSON in, UI out.

## Notes

- Audio uses the browser's built-in `speechSynthesis` with `fr-FR` — an internet-free TTS that
  works in Chrome/Edge/Safari. Voice availability depends on the OS.
- Progress (completed days, flashcard boxes/due dates, streak) is persisted in `localStorage`
  under the key `french-app-state`. Use the Progress tab to reset.
- Content is derived from the learner's own French class notes (docx files) — Bengali
  pronunciations are phonetic approximations, best combined with the audio buttons.
