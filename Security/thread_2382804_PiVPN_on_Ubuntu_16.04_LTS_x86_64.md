---
title: "PiVPN on Ubuntu 16.04 LTS x86_64"
date: 2018-01-17
forum: Security
---

### Post by JayCroghan on 2018-01-17
So, I'm trying to follow the easiest setup for OpenVPN on my VPS. I tried installing it manually, it worked and my client could connect but no internet worked. I'm in China anyway so when I saw a guide on installing with Obfsproxy I thought why not it seems easy.

Anyway, I get to installed pivpn (I know it's for Pi but it's just an installer for OpenVPN) and when it comes to selecting my IP I get:

: error fetching interface information: Device not found
: error fetching interface information: Device not found


So I tried running lspci and that also doesn't work. Here is my output from ifconfig -a and maybe explains why OpenVPN didn't work in the first place? There's no eth0?

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: 2a04:ad80:1:110::d453/64 Scope:Global
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:130535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:190830531 (190.8 MB)  TX bytes:1421725 (1.4 MB)


venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:176.126.245.30  P-t-P:176.126.245.30  Bcast:176.126.245.30  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
```


Any help would be gratefully appreciated.

---

### Post by CharlesA on 2018-01-17
Most VPSes don't call it eth0 anymore. On yours it is called venet0.

I doubt this will help, but I used [this script]("https://github.com/Nyr/openvpn-install") to set up my OpenVPN server a long while back. So far it has been pretty rock solid.

---

