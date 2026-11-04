# myagent-android

myagent 的手机端：任务跑了十分钟、卡在等你授权，而你已经不在电脑前——扫个码，在手机上看进度、批准操作、回答 plan 模式的计划确认。

它和终端界面一样**不跑 agent 逻辑**，只是 [myagent-Harness](https://github.com/wiles-agent/myagent-Harness) 的又一个客户端，
和终端连的是同一份会话（协议见后端仓库的 [docs/protocol.md](https://github.com/wiles-agent/myagent-Harness/blob/main/docs/protocol.md)）。

myagent 按端分仓库，都在 [wiles-agent](https://github.com/wiles-agent) 组织下：
[myagent-Harness](https://github.com/wiles-agent/myagent-Harness)（Java 后端）、
[myagent-tui](https://github.com/wiles-agent/myagent-tui)（终端界面）、本仓库（手机端）。

## 装上

要 Android Studio 或 Android SDK（minSdk 26）：

```bash
./gradlew installDebug        # 手机连着电脑、开了 USB 调试
./gradlew testDebugUnitTest   # 单元测试
```

## 连上

在电脑上用中继或局域网模式起 myagent，然后在终端界面里敲 `/qr`，用 app 扫码：

```bash
./myagent-tui --relay wss://relay.example.com/ws   # 任何网络都能连，中继只看得见密文
./myagent-tui --lan                                # 只在同一个局域网
```
