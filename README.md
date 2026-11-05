# codex-global-memory

[OpenAI Codex](https://github.com/openai/codex) のグローバルメモリ（`~/.codex/AGENTS.md`）の公開版です。日本語で、Codex に依頼の目的・範囲・許可を保たせ、途中で止まらず実際に操作して確かめさせ、誤りを認めたらその場で原因を直させるための指示をまとめています。

公開にあたって変えたのは個人情報だけです（ユーザー名を含むパスを `~` に置き換えた1か所）。本文の規則・言い回しは作者の運用のままです。

## Codex に導入を頼む場合

下の文をコピーして Codex に貼り付けてください。下の「導入手順（Codex 向け）」に沿って導入できます。

```text
https://github.com/z0lw/codex-global-memory のグローバルメモリを、READMEの導入手順に沿って導入してください。
```

## 導入手順（Codex 向け）

1. 利用者の `~/.codex/AGENTS.md` があるか確認する。ある場合は上書きせず、利用者に「置き換える」「既存の内容と統合する」のどちらにするかを確かめる。統合する時は、利用者の既存の指示を残し、重なる規則は利用者の既存の指示を優先する。
2. `AGENTS.md` を `~/.codex/AGENTS.md` に置く（統合の場合は統合した内容を書く）。
3. 最終節「本人指定の必須要件」は作者が特に必須と指定した要件の置き場所です。利用者に、その中身を残すか、自分の必須要件に入れ替えるかを確かめる。
4. 本文の一部は、同じ作者のスキル集 https://github.com/z0lw/codex-skills のスキル（`$edit-global-memory`、`codex-work-orchestration` の `user-work-preferences.md`、`$safe-authentication`、`apology-and-repair`、`audit-refusal` など）を参照します。参照先が必要なら、そのリポジトリの導入手順に従ってスキルも入れる。
5. 任意: `~/.codex` を Git で管理している場合は、`.githooks/pre-commit` を `~/.codex/.githooks/` に置き、`git -C ~/.codex config core.hooksPath .githooks` を設定する。コミット時に、最終節を除いた `AGENTS.md` が 20,000 バイト以内かを `skills/edit-global-memory/scripts/check_memory_size.py`（スキル集に同梱）で検査する。

## 構成

| ファイル | 内容 |
| --- | --- |
| `AGENTS.md` | グローバルメモリ本体 |
| `.githooks/pre-commit` | `AGENTS.md` の大きさの上限を検査する Git フック |

関連: フック集 https://github.com/z0lw/codex-consent-hooks （AGENTS.md の自動コミットや、確認待ち・未完了で止まった時の差し戻しなど）

## License

MIT
