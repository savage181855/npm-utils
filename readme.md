# rollup-ts

使用`rollup`打包`ts`库的模板。

# 使用说明

## 开发环境

```
yarn dev
```

## 生产环境

```
yarn build

```

## 本地调试

在当前目录下执行

```
npm link
```

进入`example`目录执行

注意：`example`目录需要安装依赖

```
npm link roullup-ts
```

说明：开发环境会检测文件改动并重新打包，生产环境会开启混淆。


## 其他问题

### 为什么开发环境rollup不使用 watch 选项来进行热更新

在多模块开发的时候，使用watch监听文件，被修改的文件，通过watch监听重新编辑的dist，将会丢失该文件的dts文件，无法解决这个bug。
所以使用`nodemon`进行监听并执行`rollup`命令来进行热更新

### 问题

每次src编译之后，example的 link 就会丢失，需要在 根目录重新进行 npx link

link 丢失的原因是  del dist目录，不要del就行


考虑写一个 rollup 插件 进行解决 每次npm-lib都需要重复的config文件，以及手动更新重复安装依赖，考虑写一个插件预设，直接通过包就进行更新打包配置

一个 rollup plugin，在包构建好之后再进入 example 目录执行 npx link 并执行 example的入口文件