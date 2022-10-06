---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
html: true
markdown.marp.enableHtml: true

backgroundImage: url('https://marp.app/assets/hero-background.svg')

style: |
    section * {line-height: 2em;}
    footer {padding-left: 140px;background: no-repeat left/100px url("images/logo_black.png");}
    section::after {font-size: 60%;content: attr(data-marpit-pagination) ' / ' attr(data-marpit-pagination-total);}
    h1 {color: var(--main-color);}
    h2 {position: absolute;top: 0px; left: 0px;padding: 20px 40px;display: inline-block;width: 100%;border-bottom: 8px double #aaa;}
    h3 {position: absolute;top: 3em;border-left: 8px solid var(--main-color);}
    section.toc {background: linear-gradient(to right, var(--main-color) 150px, #fff 0px);}

---

# Mac開発環境2022
@reizist


---

# ペアプロの恩恵
* ドライバーの構築過程の思考をリアルタイムにトレースできる
* 開発環境を垣間見ることができる
  - 意外と数分の間に得るものが大きい瞬間がある、のが醍醐味

---

# Terminal

* https://github.com/reizist/dotfiles から抜粋して詳解

---



# Terminal

* x-motemen/ghq
  - remote repoを管理する奴
  - `git clone` は一切使わない

---

# Terminal

* peco/peco
  - 数あるインタラクティブなフィルタリングツールのうちの一つ
  - ghqとの組み合わせが最高の体験
  

---

# Terminal

```
function peco-src () {
  local selected_dir=$(ghq list -p | peco --query "$LBUFFER")
  if [ -n "$selected_dir" ]; then
    BUFFER="cd ${selected_dir}"
    zle accept-line
  fi
  zle clear-screen
}
```

---

# Terminal

```
function peco-select-history() {
    local tac
    if which tac > /dev/null; then
        tac="tac"
    else
        tac="tail -r"
    fi
    BUFFER=$(history -n 1 | \
        eval $tac | \
        peco --query "$LBUFFER")
    CURSOR=$#BUFFER
    zle clear-screen
}
```

---


<!-- _class: lead -->

Demo

---


# Apps

* エディタ: VSCode
  - 資料作成: Marp
  - 作図: Drawio

---

<!-- _class: lead -->
<img src="architecture.drawio.svg" height="100%" />

---

# Apps

* Docker: lima
  - https://qiita.com/naomichi-y/items/1e676139e3f9fbc75d3c

---

# Apps
* ブログ/メモ: hugo

---
# Apps

* ランチャー: Alfred

* ウィンドウマネージャ: Shiftit

* キーボードカスタマイザ: Karabinar-Elements

---

# Apps

* ブラウザ: Brave
  - デフォで広告ブロックが強い
  - 設定によって使ってるだけで仮想通貨稼いでくれる( $1/month 程度w)

