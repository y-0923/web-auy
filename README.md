# 个人课程练习与工具集成平台

这是一个基于Next.js构建的Web应用，整合了个人课程练习展示、WakaTime编码时长统计和QAnything智能问答服务。

## 项目概述

本项目使用Next.js框架，结合HTML、CSS、JavaScript和React技术，实现了以下核心功能：
- 课程练习展示：以组件化方式组织和展示所有课程练习
- 编码时长统计：通过WakaTime API获取并展示个人编码时长数据
- 智能问答服务：通过iframe嵌入QAnything提供的问答界面

## QAnything集成路径

**选择路径**：基础路径（HTML页面嵌入）

**实现细节**：
- 在`/qanything`路由下创建专用页面
- 使用iframe元素直接嵌入QAnything官方网站：`https://qanything.ai/`
- 设置iframe样式使其占满容器，提供良好的用户体验
- 优点：实现简单快捷，无需处理复杂的API交互和认证
- 缺点：对界面样式和交互的自定义程度有限

## WakaTime API集成

1. **API Key安全管理**
   - 在项目根目录创建`.env.local`文件存储API密钥
   - 使用Next.js环境变量机制保护敏感信息
   - API密钥格式：`WAKATIME_API_KEY=your_api_key_here`

2. **数据获取实现**
   - 创建API路由：`app/api/wakatime/route.js`
   - 使用axios库发起HTTP请求
   - 对API响应进行处理，转换为小时和分钟格式

3. **前端展示**
   - 创建全局Footer组件：`components/Footer.jsx`
   - 使用React hooks获取并展示数据
   - 实现错误处理和加载状态

## Next.js项目结构

```
/app
  /api                # API路由
    /wakatime
      route.js        # WakaTime数据接口
  /exercises          # 课程练习页面
    page.tsx          # 练习导航页
  /qanything          # QAnything集成页面
    page.tsx          # 包含iframe的页面
  layout.tsx          # 根布局组件
  page.tsx            # 首页
/components
  Footer.jsx          # 页脚组件（含WakaTime统计）
.env.local            # 环境变量配置
```

## 课程练习整合方式

1. 在`/app/exercises`目录下为每个练习创建独立路由
2. 使用Next.js的App Router实现路由管理
3. 在练习导航页（`/exercises`）提供所有练习的链接入口
4. 采用组件化开发思想，将重复UI元素抽象为可复用组件

## 项目运行指南

### 前提条件
- Node.js 18.x或更高版本
- npm包管理器
- WakaTime API密钥

### 安装步骤

1. 克隆本仓库
```bash
git clone <your-github-repo-url>
cd <project-directory>
```

2. 安装依赖
```bash
npm install
```

3. 配置环境变量
创建`.env.local`文件并添加：
```
WAKATIME_API_KEY=your_wakatime_api_key
```

4. 启动开发服务器
```bash
npm run dev
```

5. 在浏览器中访问
```
http://localhost:3000
```

## 运行截图

### QAnything运行截图
[详情看截图文件夹](screenshots/qanything.png)

### WakaTime API集成与展示截图
[详情看截图文件夹](screenshots/wakatime.png)

### 课程练习作业组织截图
[详情看截图文件夹](screenshots/exercise.png) 
