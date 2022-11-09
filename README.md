<h1 align="center">OAM Landing Page</h1>

<div align="center">
  <h3>
  <a href="https://docs.openaerialmap.org/ecosystem/getting-started">Ecosystem</a>
  <span> | </span>
  <a href="https://github.com/hotosm/oam-catalog">Catalog API</a>
  <span> | </span>
  <a href="https://github.com/hotosm/oam-browser">Imagery Browser</a>
  </h3>
</div>

這是 openaerialmap.org 的登錄頁面，從 [OAM Catalog API](https://github.com/hotosm/oam-catalog). 接收統計信息。

## Installation and Usage

以下步驟將引導您設置自己的 openaerialmap.org 實例。

### Install Project Dependencies
要設置此網站的開發環境，您需要在系統上安裝以下內容：

- [Node](http://nodejs.org/) v4 (To manage multiple node versions we recommend [nvm](https://github.com/creationix/nvm))

### Install Application Dependencies

如果你要使用 [`nvm`](https://github.com/creationix/nvm), 需啟動 Node 版本:

```
nvm install
```

安裝 Node 模組:

```
npm install
```

### Usage

#### Config files
所有配置文件都可以在 `app/assets/scripts/config` 中找到。安裝項目後，將有 3 個主要文件：
  - `local.js` - 僅用本機開發。在生產時，此文件不應存在或為空。
  - `staging.js`
  - `production.js`

The `production.js` file serves as base and the other 2 will override it as needed:
`production.js` 文件用作基礎文件，其他 2 個文件將根據需要操控(?)它：
  - `staging.js` 將會被加載只要環境變量 DS_ENV 設置為 staging。
  - `local.js` 將會被加載，如果它存在。

必須設置以下選項：（使用的文件將取決於上下文）
  - `OAMCatalogAPI` - The url of [OAM Catalog](https://github.com/hotosm/oam-catalog).
  - `OAMBrowserUrl` - The url of [OAM Browser](https://github.com/hotosm/oam-browser).

Example:
``` 
module.exports = {
  OAMBrowserUrl: 'https://beta.openaerialmap.org',
  OAMCatalogApi: 'https://api.openaerialmap.org'
};
```

#### Starting the app

```
npm run serve
```

編譯 sass 文件、javascript 並啟動，使設置在 `http://localhost:3000/` 可用。系統將監視文件並在其中一個更改時執行。該設置將自動刷新，因為它與 livereload 綁在一起。

# Deployment
準備此程式，以有效運行:
```
npm run build
```

將打包應用程序並將所有內容放在 `dist` 目錄中。然後，該應用程序可以在任何網頁伺服器上使用。

## License
Openaerialmap 在 **BSD 3-Clause License** 下獲得許可，有關更多詳細信息，請參閱 [LICENSE](LICENSE) 文件。
