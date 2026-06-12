---
title: "nvidia-304 and glmark2 segfault"
date: 2016-03-15
forum: Ubuntu Development Version
---

### Post by $yl9pAR%t on 2016-03-15
Running glmark2 with nvidia-304 gives me segmentation fault, there is no problem when I am using nouveau driver. I have got this result on Xubuntu 16.04 and Ubuntu 16.04 fallback w/metacity. Because of hardware limitation I cannot check it with Unity. This is not new problem, it exist at least since February 2016.

My system info:

```
Kernel: 4.4.0-13-generic x86_64 (64 bit)           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTek model: M2NPV-MX v: 1.xx
           Bios: Phoenix v: ASUS M2NPV-MX 0502 date: 10/17/2006
CPU:       Single core AMD Athlon 64 3500+ (-UP-) speed/max: 1000/2200 MHz
Graphics:  Card: NVIDIA C51PV [GeForce 6150]
           Display Server: X.Org 1.18.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1440x900@59.89hz
           GLX Renderer: GeForce 6150/integrated/SSE2
           GLX Version: 2.1.2 NVIDIA 304.131
Network:   Card: NVIDIA MCP51 Ethernet Controller driver: forcedeth
Drives:    HDD Total Size: 160.0GB (6.3% used)
Info:      Processes: 176 Uptime: 1:18 Memory: 753.3/2251.4MB
```

---

### Post by $yl9pAR%t on 2016-03-30
I see this bug was confirmed on Ubuntu 15.10 and it affects a few other nvidia gpu and drivers (not only 304).

[https://bugs.launchpad.net/ubuntu/+source/glmark2/+bug/1475902](https://bugs.launchpad.net/ubuntu/+source/glmark2/+bug/1475902)

---

### Post by ilias-utcpd on 2017-02-16
I fixed this issue according to [http://git.net/ml/ubuntu-bugs/2016-06/msg09689.html](http://git.net/ml/ubuntu-bugs/2016-06/msg09689.html)

However, no need to rebuild the glmark2 package; simple [COLOR=#373A3C][FONT=-apple-system]LD_PRELOAD=/lib/x86_64-linux-gnu/libpthread.so.0 /usr/bin/glmark2 helps.
[/FONT][/COLOR]

---

### Post by oldos2er on 2017-02-19
Old thread closed.

---

