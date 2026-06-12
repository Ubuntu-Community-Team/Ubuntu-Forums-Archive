---
title: "Daily ISO"
date: 2018-08-31
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-08-31
Installed the iso from 31/8.

The snap problem is still not solved. The file /var/lib/snapd/seed/seed.yaml still has "gtk-common-themes" in the wrong place and "[COLOR=#000000][FONT=&amp]Initialize system state" [/FONT][/COLOR]is in "doing state".
The Nvidia driver didn't install properly. When I started in "Recovery Mode" and used "Fix dependencies" I got the info
```
Your python install is corrupted
Please fix the /usr/bin/python' symlink
```

---

### Post by P-I H on 2018-09-01
Enabled propose, updated and installed nvidia v: 396.54.
Turned off the computer and booted with the Nvidia driver. Was OK and Chromium worked again.
```
p-i@pi-GA-990FXA-UD3:~$ inxi -F
System:
  Host: pi-GA-990FXA-UD3 Kernel: 4.18.0-7-generic x86_64 bits: 64 
  Desktop: Gnome 3.29.90 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x 
  serial: <root required> BIOS: Award v: F5 date: 10/13/2011 
CPU:
  Topology: 8-Core model: AMD FX-8120 bits: 64 type: MCP L2 cache: 2048 KiB 
  Speed: 1492 MHz min/max: 1400/4000 MHz Core speeds (MHz): 1: 1517 2: 1434 
  3: 1453 4: 1420 5: 1452 6: 1500 7: 1565 8: 1415 
Graphics:
  Device-1: NVIDIA GK106 [GeForce GTX 660] driver: nvidia v: 396.54 
  Display: x11 server: X.Org 1.20.1 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 660/PCIe/SSE2 v: 4.6.0 NVIDIA 396.54 
Audio:
  Device-1: AMD SBx00 Azalia driver: snd_hda_intel 
  Device-2: NVIDIA GK106 HDMI Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-7-generic 
Network:
  Device-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 
  802.11bgn] 
  driver: ath9k 
  IF: wlp3s0 state: down mac: 00:21:91:0b:5f:11 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp5s0 state: up speed: 1000 Mbps duplex: full mac: 50:e5:49:3e:75:3a 
Drives:
  Local Storage: total: 819.75 GiB used: 8.92 GiB (1.1%) 
  ID-1: /dev/sda vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
  ID-2: /dev/sdb vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
  ID-3: /dev/sdc vendor: Western Digital model: WD6400AAKS-00A7B0 
  size: 596.17 GiB 
Partition:
  ID-1: / size: 109.53 GiB used: 8.92 GiB (8.1%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 25.8 C mobo: N/A gpu: nvidia temp: 39 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 30% 
Info:
  Processes: 277 Uptime: N/A Memory: 7.77 GiB used: 1.10 GiB (14.2%) 
  Shell: bash inxi: 3.0.22 
p-i@pi-GA-990FXA-UD3:~$

```

---

