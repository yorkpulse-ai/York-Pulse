# YorkPulse 🌐

> University of York Campus Community Platform

**Live site:** [theyorkpulse.uk](https://theyorkpulse.uk)

---

## 🏢 Corporate Governance

- **Parent Company:** Pulse Core Labs Ltd
- **UK Company Number:** 17103683
- **Primary Website:** [theyorkpulse.uk](https://theyorkpulse.uk)

---

## ⚖️ Intellectual Property Notice

The core source code, behavior-driven algorithms (Karma Engine), and proprietary data schemas are the exclusive property of **Pulse Core Labs Ltd**. All technical assets have been formally assigned to the corporate entity via the *IP Assignment Agreement dated 19 March 2026*.

Access to the private development repositories is restricted to authorized contributors only.

---

## 项目简介

YorkPulse 是为约克大学学生打造的校园社区平台，提供实时公交追踪、校园论坛、商城、图书馆签到、排行榜等功能，并配套完整的后台管理系统。

---

## 技术栈

| 层级 | 技术 |
|------|------|
| 后端 | Python · Flask · Flask-SocketIO · SQLAlchemy |
| 数据库 | SQLite |
| 前端 | Vanilla JS · HTML · CSS |
| 实时通信 | Socket.IO（WebSocket） |
| 邮件服务 | SMTP · Gmail |
| 部署 | VPS · theyorkpulse.uk |

---

## 功能模块

### 👤 用户系统
- 邮箱注册（OTP 验证码）+ 邀请码机制
- 用户名 / 邮箱登录
- Karma 积分体系（贡献值 / 财富值 / 月度排行）
- 等级系统（Lv.1 - Lv.21）
- VIP 会员 / 首充礼包
- 个人 Avatar 商店
- 信任分 / 经验值 / 社交贡献点

### 🏠 主页
- 实时 Live Feed
- 快速排行榜预览
- 动态首页模块（管理员可配置）
- 每日提示

### 🚌 公交系统（Bus）
- 实时公交追踪（官方 BODS 数据源）
- 用户 GPS 上报增强（Gold Bus）
- 多路线 / 多车辆支持
- Socket.IO 实时推送

### 💬 论坛（Forum）
- 帖子发布 / 回复
- Karma 奖励机制

### 🛍️ 商城（Shop）
- Avatar 身份购买
- 优惠票券（10% off · BOGO 饮品）
- VIP 会员购买
- 首充礼包

### 📚 图书馆（Library）
- LBS 地理围栏签到（JB Morrell 图书馆）
- 图书馆帖子 / 评论 Feed
- 签到奖励 Karma + EXP

### 🏆 排行榜（Rankings）
- 财富榜（Whales）
- 贡献榜（Heroes）
- 月度活跃榜
- 前 10 名自动获得月度 VIP

### 👤 个人主页（Profile）
- 用户信息展示
- Karma 分类统计
- Avatar 装备管理
- 邀请码 / 邀请记录

### 📢 商家活动（Campaign）
- 商家优惠发布
- 活动详情页
- 优惠券领取

### 📝 反馈系统（Feedback）
- Bug 反馈 / 功能建议
- 商家反馈

### ⚙️ 管理后台（Admin）
- 用户管理（角色 / 封禁 / Karma 调整）
- 商家活动管理（发布 / 编辑 / 下架）
- 优惠票券管理
- 首页模块管理
- 系统数据看板

---

## 项目结构

```
yorkpulse/
├── app.py                          # Flask 主程序 + 所有 API 路由
├── data/
│   ├── york_all_routes.json        # 公交路线数据
│   ├── library_posts.json          # 图书馆帖子
│   ├── library_comments.json       # 图书馆评论
│   ├── home_modules.json           # 首页模块配置
│   └── campaigns.json              # 商家活动数据
├── instance/
│   └── pulse_data.db               # SQLite 数据库
├── static/
│   ├── css/style.css
│   └── js/
│       ├── app-shell.js
│       ├── page-home.js
│       ├── page-bus.js
│       ├── page-forum.js
│       ├── page-shop.js
│       ├── page-library.js
│       ├── page-rankings.js
│       ├── page-profile.js
│       ├── page-campaign.js
│       ├── page-merchant.js
│       ├── page-admin.js
│       └── page-admin-dashboard.js
└── templates/
    ├── index.html
    ├── home.html
    ├── bus.html
    ├── forum.html
    ├── shop.html
    ├── library.html
    ├── rankings.html
    ├── profile.html
    ├── campaign.html
    ├── merchant.html
    ├── feedback.html
    ├── admin.html
    └── admin-dashboard.html
```

---

## 主要 API 端点

| 端点 | 方法 | 说明 |
|------|------|------|
| `/login` | POST | 登录 |
| `/logout` | POST | 退出 |
| `/send_code` | POST | 发送邮箱验证码 |
| `/api/register` | POST | 注册 |
| `/api/me` | GET | 获取当前用户信息 |
| `/api/daily_checkin` | POST | 每日签到 |
| `/api/bus/routes` | GET | 获取公交路线列表 |
| `/api/bus/route/<n>` | GET | 获取路线详情 |
| `/api/bus/report` | POST | 上报 GPS 位置 |
| `/api/forum/posts` | GET | 获取论坛帖子 |
| `/api/rankings` | GET | 获取排行榜数据 |
| `/api/avatar_store` | GET | 获取 Avatar 商店 |
| `/api/avatar_purchase` | POST | 购买 Avatar |
| `/api/campaigns` | GET | 获取活动列表 |
| `/api/feedback` | POST | 提交反馈 |

---

## Karma 积分体系

| 类型 | 说明 |
|------|------|
| `contribution_karma` | 通过参与行为获得（签到、发帖等） |
| `wealth_karma` | 通过充值 / 邀请 VIP 获得 |
| `total_karma` | 当前余额（用于消费） |
| `karma_monthly` | 月度排行分 |
| `experience` | 经验值（影响等级） |
| `trust_score` | 信任分（初始 100） |

---

## 相关仓库

- 📱 Android / iOS App：[YorkPulse-android-app](https://github.com/yorkpulse-ai/YorkPulse-android-app)

---

## 部署

```bash
pip install -r requirements.txt
python app.py
```

环境变量：

```
YORKPULSE_SECRET_KEY=your_secret_key
YORKPULSE_SENDER_EMAIL=your@gmail.com
YORKPULSE_SENDER_PASSWORD=your_app_password
DEBUG_RETURN_OTP=0
```

---

*© 2026 Pulse Core Labs Ltd. All rights reserved.*
