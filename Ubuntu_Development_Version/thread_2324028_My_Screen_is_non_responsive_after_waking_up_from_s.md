---
title: "My Screen is non responsive after waking up from sleep"
date: 2016-05-10
forum: Ubuntu Development Version
---

### Post by danc-dccathome on 2016-05-10
After my computer goes to sleep and I wake it back up.
I can't click on anything and I have dual monitors and the mouse won't go to the other monitor.
All I can do is hit Ctrl-Alt-F1 and login and reboot.
```
dcihon@dcihon-ubuntu-testing:~$ inxi -Fxx
System:    Host: dcihon-ubuntu-testing Kernel: 4.4.0-22-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3) dm: lightdm Distro: Ubuntu 16.10 yakkety
Machine:   Mobo: ASUSTeK model: M3A78-EM v: Rev X.0x Bios: American Megatrends v: 2003 date: 10/12/2009
CPU:       Dual core AMD Athlon 64 X2 6000+ (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 svm) bmips: 4021 
           clock speeds: min/max: 1000/3000 MHz 1: 1000 MHz 2: 1000 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0 chip-ID: 10de:104a
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.2.1 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 chip-ID: 10de:0e08
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2 chip-ID: 1002:4383
           Card-3 Logitech Webcam C270 driver: USB Audio usb-ID: 001-002 chip-ID: 046d:0825
           Sound: Advanced Linux Sound Architecture v: k4.4.0-22-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0 chip-ID: 10ec:8168
           IF: enp3s0 state: down mac: 00:22:15:2c:76:9b
           Card-2: Ralink RT2561/RT61 802.11g PCI driver: rt61pci v: 2.3.0 bus-ID: 04:07.0 chip-ID: 1814:0301
           IF: wlp4s7 state: up mac: 00:1d:7d:7a:df:04
Drives:    HDD Total Size: 1500.3GB (29.9% used)
           ID-1: /dev/sda model: WDC_WD5000AAKS size: 500.1GB serial: WD-WCAS85254785 temp: 31C
           ID-2: /dev/sdb model: ST31000528AS size: 1000.2GB serial: 5VP96E76 temp: 34C
Partition: ID-1: / size: 29G used: 5.4G (20%) fs: ext4 dev: /dev/sdb2
           ID-2: /home size: 883G used: 408G (49%) fs: ext4 dev: /dev/sdb5
           ID-3: swap-1 size: 5.24GB used: 0.00GB (0%) fs: swap dev: /dev/sdb3
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 41.0C mobo: 38.0C gpu: 42.0
           Fan Speeds (in rpm): cpu: 2547 psu: 0 sys-1: 0
Info:      Processes: 242 Uptime: 6 min Memory: 1100.3/5965.3MB
           Init: systemd v: 229 runlevel: 5 default: 2 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421 running in gnome-terminal-) inxi: 2.2.35 
d
```

---

### Post by ventrical on 2016-05-10
Have you tried to roll back to a previous kernel or is this a fresh install?

Regards..

---

### Post by danc-dccathome on 2016-05-10
Kernel just upgraded yesterday and I haven't put the computer to sleep yet.
I am going to try that now and see what happens.

---

### Post by danc-dccathome on 2016-05-10
I just did a suspend and it returned normally.
I will not let it go to sleep on its own and see what happens.

---

### Post by danc-dccathome on 2016-05-10
Seems to be working.
Maybe a false alarm. Or some other update fixed it.
Hope its fixed for good.
If not I will make another post.

---

