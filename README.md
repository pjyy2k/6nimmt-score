# 6 nimmt! Scorekeeper

A lightweight, multilingual scorekeeper for **2–10 players**. Enter penalty points after each round and follow the running totals and rankings.

**Operator:** [JinYoungPark](https://github.com/pjyy2k)  
**Repository:** [pjyy2k/6nimmt-score](https://github.com/pjyy2k/6nimmt-score)

## Features

- Choose 2–10 players and edit their names.
- Record, edit, and delete round scores.
- Calculate cumulative totals and rankings automatically; tied scores share a rank.
- Set the end score (default: **66**). When anyone reaches it, the lowest total is shown as the winner.
- Automatically save names, scores, and the current entry in the same browser.
- Export/import JSON backups and export scores as UTF-8 CSV.
- Use the responsive interface on phones, tablets, and desktops.
- Run without a backend, build step, package installation, or third-party libraries.

This is a scorekeeping companion; it does not manage cards or enforce card-play rules.

## Languages

English, Korean, Japanese, Simplified Chinese, German, French, Spanish, and Portuguese.

The initial interface language follows supported browser language preferences, with English as the fallback. Select another language using the selector at the top; the choice is remembered in that browser.

Default participant names are always **Player 1**, **Player 2**, and so on. Custom names and recorded scores remain unchanged when switching languages.

## Quick start

1. Download or clone this repository.
2. Keep `index.html` and `app.js` in the **same directory**.
3. Open `index.html` in a modern web browser.
4. Open **Players** to set the player count and names.
5. Enter each player's penalty points for the current round, then select **Save round**.

A local HTTP server can also serve the directory. For example, with Python installed:

```sh
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

Direct file opening works offline in browsers that allow local JavaScript. File preview apps may restrict script execution or saving. There is no service worker, so an online deployment does not guarantee offline access.

## Static deployment

Publish the repository root as the site's public directory:

- Entry page: `index.html`
- JavaScript: `app.js`
- Build command: none
- Backend: none

For a static host such as Coolify, GitHub Pages, or a conventional web server, serve **both files together** and preserve their relative paths. Uploading only `index.html` is insufficient.

## Player changes

- Adding players preserves existing scores. New players receive **0** for earlier rounds.
- Reducing the player count removes players from the end of the list and their score history after confirmation.
- Starting a new game clears the scores while keeping the participant names and end score.

For a fair new session with a different group, start a new game after setting the participants.

## Saving and backups

Game data and the selected language are stored in the browser's `localStorage`.

- Records are local to that browser and site address. They are **not synchronized** between devices.
- Clearing site data or using private browsing may remove records.
- Use **Save backup** to download a JSON backup before moving to another device or clearing browser data.
- **Load backup** replaces the current participant names and scores after confirmation.
- CSV exports are for viewing or spreadsheet analysis; import uses JSON backups.
- The application does not send scores or participant names to a server.

Previous six-player JSON backups remain supported. Existing translated default names are normalized to English when loaded.

## Project structure

```text
index.html   Page structure and styles
app.js       Translations, scoring, browser storage, and UI interactions
README.md    Usage and deployment documentation
```

The page loads `app.js` with `defer`. Keeping JavaScript separate makes maintenance easier and allows browsers to cache it independently; actual cache behavior depends on the hosting server's HTTP headers.

## 한국어 안내

참가자 설정에서 2~10명과 이름을 지정한 후, 라운드별 벌점을 입력하고 저장하세요. 누적 점수가 낮은 사람이 높은 순위입니다. 이름과 점수는 현재 브라우저에 저장되므로 중요한 기록은 JSON으로 백업하세요.

정적 배포 시 `index.html`과 `app.js`를 같은 폴더에 함께 배포해야 합니다. 별도의 빌드나 서버 프로그램은 필요하지 않습니다.
