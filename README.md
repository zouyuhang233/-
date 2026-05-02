# 登山背包智能监测系统

一个基于Web技术的登山队实时监测系统，通过3D可视化展示成员状态，提供实时数据监控和报警功能。

## 🎯 项目简介

本项目旨在为登山活动提供智能化的队员状态监测解决方案。系统通过集成多种传感器数据，实时监控队员的生命体征、环境数据和位置信息，及时发现潜在危险并报警。

### 核心功能

- **实时数据监控** - 监测队员温度、湿度、心率、电池电量等
- **3D可视化展示** - 交互式3D背包模型展示
- **成员详情查看** - 点击队员卡片查看详细参数
- **智能报警系统** - 摔倒、溺水、坠崖、间距过大等危险预警
- **响应式设计** - 支持PC、平板、手机等多种设备

## 🛠️ 技术栈

### 前端技术
- **HTML5** - 页面结构
- **CSS3** - 样式和动画效果
- **JavaScript (ES6+)** - 业务逻辑
- **Three.js** - 3D图形渲染

### 设计特点
- 现代化UI设计，深色主题
- 流畅的动画和过渡效果
- 响应式布局，适配各种屏幕
- 粒子背景效果增强视觉体验

## 📱 界面展示

### 主要布局
- **左侧面板** - 实时概览和成员列表
- **中间区域** - 3D背包模型展示
- **右侧面板** - 系统状态和报警日志

### 关键组件

#### 1. 成员监测卡片
```
[成员姓名] · [角色]
温度: 8.5°C   |   湿度: 72%   |   位置: 海拔3200m
[状态指示灯]
```

#### 2. 3D模型交互
- 鼠标拖拽：360度旋转查看
- 滚轮缩放：放大缩小模型
- 自动旋转：停止操作后自动恢复

#### 3. 详情面板
点击任意成员卡片弹出详细信息：
- 实时温度、湿度
- 心率、电池电量
- 位置信息
- 状态评估

## 🚨 报警系统

### 支持的报警类型
1. **摔倒检测** - 检测到异常姿态时触发
2. **溺水风险** - 检测到水下环境时触发
3. **坠崖预警** - 检测到悬崖边缘时触发
4. **间距过大** - 成员间距离超过安全阈值时触发

### 报警等级
- 🔴 **严重报警** - 需要立即处理的生命危险
- 🟠 **预警** - 潜在风险提醒

## 📊 数据监控

### 环境参数
- 温度范围：-20°C ~ 50°C
- 湿度范围：0% ~ 100%
- 采样频率：3秒

### 生理指标
- 心率范围：50 ~ 120 bpm
- 电池电量实时显示

### 位置信息
- 海拔高度实时更新
- GPS定位精度显示

## 🚀 快速开始

### 本地运行
1. 克隆项目
```bash
git clone https://github.com/zouyuhang233/-.git
cd backpack-dashboard
```

2. 打开页面
```bash
# 直接在浏览器中打开 index.html
# 或使用本地服务器
python -m http.server 8000
# 然后访问 http://localhost:8000
```

### 系统要求
- 现代浏览器（Chrome、Firefox、Safari、Edge）
- 支持WebGL的图形卡
- 网络连接（加载Three.js库）

## 📁 项目结构

```
backpack-dashboard/
├── index.html      # 主页面文件
├── .gitignore      # Git忽略规则
└── README.md       # 项目文档
```

## 🔧 开发说明

### 模拟数据
当前使用模拟数据进行展示，实际部署时需要：

1. **API接口集成**
   ```javascript
   // 替换 MOCK_DATA 为真实API调用
   const API_ENDPOINT = 'https://your-api.com/members';
   
   async function fetchMembers() {
     const response = await fetch(API_ENDPOINT);
     return await response.json();
   }
   ```

2. **WebSocket实时更新**
   ```javascript
   // 建立WebSocket连接
   const ws = new WebSocket('wss://your-server.com');
   ws.onmessage = (event) => {
     updateRealtimeData(JSON.parse(event.data));
   };
   ```

3. **传感器数据格式**
   ```javascript
   {
     id: 1,
     name: "队员姓名",
     temperature: 36.5,
     humidity: 65,
     heartRate: 75,
     battery: 85,
     location: "GPS坐标",
     alarm: false,
     alarmType: "报警类型"
   }
   ```

## 🎨 自定义配置

### 主题颜色
```css
/* 在CSS中修改颜色变量 */
:root {
  --primary-color: #00b4ff;
  --secondary-color: #00ffd5;
  --warning-color: #ffa502;
  --danger-color: #ff4757;
}
```

### 3D模型参数
```javascript
// 调整模型大小和位置
const camera = new THREE.PerspectiveCamera(35, width / height, 0.1, 1000);
camera.position.set(0, 0.5, 4);
```

## 📱 移动端适配

系统已针对移动设备进行优化：
- 触摸手势支持
- 响应式布局调整
- 侧边栏折叠功能
- 优化的字体大小

### 媒体查询
- `@media (max-width: 768px)` - 平板设备
- `@media (max-width: 480px)` - 手机设备

## 🔒 安全注意事项

1. **数据安全**
   - 所有敏感数据应通过HTTPS传输
   - 实施适当的认证和授权机制

2. **性能优化**
   - 限制并发连接数
   - 实施数据缓存策略
   - 定期清理旧数据

3. **隐私保护**
   - 遵循相关隐私法规
   - 提供数据加密选项

## 🤝 贡献指南

欢迎提交Issue和Pull Request来改进项目！

### 开发流程
1. Fork 项目
2. 创建功能分支
3. 提交更改
4. 推送到分支
5. 创建Pull Request

### 代码规范
- 使用ES6+语法
- 保持代码风格一致
- 添加必要的注释
- 确保代码可测试

## 📄 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 📞 联系方式

如有问题或建议，请通过以下方式联系：

- GitHub Issues: [提交问题](https://github.com/zouyuhang233/-/issues)
- Email: [您的邮箱]

---

**注意**：这是一个演示项目，实际部署前需要进行充分的测试和安全评估。
