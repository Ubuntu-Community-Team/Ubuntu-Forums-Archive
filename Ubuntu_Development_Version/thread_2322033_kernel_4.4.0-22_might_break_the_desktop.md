---
title: "kernel 4.4.0-22 might break the desktop"
date: 2016-04-25
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-04-25
UTC 1:15    Heads up

Just upgraded and received kernel 4.4.0-22. On restart the login screen was low resolution and with login bounce. Using Nvidia driver 340.96. Video adapter not supported by newer Nvidia drivers. I got a system error message during the installation of the new kernel. It was to do with the Nvidia driver.

Recovery mode>Resume did not change anything but loading into the previous kernel 4.4.0-21 works fine. 

Regards

Progress: Reverted to Nouveau and I am now running on kernel 4.4.0-22. Next step to purge the Nvidia driver and re-install it to see if that fixes it.

Going backwards. Purging & re-installing Nvidia did not work. In fact it made things worse as the 2 previous kernel now became affected in the same way. Had to purge Nvidia from recovery mode. That loaded to a desktop on llvmpipe in low resolution mode. But a restart brought things up as normal on Nouveau (Gallium 0.4)

I tested Nvidia 304.131 and it failed to build. So, much excitement so early in the development cycle. There ought to be a law against it.

---

### Post by dino99 on 2016-04-26
Get it with an old q9550 intel cpu
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1574838](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1574838)  Bug #1574982

Installing 4.4.0-22 on xenial is fine; only yakkety is affected, due to the recent gcc-5/gcc-6 updates

---

### Post by cfbauer2 on 2016-04-26
I'm experiencing the same login bounce issue, 4.4.0-22 and4.4.0-21 are both giving me trouble. 4.2.0-36 appears to work. I'm running the 361.42 nvidia driver.

edit: Running Ubuntu Gnome 16.04

---

### Post by jimmy-frydkaer on 2016-04-26
Just upgraded my yakkety with kernel 4.4.0.22 on my Lenovo Ideapad 100 without any issues

---

### Post by grahammechanical on 2016-04-26
> Installing 4.4.0-22 on xenial is fine; only yakkety is affected, due to the recent gcc-5/gcc-6 updates

That is interesting. I might experiment again tomorrow after updating. Or wait until there is another kernel upgrade. Not that I need Nvidia drivers.

---

### Post by dino99 on 2016-04-26
@Jimmy

This affect systems with nvidia cards/chipsets and also virtualbox

---

### Post by ventrical on 2016-04-29
> **grahammechanical said:**
> UTC 1:15    Heads up

Just upgraded and received kernel 4.4.0-22. On restart the login screen was low resolution and with login bounce. Using Nvidia driver 340.96. Video adapter not supported by newer Nvidia drivers. I got a system error message during the installation of the new kernel. It was to do with the Nvidia driver.

Recovery mode>Resume did not change anything but loading into the previous kernel 4.4.0-21 works fine. 

Regards

Progress: Reverted to Nouveau and I am now running on kernel 4.4.0-22. Next step to purge the Nvidia driver and re-install it to see if that fixes it.

Going backwards. Purging & re-installing Nvidia did not work. In fact it made things worse as the 2 previous kernel now became affected in the same way. Had to purge Nvidia from recovery mode. That loaded to a desktop on llvmpipe in low resolution mode. But a restart brought things up as normal on Nouveau (Gallium 0.4)

I tested Nvidia 304.131 and it failed to build. So, much excitement so early in the development cycle. There ought to be a law against it.

yes . thats exactly it. kernel is as kernel does :)

regards..

---

### Post by ventrical on 2016-04-30
I put  a new card in and installed nVidia proprietary. It installed but it kept booting to nouveau. I removed nouveau and it kept booting to nouveau??? So there is problems with nVidia drivers atm and kernel too.

regards..

---

### Post by ventrical on 2016-04-30
Removed nVida drivers and still cannot get rid of (unloaded fbdev) FAILED pointer.

[CODE]
ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 4.4.0-22-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.4 Distro: Ubuntu 16.10 yakkety
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 2995 MHz (max)
Graphics:  Card: NVIDIA GF119 [GeForce GT 610]
           Display Server: X.Org 1.18.3 drivers: vesa (unloaded: fbdev) FAILED: nouveau
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.2.0
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 80.0GB (16.7% used)
Info:      Processes: 215 Uptime: 0 min Memory: 670.3/1999.8MB
           Client: Shell (bash) inxi: 2.2.35 
ventrical@ventrical-MS-7850:~$ 

[CODE]

---

