---
title: "Videos in Firefox playing like forward 2x mode and no sound"
date: 2016-12-06
forum: Ubuntu Studio
---

### Post by mgundogdu on 2016-12-06
Hi,
I newly installed UbuntuStudio, I made a little search and I found killed pulse audio and re-start pulseaudio; but this didn't solve my problem.
When I open youtube, vimeo videos they playing fast mode and no sound, thanks in advance.
```
Kernel: 4.4.0-52-lowlatency x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: Acer (portable) product: Aspire 5738 v: 0100
           Mobo: Acer model: JV50 v: Rev
           Bios: Phoenix v: V1.21 date: 10/23/2009
CPU:       Dual core Intel Core2 Duo P7370 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 7980
           clock speeds: max: 2001 MHz 1: 2001 MHz 2: 1600 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.11hz
           GLX Renderer: Gallium 0.4 on AMD RV710 (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-52-lowlatency
Network:   Card-1: Broadcom NetLink BCM5784M Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Intel WiFi Link 5100 driver: iwlwifi bus-ID: 04:00.0
           IF: wlp4s0 state: up mac: <filter>
Drives:    HDD Total Size: 320.1GB (41.0% used)
           ID-1: /dev/sda model: WDC_WD3200BEVT size: 320.1GB temp: 55C
Partition: ID-1: / size: 24G used: 8.4G (38%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 32G used: 4.0G (14%) fs: ext4 dev: /dev/sda1
           ID-3: swap-1 size: 4.29GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: 53.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 205 Uptime: 46 min Memory: 852.2/3947.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 


```

---

### Post by mgundogdu on 2016-12-07
I changed Radeon settings to Build-in Audio Analog Stereo and problem solved.

[IMG]https://s15.postimg.org/hgko4wvzv/ses_sorunu.png[/IMG]

---

