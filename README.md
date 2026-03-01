# 3Dマップビューア

国土交通省 PLATEAU 3D都市モデルおよびGoogle Earthデータ（KML/KMZ）に対応した、静的HTMLのみで動作する3Dマップ表示Webアプリケーションです。

## 使い方

`index.html` をブラウザで直接開くだけで動作します。サーバー不要です。

### 主な機能

| 機能 | 説明 |
|------|------|
| **PLATEAU 3D都市モデル** | 国土交通省 PLATEAU の3D建築物モデル（3D Tiles）を表示 |
| **PLATEAU 航空写真** | PLATEAU Ortho 2023 航空写真オーバーレイ |
| **3D地形表示** | 世界中の地形を3Dで表示（CesiumJS + Cesium World Terrain） |
| **3D建物表示** | OpenStreetMap Buildingsによる建物の3D表示 |
| **場所検索** | 地名・住所で場所を検索してフライ移動 |
| **プリセットエリア** | 日本の主要ランドマーク（東京タワー、富士山、大阪城など）にワンクリック移動 |
| **ファイルインポート** | KML / KMZ / GeoJSON / CZML ファイルの読み込み・表示 |
| **カスタム3D Tiles** | 任意の3D Tiles（tileset.json）URLを読み込み・表示 |
| **表示設定** | 地形誇張、建物表示、影、大気効果、霧の切替 |
| **時刻設定** | 太陽の位置（時刻）を変更して光の当たり方を調整 |
| **スクリーンショット** | 現在の3Dビューを画像として保存 |

### Google Earthデータのインポート

1. Google Earthで「場所」を右クリック → 「名前を付けて場所を保存」でKML/KMZファイルをエクスポート
2. このアプリのサイドパネル「ファイルインポート」エリアにドラッグ＆ドロップ
3. データが3Dマップ上に表示されます

### Cesium Ionトークン

アプリに含まれているトークンはデモ用です。本格的に利用する場合は、以下の手順で自分のトークンを取得してください：

1. [Cesium Ion](https://ion.cesium.com/signup/) で無料アカウントを作成
2. Access Tokenを取得
3. `index.html` 内の `Cesium.Ion.defaultAccessToken` の値を置き換え

### PLATEAU 3D都市モデル

サイドパネルの「PLATEAU 3D都市モデル」セクションから、プリセットされた都市の3D建築物モデルをワンクリックで読み込めます。

カスタムURL欄に任意の `tileset.json` URLを入力することで、[PLATEAU配信サービス](https://github.com/Project-PLATEAU/plateau-streaming-tutorial)の他の都市データも表示できます。

## 技術スタック

- **CesiumJS** - 3Dグローブ・地図ライブラリ（CDN読み込み）
- **PLATEAU 3D Tiles** - 国土交通省 3D都市モデル（建築物・LOD1/LOD2）
- **PLATEAU Ortho** - 航空写真タイル
- **Cesium World Terrain** - 高精細3D地形データ
- **OSM Buildings** - OpenStreetMapベースの3D建物データ
- **Nominatim API** - OpenStreetMapの地名検索API

全て静的HTML + CSS + JavaScriptのみで構成されており、ビルドツールやサーバーサイド処理は不要です。
