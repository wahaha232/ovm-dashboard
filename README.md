# OpenVerusMiner 網頁版儀表板

`index.html` 是一個靜態網頁，放在 GitHub Pages 上。它會讀取各電腦定時寫入的 GitHub Gist，
在任何瀏覽器（手機、公司電腦）顯示所有電腦的挖礦狀態。網頁本身不含任何 Token 或錢包地址。

## 一、建立 GitHub Token（每台電腦可共用同一組）

建議用傳統 Token（classic），只需要勾一個權限：

1. 打開 <https://github.com/settings/tokens/new>（Settings → Developer settings → Personal access tokens → **Tokens (classic)** → **Generate new token (classic)**）
2. Note：`OpenVerusMiner`；Expiration：90 天或 1 年
3. **Select scopes** 只勾 **gist**，其他都不要勾
4. **Generate token**，複製 `ghp_` 開頭的 Token（只會顯示一次）

也可用 Fine-grained token：權限在 **User permissions**（舊畫面叫 Account permissions）→ **Gists → Read and write**；新畫面看不到時先按 **Add permissions** 再搜尋 Gists。

## 二、在第一台電腦建立 Gist

管理工具 → 設定 → 自動化與通知 → **GitHub 回報**：

1. 貼上 Token → 按 **建立 Gist**（會建立一個私密 Gist，並自動填入 Gist ID）
2. 選回報間隔（預設每 10 分鐘，對齊時鐘）→ 勾選 **啟用 GitHub 回報** → **儲存**

## 三、其他電腦

同一個畫面貼上同一組 Token、填同一個 Gist ID → 勾選啟用 → 儲存。

## 四、放上 GitHub Pages

1. 在 GitHub 建立一個儲存庫（例如 `ovm-dashboard`），把 `index.html` 上傳到根目錄
2. 儲存庫 → **Settings → Pages** → Source 選 *Deploy from a branch*，Branch 選 `main` / `(root)` → Save
3. 約 1 分鐘後網址為 `https://<帳號>.github.io/ovm-dashboard/`
4. 打開 `https://<帳號>.github.io/ovm-dashboard/?gist=<Gist ID>`（瀏覽器會記住 Gist ID）
5. 把網頁版網址填回管理工具的「網頁版網址」，之後可按「開啟網頁版」

## 注意

- 私密 Gist 不會被搜尋到，但**知道 Gist ID 的人就能看到內容**（算力、份額、錢包層級收益；不含錢包地址）。請勿公開 Gist ID。
- 未登入的瀏覽器讀取 GitHub API 每小時限 60 次，網頁每 5 分鐘自動更新一次。
- 網頁是唯讀的，不能遠端操作挖礦。
- 收益換算僅供參考，不構成財務建議。
