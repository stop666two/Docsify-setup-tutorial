# 📚 stop666的Docsify基础使用教程：无插件精简版

<div style="background-color:#f0f8ff; padding:15px; border-radius:8px; border-left:4px solid #42b983;">
**✨ 本教程特色**  
✅ 2025年最新v5.0.0-rc.1版本基础功能  
✅ 完全无插件配置，专注核心功能  
✅ 精简实用的示例代码与配置说明  
✅ 从安装到部署的完整基础流程  
</div>

## 📋 目录导航

* [什么是Docsify？](#1-什么是-docsify)
* [环境准备](#2-环境准备)
* [快速开始](#3-快速开始)
* [核心配置详解](#4-核心配置详解)
* [Markdown基础语法](#5-markdown基础语法)
* [界面定制指南](#6-界面定制指南)
* [部署方案对比](#7-部署方案对比)
* [常见问题排查](#8-常见问题排查)
* [高级技巧与资源](#9-高级技巧与资源)

---

## 1. 什么是 Docsify？

Docsify 是一个**动态文档生成工具**，它可以将 Markdown 文件直接转换为美观的文档网站，无需预先生成静态 HTML 文件。与其他工具相比，Docsify 具有以下核心优势：

- **轻量级**：核心仅 ~21KB，加载速度快
- **零构建**：直接渲染 Markdown，修改后实时预览
- **原生简洁**：无需插件即可实现基础文档功能
- **易于部署**：支持多种部署方式，配置简单
- **高度可定制**：支持自定义主题、导航和布局

### 📸 效果展示

![Docsify基础文档示例](https://picsum.photos/id/0/800/400 ':size=100%')

> **💡 提示**：Docsify 特别适合快速搭建API文档、技术手册、教程网站等场景，无需复杂配置即可获得专业的文档网站。

---

## 2. 环境准备

### 2.1 安装 Node.js

Docsify 需要 Node.js 环境支持，推荐安装 LTS 版本：

```bash
# 检查是否已安装Node.js
node -v  # 应输出 v16.x 或更高版本
npm -v   # 应输出 8.x 或更高版本

# 如果未安装，执行以下命令（Ubuntu示例）
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs

# 验证安装
node -v && npm -v  # 应显示Node.js和npm版本号
```

> **🔍 验证方法**：打开终端输入`node -v`，如果显示版本号则安装成功。

### 2.2 安装 Docsify CLI

使用 npm 全局安装 docsify 命令行工具：

```bash
# 全局安装
npm i docsify-cli -g

# 验证安装
docsify -v  # 应输出 5.0.0-rc.1 或更高版本
```

---

## 3. 快速开始

### 3.1 项目初始化

```bash
# 创建项目文件夹
mkdir my-docs && cd my-docs

# 初始化文档目录
docsify init ./docs

# 查看生成的目录结构
tree docs/
```

生成的基础目录结构：

```
docs/
├── index.html       # 入口文件（核心配置）
├── README.md        # 主页内容
└── .nojekyll        # 防止GitHub Pages忽略下划线文件
```

### 3.2 本地预览

```bash
# 启动本地服务器
docsify serve docs

# 输出信息示例：
# Serving /path/to/my-docs/docs now.
# Listening at http://localhost:3000
```

打开浏览器访问 [http://localhost:3000](http://localhost:3000)，你将看到基础文档网站。

> **💡 开发技巧**：修改Markdown文件后无需重启服务，浏览器会自动刷新。

---

## 4. 核心配置详解

### 4.1 基础配置示例（index.html）

`index.html` 是 Docsify 的核心配置文件，以下是精简的基础配置：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>我的Docsify文档</title>
  <!-- 引入主题 -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@5/dist/themes/vue.css">
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      // 网站标题
      name: 'Docsify教程',
      // GitHub仓库链接（右上角图标）
      repo: 'https://github.com/yourusername/yourrepo',
      // 加载侧边栏
      loadSidebar: true,
      // 加载导航栏
      loadNavbar: true,
      // 启用封面页
      coverpage: true,
      // 最大标题层级
      maxLevel: 4,
      // 自动生成目录的层级
      subMaxLevel: 3,
      // 切换页面后滚动到顶部
      auto2top: true,
      // 支持emoji
      emoji: true,
      // 主页文件名
      homepage: 'README.md'
    }
  </script>
  <!-- Docsify核心脚本 -->
  <script src="https://cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
</body>
</html>
```

### 4.2 常用配置选项表

| 配置项 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| `name` | String | `null` | 网站标题，显示在侧边栏顶部 |
| `repo` | String | `null` | GitHub仓库地址，显示右上角图标 |
| `loadSidebar` | Boolean | `false` | 是否加载自定义侧边栏 |
| `loadNavbar` | Boolean | `false` | 是否加载自定义导航栏 |
| `coverpage` | Boolean | `false` | 是否启用封面页 |
| `maxLevel` | Number | `3` | 最大标题层级（1-6） |
| `subMaxLevel` | Number | `0` | 侧边栏显示的子标题层级 |
| `auto2top` | Boolean | `false` | 页面切换后是否滚动到顶部 |
| `homepage` | String | `README.md` | 主页文件名 |
| `basePath` | String | `./` | 基础路径，用于嵌套在子目录时 |
| `themeColor` | String | `#42b983` | 主题颜色，影响链接和强调色 |
| `emoji` | Boolean | `false` | 是否支持emoji解析 |

> **⚠️ 注意**：以上配置均为Docsify原生支持，无需任何插件即可使用。

---

## 5. Markdown基础语法

Docsify 原生支持标准 Markdown 语法，以下是常用语法示例：

### 5.1 标题层级

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

### 5.2 文本格式化

```markdown
**粗体文本**
*斜体文本*
***粗斜体文本***
~~删除线文本~~
<u>下划线文本</u>
`行内代码`
```

显示效果：
**粗体文本**

*斜体文本*

***粗斜体文本***

~~删除线文本~~

<u>下划线文本</u>

`行内代码`

### 5.3 列表

```markdown
- 无序列表项1
- 无序列表项2
  - 子列表项
  - 子列表项

1. 有序列表项1
2. 有序列表项2
   1. 子列表项
   2. 子列表项

- [x] 已完成任务
- [ ] 未完成任务
- [ ] 计划任务
```

显示效果：
- 无序列表项1
- 无序列表项2
  - 子列表项
  - 子列表项

1. 有序列表项1
2. 有序列表项2
   1. 子列表项
   2. 子列表项

- [x] 已完成任务
- [ ] 未完成任务
- [ ] 计划任务

### 5.4 链接与图片

```markdown
<!-- 内部链接 -->
[首页](/ "回到首页")
[快速开始](quickstart.md "查看快速开始指南")

<!-- 外部链接 -->
[GitHub](https://github.com)

<!-- 图片 -->
![示例图片](https://picsum.photos/id/2/600/400)

<!-- 带尺寸的图片 -->
![小图片](https://picsum.photos/id/3/200/200 ':size=100x100')
```

### 5.5 代码块

````markdown
```bash
# 终端命令示例
cd my-project
npm install
npm run dev
```

```javascript
// JavaScript示例
function greeting(name) {
  return `Hello, ${name}!`;
}

console.log(greeting("Docsify"));
```

```python
# Python示例
def add(a, b):
    return a + b
    
result = add(10, 20)
print(f"结果: {result}")  # 输出 结果: 30
```
````

### 5.6 表格

```markdown
| 姓名 | 年龄 | 职业 |
|------|------|------|
| 张三 | 25   | 工程师 |
| 李四 | 30   | 设计师 |
| 王五 | 35   | 产品经理 |
```

### 5.7 引用块

```markdown
> 这是一个基本引用块
> 
> 可以包含多行文本
> 
> > 这是一个嵌套引用
```

显示效果：
> 这是一个基本引用块
> 
> 可以包含多行文本
> 
> > 这是一个嵌套引用

### 5.8 提示框

```markdown
!> **重要提示**：这是一个重要提示框
?> **注意**：这是一个普通提示框
```

显示效果：

!> **重要提示**：这是一个重要提示框

?> **注意**：这是一个普通提示框

---

## 6. 界面定制指南

### 6.1 侧边栏定制

#### 6.1.1 创建基础侧边栏

在`docs`目录下创建`_sidebar.md`文件：

```markdown
* [首页](/ "回到首页")
* **入门指南**
  * [什么是Docsify](intro.md)
  * [环境准备](environment.md)
  * [快速开始](quickstart.md)
* **核心功能**
  * [基本配置](config.md)
  * [Markdown语法](markdown.md)
  * [侧边栏](sidebar.md)
  * [导航栏](navbar.md)
  * [封面页](coverpage.md)
* **部署上线**
  * [GitHub Pages](github-pages.md)
  * [Nginx部署](nginx.md)
* **帮助与资源**
  * [常见问题](faq.md)
  * [相关资源](resources.md)
```

#### 6.1.2 侧边栏配置选项

```javascript
window.$docsify = {
  loadSidebar: true,        // 启用侧边栏
  subMaxLevel: 3,           // 显示子标题层级
  alias: {                  // 路径别名
    '/.*/_sidebar.md': '/_sidebar.md'  // 所有目录使用同一侧边栏
  }
}
```

### 6.2 导航栏定制

#### 6.2.1 创建基础导航栏

在`docs`目录下创建`_navbar.md`文件：

```markdown
* [首页](/ "文档首页")
* [入门](quickstart.md "快速开始")
* [配置](config.md "配置指南")
* [语法](markdown.md "Markdown语法")
* [部署](deploy.md "部署教程")
* [关于](about.md "关于本项目")
```

#### 6.2.2 导航栏配置选项

```javascript
window.$docsify = {
  loadNavbar: true,         // 启用导航栏
  mergeNavbar: true,        // 在小屏幕上将导航栏合并到侧边栏
  maxLevel: 4               // 导航栏中显示的标题层级
}
```

### 6.3 封面页设计

#### 6.3.1 创建封面页

在`docs`目录下创建`_coverpage.md`文件：

```markdown
![logo](https://docsify.js.org/_media/icon.svg)

# Docsify 教程
## 从入门到精通

> 一个神奇的文档网站生成工具，让你的 Markdown 秒变网站

- 无需构建，即时预览
- 轻量级，加载迅速
- 简单部署，一键上线
- 高度可定制，满足个性化需求

[开始阅读](#/README)
[GitHub](https://github.com/docsifyjs/docsify)
```

#### 6.3.2 封面页配置

```javascript
window.$docsify = {
  coverpage: true,          // 启用封面页
  coverpageOnly: true       // 仅在首页显示封面页
}
```

### 6.4 主题切换

Docsify 内置多种主题，无需插件即可切换：

```html
<!-- Vue风格（默认） -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@5/dist/themes/vue.css">

<!-- 暗黑模式 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@5/dist/themes/dark.css">

<!-- 纯净风格 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@5/dist/themes/pure.css">

<!-- Buble风格 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@5/dist/themes/buble.css">
```

### 6.5 自定义CSS

创建`docs/css/custom.css`文件，添加自定义样式：

```css
/* 修改标题样式 */
h1 {
  color: #42b983;
  border-bottom: 2px solid #f5f5f5;
  padding-bottom: 0.5rem;
}

/* 修改链接颜色 */
a {
  color: #3eaf7c;
}

/* 修改引用块样式 */
.markdown-section blockquote {
  border-left: 4px solid #42b983;
  background-color: #f8f8f8;
}

/* 修改代码块样式 */
.markdown-section pre {
  border-radius: 6px;
  background-color: #f7f7f7;
}
```

在`index.html`中引入自定义CSS：

```html
<link rel="stylesheet" href="css/custom.css">
```

---

## 7. 部署方案对比

### 7.1 GitHub Pages部署

#### 7.1.1 部署步骤

1. **创建仓库**：在GitHub上创建新仓库（如`docsify-demo`）

2. **准备项目**：

```bash
# 初始化Git仓库
git init
git add .
git commit -m "Initial commit"

# 添加远程仓库
git remote add origin https://github.com/yourusername/docsify-demo.git

# 推送到main分支
git push -u origin main
```

3. **配置GitHub Pages**：
   - 进入仓库Settings → Pages
   - 选择**main 分支**和**/docs 目录**
   - 点击Save，等待部署完成（通常需要1-2分钟）

4. **访问网站**：
   地址格式：`https://yourusername.github.io/docsify-demo/`

#### 7.1.2 优缺点分析

| 优点 | 缺点 |
|------|------|
| 完全免费，无需服务器 | 国内访问速度较慢 |
| 自动部署，提交即更新 | 配置选项有限 |
| 支持自定义域名 | 构建日志不可见 |
| 维护简单，无需管理服务器 | 不支持高级服务器配置 |

### 7.2 Nginx部署

#### 7.2.1 安装Nginx

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nginx

# CentOS/RHEL
sudo yum install nginx

# 启动Nginx
sudo systemctl start nginx
sudo systemctl enable nginx  # 设置开机自启
```

#### 7.2.2 配置Nginx

创建配置文件 `/etc/nginx/conf.d/docsify.conf`：

```nginx
server {
  listen 80;
  server_name docs.yourdomain.com;  # 替换为你的域名
  
  root /var/www/docsify-docs;       # 文档存放目录
  index index.html;                 # 入口文件
  
  # 支持History模式路由
  location / {
    try_files $uri $uri/ /index.html;
  }
  
  # 设置缓存控制
  location ~* \.(md|html|css|js|png|jpg|jpeg|gif|ico)$ {
    expires 1h;                     # 缓存1小时
    add_header Cache-Control "public, max-age=3600";
  }
}
```

#### 7.2.3 部署文档

```bash
# 创建目录
sudo mkdir -p /var/www/docsify-docs

# 复制文档文件
sudo cp -r docs/* /var/www/docsify-docs/

# 设置权限
sudo chown -R www-data:www-data /var/www/docsify-docs

# 重启Nginx
sudo systemctl restart nginx
```

---

## 8. 常见问题排查

### 8.1 本地预览问题

#### 8.1.1 404错误

**可能原因**：
- 未正确启动docsify服务
- 文件路径错误
- index.html配置有误

**解决方法**：
```bash
# 确保在正确的目录启动服务
cd my-docs
docsify serve docs  # 确保指定了正确的文档目录

# 检查文件结构
ls docs/  # 应包含index.html和README.md
```

#### 8.1.2 页面空白

**解决方法**：
1. 打开浏览器开发者工具（F12）查看控制台错误
2. 检查网络请求，确认docsify.min.js是否加载成功
3. 验证index.html中的配置是否正确，特别是`window.$docsify`对象

### 8.2 侧边栏不显示

**可能原因**：
- 未启用`loadSidebar: true`配置
- `_sidebar.md`文件不存在或路径错误
- 文件格式错误，Markdown列表语法不正确

**解决步骤**：
1. 检查index.html配置：
   ```javascript
   window.$docsify = {
     loadSidebar: true,  // 确保此项为true
     subMaxLevel: 2      // 设置适当的子标题层级
   }
   ```

2. 确认文件路径：
   ```bash
   # 应在docs目录下
   ls docs/_sidebar.md  # 确保文件存在
   ```

3. 检查文件格式：
   ```markdown
   # 正确格式
   * [首页](/)\n
   * [开始](start.md)
     
   # 错误格式（缺少空格）
   *[首页](/)\n
   *[开始](start.md)
   ```

### 8.3 导航栏不显示

**解决方法**：
```javascript
window.$docsify = {
  loadNavbar: true,  // 启用导航栏
  mergeNavbar: true  // 在移动设备上合并到侧边栏
}
```

同时确保`_navbar.md`文件存在于docs目录中。

---

## 9. 高级技巧与资源

### 9.1 性能优化建议

#### 9.1.1 图片优化

```markdown
<!-- 使用合适尺寸的图片 -->
![优化图片](https://picsum.photos/id/20/800/400)  <!-- 宽度不超过文档容器 -->

<!-- 使用相对路径加载本地图片 -->
![本地图片](/images/example.png)  <!-- 避免外部链接失效 -->
```

#### 9.1.2 目录结构优化

```
docs/
├── index.html          # 入口文件
├── README.md           # 主页
├── _sidebar.md         # 侧边栏
├── _navbar.md          # 导航栏
├── _coverpage.md       # 封面页
├── css/                # 自定义样式
│   └── custom.css      # 样式文件
├── images/             # 图片资源
│   ├── logo.png
│   └── example.png
├── guide/              # 指南文档
│   ├── start.md
│   └── config.md
└── deploy/             # 部署文档
    ├── github.md
    └── nginx.md
```

### 9.2 实用资源

#### 9.2.1 官方资源

- **Docsify官方文档**：[docsify.js.org](https://docsify.js.org/)
- **GitHub仓库**：[docsifyjs/docsify](https://github.com/docsifyjs/docsify)
- **官方示例**：[docsifyjs/docsify-demo](https://github.com/docsifyjs/docsify-demo)

#### 9.2.2 学习资源

- **Markdown语法指南**：[markdown-it.github.io](https://markdown-it.github.io/)
- **GitHub Pages部署指南**：[pages.github.com](https://pages.github.com/)
- **Nginx配置指南**：[nginx.org/en/docs/](https://nginx.org/en/docs/)

#### 9.2.3 工具推荐

- **在线Markdown编辑器**：[StackEdit](https://stackedit.io/)
- **图片压缩工具**：[TinyPNG](https://tinypng.com/)
- **代码格式化工具**：[Prettier](https://prettier.io/)

---

> **📝 文档信息**  
> 本教程基于 Docsify v5.0.0-rc.1 编写  
> 最后更新：2025年10月  
> 作者：stop666  
> 版本：无插件精简版 v1.0