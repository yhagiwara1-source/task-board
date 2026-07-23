# CLAUDE.md

このファイルは、このリポジトリで Claude Code (claude.ai/code) が作業する際のガイドです。

## プロジェクト概要

task-board: タスク管理ボードアプリケーション（初期構築段階）。

## デプロイ先

https://yhagiwara1-source.github.io/task-board/

`main` ブランチへの push をトリガーに、GitHub Actions（[.github/workflows/deploy.yml](.github/workflows/deploy.yml)）が自動でビルド・デプロイする。

## 技術スタック

- React 18
- Vite 5（ビルドツール、`base: "/task-board/"` を GitHub Pages 配信用に設定済み）
- プレーンな CSS（コンポーネントごとに `.css` ファイルを対応させる。CSS-in-JS やUIライブラリは未導入）
- 状態管理は React の `useState` / `useEffect` のみ（外部の状態管理ライブラリは未導入）
- 永続化は `localStorage`（バックエンド・DBは未導入）
- デプロイは GitHub Actions → GitHub Pages（[.github/workflows/deploy.yml](.github/workflows/deploy.yml)）

## コンポーネントの命名規約

- コンポーネントファイルは `PascalCase.jsx`（例: `App.jsx`）。ファイル名とコンポーネント関数名を一致させる。
- コンポーネント専用のスタイルは同名の `PascalCase.css`（例: `App.css`）として同じディレクトリに置き、コンポーネント内で `import "./ComponentName.css"` する。
- コンポーネント内の関数（イベントハンドラ等）は `camelCase`（例: `addTask`, `toggleTask`, `deleteTask`）。
- 定数は `UPPER_SNAKE_CASE`（例: `STORAGE_KEY`）。

## Git 運用ルール

- **コードに変更を加えたら、その都度 GitHub にプッシュすること。** 変更をローカルに留めず、都度コミット・プッシュしてリモート（origin）に反映する。
- リモートリポジトリ: `https://github.com/yhagiwara1-source/task-board.git`
- コミットメッセージは変更内容が分かるように簡潔に書く。
- 作業の切れ目（機能単位・修正単位）ごとにコミットを分け、1コミットに無関係な変更を混在させない。
