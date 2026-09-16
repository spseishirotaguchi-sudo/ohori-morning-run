# 大濠公園朝活ラン部 — コンセプトと運用メモ

## コンセプト
さあ歩を進めよう、1日はいつも朝から。事前決済と仲間との約束で、休日の最初の一歩を支える。

## 想定ターゲット
福岡市と周辺の20〜30代社会人。仕事以外の時間を充実させたいが、一人では朝の行動が続かない人。職場以外の友人や地域のつながりを求める人。年齢は訴求の想定であり、参加制限ではない。

## 提供価値
朝の予定を先に決める仕組み／運動する気持ちよさ／共通の活動を通じたつながり／10時以降の自由な休日。
習慣化やビジネスマッチングの成果は保証しない。自己嫌悪を煽らず、実行しやすい次の一歩に変える。

## 確認済み条件
名称は「大濠公園朝活ラン部」。代表は田口勢士郎。初回開催は2026年10月3日（土）。
以降は土曜または日曜、9:00〜10:00、大濠公園、1回500円、事前決済。
参加条件は18歳以上の社会人（学生不可）。当日の流れは集合→ストレッチ→大濠公園をランニング→10時解散。ペースは喋りながら走れる速さで全員を合わせる。前日までのキャンセルはキャンセル料0%で全額返金、当日キャンセルは100%。雨天・主催者都合の中止は全額返金し、判断が決まった時点で連絡。
申込みフォームは未作成。予約・決済・受付通知機能は未接続。CTAの文言は「お申し込みはこちら」だが、リンク先は暫定で開催情報セクション（#guide）。フォームURLが決まったら3箇所（ヘッダー・ファーストビュー・末尾）のhrefを差し替える。

## 開始前の未確定項目
集合地点／走る距離／キャンセル連絡の受付方法／連絡先／申込みと決済URL。
サイト上は「悪質な勧誘・執拗な営業・ナンパ目的の参加はお断り」と明記。正式な運用ルールとして確認すること。

## デザイン
参考1: https://utage-system.com/p/5GpLJGWhahRT
参考2: https://spseishirotaguchi-sudo.github.io/pbq-lp/
全面写真と明朝体の静けさを残し、PBQの白・チャコール・赤を控えめな朱色に調整。反復カードや過度な装飾を避け、文字の階層と罫線で整理。

## 写真
組み込み画像生成で作成。dist/morning.jpg は活動イメージで、実際の大濠公園や参加者を撮影した写真ではない。ページ内に明記。
素材はこの1枚だけで、ファーストビューと本文中の帯2箇所（.band-a / .band-b）で、object-position を変えて別カットのように見せている。実写が用意できたら帯の2枚を差し替えること。
生成プロンプト: Premium Japanese lifestyle magazine photograph, landscape 3:2. Early morning Japanese urban lakeside park evocative of Fukuoka Ohori, calm wide lake on left, mature green trees, distant low buildings, jogging path on right. Three Japanese adult recreational runners late twenties to thirties, seen from behind on lower right, charcoal/off-white/olive sportswear, natural candid movement, documentary 35mm, subtle film grain, gentle sunshine, deep forest shadows, restrained highlights. Uncluttered darker left for white headline. No text, logos, collage or invented landmark.

## 設計の参考
https://research.google/pubs/the-role-of-visual-complexity-and-prototypicality-regarding-first-impression-of-websites-working-towards-understanding-aesthetic-judgments/
https://pmc.ncbi.nlm.nih.gov/articles/PMC3482144/
研究の美的評価・知覚群化を設計の参考とした。申込み率への効果を証明するものではない。

## 検証
実ブラウザで本文・主要CTAの#guide移動・FAQ開閉・画像読込みを確認。390pxと320pxで横はみ出しなし。キーボードフォーカスをCSSで可視化し、縮小モーションに対応。申込み完了の検証は受付接続後に実施する。

## 改行の設計
日本語は既定だと文字と文字のあいだで改行されるため、単語の途中で割れる。
それを避けるために、文節ごとに <span class="ph">（display:inline-block）で包み、その境目に <wbr> を置いて、そこだけで改行させている。
文節が1行に入らないときは、その中で通常どおり折り返すので、はみ出すことはない。
word-break:keep-all は使わない。折り返し先を失って文字が画面外へはみ出すブラウザ（iOS Safari）があるため。
iOS の文字自動拡大を止める text-size-adjust:100% と、横スクロールを防ぐ overflow-x:hidden も入れている。
数字と単位（1回 500円、当日 100% など）は .nw で分断を禁止。
見出しと主要な文字サイズは clamp() で画面幅に追従させ、スマホでもPCの拡大時でも1行の文字数が大きく変わらないようにしている。
本文を書き換えるときは、長い文節（おおむね全角19文字以上）に <wbr> を入れ直すこと。
