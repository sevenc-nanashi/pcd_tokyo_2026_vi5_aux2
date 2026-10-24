---
theme: default
title: p5.jsを映像制作ソフトに埋め込むといいとこ取りができるのでは？
info: |
  Processing Community Day Tokyo 2026の登壇資料です。
class: text-center
drawings:
  persist: false
transition: slide-left
comark: true
routerMode: hash
fonts:
  sans: "M PLUS 1p"
  weights: 400,700
---

<div>

# <span class="text-[#ed225d]">p5.js</span><span class="text-4xl">を</span>映像制作ソフト<span class="text-4xl">に<br>埋め込むと</span>いいとこ取り<span class="text-4xl">が<br>できるのでは？</span>

<!-- Can we embed <span class="text-[#ed225d]">p5.js</span> into video editing software,   -->
<!-- and get the best of both worlds? -->
<!---->
</div>

名無し。（@sevenc_nanashi / sevenc7c.com）

---

# 自己紹介

<v-clicks depth="2">

- 名義：「名無し。」「Nanashi.」
  - 句点/ピリオドを忘れずに！
- 何をやっているか：
  - アプリケーション開発（VOICEVOXなど）
  - 作曲（ボカロP）
  - お絵描き
  - など
- https://sevenc7c.com

</v-clicks>

<img src="./assets/general.apng" un-absolute un-right="0" un-h="60" un-top="1/2" un-translate-y="-1/2" un-pointer-events-none />

---

# p5.js / Processingを使う理由

<div class="grid-cols-3 grid gap-4">
<div class="border border-red-300 bg-red-50 rounded p-4" v-click>
インタラクティブ性を
追加できる

<p class="text-sm text-gray-500 mt-2">
VJ、ゲーム、展示品など...
</p>
</div>
<div class="border border-yellow-300 bg-yellow-50 rounded p-4" v-click>
大量の要素を動かせる

<p class="text-sm text-gray-500 mt-2">
パーティクル、フラクタル的な表現など...
</p>
</div>
<div class="border border-green-300 bg-green-50 rounded p-4" v-click>
データからビジュアルを作れる

<p class="text-sm text-gray-500 mt-2">
ビジュアライザーなど...
</p>
</div>
</div>
---

# 例：インタラクティブ性

<img src="./assets/interactive_example.png" un-w="auto" un-h="[calc(100%_-_3.5rem)]" un-mx-auto />

<p un-text="xs center" un-mt="0!">https://twitter.com/PCD_Tokyo/status/2112844060100858326</p>

---

# 例：大量の要素を動かす

<iframe src="https://haukun.github.io/p5js-baton-fireworks/viewer-fireworks/" un-w="auto" un-h="[calc(100%_-_3.5rem)]" un-mx-auto></iframe>
<p un-text="xs center" un-mt="0!">p5.js 花火大会 / https://haukun.github.io/p5js-baton-fireworks/viewer-fireworks/</p>

---

# 例：データからビジュアルを作る

<Youtube id="8T6zb3059P4" un-w="2/3" un-h="2/3" un-mx-auto />
<div class="text-sm text-center mt-2">
過置換 / 音楽：d.j.ァネイロ / 映像：melonade

文字はp5.jsによる描画、背景はGLSLシェーダーによる描画

</div>

---

# 手作業は大変

<img src="./assets/manual_visualizer.png" un-w="1/2" un-mx-auto />

<div class="text-sm text-center mt-2">
. / 音楽、映像：xxxx

音楽を変えたら画像を作り直す必要がある <br>
もしかしたら作り直すのを忘れてしまうかも + タイミングがずれるかも...

</div>

---

# 全編p5.jsはしんどい

<v-clicks depth="2">

- 先にあげたような表現は簡単ではある
- それ以外の要素を入れようとすると面倒
  - 文字MV、イラストのアニメーション、などなど...
- 実質的に動画編集ソフトを再発明することになる
  - エコシステムも作らないといけない...
- ブラウザで律速される
  - 重いエフェクト、例えばピクセルソート、モーションブラーなど...
- **既存の動画編集ソフトを使えたほうがいい**
  - WYSIWYGで編集できる

</v-clicks>

---

<div un-grid un-items-center un-h-full un-text-center>

# p5.jsのスケッチをを映像制作ソフトに<br>読み込みたい！

</div>

---

# 既存の方法

