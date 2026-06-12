---
title: "Screen flickering issue in Ubuntu 17.10"
date: 2018-05-25
forum: Virtualisation
---

### Post by saurabh412 on 2018-05-25
I've been using Ubuntu 17.10 for some time now, today suddenly my screen started flickering and I can see  frame drops. Restarting my PC doesn't solve the problem. I have a HP  Pavilion ab032tx, dual booted with Windows 10.The problem does not  appear in when using Windows. Thanks in advance!

Some specs about my pc

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"


Linux pirateking-HP-Pavilion-Notebook 4.13.0-43-generic #48-Ubuntu SMP Wed May 16 12:18:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 5500 [8086:1616] (rev 09)
    Subsystem: Hewlett-Packard Company HD Graphics 5500 [103c:8096]
    Kernel driver in use: i915

DESKTOP_AUTOSTART_ID=10586682c361fef67a152724131970580800000027710008
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

---

### Post by cruzer001 on 2018-05-25
Is it the same as this?

[https://ubuntuforums.org/showthread.php?t=2392716](https://ubuntuforums.org/showthread.php?t=2392716)

---

### Post by saurabh412 on 2018-05-25
Yes, the effects are the same. But it happens regardless of I'm scaling a window horizontally. Additionally I'm using 0SX-Arc theme and the effects are worse when I'm using the Dark or shadow theme, but disappears for full screen when using White theme (But still persists when not using a full screen), infact it goes for any theme. For light variants full screen works fine but nothing works fine when using dark themes. Will it help if I also take a video of it and post it on youtube?

---

### Post by saurabh412 on 2018-05-25
Here is my output for inxi -b just in case,

System:    Host: pirateking-HP-Pavilion-Notebook Kernel: 4.13.0-43-generic x86_64
           bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion Notebook v: Type1ProductConfigId serial: N/A
           Mobo: Hewlett-Packard model: 8096 v: 89.11 serial: N/A
           UEFI [Legacy]: Insyde v: F.21 date: 06/05/2015
Battery    BAT0: charge: 28.9 Wh 100.0% condition: 28.9/28.9 Wh (100%)
CPU:       Dual core Intel Core i5-5200U (-HT-MCP-)
           speed/max: 2499/2700 MHz
Graphics:  Card-1: Intel HD Graphics 5500
           Card-2: NVIDIA GM108M [GeForce 940M]
           Display Server: wayland (X.Org 1.19.5 ) drivers: i915,nouveau
           Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           version: 4.5 Mesa 17.2.8
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be
           Card-2: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
Drives:    HDD Total Size: 1000.2GB (7.6% used)
Info:      Processes: 281 Uptime: 4:46 Memory: 3467.2/7906.1MB
           Client: Shell (bash) inxi: 2.3.37

---

### Post by cruzer001 on 2018-05-25
Your running Wayland, try switching to Xorg.  May be the solution.

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

