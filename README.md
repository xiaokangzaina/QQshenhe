# QQshenhe 群消息内容安全审核插件

基于 OpenAI 兼容接口的 AstrBot 群聊消息安全审核插件。

## v1.5.0 重大UI更新

- 更换插件头像/logo 为新的“插电”头像。
- 自带前端升级为控制台风格 UI。
- 审核群组列表顶部新增群配置、已启用、未启用统计。
- 修复审核群组搜索框图标错位和底部大面积空白问题。
- 修复页面主题偏好未持久化的问题。
- 右侧配置栏加入蓝紫青粉渐变混色渲染。
- 修复右侧配置页面折叠卡住的问题。
- 新增后端主题保存接口：`POST /astrbot_plugin_group_aip_review/settings/theme`。

## 功能

- 文本消息审核
- 图片消息审核
- 分群独立配置
- 自定义审核提示词
- 违规消息撤回
- 达阈值禁言
- 达最终阈值直接踢出
- 禁言次数踢出
- 通知群提醒
- 疑似违规简化通知
- 配置页面备注名显示

## 安装

将插件目录放入 AstrBot：

```text
data/plugins/astrbot_plugin_group_aip_review
```

然后重载插件或重启 AstrBot。

## 基础配置

在插件配置页填写 OpenAI 兼容接口信息：

```json
{
  "base_url": "https://example.com/v1",
  "api_key": "",
  "model": "gpt-4o-mini",
  "timeout": 30,
  "audit_prompt": ""
}
```

> 发布版本不会包含任何真实 API Key、群号、用户 ID 或 Token。

## 分群配置

每个群可独立配置：

- 是否启用审核
- 通知群号
- 文本/图片审核开关
- 禁言阈值
- 禁言时长
- 禁言次数踢出阈值
- 违规次数踢出阈值
- 是否踢出并拉黑
- 群级审核提示词
- 备注名

## 处罚逻辑

```text
合规：不处理
疑似违规：发送简化通知
不合规：撤回消息，并按阈值执行禁言或踢出
```

当本次违规达到最终踢出阈值时：

```text
直接踢出，不再执行禁言
```

## 维护者

```text
xiaokangzaina
```

仓库：

```text
https://github.com/xiaokangzaina/QQshenhe
```
