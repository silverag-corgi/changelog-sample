# changelog-sample <!-- omit in toc -->

- [1. `commitizen-tools/commitizen`](#1-commitizen-toolscommitizen)
  - [1.1. インストール方法](#11-インストール方法)
  - [1.2. ツール実行ログ](#12-ツール実行ログ)
- [2. `python-semantic-release/python-semantic-release`](#2-python-semantic-releasepython-semantic-release)
  - [2.1. インストール方法](#21-インストール方法)
  - [2.2. ツール実行ログ](#22-ツール実行ログ)
- [3. `conventional-changelog/conventional-changelog-cli`](#3-conventional-changelogconventional-changelog-cli)
  - [3.1. インストール方法](#31-インストール方法)
  - [3.2. ツール実行ログ](#32-ツール実行ログ)

## 1. `commitizen-tools/commitizen`

- [commitizen-tools/commitizen - GitHub](https://github.com/commitizen-tools/commitizen)
- [Commitizen documentation](https://commitizen-tools.github.io/commitizen/)

### 1.1. インストール方法

まずは`poetry`(パッケージ管理ツール)をインストールする。

```bash
$ python3 --version
Python 3.10.10

$ pipx install poetry
(省略)

$ poetry --version
Poetry (version 1.4.1)

$ poetry config virtualenvs.in-project true
```

次に`commitizen`をインストールする。

```bash
$ cd workspace/Git/python/changelog-sample

$ poetry install
```

### 1.2. ツール実行ログ

次に`commitizen`を実行する。
バージョンはコミットログに基づいて自動計算される。

```bash
$ poetry run cz bump
chore: bump from 0.0.0 to 1.0.0
tag to create: v1.0.0
increment detected: MAJOR

tags in full_changelog: ['v1.0.0', 'v0.0.0']

[main 95a1fa6] chore: bump from 0.0.0 to 1.0.0
 2 files changed, 25 insertions(+), 2 deletions(-)

Done!
```

## 2. `python-semantic-release/python-semantic-release`

- [python-semantic-release/python-semantic-release - GitHub](https://github.com/python-semantic-release/python-semantic-release)
- [Python Semantic Release - python-semantic-release 7.32.2 documentation](https://python-semantic-release.readthedocs.io/en/latest/)

### 2.1. インストール方法

まずは`poetry`(パッケージ管理ツール)をインストールする。

```bash
$ python3 --version
Python 3.10.10

$ pipx install poetry
(省略)

$ poetry --version
Poetry (version 1.4.1)

$ poetry config virtualenvs.in-project true
```

次に`python-semantic-release`をインストールする。

```bash
$ cd workspace/Git/python/changelog-sample

$ poetry install
```

### 2.2. ツール実行ログ

次に`python-semantic-release`を実行する。
バージョンはコミットログに基づいて自動計算される。

```bash
$ poetry run semantic-release publish
Current version: 0.0.0, Current release version: 0.0.0
Bumping with a major version to 1.0.0
Pushing new version
error: Cmd('git') failed due to: exit code(128)
error:   cmdline: git push origin main
error:   stderr: remote: Repository not found.
error: fatal: Authentication failed for <repository url>
 An option like `push_changes` that specifies whether or not to push changes to the repository is not implemented yet,
 so if a env `GH_TOKEN` is not set, output error log when pushing.
```

## 3. `conventional-changelog/conventional-changelog-cli`

- [conventional-changelog/conventional-changelog-cli - GitHub](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli)

### 3.1. インストール方法

まずは、`Node.js`(JavaScript実行環境)及び`npm`(JavaScript系パッケージ管理ツール)をインストールする。

```bash
$ curl -fsSL https://deb.nodesource.com/setup_19.x | sudo -E bash -
$ # サードパーティ用のaptリポジトリ情報(ディレクトリ`/etc/apt/sources.list.d/`)にノードソース`Node.js 19.x`を追加する
(省略)

$ cat /etc/apt/sources.list.d/nodesource.list
$ # サードパーティ用のaptリポジトリ情報(ディレクトリ`/etc/apt/sources.list.d/`)を確認する
deb [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_19.x bullseye main
deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_19.x bullseye main

$ sudo apt update && sudo apt install -y nodejs
(省略)

$ node --version
v19.8.1

$ npm --version
9.5.1
```

次に`conventional-changelog-cli`をインストールする。

```bash
$ cd workspace/Git/python/changelog-sample

$ sudo npm install conventional-changelog-cli
(省略)

$ npm ls
changelog-sample@0.0.0 /root/workspace/Git/python/changelog-sample
└── conventional-changelog-cli@2.2.2
```

### 3.2. ツール実行ログ

次に`conventional-changelog-cli`を実行する。
バージョンはコミットログに基づいて自動計算される訳ではなく、どのバージョンを上げるかユーザが指定する必要がある。

```bash
$ npm version major

> version
> conventional-changelog --preset angular --release-count 0 --tag-prefix v --pkg package.json --infile CHANGELOG_cc.md --same-file && git add CHANGELOG_cc.md

v1.0.0
```
