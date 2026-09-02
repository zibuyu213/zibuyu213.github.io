# 部署到 GitHub Pages（免费、永久在线）

本指南使用 **GitHub 网页版**操作，**无需安装 git、无需命令行**。

## 准备工作

- 一个 GitHub 账号（已登录）
- 博客已用 `node build.js` 导出，静态文件在 `dist/` 目录

## 第 1 步：创建 GitHub 仓库

1. 打开 <https://github.com/new>
2. **Repository name** 必须填：`你的用户名.github.io`
   （例如你的用户名是 `zhangsan`，就填 `zhangsan.github.io`）
3. 选择 **Public**（公开）
4. 不要勾选 “Add a README file”（保持空仓库）
5. 点击 **Create repository**

> 为什么必须是 `用户名.github.io`？这样博客会直接部署在根域名，访问地址就是 `https://用户名.github.io`，最简单。

## 第 2 步：上传博客文件

1. 进入刚创建的仓库页面
2. 点击 **Add file → Upload files**
3. 用文件管理器打开本地 `D:\File\DSH_project\dist\` 目录，**把里面的内容全部选中**（`index.html`、`about.html`、`post` 文件夹、`style.css`、`favicon.svg`、`README.md`）
4. 拖拽到 GitHub 上传区域
5. 下拉到底部，点 **Commit changes**（提交信息可随意填，比如 `publish blog`）

## 第 3 步：开启 GitHub Pages

1. 进入仓库页面 → 点击 **Settings**（设置）
2. 左侧菜单找到 **Pages**
3. 在 **Build and deployment** 下：
   - Source 选择 **Deploy from a branch**
   - Branch 选择 **main**，文件夹选 **/ (root)**
4. 点击 **Save**

## 第 4 步：等待并访问

1. 保存后，GitHub 会自动开始构建，通常 **1~3 分钟**完成
2. 等页面出现绿色的 “Your site is live at ...” 提示
3. 在浏览器打开：

```
https://你的用户名.github.io
```

把上面这个地址发给朋友，他们就能访问你的博客了！

## 以后更新文章

每次写完新文章后，重复两步：

```bash
node build.js          # 1. 重新生成静态文件
```

然后去 GitHub 仓库 → **Add file → Upload files** → 重新上传 `dist/` 里改动过的文件 → **Commit changes**，等 1 分钟即可生效。

> 小技巧：也可以在仓库页面直接点 **Add file → Upload files**，把 `dist/` 里新增/改动的文件单独传上去，不用全部重传。

## 常见问题

- **访问 404**：仓库名必须严格是 `用户名.github.io`；或 Pages 构建还没完成（等 1-3 分钟再刷新）。
- **样式丢了**：确认 `style.css` 和 `favicon.svg` 上传到了仓库根目录（和 `index.html` 同级）。
- **想用自定义域名**：在 Pages 设置里填域名，并按提示在域名服务商加一条 CNAME 记录。
