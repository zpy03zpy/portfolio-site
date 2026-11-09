# John 的作品集网站 · 使用说明

- **线上地址：** <https://zpy03zpy.github.io/portfolio-site/>
- **代码仓库：** <https://github.com/zpy03zpy/portfolio-site>

一个**深色科技风**的单页作品集：首屏介绍 → 精选作品 → 关于我 → 联系方式。
背景是一层缓缓旋转的「环形尘埃」，纯 HTML + CSS + JavaScript 绘制，没有框架、没有依赖，**不用安装任何东西**。

---

## 一、先打开看看

在文件夹里**双击 `index.html`**，它会用你的浏览器打开。

- 建议用 Chrome / Edge / Safari 的较新版本。
- 手机上也能看，布局会自动变成单列。

## 二、文件结构

```
portfolio-site/
├── index.html      ← 整个网站（文字、样式、脚本都在这个文件里）
├── 404.html        ← 找不到页面时显示的页面
├── sitemap.xml     ← 给搜索引擎的页面清单
├── robots.txt      ← 告诉搜索引擎可以抓取什么
├── images/         ← 放项目封面图（现在可以先不管）
├── README.md       ← 你正在看的说明
└── preview-*.png   ← 预览截图，可以删
```

> 改之前，先把 `index.html` 复制一份备份，比如 `index-备份.html`。改坏了还能找回来。

---

## 三、改成你自己的（约 10 分钟）

用任意文本编辑器打开 `index.html`：Windows 用「记事本」或 VS Code，Mac 用「文本编辑」。
建议装免费的 **VS Code**，搜索和替换会方便很多。

### 1. 换名字

站里的名字已经换成 `John`。想换成别的，搜索 `John`，**全部替换**。
它会出现在：导航、首屏介绍、关于我、页脚、网页标题，以及 logo 的首字母 `J`。

### 2. 换首屏那句话

搜索 `把复杂的事`，改成你想说的话。例如：

```html
<h1>把复杂的事，<br>做得简单，<br><span class="grad">也好看。</span></h1>
```

- `<br>` 是换行，别删。
- `<span class="grad">…</span>` 里的字会显示成渐变色。

下面的自我介绍搜索 `我是 John` 修改。

### 3. 换邮箱

搜索 `3303295930@qq.com`，换成你的邮箱（两处：按钮链接和显示文字）。

### 4. 换作品（4 个项目）

每个作品卡片都有注释 `<!-- 项目 1 -->` 到 `<!-- 项目 4 -->`。以第一个为例：

```html
<a class="work-card reveal" href="#" data-demo="…" style="--c1:#22d3ee; --c2:#6366f1;">
  <div class="work-art">
    <span class="work-year">2026 · PRODUCT</span>
    <span class="work-index">01</span>
  </div>
  <div class="work-body">
    <div class="work-tags"><span>产品设计</span><span>前端</span></div>
    <h3>Aurora 数据看板</h3>
    <p>把 12 个分散指标，收进一屏就能读懂的界面。</p>
    <span class="work-link">查看项目 <span aria-hidden="true">↗</span></span>
  </div>
</a>
```

| 想改什么 | 改哪里 |
| --- | --- |
| 项目名 | `<h3>` 里的文字 |
| 一句话说明 | `<p>` 里的文字 |
| 分类标签 | `<span>产品设计</span>` 这类标签 |
| 年份 | `<span class="work-year">` 里的文字 |
| 点击去哪 | 把 `href="#"` 换成真实网址，例如 `href="https://example.com"` |

> **小提示**：链接还是 `#` 时，点击会弹出「概念项目」的提示，这是故意的。
> 换成真实网址后提示会自动消失，不用改别的。

#### 想换封面图？

1. 准备 4 张图，建议尺寸 **1600 × 1000**，JPG 格式，每张小于 300KB。
2. 命名为 `project-1.jpg`、`project-2.jpg`……放进 `images/` 文件夹。
3. 在 `index.html` 里找到 `有真实项目图时` 这段注释，把 `<img>` 那一行的注释符号 `<!--` 和 `-->` 删掉：

