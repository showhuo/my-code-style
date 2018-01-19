## Prettier 升级指南

### prettier 是做什么的？
> prettier 是一个代码格式化工具

### 为什么要引入 prettier？

即使在最严格的 lint 规则下，我们写出来的代码风格仍然可能是各式各样的，有了 prettier ，同样的一份代码的输出呈现将是一致的。这保证了代码的可读性，尤其是多人维护一个项目时，不用熟悉别人的风格，因为大家的风格都是一致的。

### 集成方式

初期考虑的集成方式是做到`precommit`或者`prepush`中，但是可能提交以后会发现和提交时代码不一致的变动，考虑到大家的***安全感***，决定将 prettier 集成到 lint 规则当中，这样在文件未提交的时候，基于 `eslint` 大家就可以直观的发现哪些是不符合代码格式规范的，做到心中有数。

### 如何升级
- 安装依赖项：使用 Airbnb 规范的话请先参看它们的[文档](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)

  `npm install prettier eslint-config-prettier eslint-plugin-prettier --save-dev`

- 修改`.eslintrc`文件

  react项目
  ```js
  {
    "extends": ["airbnb", "prettier"],
    "plugins": ["prettier"],
    "rules": {
      "prettier/prettier": [
        "error",
        {
          "printWidth": 100,
          "semi": false,
          "singleQuote": true
        }
      ]
    }
  }
  ```
  rn项目
  ```js
  {
    "extends": ["airbnb", "prettier"],
    "plugins": ["prettier"],
    "rules": {
      "prettier/prettier": [
        "error",
        {
          "printWidth": 100,
          "semi": false,
          "singleQuote": true
        }
      ]
    }
  }
  ```
- 批量处理

  `npm run eslint . --fix --format codeframe`

  ***友情提示***：批量处理时可能会有较多的文件变动，虽然 prettier 只会对代码格式进行变更，不会修改你的代码逻辑，但是出于谨慎，建议大家还是看一下每个文件变动了哪些，做到心中有数。

### 编辑器集成
- 安装 Prettier 扩展
- 安装 ESLint 扩展
- 打开 vscode 设置文件
  增加如下配置

  ```js
  "editor.formatOnSave": true,
  "prettier.eslintIntegration": true
  ```