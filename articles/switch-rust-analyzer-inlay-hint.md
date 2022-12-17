---
title: "rust-analyzerのinlay hintsの表示をショートカットで切り替える"
emoji: "🕊️"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [vscode, rust]
published: true
---


## TL;DR

~~`Rust Analyzer: Toggle inlay hints`にキーバインドを割り当てる~~
VSCodeの`editor.inlayHints.enabled`を`onUnlessPressed`または`offUnlessPressed`に設定する

Toggle inlay hintsはrust-analyzerから削除されました。 ([PR#13215](https://github.com/rust-lang/rust-analyzer/pull/13215))
エディタが全般的にサポートするようになった今、言語ごとに特化した拡張機能でサポートするべきではないという思想らしいです。  
ただし今でもちょいちょいなんで消したの？ってコメントがついているのでVSCodeが提供する機能との使い勝手の微妙な違いが受け入れられない人が一定数はいるみたいですね。

:::message alert
2022/12/18
以降の内容は更新前のまま残しているので読む必要なし
:::

## 背景

RustのコードをVSCodeで書いている時、rust-analyzerのinlay hintsを表示させていると型情報など長ったらしくて邪魔。でも見れたら嬉しい時もあるし、キーボードショートカットでパパっと切り替えたいなーと思ったので調べてみた  
当たり前すぎるからなのか、逆になかなか見つからなかったのでまとめておく

## ずっと非表示

表示させる必要がないなら拡張機能のRust Analyzerの設定から、Inlay HintsのParameter Hintsなり、Type Hintsなりをfalseにすればよい

![](/images/switch-rust-analyzer-inlay-hint/setting_param.png)

## コマンドパレットで切り替え

自分は表示/非表示を実装しながら切り替えたかったので、切り替える方法がないか調べてみたらVS Codeのコマンドパレットを使って切り替える方法が用意されてた

![](/images/switch-rust-analyzer-inlay-hint/command.png)

## キーボードショートカット

とはいえコマンドパレットもいちいち入力するのはめんどくさいのでキーバインドを割り当ててショートカット設定する

[ファイル]->[ユーザー設定]->[キーボードショートカット]から`Rust Analyzer: Toggle inlay hints`に好きなキーバインドを設定すればOK！

![](/images/switch-rust-analyzer-inlay-hint/key_bind.png)

## 参考

- https://stackoverflow.com/questions/69909997/can-i-remove-type-annotation-help-from-rust-analyzer

- https://github.com/rust-lang/rust-analyzer/issues/1977