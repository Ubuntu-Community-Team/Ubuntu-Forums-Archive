---
title: "libre-office-writer erratic behaviour"
date: 2015-12-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-07
Brief details in bug description.

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1523650](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1523650)

---

### Post by sgage on 2015-12-07
> **ventrical said:**
> Brief details in bug description.

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1523650](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1523650)

When I try to open a pdf file in LO Writer, it comes up in LO Draw. Even if I say 'open with LO Writer'. That said, it seems to render flawlessly.

---

### Post by ventrical on 2015-12-07
> **sgage said:**
> When I try to open a pdf file in LO Writer, it comes up in LO Draw. Even if I say 'open with LO Writer'. That said, it seems to render flawlessly.

Yes... thats true .. but i was benchmarking this bug with an older machine .. maybe it is exclusive to older machines.

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity (Gtk 3.18.5-1ubuntu2) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5LD2 v: Rev 1.xx
           Bios: American Megatrends v: 0901 date: 12/15/2005
CPU:       Dual core Intel Pentium D (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3) bmips: 15326
           clock speeds: max: 3831 MHz 1: 3831 MHz 2: 3831 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 04:00.0
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel NM10/ICH7 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 04:00.1
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (8.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 54G used: 5.8G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.15GB used: 0.02GB (1%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.5C mobo: 38.0C gpu: 35.0
           Fan Speeds (in rpm): cpu: 4115 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 202 Uptime: 2:09 Memory: 940.2/2000.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by lonniehenry-gmail on 2015-12-07
Libreoffice opens pdf files in draw by default.  It handles pdfs as images.  They can be edited but it is kind of a piecemeal solution.  Writer files can be saved as pfd, but when you reopen them they will open in libreoffice draw. That is intended behavior.

---

### Post by sgage on 2015-12-07
Actually, that's quite similar to my machine:

```
sgage@xenial:~$ inxi -Fxz
System:    Host: xenial Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Gnome 3.18.2 (Gtk 3.18.5-1ubuntu2)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Compaq-Presario product: FJ379AA-ABA SR5518F
           Mobo: MSI model: Boston v: 1.0
           Bios: Phoenix v: 5.22 date: 05/07/2009
CPU:       Dual core Intel Pentium Dual E2180 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 ssse3) bmips: 7981
           clock speeds: max: 2000 MHz 1: 1600 MHz 2: 1600 MHz
Graphics:  Card: NVIDIA G86 [GeForce 8500 GT] bus-ID: 01:00.0
           Display Server: X.Org 1.17.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: GeForce 8500 GT/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 340.96 Direct Rendering: Yes

```

> **ventrical said:**
> Yes... thats true .. but i was benchmarking this bug with an older machine .. maybe it is exclusive to older machines.

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity (Gtk 3.18.5-1ubuntu2) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5LD2 v: Rev 1.xx
           Bios: American Megatrends v: 0901 date: 12/15/2005
CPU:       Dual core Intel Pentium D (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3) bmips: 15326
           clock speeds: max: 3831 MHz 1: 3831 MHz 2: 3831 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 04:00.0
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel NM10/ICH7 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 04:00.1
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (8.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 54G used: 5.8G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.15GB used: 0.02GB (1%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.5C mobo: 38.0C gpu: 35.0
           Fan Speeds (in rpm): cpu: 4115 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 202 Uptime: 2:09 Memory: 940.2/2000.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by P-I H on 2015-12-07
Ods  documents open OK with Writer and pdf  documents open OK with Draw, but to to re-size the documents don't work that well. It takes quite a long time and the documents are grayed out during the process.

```
p-i@pi-GA-990FXA-UD3-xenial:~$ inxi -Fxz
System:    Host: pi-GA-990FXA-UD3-xenial Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.5-1ubuntu2)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x
           Bios: Award v: F5 date: 10/13/2011
CPU:       Octa core AMD FX-8120 Eight-Core (-MCP-) cache: 16384 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 64427
           clock speeds: max: 4000 MHz 1: 1400 MHz 2: 1400 MHz 3: 1900 MHz
           4: 1400 MHz 5: 1400 MHz 6: 1900 MHz 7: 1400 MHz 8: 4000 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           bus-ID: 01:00.0
           Display Server: X.Org 1.17.3 drivers: ati (unloaded: fbdev,vesa,radeon)
           Resolution: 1920x1200@59.95hz
           GLX Renderer: Gallium 0.4 on AMD TONGA (DRM 3.1.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0-devel (padoka PPA) Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Device aad8
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 C-Media CMI8788 [Oxygen HD Audio]
           driver: snd_virtuoso port: ee00 bus-ID: 04:04.0
           Card-3 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: ae00 bus-ID: 06:00.0
           IF: enp6s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 360.1GB (14.1% used)
           ID-1: /dev/sda model: SSD2SC120GE2DA08 size: 120.0GB temp: 27C
           ID-2: /dev/sdb model: OCZ size: 120.0GB temp: 128C
           ID-3: /dev/sdc model: KINGSTON_SV300S3 size: 120.0GB temp: 25C
Partition: ID-1: / size: 103G used: 40G (42%) fs: ext4 dev: /dev/sdb1
           ID-2: swap-1 size: 8.57GB used: 0.00GB (0%) fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.0C mobo: 20.2C
           Fan Speeds (in rpm): cpu: 873 fan-1: 1442 fan-3: 0 fan-4: 1027
Info:      Processes: 259 Uptime: 35 min Memory: 1176.6/7965.4MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
p-i@pi-GA-990FXA-UD3-xenial:~$ 

```

---

### Post by ventrical on 2015-12-07
Thanks.

Grahammechcanical was mentioning that he was having probs similar with large documents. So I tired to emulate and reported the behaviour as a bug.

---

