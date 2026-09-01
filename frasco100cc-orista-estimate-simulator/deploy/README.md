# オリスタ見積りシミュレーター

オリジナルウェア（Tシャツ・パーカー等）のプリント加工・アパレル製作における見積り試算および粗利シミュレーションを行う、単一HTMLファイルのWebアプリケーションです。ビルド不要の静的サイトなので、そのままVercelにデプロイできます。

- 本体: `index.html`（HTML / CSS / JavaScriptすべてインライン、外部ライブラリ依存なし。フォントのみGoogle Fontsを読み込みます）
- 仕様書: 別途お渡ししている `spec_v1.2.md` を参照してください（このリポジトリには含めていません）

## ローカルで確認する

ビルドや依存パッケージのインストールは不要です。`index.html` をブラウザで直接開くか、簡易サーバーで確認できます。

```bash
# 方法1: ファイルを直接開く
open index.html   # Macの場合。Windowsはダブルクリックでも可

# 方法2: 簡易サーバーで確認する場合
npx serve .
```

## GitHubにアップロードする

このフォルダの中身（`index.html` / `vercel.json` / `.gitignore` / `README.md`）をそのまま新しいリポジトリにしてください。

1. GitHub上で新しいリポジトリを作成する（例: `orista-estimate-simulator`）。READMEなどは追加せず「空のリポジトリ」として作成するのがおすすめです。
2. ダウンロードしたこのフォルダで、ターミナルから以下を実行します（`<username>`と`<repo-name>`はご自身のものに置き換えてください）。

```bash
cd このフォルダのパス
git init
git add .
git commit -m "Initial commit: オリスタ見積りシミュレーター"
git branch -M main
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

## Vercelにデプロイする

1. [vercel.com](https://vercel.com) にログイン（GitHubアカウントでログイン可能）。
2. 「Add New...」→「Project」を選択。
3. 先ほどpushしたGitHubリポジトリを選び「Import」。
4. Framework Presetは自動で **Other**（または `Static`）が選ばれます。Build CommandやOutput Directoryは空欄のままで問題ありません（ビルド不要の静的サイトのため）。
5. 「Deploy」をクリックすれば数十秒で公開されます。

以降は、`main`ブランチにpushするたびにVercelが自動で再デプロイします。修正版のコードをもらったら、この`index.html`を置き換えて同じ手順で`git add` → `commit` → `push`するだけで反映されます。

```bash
git add index.html
git commit -m "Update: 見積りロジック/UI修正"
git push
```

## メモ

- `vercel.json` はURLの末尾スラッシュ挙動を整えるための最小設定です。特にカスタマイズが必要なければそのままで問題ありません。
- 独自ドメインを使いたい場合は、Vercelのプロジェクト設定 → Domains から追加できます。
