# 给基于 ubuntu18.04 的 Picgo 2.3.1 安装 picgo-plugin-s3 插件

## 安装 Node.js 17.9.1

首先，你需要安装 Node.js 17.9.1。你可以通过以下命令来下载预编译二进制可执行文件

为什么不安装最新的 Node.js 版本？

因为 Picgo 插件需要 Node.js 17.9.1 版本的支持。因为 Node.js 18.x 版本已经不再支持 Ubuntu18.04 了，别问我为啥知道。
- [recent v18.0.0 nightly builds require GLIBC_2.28](https://github.com/nodejs/node/issues/42351)

```bash
wget https://nodejs.org/dist/v17.9.1/node-v17.9.1-linux-x64.tar.xz
```

## 源码构建安装
### 拉取源码

```bash
git clone https://github.com/ruoxi521/picgo-plugin-s3.git
```

### 安装依赖

```bash
cd picgo-plugin-s3
npm install pnpm -g   # 推荐使用 pnpm 安装依赖
pnpm install
```

### 构建插件

```bash
npm run build
```

### 配置 Picgo

在 Picgo 的设置中，找到插件设置，选择导入本地插件，并启用插件。

- 如果遇到报错 npm ERR Cannot read properties of null (reading‘matches‘)

使用如下命令清理 npm 的缓存
```bash
npm cache verify 
```

如未能解决，直接删除 `node_modules`` 目录，并再次运行 
```bash
pnpm install
```
## 使用插件

在 Picgo 的图床设置中，找到 Amazon S3 插件设置，翻到最底，选择设置为默认图床。

## 常见问题

### 为什么我无法使用插件？

- 检查你的 Node.js 版本是否为 17.9.1。
- 检查你的 Picgo 版本是否为 2.3.1。
- 检查你的操作系统是否为 Ubuntu18.04。
- 检查你的插件是否正确安装和配置。

### 为什么我无法上传图片？

- 检查你的网络连接是否正常。
- 检查你的 S3 存储桶是否正确配置。
