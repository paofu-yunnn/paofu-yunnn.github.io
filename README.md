# 泡芙🐈藏書室

靜態網頁，可直接用 GitHub Pages 發布，不必安裝任何建置工具。
本機預覽時，用瀏覽器打開 `index.html` 即可，或用資料夾開一個本機網頁伺服器。

頁面上有兩個區塊：**劇本**與**角色卡**。新增、刪除、改簡介都只改 `scripts.js`。
點進劇本或角色卡，都會打開同一套獨立詳情頁（GitHub Pages 也適用，可直接分享網址）：劇本是 `detail.html?id=劇本代號`，角色卡是 `detail.html?type=char&id=角色代號`。

## 資料夾

- `index.html`：首頁外觀與互動（一般不用改）
- `detail.html`：劇本與角色卡的詳情頁（一般不用改）
- `scripts.js`：**新增、刪除、改簡介、改平台欄位與分頁內容都改這一份**
- `assets/covers/`：劇本封面（建議 16:9，例如 1024×576）。橫式圖會完整顯示，不會被裁切
- `assets/portraits/`：角色卡肖像（直式圖會以 3:4 的框完整顯示，不會被裁切）
- `assets/leads/`：詳情頁「角色介紹」用的肖像（可選，男女或其他登場角色都可以）
- `assets/screenshots/`：「作者的話」裡的試玩截圖（可選）
- `preview-*.png`：本機預覽截圖（上傳網站時不必放上去）

## 自己新增一部劇本

1. 若有封面，把圖檔放到 `assets/covers/`（只放檔案，例如 `my-cover.jpg`）
2. 打開 `scripts.js`，複製「劇本範本」那一整段（大括號 `{ }` 裡的內容）
3. 貼到 `WORKS` 陣列裡，通常放在最後一部的後面；若前面還有一部，記得在它的 `}` 後面加逗號
4. 一定要寫不重複的 `id`（詳情頁網址會用到，例如 `detail.html?id=transferlove`）
5. 改標題、版本、標籤、短介；有封面就把 `cover` 改成檔名，沒有就留 `""`
6. 平台欄位可按需要填：`category`、`hashtags`、`length`、`playerRole`、`targetGender`、`artStyle`、`blurb`、`quote`、`r18`、`chatLink`
7. 詳情分頁可按需要填：`story`（故事介紹，可用 `##` / `###` 小標）、`leads`（角色介紹，可寫任何性別）、`opening`（開場白試閱）、`authorNote` 與 `screenshots`（作者的話）
8. 「開始聊天」只要在 `chatLink` 填上網址就會出現按鈕；留空則不顯示
9. 沒有內容的分頁會自動隱藏。若「作者的話」還沒寫、但想先露出分頁，可把 `authorTab` 設成 `true`
10. 存檔後重新整理瀏覽器

標籤裡若寫了「穿書、快穿、校園、獸人、奇幻、都會、18禁」其中一個，這部就會出現在首頁對應的分類按鈕。想加新分類，在 `scripts.js` 上方的 `FILTERS` 加一個詞，並在該部的 `tags` 裡也寫上。

## 自己刪除一部劇本

打開 `scripts.js`，在 `WORKS` 裡找到那一部，把從 `{` 到 `}` 的整塊刪掉（若不是最後一筆，連同後面的逗號一起刪）。
封面圖若不再使用，可一併從 `assets/covers/` 刪除，但不刪圖也不會出錯。

## 自己新增一張角色卡

1. 若有直式肖像，把圖檔放到 `assets/portraits/`（只放檔案，例如 `my-portrait.jpg`）
2. 打開 `scripts.js`，複製「角色卡範本」那一整段，貼到 `CHARACTERS` 陣列裡
3. 一定要寫不重複的 `id`（詳情頁網址會用到，例如 `detail.html?type=char&id=kanzaki`）
4. 改名稱、副標、年齡、標籤、短介、長介
5. 有肖像就把 `portrait` 改成檔名；沒有肖像就留 `""`，網頁會顯示「肖像待補」
6. 可按需要填 `quote`（一句代表性的話）、`chatLink`（有網址才會出現「開始聊天」）、`opening`（開場白試閱）、`authorNote` 與 `screenshots`（作者的話）
7. 沒有內容的分頁會自動隱藏。若「作者的話」還沒寫、但想先露出分頁，可把 `authorTab` 設成 `true`
8. 存檔後重新整理瀏覽器

## 自己刪除一張角色卡

打開 `scripts.js`，在 `CHARACTERS` 裡找到那一張，把從 `{` 到 `}` 的整塊刪掉即可。
肖像圖若不再使用，可一併從 `assets/portraits/` 刪除，但不刪圖也不會出錯。

## 提問與 Discord

頁尾與「作者的話」分頁都放了 [Lunly 的 Discord 社群](https://discord.gg/wNgvn5wBC)。有問題可以到上面找作者，直接 @泡芙Yunnn。

## 發布到 GitHub Pages

1. 到 GitHub 免費註冊，開一個公開（Public）的專案，例如叫 `script-portfolio`
2. 把 `index.html`、`detail.html`、`scripts.js` 和 `assets` 資料夾上傳到專案（不必上傳預覽圖）
3. 到專案的 Settings → Pages，Source 選 Deploy from a branch，分支選 `main`，資料夾選 `/ (root)`
4. 做好之後網址會是 `https://你的帳號.github.io/script-portfolio/`
5. 單部劇本詳情頁會是 `https://你的帳號.github.io/script-portfolio/detail.html?id=劇本代號`；角色卡則是 `.../detail.html?type=char&id=角色代號`

若希望網址根目錄就能打開，也可把檔案放在帳號同名的 `你的帳號.github.io` 專案裡。

## 說明

封面與肖像只收已找到的正式或準正式圖檔；尚無圖片的卡片會顯示待補底圖。簡介依各劇本、角色卡最新版改寫，避免劇透後續發展。詳情頁「故事介紹」不放好感度解鎖表。
