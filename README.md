# fe-publish

使用 node-ssh 模块，实现一条命令，自动打包并将打包文件快速更新到服务器对应路径，可用于快速发布；支持错误回滚。

## 安装

```
npm i fe-publish
or
yarn add fe-publish
```

## 使用

在项目根目录下新建 dtstack.config.js，以 JSON 格式配置以下配置项:

- host 服务器 ip，必填
- user 登录用户名，必填
- sourcePath 本地包路径，选填、默认为`./dist`
- targetPath 映射文件路径，必填, targetPath 必须为真实已有的路径
- closeAutoBuild 是否需要关闭自动打包功能，选填，不传默认为 false

配置示例

```
{
  "host": "127.0.0.1",
  "user": "root",
  "sourcePath": "./dist",
  "targetPath": "/tmp/dist"
}
```

在项目中的 package.json 里添加 script

```
"scripts": {
  "pub": "fe-publish"
},
```

```
npm run pub
或
fe-publish
```

## 注意事项

targetPath 必须为一个真实路径，如/tmp/dist，必须要有 dist 这个目录
