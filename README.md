## mihomo for router only

说明：

1. with_gvisor (GVisor 网络栈模块)
当前状态：❌ 构建中被剔除
功能：集成由 Google 开发的 GVisor 用户态协议栈。它主要用于接管基于 TUN 的底层流量。
路由器用途：极低。路由器通常使用内核层面的 iptables（Tproxy / Redirect）。GVisor非常吃CPU和内存，且体积巨大。


2. no_tailscale (Tailscale 节点模块)
当前状态：❌ 构建中被剔除
功能：将 Mihomo 直接注册为 Tailscale 虚拟局域网中的一个节点，支持走 Tailscale 的专属内网协议。
路由器用途：极低。路由器上的代理主要是用来科学上网，如果需要 Tailscale，通常会直接在路由器上安装官方的 Tailscale 插件，而不是让代理软件去兼职处理。

3. no_fake_tcp (Fake TCP 伪装模块)
当前状态：❌ 构建中被剔除
功能：用来将代理的底层 UDP 数据包强行套上 TCP 的包头，从而骗过国内宽带运营商针对 UDP 协议的限速或丢包（QoS）。
路由器用途：较低。绝大多数科学上网协议（Vmess, Trojan, SS）默认就是走常规 TCP 或者像 Hysteria/TUIC 等有自身抗封锁机制的 UDP。路由器用户极少会用到原生的 Fake TCP 功能。

4. cmfa (Android 安卓专属模块)
当前状态：❌ 构建中被剔除
功能：Clash Meta For Android 的缩写。包含为了适配安卓系统的 VPN Service、后台保活、安卓专属界面通讯等代码。
路由器用途：完全无用。这是专为安卓手机 App 准备的。

5. with_low_memory (低内存优化模块)
当前状态：✅ 构建中被强制启用。
功能：这是用来做加法的优化标签。一旦开启，它会调整 Mihomo 内部的内存分配策略，强行缩小并发时的缓存区大小和堆栈预留内存。
路由器用途：极高。这是专为 RAM 只有 256MB 或 512MB 的路由器和 IoT 弱电设备量身定制的救命功能。
