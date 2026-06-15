# VTuberモデル かんたん診断 | Crom Works

VTuberの **Live2Dモデル制作を依頼したい初心者向け** の無料診断ツールです。
質問に答えていくと、

- どんなモデル構成が向いているか(そもそもLive2Dが必要かも判定)
- 必要なイラスト・素材
- 活動するうえで便利なイラスト・素材
- 依頼するときにあると便利な情報
- **あなたに合うCrom Worksのおすすめプランと概算の目安**
- **そのままGoogleフォームに貼れる依頼文**

がわかり、ボタンひとつで **Crom Worksの依頼フォーム／公式サイト** へ移動できます。
`index.html` の1ファイルだけで動きます。

---

## 公開について

GitHub Pages で公開されます(Settings → Pages → Branch: main / root)。
公開URL例: `https://seracrom.github.io/VTuber-/`

公式サイト([Crom-works](https://seracrom.github.io/Crom-works/))のメニューやSNSから、このURLにリンクを貼って誘導できます。

---

## 設定(最初に確認するところ)

`index.html` の `<script>` 先頭、**ここだけ**でURL等を管理しています。

```js
const FORM_URL = "https://docs.google.com/forms/d/e/.../viewform"; // 依頼フォーム
const HP_URL   = "https://seracrom.github.io/Crom-works/";          // 公式サイト
const GROUP_NAME = "Crom Works";
```

- `FORM_URL` … 「相談する／依頼フォームを開く」ボタンの飛び先。空にすると「準備中」表示になります。
- `HP_URL` … ヘッダー・フッター・結果画面の「Crom Works公式サイト」リンク先。

## 料金・見積もりを変更したいとき

概算は **`buildEstimate()` 関数**(`index.html` 内)で、Crom Worksの料金表をもとに計算しています。
料金改定時は、この関数内の数字を書き換えるだけです。

| 項目 | 変数 | 現在の値 |
|---|---|---|
| Live2D用イラスト(パーツ分け) | `base` | 130,000 |
| Vtuberお試しセット | `base` | 150,000 |
| 基本Live2Dモデリング | `base` | 160,000 |
| Live2Dモデリング＋ | `base` | 220,000 |
| 基本セット | `base` | 275,000 |
| フルセット | `base` | 345,000 |
| 表情差分 / 揺れ物 等(オプション) | `price` | 5,000〜 |
| 一部アニメ(手を振る等) | `price` | 10,000 |
| 全身アニメ(歩き等) | `price` | 20,000 |
| 衣装差分(別途イラスト) | `price` | 80,000 |

> ※ 表示はすべて「〜(から)」「税込」。実際の金額はデザインの複雑さで変動する旨を画面にも明記しています。

## その他のカスタマイズ

| 変えたいもの | 場所 |
|---|---|
| 色・見た目 | `<style>` 内の `:root{ ... }` の変数 |
| 質問の追加・編集 | `QUESTIONS` 配列 |
| 分岐(前の回答で出し分け) | 各質問の `when: s => ...` |
| 結果(必要素材・便利素材・依頼情報・注意点) | `buildResult()` 関数 |
| おすすめプラン・概算ロジック | `buildEstimate()` 関数 |
| 依頼文テンプレート | `buildResult()` 内の `req` 文字列 |

---

## 注意

診断結果・金額はあくまで目安です。最終的な料金・納期・著作権などは、お見積もり・公式サイトでご確認ください。
