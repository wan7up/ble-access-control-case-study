# 发布前脱敏清单

## 必须删除

- 账号、手机号、姓名、住址和小区名称。
- 服务器 IP、域名、端口和 SSH 信息。
- URL 中的 Token、Cookie、签名和授权码。
- 设备 MAC、序列号、蓝牙名称和门栋/门厅名称。
- APK、IPA、证书、私钥、mitmproxy CA 和抓包原件。
- 门禁钥匙列表、挑战响应密钥和可运行的协议实现。
- 服务器日志、浏览器本地存储和完整截图。

## 可以保留

- 抽象后的流程图。
- 脱敏后的时间线和相对耗时。
- 不可执行的伪代码。
- 通用的 mitmproxy 配置思路。
- Web Bluetooth API 的公开概念。
- 测试设计、失败分类和性能取舍。

## 发布前检查

```sh
rg -n -i 'token|cookie|authorization|password|secret|private|mac|ssh|\\.apk|\\.pcap|\\.har' .
git diff --cached --check
git ls-files
```

命中关键词后应逐项确认是否为占位符、通用说明或真实敏感材料。不要因为文件名看起来普通，就把原始日志或配置加入提交。
