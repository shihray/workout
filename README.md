# GYM DAILY － 健身訓練紀錄器

一個純前端、行動裝置優先的健身課表追蹤工具。可記錄每日訓練的組數、次數與重量（lb），統計訓練量與完課率，並可一鍵匯出 CSV。

## 功能特色

- 三大訓練日分頁：胸肩三頭、背肩二頭、腿日課表
- 即時統計：已完成動作數、總訓練量（lb）、完課率與進度條
- 內建休息計時器（含音效與震動提示）
- 追加自訂動作、重設今日進度
- 課表 JSON 編輯器，可直接修改預設組數 / 次數 / 重量
- 一鍵匯出當日訓練紀錄為 CSV
- 課表資料獨立為 [`workout-data.json`](workout-data.json)，方便直接編輯擴充

## 線上使用（GitHub Pages）

1. 將本專案推上 GitHub。
2. 進入 repository 的 **Settings → Pages**。
3. **Build and deployment → Source** 選 `Deploy from a branch`，分支選 `main`、資料夾選 `/ (root)`，儲存。
4. 稍候片刻，即可由 `https://<你的帳號>.github.io/<repo 名稱>/` 開啟。

## 本機開發

由於頁面會以 `fetch` 載入 `workout-data.json`，直接以 `file://` 雙擊開啟會被瀏覽器的 CORS 政策擋下。請改用本機伺服器：

```bash
cd 專案資料夾
python3 -m http.server 8000
```

接著瀏覽 <http://localhost:8000/>。

## 檔案結構

```
.
├── index.html         # 應用程式主體（HTML + CSS + JS）
├── workout-data.json  # 預設課表資料
└── README.md
```

## 自訂課表

直接編輯 [`workout-data.json`](workout-data.json)。每個動作欄位說明：

| 欄位       | 說明                                   |
| ---------- | -------------------------------------- |
| `id`       | 動作唯一識別碼                         |
| `name`     | 中文名稱                               |
| `eng`      | 英文名稱                               |
| `sets`     | 預設組數                               |
| `reps`     | 預設次數（或秒數）                     |
| `weightLb` | 預設重量（磅 lb）                      |
| `rest`     | 建議休息秒數                           |
| `unit`     | `reps`（次）或 `sec`（秒）             |

> 注意：頁面也支援在「編輯課表 JSON」中即時修改，修改後會儲存在瀏覽器 `localStorage`，優先於 `workout-data.json`。如需恢復檔案預設值，可在編輯器中點「恢復原廠預設值」。
