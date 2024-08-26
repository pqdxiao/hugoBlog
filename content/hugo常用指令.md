---
title: hugo常用指令
---
hugo new site hugoBlog --format=toml
cd hugoBlog

# 初始化 Hugo 模块
hugo mod init github.com/pqdxiao/hugoBlog

# 添加 Hextra 
hugo mod get github.com/imfing/hextra


## 通过 Git Submodule 安装 
先决条件 
在我们开始之前，你必须先确保以下软件已经安装：
Hugo (extended version)
Git
步骤 

### 初始化 Hugo 站点 
hugo new site my-site --format=yaml

将 Hextra 添加为 Git Submodule 
git submodule add https://github.com/imfing/hextra.git themes/hextra

添加以下内容来配置 hugo.yaml 以使用 Hextra：

theme: hextra

创建你的第一个内容页 
让我们为主页和文档页面创建一个新的内容页面：

hugo new content/_index.md
hugo new content/docs/_index.md

在本地预览站点 
hugo server --buildDrafts --disableFastRender

瞧！你现在可以在 http://localhost:1313/ 看到你的新站点。

使用 CI/CD 进行部署时，必须确保在运行 hugo 命令之前执行以下命令。

git submodule update --init

如果不运行此命令，theme 中将不会存在 Hextra 文件，进而导致构建失败。

如需把项目中所有的 Hugo Modules 都升级到最新，在终端中运行此命令：

hugo mod get -u

如需把 Hextra 升级到最新的发行版本, 在终端中运行此命令：

hugo mod get -u github.com/imfing/hextra

如果你需要获得更多信息，参见 Hugo Modules.