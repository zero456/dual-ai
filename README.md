# 双 AI 协作系统

Dual AI 是一个创新的 AI 聊天应用，通过两个性格迥异的 AI 代理（Cognito 逻辑引擎
和 Muse 创意引擎）之间的内部辩论与协作，为用户提供更准确、更全面的答案。

## 核心特点

- 双 AI 辩证系统：用户提问触发两个 AI 的协作讨论
- 共享记事本：两个 AI 可以共同编辑和使用的工作区
- 思考模型支持：原生集成 Google Gemini 2.5/3.0 系列的深度思考能力
- 多后端兼容：支持 Google Gemini 和 OpenAI 兼容接口（DeepSeek、Ollama 等）
- 现代化 UI：基于 React 19 构建，响应式设计，移动端友好

## 技术栈

```
核心框架：
├── React 19.1.0          # 最新的 React 版本
├── TypeScript 5.8.2      # 类型安全
├── Vite 6.2.0           # 构建工具
└── Tailwind CSS         # 样式框架（通过 CDN）

AI 集成：
├── @google/genai 1.0.1  # Google Gemini SDK
└── OpenAI Compatible    # 支持 OpenAI 兼容接口

UI 组件：
├── lucide-react 0.511.0 # 图标库
├── marked 13.0.2        # Markdown 渲染
├── dompurify 3.1.6      # XSS 防护
├── katex 0.16.10        # 数学公式渲染
└── diff 5.2.0           # 文本差异对比
```

## 项目结构

```
dual-ai/
├── components/          # React 组件
│   ├── AlertBanner.tsx
│   ├── AppSettingsDialog.tsx
│   ├── ChatInput.tsx
│   ├── ChatPanel.tsx
│   ├── Header.tsx
│   ├── MessageBubble.tsx
│   ├── ModelSelector.tsx
│   ├── Notepad.tsx
│   ├── ResizeHandle.tsx
│   ├── SettingsModal.tsx
│   └── settings/       # 设置相关子组件
│
├── hooks/              # 自定义 Hooks（业务逻辑）
│   ├── useAppController.ts    # 主控制器
│   ├── useAppUI.ts            # UI 状态管理
│   ├── useChatLogic.ts        # 聊天逻辑
│   ├── useChatProcessing.ts   # 聊天处理流程
│   ├── useChatState.ts        # 聊天状态
│   ├── useDiscussionLoop.ts   # 讨论循环逻辑
│   ├── useNotepadLogic.ts     # 记事本逻辑
│   ├── useRetryLogic.ts       # 重试逻辑
│   ├── useSettings.ts         # 设置管理
│   └── useStepExecutor.ts     # 步骤执行器
│
├── services/           # AI 服务层
│   ├── geminiService.ts       # Google Gemini API
│   └── openaiService.ts       # OpenAI 兼容 API
│
├── utils/              # 工具函数
│   ├── aiResponseParser.ts    # AI 响应解析
│   ├── appUtils.ts            # 应用工具
│   ├── commonUtils.ts         # 通用工具
│   ├── markdownUtils.ts       # Markdown 工具
│   ├── messageUtils.ts        # 消息工具
│   ├── notepadUtils.ts        # 记事本工具
│   └── promptBuilder.ts       # 提示词构建
│
├── App.tsx             # 主应用组件
├── index.tsx           # 入口文件
├── index.html          # HTML 模板
├── types.ts            # TypeScript 类型定义
├── constants.ts        # 常量配置
├── vite.config.ts      # Vite 配置
└── tsconfig.json       # TypeScript 配置
```

## 数据持久化

使用 `localStorage` 存储：

- 聊天消息历史
- 记事本内容
- API 配置（Key、Endpoint）
- 模型选择
- 思考配置
- 讨论模式设置

## 本地部署

### 1. 环境要求

- Node.js v18+
- npm 或 yarn

### 2. 安装项目

```bash
git clone https://github.com/zero456/dual-ai.git
cd dual-ai
npm install
```

### 3. 配置 API Key (可选)

- 为了方便开发，您可以在根目录创建 `.env.local` 文件
- 也可以稍后在网页 UI 中设置）：

```env
GEMINI_API_KEY="AIzaSy..."
```

### 4. 启动开发服务器

```bash
npm run dev
```

访问终端显示的地址（通常为 `http://localhost:3000`）。

## Cloudflare pages 部署

- 主页 `Workers 和 Pages`
- `创建应用程序`
- 选择底部：`Looking to deploy Pages? Get started`
- `导入现有 Git 存储库`，`开始使用`
- `选择存储库`，`开始设置`
- `构建命令`：`npm run build`
- `构建输出目录`：`dist`
- `保存并部署`