```html
<img src="images/project-1.jpg" alt="Aurora 数据看板项目封面">
```

`alt` 里写图片内容，方便搜索引擎和读屏软件理解。

### 5. 换「关于我」

搜索 `你好，我是 John`，改下面三段文字和技能标签。
右侧的 `profile.json` 也同步成了 AIGC 新人的信息，把里面的名字、城市、工具改成你的。

### 6. 换社交链接

GitHub 和 Bilibili 已经换成你的主页，点击会在新窗口打开：

- GitHub：`https://github.com/zpy03zpy`
- Bilibili：`https://space.bilibili.com/3690987675191907`

要改的话搜索对应地址，换成新的即可。想加别的平台，按同样的格式加一行：

```html
<a href="https://你的主页地址" target="_blank" rel="noopener noreferrer">平台名</a>
```

`target="_blank"` 表示新窗口打开，`rel="noopener noreferrer"` 是安全写法，建议保留。

### 7. 换配色

打开文件最上面的 `:root` 部分：

```css
--violet: #8b5cf6;   /* 紫 */
--cyan:   #22d3ee;   /* 青 */
--pink:   #f472b6;   /* 粉 */
```

改这三个色值，整站的渐变、光晕、强调色会一起变。
不会配色的话，可以去 [coolors.co](https://coolors.co) 找一组喜欢的颜色。

### 8. 背景动效（可选）

背景里那层缓慢旋转的「环形尘埃」是用原生 Canvas 画的（视觉参考 Ring Field），
没有引入 React、没有第三方库，也不需要 license key，双击 `index.html` 就能跑。

想调整的话，搜索 `环形尘埃背景`：

| 想改什么 | 找哪里 | 说明 |
| --- | --- | --- |
| 环的数量 | `var count = mobile ? 18 : 28` | 数字越大越密，低端设备可以再降到 14 / 20 |
| 尘埃数量 | `var n = Math.round(...)` | 每环的粒子数，太大可能卡 |
| 清晰度 / 性能 | `dpr = Math.min(...)` | 移动端 1.5、桌面 1.75；数字越小越省性能 |
| 波纹幅度 | `var amp1` / `var amp2` | 数字越大，环越“波浪” |
| 漂移速度 | `t * 0.011` | 改大一点转得快 |
| 环线亮度 | `fade * 0.16` | 改小更淡，改大更明显 |
| 点缀色 | `34,211,238` / `167,139,250` / `244,114,182` | 青 / 紫 / 粉，改成你喜欢的 RGB |

不想要这个动效：删掉 `<canvas class="ring-field" …>` 这一行即可，
背景的网格、光晕和噪点还会保留。系统开启「减少动态效果」时，它只画一帧静态图，不会动。

### 9. 404、sitemap 和 robots

- `404.html`：访问不存在的地址时显示。它有一个「回到首页」按钮，链接写死了线上地址；换域名时记得改。
- `sitemap.xml`：给搜索引擎的页面清单。换域名时把 `<loc>` 改掉。
- `robots.txt`：允许搜索引擎抓取，并指向 sitemap。
- 发布时这三个文件要和 `index.html` 一起上传，否则线上不会生效。

按 `Tab` 键时，页面左上角会出现「跳到主要内容」，这是给键盘用户的快捷入口，不用时可以不管。

### 10. 删掉不想要的板块

比如不想要「关于我」：

1. 搜索 `<!-- ==================== 关于 ==================== -->`，把整个 `<section … id="about">` 到 `</section>` 删掉。
2. 再把导航里的 `<a href="#about">关于</a>` 删掉。

页脚的联系方式是我额外加的（你只选了三个板块）。不需要的话，删掉 `<footer>…</footer>` 整段，或只改邮箱保留。

### 11. 看访问统计

本站接了 Umami Cloud 做匿名访问统计（无 Cookie，免费 Hobby 计划）。

- 打开 <https://cloud.umami.is>，登录后选择 `John Portfolio`。
- **Overview** 看总访问量、访客数、跳出率；**Realtime** 看当前在线；**Pages / Referrers / Countries / Devices** 看访问了哪些页面、从哪里来、用什么设备。
- 统计代码在 `index.html` 的 `</head>` 前，`data-website-id` 那串不要改；`data-domains="zpy03zpy.github.io"` 让本地预览和别的域名不上报。
- 广告拦截插件会拦掉一部分请求，所以后台数字通常比真实访问略低；404 页面也单独加了代码。

---

## 四、发布到网上（免费）

### 方案 A：Netlify Drop（最快，1 分钟）

1. 打开 <https://app.netlify.com/drop>。
2. 把整个 `portfolio-site` 文件夹拖进网页。
3. 等几秒，你会得到一个 `https://xxx.netlify.app` 的网址。
4. 以后想更新：改完文件，再拖一次文件夹（或注册账号绑定这个站点）。

> 优点：不用 Git、不用命令行。缺点：国内访问速度一般。

### 方案 B：GitHub Pages（免费、稳定、适合长期）

> 本站已经发布在 `zpy03zpy/portfolio-site`，网址是 <https://zpy03zpy.github.io/portfolio-site/>。
> 以后更新只需替换仓库里的 `index.html`（以及 `404.html` 等文件），Pages 会自动重建；下面是从零搭建的通用步骤。

1. 注册 <https://github.com>。
2. 右上角 **+ → New repository**：
   - 仓库名填 `你的用户名.github.io`（例如 `xiaolin.github.io`）
   - 选 **Public**
   - 点 **Create repository**
3. 点 **Add file → Upload files**，把 `index.html`、`404.html`、`sitemap.xml`、`robots.txt` 和 `images` 文件夹拖进去，点 **Commit changes**。
4. 进入仓库 **Settings → Pages**：
   - Source 选 **Deploy from a branch**
   - Branch 选 **main**，目录选 **/ (root)**，点 **Save**
5. 等 1–2 分钟，访问 `https://你的用户名.github.io`。

> 如果仓库名不是 `用户名.github.io`，网址会变成 `https://你的用户名.github.io/仓库名`，也能用。

### 方案 C：国内云静态托管（以后再说）

阿里云 OSS、腾讯云 COS 都支持静态网站托管，访问速度快，但**绑定自己的域名需要备案**。先用 A 或 B 上线，之后想升级再迁。

---

## 五、常见问题

**Q：图片不显示？**
检查三点：图片确实在 `images/` 文件夹里；文件名大小写完全一致（`Project-1.jpg` ≠ `project-1.jpg`）；`src` 路径写对。

**Q：字体和截图不一样？**
网站用的是电脑系统自带的字体，所以 Windows 和 Mac 上会略有差别，这是正常的，也保证离线能打开、加载快。想用特定字体可以引入 Google Fonts，但国内加载可能慢。

**Q：手机上排版乱了？**
先确认 `<meta name="viewport" …>` 那行没删。然后用浏览器开发者工具（F12）切到手机尺寸检查。

**Q：点击「查看项目」没反应？**
因为 `href` 还是 `#`，这是概念项目的状态。换成真实网址就好。

**Q：想加「下载简历」？**
把 PDF 放进文件夹，然后在按钮位置加：

```html
<a class="btn btn-ghost" href="resume.pdf" download>下载简历</a>
```

**Q：改坏了怎么办？**
用备份文件覆盖回来，或重新找我要一份。

---

## 六、接下来可以做的

- 把 4 个概念项目换成你**真正做过的东西**，每个写清「问题 → 我的做法 → 结果」。
- 给每个项目做单独的详情页（进阶，需要多几个 HTML 文件）。
- 加一个访问统计（Umami、Google Analytics）。
- 买一个自己的域名，比如 `yourname.com`。

有想改但不知道怎么下手的，直接告诉我，我可以继续帮你改。
