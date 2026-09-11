# 峴港員旅行程｜2026/9/14–9/17

單頁式旅遊行程表，為 2026 年 9 月 14 日至 17 日的峴港（Đà Nẵng）員工旅遊所製作。整份行程是一個不需安裝、不需登入的網頁，用手機打開就能看到每天的時間表，每個地點都附 Google Maps 連結，點下去直接導航。

**線上版本：** https://wa-hsiang.github.io/DaNangSchedule/

## 行程概覽

住宿全程為 Peninsula Hotel Danang（84 Võ Nguyên Giáp, Đà Nẵng）。

| 日期 | 主題 | 關鍵時間 |
| --- | --- | --- |
| 9/14（一） | 抵達峴港 → Spa → PPA 部門聚餐 | 07:00 桃園 T2 集合、18:00 Mộc Quán Seafood 聚餐 |
| 9/15（二） | 會安古城一日遊 → 咖啡 → Spa | 09:00 出發前往會安、18:30 返回峴港 |
| 9/16（三） | 漢市場 → Pizza 4P's → Spa → 公司晚宴 | 13:00 午餐訂位、17:50 Brilliant Seafood 全公司晚宴 |
| 9/17（四） | Vincom → 市中心景點 → Spa → Bếp Cuốn | 16:00 按摩、晚間 Bếp Cuốn |

餐廳與 Spa 有數處列出兩間備選，最終分店與時間以實際訂位為準。

## 內容結構

`index.html` 是整個專案的全部：HTML、CSS 與所有行程資料都在這一個檔案裡，沒有外部相依、沒有 JavaScript、沒有框架。

頁面由上而下分為四個區塊。最上方的 hero 顯示行程名稱、日期與住宿；接著是四張日期摘要卡，一眼看完四天各做什麼；主體是四個 `<section class="day">`，每天一塊，包含當日主題、一個串連當天所有地點的 Google Maps 路線按鈕，以及一條「時間 ／ 事件」兩欄的時間軸；部分日期的時間軸下方有黃色的小提醒框，標註需要留意的訂位時間或待確認事項。

排版在 850px 與 520px 兩個斷點做了調整，主要使用情境是手機。

## 修改方式

編輯 `index.html`，commit 後 push 到 `main`，GitHub Pages 會自動重新部署，通常一分鐘內生效。沒有建置步驟、沒有相依套件需要安裝。

要在本機預覽，直接用瀏覽器開啟 `index.html` 即可，不需要起伺服器。

新增一個行程項目，就是在對應日期的 `.timeline` 裡加一個 `.row`：

```html
<div class="row">
  <div class="time">15:00</div>
  <div class="event">
    <b>地點名稱</b>
    <div class="meta">地址或補充說明</div>
    <a class="link" target="_blank" href="https://www.google.com/maps/search/?api=1&query=地點+英文名">📍 地點</a>
  </div>
</div>
```

地點連結統一使用 Google Maps 的 [Search URL](https://developers.google.com/maps/documentation/urls/get-started#search-action) 格式，`query` 帶英文店名加地址；每日路線按鈕使用 [Directions URL](https://developers.google.com/maps/documentation/urls/get-started#directions-action) 格式，以 `waypoints` 用 `|`（需編碼為 `%7C`）串接當天各站。越南地名的變音符號在 `query` 裡可能導致比對失敗，因此連結一律使用無變音的英文拼寫，顯示文字才用中文或越南文原名。

## 注意事項

頁面上的營業資訊、地址與價格未經即時查證，出發前建議再確認一次店家是否營業。網址已分享給同團成員，修改內容時請留意他們手機上可能仍是舊的快取版本。
