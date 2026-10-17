---
title: "レッスン 10 - 振り返りと次のステップ"
description: "Copilot CLI のワークフロー、2 つのプルリクエスト、再利用可能なカスタマイズ、その他のリソースを振り返ります。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

Tailspin Toys の一連のワークフローで GitHub Copilot CLI を使いました。次の作業を行いました。

- Codespace を準備し、Copilot CLI をインストールしてプロジェクトを確認し、あらかじめ用意されたフィルタリングのイシューを見つけました。
- 星評価を追加し、ポート転送されたブラウザーで結果を確認して、最初のプルリクエスト (PR) を手動でマージしました。
- フィルタリングのイシューから始め、Plan モードで方針を決め、Autopilot モードで実装し、Interactive モードでレビューしました。
- カスタム指示でエージェントを導き、既存の `quality-checks` スキルをカスタマイズして、ユニットテスト、lint、型チェックに利用しました。
- Playwright Model Context Protocol (MCP) サーバーを追加し、実際のブラウザーでフィルタリングを確認しました。
- QA カスタム エージェントを作成して選択し、要件、テスト カバレッジ、スキルの結果、ブラウザーでの確認内容を評価しました。
- フィルタリングに関する変更全体をレビューし、その PR に Agent Merge を許可しました。
- コンテキスト、モデル、共有、任意のクラウドへの委任に関するスラッシュコマンドを確認しました。

## 実装した内容

このワークショップには 2 つの PR の節目があり、それぞれ更新された `main` から作成した別のブランチで作業します。

1. **星評価:** 既存の `starRating` と、評価がない場合に明示する状態をゲームカードに表示します。
2. **フィルタリングと品質ワークフロー:** フィルタリングを実装し、指示を更新して機能に適用します。`quality-checks` のレポートをカスタマイズし、QA プロファイルと関連テストを追加します。

フィルタリングの計画から PR の作成まで、同じ会話とブランチを使いました。ワークショップを簡潔にするため、この作業は 1 つの PR にまとめました。

## さまざまな検証方法

自動テスト、自分でのブラウザー確認、MCP を使った Copilot のブラウザー操作など、複数の方法でコードを確認しました。`quality-checks` スキルはユニットテスト、lint、型チェックを実行し、新しい形式で結果を報告しました。QA は PR の前に、これらの結果と要件およびテスト カバレッジのレビューをまとめました。

追加するテストは実際の不足を補うものである必要があります。QA の実行で新しいテストが不要という結果になることもあります。マージを許可する前にコードと証拠を確認し、変更後は影響を受ける証拠を更新してください。

## ベスト プラクティス

Copilot に提供するコンテキストとツールによって、その作業内容が変わります。このワークショップでは、指示を更新し、スキルをカスタマイズし、QA プロファイルを作成し、MCP サーバーを設定しました。こうしたカスタマイズは別の会話でも再利用し、チームのニーズに合わせて調整してください。指示は標準を定め、スキルは繰り返し行うタスクを示し、カスタム エージェントは専門的な役割を定義し、MCP サーバーは外部ツールに接続します。エージェントの要約だけでなく、実際の変更とツールの結果を確認してください。

タスクに合わせて**モードとモデル**を選びます。実装前の検討には **Plan**、範囲の限られた変更を進めながら確認するには **Interactive**、明確に範囲を定めたタスクには **Autopilot** を使います。定型的な編集には高速なモデルを、複雑な作業には高性能なモデルを選びます。

インフラストラクチャと同様に、コンテキストも重要です。*何を*、*なぜ*、*どのように*作るのかを明確に伝えることで、出力は大きく変わります。

## さらに試す

中心的なワークフローは完了しました。Copilot CLI には、ほかにも便利な機能があります。

- `/review` でコードレビュー エージェントに変更を分析してもらいます。
- `/rubber-duck` で問題を整理し、別の視点を得ます。
- `/fleet` で独立したサブタスクを並行して調整します。
- `/worktree` で別のタスクを分離します。
- `/delegate` で GitHub Copilot クラウド エージェントにタスクを送ります。

## 次のステップ

ツールの使い方を身につけるには、使い続けるのが一番です。プロダクション コード、個人のプロジェクト、何年も作りたいと思っていた小さなアプリで活用してください。学んだことをチームで共有し、チームからも学びましょう。そして、いつものようにドキュメントを確認してください。

ターミナルから Tailspin Toys を拡張する場合は、任意の [Foundry Backer Concierge シリーズ][foundry]に進みます。ほかの環境と比較するには、[VS Code ワークショップ][vscode]、[GitHub Copilot アプリのワークショップ][app]、または[GitHub Copilot クラウド エージェントのワークショップ][cloud]を確認してください。

## リソース

- [GitHub Copilot CLI について][about-cli]
- [Copilot CLI コマンド リファレンス][cli-reference]
- [Copilot CLI のカスタマイズ][customize-cli]
- [Copilot CLI でプルリクエストを管理する][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
