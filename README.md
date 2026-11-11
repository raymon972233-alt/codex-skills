# codex-skills

我的 Codex 常用技能。把完整技能保存在这里，换电脑后通过仓库链接重新安装。

## 在另一台电脑上安装

打开 Codex，把下面这段话完整发送给它：

```text
请使用 skill-installer，从 https://github.com/raymon972233-alt/codex-skills 安装 skills/arxiv 技能。
请安装整个 skills/arxiv 文件夹，包含 scripts、references、LICENSE 和 installation.json。
如果同名技能已经存在，请先检查版本和本地修改，不要直接覆盖。
安装后检查脚本能否运行，并告诉我如何使用。
```

通常安装完成后的下一条消息即可使用；如果技能没有出现，重启 Codex 后重试。
本仓库为公开仓库，读取和下载文件无需 GitHub 登录。

## arxiv：论文搜索、下载与摘要

基于 [ARIS](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) 的 arxiv 技能，支持按关键词或 arXiv ID 查找论文、下载 PDF、生成摘要。
搜索和下载只需要 Python 3，无需配置 API Key，也不需要安装整个 ARIS 项目。

本仓库把原本位于 ARIS 其他目录的下载脚本和引用文档一起打包，方便独立安装。
可选的 Research Wiki 集成仍需完整 ARIS 的相应工具；普通搜索和下载不依赖它。

安装后可以直接对 Codex 说：

```text
使用 arxiv 技能，搜索关于 retrieval augmented generation 的论文，列出 5 篇。
```

```text
使用 arxiv 技能，下载论文 1706.03762 到当前项目的 papers 文件夹，并总结主要贡献。
```

```text
使用 arxiv 技能，搜索关于 diffusion models 的论文，下载前 3 篇到 papers 文件夹。
```

下载的 PDF 默认保存在当前项目的 `papers/` 文件夹，也可以在请求中指定其他位置。
技能文件保存在本仓库；下载后的论文和阅读笔记需要另行保存或同步。

## 手动安装

在 GitHub 页面选择 **Code → Download ZIP**，解压后将整个 `skills/arxiv` 文件夹复制到 Codex 的个人技能目录。
使用内置 skill-installer 时，由它选择正确的安装位置。

脚本也可以单独使用。在 `skills/arxiv` 文件夹中运行：

```bash
python3 scripts/arxiv_fetch.py search "id:1706.03762" --max 1
python3 scripts/arxiv_fetch.py download 1706.03762 --dir papers
```

Windows 上如果没有 `python3` 命令，可使用已安装的 `python` 命令。

## 文件结构

```text
skills/arxiv/
├── SKILL.md
├── LICENSE
├── installation.json
├── scripts/
│   └── arxiv_fetch.py
└── references/
    ├── integration-contract.md
    └── wiki-helper-resolution.md
```

## 来源与更新

- 上游：[wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)
- 当前基于上游提交：`8f493923f28c3f991dcca1287db97aa780d0969b`
- 原始技能及脚本采用 MIT 许可证，保留在 [skills/arxiv/LICENSE](skills/arxiv/LICENSE)。
- 配套文件、版本和本地适配记录见 [installation.json](skills/arxiv/installation.json)。
- 后续更新时保留本仓库的独立安装适配，并再次检查搜索和 PDF 下载。
