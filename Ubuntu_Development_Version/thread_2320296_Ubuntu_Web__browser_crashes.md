---
title: "Ubuntu Web  browser crashes"
date: 2016-04-12
forum: Ubuntu Development Version
---

### Post by viljeml on 2016-04-12
Ubuntu Web  browser crashes with Nvidia proprietary drivers

---

### Post by grahammechanical on 2016-04-12
It also crashes with Nouveau. In fact it blinks out of existence as soon as it begins to appear on the desktop.

 About 18 months ago I was using Browser daily and enjoying the improvements being made from being a browser for a phone to being a browser for the desktop. But for a year now it crashes.

There have been many updates both to Ubuntu Web Browser and to Oxide and the web containers that are all part of this but no improvement in Browser not crashing. At the moment it is crashing with SIGABRT in QmessageLogger.

Regards.

---

### Post by ventrical on 2016-04-12
Works ok here on intel graphics.

---

### Post by ventrical on 2016-04-12
Also works on my ..

```

ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 4.4.0-18-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 2995 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 11.2.0
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (11.3% used)
Info:      Processes: 228 Uptime: 2 min Memory: 967.7/1999.8MB
           Client: Shell (bash) inxi: 2.2.35 
ventrical@ventrical-MS-7850:~$ 

```

---

