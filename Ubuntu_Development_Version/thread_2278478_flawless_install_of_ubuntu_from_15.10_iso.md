---
title: "flawless install of ubuntu from 15.10 iso"
date: 2015-05-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-05-16
Did a hard install of ubuntu unity from MAY10/2015/daily and it is flawless. No systemd errors.

```


ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 1.686s (kernel) + 8.339s (userspace) = 10.025s
ventrical@ventrical-System-Product-Name:~$ 



```

```

ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-17-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 4004 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (6.1% used)
Info:      Processes: 168 Uptime: 14 min Memory: 608.2/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ 


```



just a bit slower boot but negligible .

upstart still an option (was it gone and then came back ?)

Regards..

---

