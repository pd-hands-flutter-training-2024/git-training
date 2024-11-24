# hands-on-git-practice

Flutter研修のGit演習用レポジトリです。

## Gitのコマンド確認

### インストール

### バージョン確認とusernameの設定

以下のコマンドでバージョンが返ってこない場合はgitがインストールされていないため、インストールを再度お試しください。

```sh
git --version

# git version 2.44.2
```

（任意）usernameなどを変更したい場合は以下で変更可能です。

```sh
git config --global user.name [username]
```

設定された値は以下で確認できます。

```sh
❯ git config -l | grep user
user.email=[YOUR_EMAIL]
user.name=[YOUR_USERNAME]
```

## 演習: プルリクエストを作成してコミットする

### ブランチの準備

```sh
git checkout -b feature/[username]/create-profile

# 例
git checkout -b feature/htsuruo/create-profile
```

ブランチが切り替わったかを確認します。作成したブランチに`*`マーク（環境次第）が付いていればOKです。

```sh
git branch

# 例
* feature/[username]/create-profile
  main
```

### コミットする

1. `self_introduction`フォルダ配下に、`[自分の名前]_[自分の名字].md`のファイルを作成し自己紹介を[Markdown記法](https://ja.wikipedia.org/wiki/Markdown)を使って書いてみましょう。[hideki_tsuruoka.md](self_introduction/hideki_tsuruoka.md)を参考にしてください。
    - 参考: [Markdown記法一覧](https://qiita.com/oreo/items/82183bfbaac69971917f)

1. 記入が終わったらコミットします。

```sh
# 変更差分を見る
git status

# modifiedファイルをstagedにあげる（ファイルをコミット対象にする）
git add [YOUR_NAME].md
# 例: git add hideki_tsuruoka.md


# コミットする
git commit -m "Create file to introduce myself" # 日本語でもOKです

# プッシュする
# ※この際に、はじめてプッシュする場合はUsernameとPasswordが要求されるので適宜入力してください。
# - Username: GitHubのusername
# - Password: ご自身で生成したPAT
git push origin HEAD

```

## プルリクエストを作成する

先程の作業内容をレビュワーに「受け入れて下さい」というリクエストを出します。

1. GitHubのWebコンソール（GUI）で操作します。
1. レビュワーがわかるようにコメントを書きましょう。
1. レビュワーは作業内容に問題が無いことを確認したらマージします。
1. マージが完了したら各人の作業内容がmainブランチに統合されます。

## マージを確認する

`main`ブランチに切り替えて、みなさんの変更内容を確認しましょう。

```sh
# mainブランチにチェックアウト（切り替え）して
git checkout main

# リモートブランチから変更内容を取得し、ローカルブランチに取り込む
git pull origin
```

これで、`self_introduction`のファイルを見ると各人のプロフィールファイルを確認することができます。
