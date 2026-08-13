# digua-ui-registry

迪瓜项目的 shadcn/ui 组件注册表。

## 使用方式

### 1. 在项目中添加命名空间

在项目的 `components.json` 中配置：

```json
{
  "registries": {
    "@digua": "https://qiuruijie.github.io/digua-ui-registry/{name}.json"
  }
}
```

### 2. 安装组件

```bash
npx shadcn@latest add @digua/button
npx shadcn@latest add @digua/toast
```

## 可用组件

| 组件 | 安装命令 | 说明 |
|---|---|---|
| Button | `@digua/button` | 自定义按钮组件 |
| Toast | `@digua/toast` | Toast 通知组件（依赖 `@base-ui/react`、`lucide-react`） |

## 开发

### 添加新组件

1. 在 `registry/default/<组件名>/` 下创建组件文件
2. 在 `registry.json` 的 `items` 数组中添加条目
3. 运行 `npx shadcn@latest build` 构建
4. 提交推送，GitHub Actions 自动部署

### registry.json 示例

```json
{
  "name": "my-component",
  "type": "registry:ui",
  "title": "My Component",
  "description": "组件说明",
  "dependencies": ["some-npm-package"],
  "registryDependencies": ["button"],
  "files": [
    {
      "path": "registry/default/my-component/my-component.tsx",
      "type": "registry:ui"
    }
  ]
}
```

### 构建

```bash
npx shadcn@latest build
```

构建产物输出到 `public/r/` 目录，由 GitHub Pages 托管。

## 技术栈

- [shadcn/ui](https://ui.shadcn.com/docs/registry) - 组件注册表规范
- [GitHub Pages](https://pages.github.com/) - 静态文件托管
