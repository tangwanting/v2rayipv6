# v2rayipv6

三、VPS设置IPV4访问
注：这篇文章是以Debian9为例子来安装，你可以重新安装一下系统

          1. SSH连接到你的VPS，还不会SSH连接的看上期文章

输入下面代码修改nameserver

 echo -e "nameserver 2001:67c:2b0::4•\nnameserver 2001:67c:2b0::6" > /etc/resolv.conf
安装Curl

 apt-get update -y && apt-get install curl -y
v2ray一键安装代码

 source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh
安装完成自动生成的是V2ray+TCP这种模式，如果你支持IPV6地址，你就可以用客户端软件上网了

四、修改v2ray

因为还有很多没有IPV6地址的朋友，所以我们还要修改v2ray让IPV4可以访问，

SSH连接后我们输入v2ray回车就会显示中文的控制面板

V2ray控制面板

选择3 更改配置，进入到另一个界面

 修改配置

再选11，输入你的域名，

选择1、443端口

选择1、Let Encrypt生成证书

等待证书申请完成

生成完成后会回到管理主界面

选择4、查看配置就会生成vmess链接

五、常用命令
 v2ray [-h|--help] [options]
     -h, --help           查看帮助
     -v, --version        查看版本号
     start                启动 V2Ray
     stop                 停止 V2Ray
     restart              重启 V2Ray
     status               查看 V2Ray 运行状态
     new                  重建新的v2ray json配置文件
     update               更新 V2Ray 到最新Release版本
     update.sh            更新 multi-v2ray 到最新版本
     add                  新增mkcp + 随机一种 (srtp|wechat-video|utp|dtls|wireguard) header伪装的端口(Group)
     add [wechat|utp|srtp|dtls|wireguard|socks|mtproto|ss]     新增一种协议的组，端口随机,如 v2ray add utp 为新增utp协议
     del                  删除端口组
     info                 查看配置
     port                 修改端口
     tls                  修改tls
     tfo                  修改tcpFastOpen
     stream               修改传输协议
     cdn                  走cdn
     stats                v2ray流量统计
     iptables             iptables流量统计
     clean                清理日志
     log                  查看日志
六、VPS增加SWAP（不需要）

1
wget https://www.moerats.com/usr/shell/swap.sh && bash swap.sh