- [p5.jsのスケッチを動画化する方法](https://note.com/outburst/n/n16c9a937d2ea?sub_rt=share_pb) by おかず / Okazz
  - pupetterでブラウザを操作して動画化する方法
- [p5.capture](https://github.com/tapioca24/p5.capture) by tapioca24
  - p5.jsのcanvasを動画や連番画像のZIPとして出力するライブラリ
- [p5-frame-capturer](https://github.com/sevenc-nanashi/p5-frame-capturer)（拙作）
  - File System APIでダイレクトにフォルダ内に連番画像を書き出すライブラリ

<div v-click un-text="center [#48b0d5] 2xl" un-mt="8">

<div un-text="2xl">
「スケッチを素材として読み込む」でしかない！
</div>

<div un-text="xl" un-mt="2">
例えばパラメーターを動画編集ソフトから渡すとかはできない
</div>

</div>

---

<div un-grid un-items-center un-h-full un-text-center>

# p5.jsを映像制作ソフトの<br>オブジェクトとして使いたい！

</div>

---

<div un-grid un-items-center un-h-full un-text-center>

# 作った！！（開発中）

</div>

---

# vi5.aux2

<v-clicks depth="2">

- AviUtl2プラグイン
- p5.jsのスケッチをオブジェクトとして読み込める
- パラメーターを動画編集ソフトから渡せる
- Powered by Vite
  - TypeScriptはもちろん、既存のプラグインも使える
    - @rollup/plugin-yamlなど

</v-clicks>

<div un-h="4" />

<v-clicks depth="2">

- 他のオブジェクトと同じ感覚でp5.jsのスケッチを扱える！
- ネイティブバイナリで動作するのでスケッチ以外は律速されない！

</v-clicks>

---

# 動作デモ

<div un-h="[calc(100%_-_3.5rem)]">
<video src="./assets/vi5_demo.mp4" controls un-w="auto" un-h="full" un-z="20" un-mx-auto></video>
</div>

---

# 作品例

<div un-h="[calc(100%_-_3.5rem)]">
<video src="./assets/himawari.mp4" controls un-w="auto" un-h="full" un-z="20" un-mx-auto></video>
</div>

<p un-text="xs center" un-mt="0!">ひまわりれしーば / 音楽・映像・イラスト：Nanashi. / ボーカル：春日部つむぎ（VOICEVOX）</p>

---

# vi5.aux2の仕組み

<div un-h="[calc(100%_-_3.5rem)]" un-transform un-scale="90%" un-transform-origin="[top_right]">

```mermaid
sequenceDiagram
    participant au2 as AviUtl2
    participant vi5 as vi5.aux2
    participant p5 as p5.js on CEF

    au2->>vi5: オブジェクトの描画要求
    vi5->>p5: スケッチの描画要求
    p5->>vi5: 描画結果を返す
    vi5->>au2: 描画結果を返す
```

</div>

---

# 課題点

<v-clicks depth="1">

- AviUtl2限定
  - （内部的にはAviUtl2以外にも差し替えられるようにはしている）
- 遅い！
  - 固定コストとして30msぐらいかかってくる、60fpsが困難
- 不安定
  - 例えば色々と挙動が怪しい

</v-clicks>

---

# Future Work

<v-clicks depth="1">

- p5.jsをやめる！

</v-clicks>

<div un-h="4" />

<v-clicks depth="3">

- [libprocessing](https://github.com/processing/libprocessing)を使う
  - Rustで書かれたProcessingの実装
  - CEFを経由せずテクスチャを取得できる
  - JS以外でもできるかも
    - もしかしたらRubyからでも？
    - HSPからでも？

</v-clicks>

---

# まとめ

<v-clicks depth="1">

- p5.jsはコードでビジュアルを作るのに便利
- 既存の映像制作ソフトはWYSIWYGで編集できるのが便利
- p5.jsを映像制作ソフトに埋め込むといいとこ取りができそう
- プロトタイプとしてvi5.aux2を作った
- まだまだ課題はあるが、libprocessingを使うことで解決できるかも
- ご清聴ありがとうございました！

</v-clicks>

<div un-h="8" />

<v-click>

- vi5.aux2：<https://github.com/sevenc-nanashi/vi5.aux2>
- この資料：<https://sevenc7c.com/pcd_tokyo_2026_vi5_aux2>

</v-click>
