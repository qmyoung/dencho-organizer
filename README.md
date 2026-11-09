# 公开页面（site/）

电账整理箱的公开静态页面：帮助、支持、隐私政策、使用条款，日语、简体中文、英语三语。源文件在本仓 `site/`，走本仓 PR 评审；发布时把 `site/` 的内容推到 yang 自己 GitHub 账号下的公开仓，由 GitHub Pages 托管。

## 结构与网址约定

```
site/
  index.html              语言入口
  assets/site.css         共用样式，不引外部字体、脚本与统计代码
  ja/ zh-Hans/ en/        每种语言一个目录
    index.html help.html support.html privacy.html terms.html
```

公开网址 = `https://qmyoung.github.io/dencho-organizer/` + `<语言>/<页面>.html`，语言目录名取 `ja`、`zh-Hans`、`en`，页面取 `help`、`support`、`privacy`、`terms`。应用里 `ReceiptKit/Sources/ReceiptAppSupport/SupportLinks.swift` 按同一形态拼网址（界面语言为 `ja`、`zh-Hans` 以外一律取 `en`），两边必须一致，改目录名或页面名要同时改那里。

## 发布步骤

1. 公开仓 `qmyoung/dencho-organizer` 已建好，是空仓（无 README、gitignore、license）；本机克隆到 `site/` 之外的目录。
2. 在本仓合并后的 `main` 上，把 `site/` 的内容拷到公开仓的根目录（`README.md` 不必带上）。
3. 提交并推送公开仓的 `main`。推到 GitHub 是对外发布，由 yang 本人操作。
4. 公开仓 Settings › Pages：Source 选 Deploy from a branch，分支 `main`，目录 `/ (root)`，保存。
5. 等 Pages 部署完成后，打开 `https://qmyoung.github.io/dencho-organizer/` 与每种语言的四页，确认都能打开、页间链接可用。
6. 网址与应用里的 `SupportLinks` 常量一致后，才可提审。

页面有改动时，先在本仓走 PR 改 `site/`，合并后重复第 2 至 3 步。

## 改页面时的约束

- 三种语言的同名页面内容对等，一处改动三语同改。
- 凡涉及電帳法、インボイス等税务与法规的句子，都带「仅供参考，请找税理士确认」的对应语言句式；不使用暗示官方认可的字眼。
- 隐私政策只写应用实际的行为：不收集数据、收据不出本机、购买由 Apple 处理；应用行为变了，同步改。
- 利用规约页用 Apple 标准 EULA 链接。
- 帮助页只写当前版本存在的功能。
