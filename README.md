
# XH-AI-Float-Assistant

一款轻量级的网页智能助手浮窗，集成AI服务，支持前端一行代码快速接入及高度自定义。采用现代化的设计风格，支持完整的状态管理和本地缓存。

## ✨ 功能特性

### 🎯 核心功能
- 🪟 **智能浮窗**: 悬浮助手一键开启/关闭/全屏/最小化
- 🖼️ **人性化交互**: 窗口拖拽、缩放、双击最小化、Windows风格按钮
- 🎨 **多主题支持**: 5种内置主题(默认/蓝色/绿色/紫色/暗色) + 自定义主题
- � **智能缓存**: 完整的状态管理和本地存储，刷新页面保持状态
- ⌨️ **快捷键操作**: 全局快捷键支持，提升操作效率
- 📱 **响应式设计**: 自适应不同设备和屏幕尺寸

### �🛠️ 技术特性  
- 🚀 **纯前端**: 无需后端配置，即插即用
- 🔧 **丰富API**: 完整的控制方法和事件系统
- 📎 **灵活嵌入**: 支持任意网页/AI对话平台嵌入
- �️ **高度自定义**: 支持外观、行为、功能的深度定制
- � **轻量级**: 压缩后仅约50KB，加载快速
- 🔒 **安全可靠**: 客户端存储，数据隐私保护

## 🚀 快速开始

### 1. 下载核心文件

将 [floating-assistant.js](./public/floating-assistant.js) 文件部署到你的服务器。

### 2. 基础接入

在 `<body>` 末尾插入以下代码：

```html
<script src="./floating-assistant.js"></script>
<script>
  // 基础配置 - 系统会自动初始化
  window.FLOATING_ASSISTANT_CONFIG = {
    iframeUrl: "https://tongyi.aliyun.com", // AI助手URL
    title: "XH智能助手",
    iconText: "XH",
    width: 400,
    height: 600
  };
</script>
```

### 3. 高级接入（编程控制）

```html
<script src="./floating-assistant.js"></script>
<script>
  // 高级配置
  const assistant = window.FloatingAssistant;
  
  // 初始化配置
  assistant.init({
    iframeUrl: "https://your-ai-platform.com",
    title: "智能助手",
    iconText: "AI", 
    theme: "blue",
    width: 450,
    height: 650,
    minWidth: 320,
    minHeight: 200
  });
  
  // 手动控制
  assistant.show();        // 显示助手
  assistant.hide();        // 隐藏助手
  assistant.fullscreen();  // 全屏模式
  assistant.minimize();    // 最小化
</script>
```

## ⚙️ 配置参数

### 基础配置
| 参数名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| `iframeUrl` | string | 'https://tongyi.aliyun.com' | 内嵌页面URL |
| `title` | string | 'XH智能助手' | 窗口标题 |
| `iconText` | string | 'XH' | 最小化图标文字 |
| `width` | number | 400 | 初始宽度(px) |
| `height` | number | 600 | 初始高度(px) |
| `minWidth` | number | 300 | 最小宽度(px) |
| `minHeight` | number | 200 | 最小高度(px) |
| `minimizedSize` | number | 60 | 最小化时的大小(px) |
| `zIndex` | number | 999999 | 层级 |
| `animationDuration` | number | 300 | 动画持续时间(ms) |
| `storageKey` | string | 'floating-assistant-prefs' | 本地存储键名 |

### 主题配置
| 主题名 | 说明 | 主色调 |
|--------|------|--------|
| `default` | 默认主题 | 紫蓝渐变 |
| `blue` | 蓝色主题 | 天蓝色系 |
| `green` | 绿色主题 | 翠绿色系 |
| `purple` | 紫色主题 | 紫罗兰色系 |
| `dark` | 暗色主题 | 深灰色系 |

### 高级配置
```javascript
window.FLOATING_ASSISTANT_CONFIG = {
  // 自定义主题
  themes: {
    custom: {
      primary: '#ff6b6b',
      secondary: '#4ecdc4', 
      accent: '#45b7d1',
      text: '#ffffff'
    }
  },
  // 其他配置...
};
```

## 🎮 API方法

