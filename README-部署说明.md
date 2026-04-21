# QS1000 Firebase 真在线版（Vercel 部署包）

这个包已经可以直接部署到 Vercel。  
核心入口文件是 `index.html`，前端会从页面顶部读取：

```html
window.__QS1000_FIREBASE_CONFIG = {
  apiKey: "REPLACE_ME",
  authDomain: "REPLACE_ME",
  projectId: "REPLACE_ME",
  storageBucket: "REPLACE_ME",
  messagingSenderId: "REPLACE_ME",
  appId: "REPLACE_ME"
};
```

## 部署前先做 4 件事

### 1. 创建 Firebase 项目
在 Firebase Console 创建项目，并开启：

- Authentication → Email/Password
- Firestore Database
- Storage

### 2. 替换 Firebase 配置
打开 `index.html`，搜索：

`window.__QS1000_FIREBASE_CONFIG`

把里面的 `REPLACE_ME` 全部换成你自己的 Firebase Web 配置。

### 3. 部署 Firebase 规则
把本包里的：
- `firestore.rules`
- `storage.rules`

部署到你的 Firebase 项目。

### 4. 再部署到 Vercel
你可以二选一：

#### 方式 A：网页拖拽上传
1. 登录 Vercel
2. 新建 Project
3. 直接上传这个文件夹

#### 方式 B：GitHub 部署
1. 把整个文件夹上传到 GitHub 仓库
2. 在 Vercel 导入这个仓库
3. Framework 选择 `Other`
4. Output 不用额外设置

## Firebase Hosting 和 Vercel 的分工
- **Vercel**：负责网站访问入口
- **Firebase Auth / Firestore / Storage**：负责登录、数据库、文件上传

## 上线后建议先测试
- 注册
- 登录
- 发布动态
- 上传图片 / 视频
- 聊天
- 刷新页面后数据是否还在
- 两个不同设备能否互通

## 注意
这一版是“保留原 UI + 数据层改成 Firebase 优先”的上线包。  
适合先上线验证功能，但管理员权限、复杂规则、直播推流等还建议继续工程化升级。
