# Create Project Card Action

[![CI Status](https://github.com/technote-space/create-project-card-action/workflows/CI/badge.svg)](https://github.com/technote-space/create-project-card-action/actions)
[![codecov](https://codecov.io/gh/technote-space/create-project-card-action/branch/master/graph/badge.svg)](https://codecov.io/gh/technote-space/create-project-card-action)
[![CodeFactor](https://www.codefactor.io/repository/github/technote-space/create-project-card-action/badge)](https://www.codefactor.io/repository/github/technote-space/create-project-card-action)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/technote-space/create-project-card-action/blob/master/LICENSE)

*Read this in other languages: [English](README.md), [日本語](README.ja.md).*

Project card を作成する `GitHub Actions` です。

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
<details>
<summary>Details</summary>

- [使用方法](#%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)
- [オプション](#%E3%82%AA%E3%83%97%E3%82%B7%E3%83%A7%E3%83%B3)
- [Action イベント詳細](#action-%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88%E8%A9%B3%E7%B4%B0)
  - [対象イベント](#%E5%AF%BE%E8%B1%A1%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88)
- [このアクションを使用しているリポジトリの例](#%E3%81%93%E3%81%AE%E3%82%A2%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%81%AE%E4%BE%8B)
- [Author](#author)

</details>
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 使用方法
e.g. issue_opened.yml
```yaml
on:
  issues:
    types: [opened]
name: Issue opened
jobs:
  assign:
    name: Assign issues to project
    runs-on: ubuntu-latest
    steps:
      - name: Assign issues to project
        uses: technote-space/create-project-card-action@v1
        with:
          PROJECT: Backlog
          COLUMN: To do
```

e.g. pr-opened.yml
```yaml
on:
  pull_request:
    types: [opened]
name: Pull Request opened
jobs:
  assignToProject:
    name: Assign PullRequest to Project
    runs-on: ubuntu-latest
    steps:
      - name: Assign PullRequest to Project
        uses: technote-space/create-project-card-action@v1
        with:
          PROJECT: Backlog
          COLUMN: To do
```

## オプション
| name | description | default | required | e.g. |
|:---:|:---|:---:|:---:|:---:|
|PROJECT|プロジェクト名| |true|`Backlog`|
|COLUMN|カラム名| |true|`To do`|
|CHECK_ORG_PROJECT|Organizationプロジェクトをチェックするかどうか<br>このオプションを使用する場合、`admin` へのアクセス許可が必要です。<br>`secrets.GITHUB_TOKEN` の代わりに Personal access token を使用してください。|false| |`true`|
|CHECK_USER_PROJECT|Userプロジェクトをチェックするかどうか<br>このオプションを使用する場合、`repo` へのアクセス許可が必要です。<br>`secrets.GITHUB_TOKEN` の代わりに Personal access token を使用してください。|false| |`true`|
|GITHUB_TOKEN|アクセストークン|`${{github.token}}`|true|`${{secrets.ACCESS_TOKEN}}`|

## Action イベント詳細
### 対象イベント
| eventName | action |
|:---:|:---:|
|pull_request|opened, reopened|
|issues|opened, reopened|

## このアクションを使用しているリポジトリの例
- [Release GitHub Actions](https://github.com/technote-space/release-github-actions)
  - [pr-opened.yml](https://github.com/technote-space/release-github-actions/blob/master/.github/workflows/pr-opened.yml)
- [Auto card labeler](https://github.com/technote-space/auto-card-labeler)
  - [pr-opened.yml](https://github.com/technote-space/auto-card-labeler/blob/master/.github/workflows/pr-opened.yml)
- [Assign Author](https://github.com/technote-space/assign-author)
  - [pr-opened.yml](https://github.com/technote-space/assign-author/blob/master/.github/workflows/pr-opened.yml)
- [TOC Generator](https://github.com/technote-space/toc-generator)
  - [pr-opened.yml](https://github.com/technote-space/toc-generator/blob/master/.github/workflows/pr-opened.yml)
- [Package Version Check Action](https://github.com/technote-space/package-version-check-action)
  - [pr-opened.yml](https://github.com/technote-space/package-version-check-action/blob/master/.github/workflows/pr-opened.yml)
- [Get Diff Action](https://github.com/technote-space/get-diff-action)
  - [pr-opened.yml](https://github.com/technote-space/get-diff-action/blob/master/.github/workflows/pr-opened.yml)
- [Create Project Card Action](https://github.com/technote-space/create-project-card-action)
  - [pr-opened.yml](https://github.com/technote-space/create-project-card-action/blob/master/.github/workflows/pr-opened.yml)
- [Get git comment action](https://github.com/technote-space/get-git-comment-action)
  - [pr-opened.yml](https://github.com/technote-space/get-git-comment-action/blob/master/.github/workflows/pr-opened.yml)

## Author
[GitHub (Technote)](https://github.com/technote-space)  
[Blog](https://technote.space)