### 基础控制
```javascript
const FA = window.FloatingAssistant;

// 显示控制
FA.show();                    // 显示助手
FA.hide();                    // 隐藏助手
FA.toggle();                  // 切换显示/隐藏

// 窗口状态
FA.minimize();                // 最小化
FA.restore();                 // 恢复窗口
FA.fullscreen();              // 进入全屏
FA.exitFullscreen();          // 退出全屏

// 主题控制
FA.setTheme('blue');          // 设置主题
FA.cycleTheme();              // 循环切换主题

// 生命周期
FA.destroy();                 // 销毁助手
```

### 状态管理API
```javascript
// 本地存储管理
FA.saveCurrentState();        // 保存当前状态
FA.getPreferences();          // 获取所有偏好设置
FA.setPreference(key, value); // 设置单个偏好
FA.getPreference(key);        // 获取单个偏好
FA.resetSettings();           // 重置为默认设置

// 自动保存
FA.enableAutoSave(30000);     // 启用自动保存(30秒间隔)
FA.disableAutoSave();         // 禁用自动保存

// 导入导出
FA.exportSettings();          // 导出设置为JSON
FA.importSettings(jsonString); // 从JSON导入设置
FA.getStorageInfo();          // 获取存储使用情况
```

### 配置管理
```javascript
// 动态配置
FA.config({
  iframeUrl: 'https://new-url.com',
  title: '新标题',
  theme: 'dark'
});

// 获取当前配置
const currentConfig = FA.config();

// 检查状态
FA.isAuthorized();            // 检查授权状态
```

## ⌨️ 快捷键操作

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + Shift + H` | 切换显示/隐藏 |
| `Ctrl + Shift + M` | 最小化/恢复 |
| `Ctrl + Shift + F` | 切换全屏模式 |
| `Ctrl + Shift + T` | 切换主题 |
| `Ctrl + Shift + X` | 关闭助手 |
| `ESC` | 退出全屏(仅全屏时) |

## 🎨 界面特性

### 现代化设计
- **Windows风格按钮**: 简洁的SVG图标，直观的操作反馈
- **玻璃拟态效果**: 半透明背景，毛玻璃模糊效果
- **流畅动画**: 自然的缩放、渐变和移动动画
- **响应式布局**: 自适应不同屏幕尺寸

### 交互体验
- **智能拖拽**: 标题栏拖拽移动，边界自动吸附
- **双击操作**: 双击标题栏快速最小化/恢复
- **悬停反馈**: 按钮悬停时的视觉反馈
- **状态记忆**: 自动保存窗口位置、大小、主题等状态

## 💾 本地缓存功能

### 自动保存状态
- ✅ 窗口位置和大小
- ✅ 显示/隐藏状态  
- ✅ 最小化/全屏状态
- ✅ 当前主题设置
- ✅ 用户偏好配置
- ✅ 最后操作时间

### 缓存管理
```javascript
// 监听保存事件
window.addEventListener('floatingAssistantSave', (event) => {
  console.log('状态已保存:', event.detail.data);
});

// 手动操作缓存
FA.saveCurrentState();           // 立即保存当前状态
FA.enableAutoSave(10000);        // 10秒间隔自动保存
FA.resetSettings();              // 清除所有缓存，恢复默认

// 导入导出配置
const settings = FA.exportSettings();  // 导出配置
FA.importSettings(settings);           // 导入配置
```

## 🛠️ 高级使用

### 事件监听
```javascript
// 监听助手状态变化
window.addEventListener('floatingAssistantSave', (event) => {
  const { data, timestamp } = event.detail;
  console.log('助手状态更新:', data);
});

// 自定义初始化
document.addEventListener('DOMContentLoaded', () => {
  window.FloatingAssistant.init({
    iframeUrl: 'https://your-service.com',
    autoRestore: true,        // 自动恢复上次状态
    rememberState: true,      // 记住用户偏好
    animationsEnabled: true   // 启用动画效果
  });
});
```

### 自定义主题
```javascript
// 扩展主题
window.FLOATING_ASSISTANT_CONFIG = {
  themes: {
    // 自定义主题
    custom: {
      primary: '#ff6b6b',     // 主色
      secondary: '#4ecdc4',   // 辅色  
      accent: '#45b7d1',      // 强调色
      text: '#ffffff'         // 文字色
    },
    // 企业主题
    enterprise: {
      primary: '#2c3e50',
      secondary: '#34495e', 
      accent: '#3498db',
      text: '#ecf0f1'
    }
  }
};

