# 卒業研究でのレジュメ

## 2021/06/13

### windows用gitを入れた後にgit bashに行うコマンド

git config --global user.name 'smastu'
git config --global user.email 's.matsumoto.gk@cc.it-hiroshima.ac.jp'
git config --global core.editor 'code --wait'
git config --global merge.tool 'code --wait "$MERGED"'
git config --global push.default simple

### latex workshopの設定

setting.jsonの記述について，Latexの箇所を抜粋．jbibtexを使うためには，ptex2pdfを3回使わないといけない点に注意．

{

    //LaTeX
    "latex-workshop.latex.recipes": [
        {
            "name": "toolchain",
            "tools": [
                "ptex2pdf",
                "pbibtex",
                "ptex2pdf",
                "ptex2pdf",
                "platex"
            ]
        },
    ],
    "latex-workshop.latex.tools": [
        {
            "name": "ptex2pdf",
            "command": "ptex2pdf",
            "args": [
                "-l",
                "-ot",
                "-kanji=utf8 -synctex=1",
                "%DOC%"
            ]
        },
        {
            "name": "platex",
            "command": "platex",
            "args": [
                "-kanji=utf8 -synctex=1",
                "%DOC%"
            ]
        },
        {
            "name": "pbibtex",
            "command": "pbibtex",
            "args": [
                "%DOCFILE%",
                "-kanji=utf8"
            ]
        },        
    ],
    "latex-workshop.latex.autoClean.run": "onBuilt",
    //自動コンパイルしない
    "latex-workshop.latex.autoBuild.run": "never", //"onFileChange",
    //自動コンパイルしない
    "latex-workshop.latex.autoBuild.onSave.enabled": false,
    "latex-workshop.latex.autoBuild.interval": 0,
    "latex-workshop.view.pdf.viewer": "tab",
    "latex-workshop.chktex.enabled": false
}
