---
title: "libertine-bug: recycles back to install screen"
date: 2016-08-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-31
Libertine recycles back to install screen while creating container in background.

```


ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.4.0-25-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.5.0 (Gtk 3.20.6-1ubuntu1) Distro: Ubuntu 16.10
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 12.0.1 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-25-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (13.1% used)
           ID-1: /dev/sda model: WDC_WD800HLFS size: 80.0GB temp: 30C
Partition: ID-1: / size: 71G used: 6.9G (11%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.01GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.0C mobo: 37.0C gpu: 39.0
           Fan Speeds (in rpm): cpu: 4272 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 241 Uptime: 1:37 Memory: 1028.6/3007.8MB
           Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.0 
ventrical@ventrical-System-Product-Name:

```

[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1618979](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1618979)

---

### Post by ventrical on 2016-08-31
libertine bug (of same) reported by apport.



[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1618985](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1618985)

---

### Post by ventrical on 2016-08-31
these bugs are dups. Fix commited.

[https://bugs.launchpad.net/libertine/+bug/1615697](https://bugs.launchpad.net/libertine/+bug/1615697)

---