// 应用自定义主题
window.FloatingAssistant.setTheme('custom');
```

### 多实例管理
```javascript
// 创建多个助手实例(不推荐，但支持)
const assistant1 = window.FloatingAssistant;
assistant1.init({ iframeUrl: 'https://service1.com' });

// 配置第二个实例
window.FLOATING_ASSISTANT_CONFIG = {
  storageKey: 'assistant-2-prefs', // 使用不同的存储键
  zIndex: 1000000
};
```

## 📱 兼容性

### 浏览器支持
- ✅ Chrome 70+
- ✅ Firefox 65+  
- ✅ Safari 12+
- ✅ Edge 79+
- ✅ 移动端浏览器

### 设备支持
- 🖥️ 桌面端: 完整功能
- 📱 移动端: 自适应布局，触摸优化
- 📟 平板: 响应式界面

## 🔧 开发指南

### 本地开发
```bash
# 克隆项目
git clone https://github.com/your-repo/xh-ai-float-assistant.git
cd xh-ai-float-assistant

# 安装依赖
pnpm install

# 开发模式
pnpm dev

# 构建项目
pnpm build
```

### 项目结构
```
xh-ai-float-assistant/
├── public/
│   └── floating-assistant.js    # 生产版本
├── src/
│   ├── floating-assistant.js    # 源代码
│   ├── pages/Home.tsx           # 演示页面
│   └── test-storage.html        # 功能测试页面
├── scripts/
│   └── build-simple.mjs         # 构建脚本
└── README.md
```

### 自定义构建
```javascript
// 修改 scripts/build-simple.mjs
export default {
  entryPoints: ['src/floating-assistant.js'],
  bundle: true,
  minify: true,
  outfile: 'public/floating-assistant.js'
};
```

## 🚀 使用案例

### 基础示例
```html
<!DOCTYPE html>
<html>
<head>
    <title>AI助手示例</title>
</head>
<body>
    <h1>我的网站</h1>
    <p>这是网站的主要内容...</p>
    
    <!-- 引入浮窗助手 -->
    <script src="./floating-assistant.js"></script>
    <script>
        // 最简配置
        window.FLOATING_ASSISTANT_CONFIG = {
            iframeUrl: "https://tongyi.aliyun.com",
            title: "AI助手"
        };
    </script>
</body>
</html>
```

### 进阶示例
```html
<script src="./floating-assistant.js"></script>
<script>
    // 高级配置示例
    const assistant = window.FloatingAssistant;
    
    assistant.init({
        iframeUrl: "https://your-ai-chatbot.com",
        title: "智能客服",
        iconText: "CS",
        theme: "blue",
        width: 480,
        height: 680
    });

    // 程序化控制
    document.getElementById('show-btn').onclick = () => assistant.show();
    document.getElementById('hide-btn').onclick = () => assistant.hide();
    document.getElementById('fullscreen-btn').onclick = () => assistant.fullscreen();
</script>
```

## 📝 更新日志

### v1.2.0 (2025-01-24)
- ✨ 新增完整的本地缓存系统
- 🎨 优化Windows风格按钮设计  
- ⌨️ 完善快捷键功能(`Ctrl+Shift+F`等)
- 🐛 修复全屏功能问题
- 📚 完善API文档和使用说明

### v1.1.0 
- ✨ 新增多主题支持
- 🎮 增加快捷键操作
- 💾 实现状态持久化
- 🎨 UI界面优化

### v1.0.0
- 🎉 首个稳定版本发布
- ✨ 基础浮窗功能
- 🛠️ 完整API支持

## ❓ 常见问题

### Q: 全屏功能不工作？
A: 请确保使用正确的快捷键 `Ctrl+Shift+F`，或通过API调用 `FloatingAssistant.fullscreen()`

### Q: 状态没有保存？
A: 检查浏览器是否支持localStorage，或手动调用 `FloatingAssistant.saveCurrentState()`

### Q: 主题设置失效？
A: 确认主题名称正确，支持的主题: `default`, `blue`, `green`, `purple`, `dark`

### Q: iframe内容无法显示？
A: 检查目标网站的 X-Frame-Options 设置，确保允许iframe嵌入

## 📄 许可证

MIT License - 详见 [LICENSE](./LICENSE) 文件

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 📞 支持

- 📧 邮箱: info@xhaotech.cn

---

<div align="center">
  <p>由 <strong>小浩科技</strong> ❤️ 开发维护</p>
  <p>⭐ 如果这个项目对你有帮助，请给一个星标支持！</p>
</div>
