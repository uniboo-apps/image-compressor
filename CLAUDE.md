# image-compressor（画像圧縮ツール）

ブラウザ完結の画像圧縮ツール。4.8MB 超の画像を Canvas API で自動圧縮し JPEG 出力。iPhone の HEIC/HEIF にも対応。

## 構成・技術
- **`index.html` 1枚で完結**（静的）。サーバーに画像を送らずブラウザ内で処理。
- 対応入力: JPEG / PNG / WebP / HEIC・HEIF（iPhone）。
- 圧縮: Canvas で再エンコード、4.8MB 以下に収まるよう品質を調整。
- HEIC 変換: `heic2any@0.0.4`（jsDelivr CDN・バージョン固定）。

## デプロイ
- `main` に push → GitHub Actions で Cloudflare Pages へ自動デプロイ。
- 旧 URL（廃止）: `super-cat-6ab3f4.netlify.app`（Netlify Drop）。
- リポジトリは **public**（`uniboo-apps` の組織シークレット `CLOUDFLARE_API_TOKEN` を使用）。
- push 時に `notion-commit.yml` が NotionのコミットDBへコミットを記録（AI DB「画像圧縮ツール」行に紐づけ）。

## ルール
- **public なので秘密をコードに置かない**（画像はすべてブラウザ内処理・送信なし）。
- CDN を増やす場合はバージョン固定＋SRI を付ける（プロジェクト全体ルール）。
