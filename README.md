# Vibe-Coding Workshop Site (CARAVAN 2026)

**Live site:** https://urimtal.github.io/vibe/

🇬🇧 [English](#english) · 🇰🇿 [Қазақша](#қазақша)

---

## English

Interactive session site for the masterclass **"AI in Journalism: Vibe-Coding and News Automation"** — CARAVAN · Connect for Peace 2026 festival, Almaty, SmartPoint (Freedom hall), **8 July 2026, 11:30–13:00**, session language: Russian. Trainer: Askhat Yerkimbay (Internews).

> ⚡ The site itself is a live demonstration of the method it teaches: built in one evening with Claude Code, zero lines of code written by hand.

### What the site does

The whole session runs through this site on participants' phones:

1. **Team assignment** — a participant enters their name and is assigned to one of 6 fictional Central Asian newsrooms: *Aral* (ecology, Aral Sea region) · *Kosh* (labour migration, Bishkek/Osh) · *Zhibek Zholy* (cross-border economy, Khujand–Shymkent) · *Khazar* (Caspian coast, Turkmenistan) · *Fact.Asia* (regional fact-checking/FIMI) · *Yoshlar* (youth media, Tashkent)
2. **Programme** — the 90-minute timeline
3. **The task** — build an editorial AI assistant + Joe Amditis's 4 questions + team roles
4. **Practice: 2 tracks** — step-by-step checklists (Google AI Studio prompt agent / Build mini-app), a **prompt constructor** auto-filled from the newsroom card, and a v1→v4 upgrade ladder
5. **The Radar formula** — agent + "hands" + "alarm clock" = Radar
6. **Demo** — teams share their agent links via Telegram
7. **Materials** — "Build Your Own Radar" guides (KK/RU), the Amditis article, Knight Center
8. **Ethics and boundaries** — a digest of Knight Center courses and the Internews GenAI Policy

### How it works (technical)

- **Single file** — `index.html`: HTML + CSS + JS, no build step. The only external request is Google Fonts (Montserrat); if blocked, the site falls back to system fonts.
- **No backend, no data collection.** Name, team and checklist state live only in the participant's own browser (`localStorage`). Nothing is ever sent to a server.
- **Hash-based assignment:** djb2 hash of the name → `hash % 6` → newsroom. Deterministic (same name = same team), computed on the phone. Not perfectly balanced — the trainer merges small teams in the room (the site tells participants to expect this).
- **Hosting:** GitHub Pages (`main` branch, root). Static CDN — does not fall over regardless of audience size.
- **Design:** the festival's official style — cream `#F6ECE0`, navy `#1B2A4A`, orange `#D9661E`, Montserrat, EU + Connect for Peace + Internews logo band on top, ornament strip at the bottom. Mobile-first, two-column grid on large screens.

### Reusing for a future training

Everything to adapt lives in `index.html`:

| What to change | Where |
|---|---|
| Newsrooms (name, region, audience, topics, language) | `TEAMS` array (top of `<script>`) |
| Telegram group link | `TELEGRAM_LINK` constant (if empty, a "shared group" notice is shown) |
| Title, date, venue | `<header>` + `<title>` |
| Programme timeline | `#program` section |
| Checklist steps | `#track1` / `#track2` |
| Prompt template text | `tplText()` and `renderBuildTpl()` functions |
| Colours | `:root` CSS variables |

After editing: `git commit` + `git push` — GitHub Pages redeploys in 1–2 minutes.

### Credits

Askhat Yerkimbay — ayerkimbay@internews.org
Built by vibe-coding with Claude Code (July 2026).
Frameworks referenced: Joe Amditis (Center for Cooperative Media / Knight Center), Internews GenAI Policy.

---

## Қазақша

**«ИИ в журналистике: вайб-кодинг и автоматизация новостей»** мастер-класының интерактивті сайты — CARAVAN · Connect for Peace 2026 фестивалі, Алматы, SmartPoint (Freedom залы), **8 шілде 2026, 11:30–13:00**, сессия тілі — орысша. Тренер: Асхат Еркімбай (Internews).

> ⚡ Бұл сайттың өзі — үйрететін әдістің көрнекі мысалы: бір кеште, қолмен нөл жол код жазылмай, Claude Code-пен құрастырылған.

### Сайт не істейді

Сессия қатысушы телефонындағы осы сайт арқылы жүргізіледі:

1. **Редакцияға бөлу** — қатысушы атын енгізеді, сайт оны Орталық Азияның 6 фиктивті редакциясының біріне бөледі: «Арал» (экология, Приаралье) · «Көш» (еңбек миграциясы, Бішкек/Ош) · «Жібек Жолы» (шекара экономикасы, Худжанд–Шымкент) · «Хазар» (Каспий жағалауы, Түрікменстан) · «Факт.Азия» (аймақтық фактчек/FIMI) · «Yoshlar» (жастар медиасы, Ташкент)
2. **Бағдарлама** — 90 минуттың таймлайны
3. **Тапсырма** — редакциялық ЖИ-ассистент құру + Джо Амдитистің 4 сұрағы + командадағы рөлдер
4. **Практика: 2 трек** — қадамдық чек-листтер (Google AI Studio промпт-агент / Build мини-қосымша), редакция деректерінен автотолатын **промпт-конструктор**, v1→v4 апгрейд сатысы
5. **Радар формуласы** — агент + «қолдар» + «оятар» = Радар
6. **Демо** — командалар агент сілтемесін Telegram арқылы бөліседі
7. **Материалдар** — «Өз Радарыңды құрастыр» гайдтары (қаз/ор), Амдитис мақаласы, Knight Center
8. **Этика және шекаралар** — Knight Center курстары мен Internews GenAI Policy конспектісі

### Қалай жұмыс істейді (техникалық)

- **Бір файл** — `index.html`: HTML + CSS + JS, құрастыру қадамы жоқ. Жалғыз сыртқы сұраныс — Google Fonts (Montserrat); жүктелмесе жүйелік шрифтпен ашыла береді.
- **Бэкенд жоқ, дерек жиналмайды.** Аты-жөн, редакция, чек-лист күйі — тек қатысушының өз браузерінде (`localStorage`). Серверге ешбір байт кетпейді.
- **Хэш-бөлу:** аттың djb2-хэші → `hash % 6` → редакция. Детерминді (сол ат = сол редакция), телефон ішінде есептеледі. Дәл тепе-тең емес — аз топты тренер залда біріктіреді (сайт бұл туралы алдын ала ескертеді).
- **Хостинг:** GitHub Pages (`main` бұтағы, түбір). Статикалық CDN — қатысушы санынан құламайды.
- **Дизайн:** фестивальдің ресми стилі — кремовый `#F6ECE0`, navy `#1B2A4A`, қызғылт сары `#D9661E`, Montserrat, жоғарыда EU + Connect for Peace + Internews лого-жолағы, төменде ою-өрнек. Mobile-first, үлкен экранда 2 бағанды grid.

### Болашақта қайта пайдалану

Бейімдейтіннің бәрі — `index.html` ішінде:

| Не өзгертесің | Қайда |
|---|---|
| Редакциялар (аты, аймақ, аудитория, темалар, тіл) | `TEAMS` массиві (`<script>` басында) |
| Telegram-топ сілтемесі | `TELEGRAM_LINK` константасы (бос болса — «жалпы топ» ескертуі шығады) |
| Тақырып, күн, орын | `<header>` + `<title>` |
| Бағдарлама таймлайны | `#program` секциясы |
| Чек-лист қадамдары | `#track1` / `#track2` |
| Промпт-шаблон мәтіні | `tplText()` және `renderBuildTpl()` функциялары |
| Түстер | `:root` CSS айнымалылары |

Өзгерткен соң: `git commit` + `git push` — GitHub Pages 1–2 минутта жаңартады.

### Авторлық

Асхат Еркімбай — ayerkimbay@internews.org
Claude Code-пен вайб-кодинг әдісімен жасалған (шілде 2026).
Фреймворк-дереккөздер: Джо Амдитис (Center for Cooperative Media / Knight Center), Internews GenAI Policy.
