---
title: "Skylake and 16.04"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by fjgaude on 2016-03-29
The pair works good right now but for the fact the video HDMI doesn't work, only DisplayPort does. That works for me, but curious. Audio is fine, all else is also. I'm Intel all the way,  no games.

```
frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.4.0-040400rc5-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P1.50 date: 11/04/2015
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed/max: 799/3700 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel Skylake DT GT2
           GLX Version: 3.0 Mesa 11.0.7frank@flash:~$ inxi -b
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: wl
Drives:    HDD Total Size: 756.2GB (33.7% used)
Info:      Processes: 244 Uptime: 0 min Memory: 606.7/15736.5MB
           Client: Shell (bash) inxi: 2.2.35 
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: bcma-pci-bridge
Drives:    HDD Total Size: 756.2GB (32.1% used)
Info:      Processes: 250 Uptime: 1 min Memory: 615.2/15736.5MB
           Client: Shell (bash) inxi: 2.2.28

```

Here's a much later scan:

```
frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.4.0-15-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P2.00 date: 03/01/2016
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed: 3700 MHz (max)
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.18.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.1.2
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: wl
Drives:    HDD Total Size: 756.2GB (33.7% used)
Info:      Processes: 244 Uptime: 0 min Memory: 606.7/15736.5MB
           Client: Shell (bash) inxi: 2.2.35
``` 
---
No issues with WiFi or LAN.

---

