---
title: "New computer, boot time a few seconds"
date: 2017-08-17
forum: The Cafe
---

### Post by Perfect Storm on 2017-08-17
So I bought a new computer the other day. A Ryzen x1700 with 32 GB ram and a nice nvidia card 1070 8 GB. Both the videocard and the motherboard is Asus with seems to work fine with kernel 4.4. The only thing I needed was to add nomodest to grub to bootup until I had installed the latest nvidia driver. Other than that no problems at all. I see people with different brand have troubles but with Asus it works out of the box on ubuntu 16.04/elementary OS. Regardless of that I install the latest stable kernel to get full credit of my hardware and ofcause the latest driver for video card.
I dual boot windows 10 and elementary OS. eos have 80 GB / on the SDD and 50GB /home at the HDD.

The specs
**Cabinet**: Cooler Master Silencio 550 Black
**CPU**: AMD Ryzen 7 1700X / 3.4 GHz Processor - AM4
**Motherboard**: ASUS PRIME X370-A
**RAM**: HyperX FURY 32GB DDR4  2400MHz 
**Video**: ASUS GTX1070 8GB DDR5
**SSD**: Samsung 850 250GB - SATA 6 Gb/s 
**HDD**: Toshiba  1TB - SATA 6 Gb/s 

Here's a video of the boot time. It's a bit shaky but I have a decease that makes my hands shaky.
[video=youtube;OE28AAfDm-Y]https://www.youtube.com/watch?v=OE28AAfDm-Y[/video]

---

### Post by mastablasta on 2017-08-17
very nice build. i am saving for something like Ryzen 5 and 16gb ram & maybe Nvidia 1050 or one of the opensoruce supported AMD cards.

is it a gaming PC? because i read that some new games need ridiculously large amounts of disk space.

---

### Post by Perfect Storm on 2017-08-17
Aye, I love gaming. New games takes a lot of GB. For instance xcom2 which also are available for linux takes 28 GB.

---

### Post by P-I H on 2017-08-17
My boot time
```
p-i@pi-MS-7A34:~$ systemd-analyze
Startup finished in 13.348s (firmware) + 1.912s (loader) + 3.149s (kernel) + 8.227s (userspace) = 26.638s
p-i@pi-MS-7A34:~$

```
The loader time depends on how fast you start boot in grub.
My build
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.12.0-11-generic x86_64 bits: 64
           Desktop: Gnome 3.24.3
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0
           UEFI: American Megatrends v: 1.70 date: 07/27/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3700 MHz 1: 1550 MHz 2: 1550 MHz 3: 1550 MHz
           4: 1550 MHz 5: 1550 MHz 6: 1550 MHz 7: 1550 MHz 8: 1550 MHz
           9: 1550 MHz 10: 1550 MHz 11: 1550 MHz 12: 1550 MHz 13: 1550 MHz
           14: 1550 MHz 15: 1550 MHz 16: 2700 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: x11 (X.Org 1.19.3 ) driver: amdgpu
           Resolution: 1920x1200@59.95hz
           OpenGL: renderer: Gallium 0.4 on AMD TONGA (DRM 3.15.0 / 4.12.0-11-generic, LLVM 4.0.1)
           version: 4.5 Mesa 17.1.4
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.12.0-11-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
            Drives:    HDD Total Size: 490.1GB (10.2% used)
           ID-1: /dev/nvme0n1 model: N/A size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 219G used: 47G (23%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: 42.0C gpu: 52.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 642 fan-2: 587 fan-3: 874 fan-4: 0 fan-5: 654
Info:      Processes: 381 Uptime: 11:47 Memory: 2524.1/16057.4MB
           Client: Shell (bash) inxi: 2.3.34 
p-i@pi-MS-7A34:~$
```

---

### Post by sp40140 on 2017-08-19
Surprising that your boot time is so high!
I am running 10+ years hardware and boot full ubuntu 17.04 in 18 sec. (I have added a cheap ssd a while back though). Not bragging, my hardware is far from worthy. But it surprised me that your new Ryzen machine takes this long.

---

### Post by cariboo on 2017-08-19
I'm running a two year old system here:

```
inxi -F
System:    Host: skynet Kernel: 4.12.0-11-generic x86_64 bits: 64
           Desktop: Gnome 3.24.3
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: M5A97 R2.0 v: Rev 1.xx
           UEFI: American Megatrends v: 2201 date: 12/10/2013
Battery    hidpp__0: charge: 70% condition: NA/NA Wh
CPU:       Octa core AMD FX-8350 Eight-Core (-MCP-) cache: 16384 KB
           clock speeds: max: 4000 MHz 1: 1400 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1400 MHz 5: 2800 MHz 6: 1400 MHz 7: 1400 MHz 8: 1400 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: x11 (X.Org 1.19.3 ) driver: nvidia
           Resolution: 1680x1050@59.95hz, 1360x768@60.02hz
           OpenGL: renderer: GeForce 210/PCIe/SSE2
           version: 3.3.0 NVIDIA 340.102
Audio:     Card-1 NVIDIA High Def. Audio Controller driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.12.0-11-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full
           mac: e0:3f:49:a4:8d:f7
Drives:    HDD Total Size: 2240.5GB (52.5% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 240.1GB
           ID-2: /dev/sdb model: ST1000DM003 size: 1000.2GB
           ID-3: /dev/sdc model: ST1000DM003 size: 1000.2GB
Partition: ID-1: / size: 96G used: 7.8G (9%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 674G used: 245G (39%) fs: ext4 dev: /dev/sdb3
           ID-3: swap-1 size: 2.10GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.0C mobo: 27.2C gpu: 60C
           Fan Speeds (in rpm): cpu: 0 fan-1: 1229 fan-2: 0 fan-3: 440
Info:      Processes: 325 Uptime: 3 days Memory: 3156.8/15939.6MB
           Client: Shell (bash) inxi: 2.3.34 

```

Systemd says:

```
systemd-analyze
Startup finished in 175us (firmware) + 70us (loader) + 3.350s (kernel) + 4.904s (userspace) = 8.254s
```

although subjectively it seems to take longer.

---

### Post by Perfect Storm on 2017-08-20
I'm not sure if systemd-analyze is accurate. Mine says:
```
Startup finished in 4.558s (kernel) + 25.846s (userspace) = 30.404s
```

and it's diffently not 30 secs to boot.

---

### Post by P-I H on 2017-08-20
In my case most time is spent by the motherboard before post, 13.348s. Ryzen systems do not boot that fast at least when using UEFI. I think it is quite common with a boot time of about 25s.

---

### Post by sp40140 on 2017-08-20
> **Artificial Intelligence said:**
> I'm not sure if systemd-analyze is accurate. Mine says:
```
Startup finished in 4.558s (kernel) + 25.846s (userspace) = 30.404s
```

and it's diffently not 30 secs to boot.
I ran the same command. So, if there is any question of reliability, it would apply to both of our times.

@P-I H
Possible, due to new platform. Hopefully it will get better over time.

---

### Post by echotech2 on 2017-08-21
Ubuntu 16.04.1 - Intel q9300 Quad core @ 2500 Mhz. 8 Years old.

 ```
Startup finished in 6.860s (kernel) + 11.244s (userspace) = 18.104s
```

 From Power-On to Grub about 10 seconds, most of that time BIOS enumerating 1 SSD, 2 HDD's, 1 USB HDD.

---

### Post by PJs Ronin on 2017-08-21
I hate waiting

```
wayne@artful:~$ systemd-analyze
Startup finished in 6.711s (kernel) + 1.822s (userspace) = 8.534s
```

Based on: ```
wayne@artful:~$ inxi -F
System:    Host: artful Kernel: 4.12.0-11-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: ASUS product: All Series
           Mobo: ASUSTeK model: H97M-PLUS v: Rev X.0x
           BIOS: American Megatrends v: 2404 date: 03/04/2015
CPU:       Quad core Intel Core i7-4790 (-HT-MCP-) cache: 8192 KB
           clock speeds: max: 4000 MHz 1: 999 MHz 2: 999 MHz 3: 1006 MHz 4: 1205 MHz 5: 1031 MHz
           6: 1003 MHz 7: 1091 MHz 8: 1003 MHz
Graphics:  Card: NVIDIA GK107 [GeForce GTX 650]
           Display Server: x11 (X.Org 1.19.3 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 650/PCIe/SSE2 version: 4.5.0 NVIDIA 375.82
Audio:     Card-1 NVIDIA GK107 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Intel 9 Series Family HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.12.0-11-generic
Network:   Card: Intel Ethernet Connection (2) I218-V driver: e1000e
           IF: eth1 state: up speed: 1000 Mbps duplex: full mac: 08:62:66:c8:90:74
Drives:    HDD Total Size: 4240.9GB (63.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
           ID-2: /dev/sdb model: ST2000DM001 size: 2000.4GB
           ID-3: /dev/sdc model: WDC_WD20EZRZ size: 2000.4GB
           ID-4: /dev/sdd model: KINGSTON_SV300S3 size: 120.0GB
Partition: ID-1: / size: 9.5G used: 6.3G (70%) fs: ext4 dev: /dev/sda9
           ID-2: /home size: 4.7G used: 726M (17%) fs: ext4 dev: /dev/sdd6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 35.0C gpu: 33C
           Fan Speeds (in rpm): cpu: 0 fan-1: 0 fan-2: 1250 fan-3: 0
Info:      Processes: 230 Uptime: 14 min Memory: 1039.6/15987.3MB
           Client: Shell (bash) inxi: 2.3.34
```

---

### Post by exhile on 2017-08-23
I have no choice but to wait

```

exhile@DG45ID:~$ systemd-analyze
Startup finished in 10.506s (kernel) + 24.732s (userspace) = 35.238s

```

System info:
```

exhile@DG45ID:~$ inxi -F
System:    Host: DG45ID Kernel: 4.10.0-32-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Intel model: DG45ID v: AAE27729-307
           Bios: Intel v: IDG4510H.86A.0107.2009.0624.1357 date: 06/24/2009
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB 
           clock speeds: max: 2830 MHz 1: 1998 MHz 2: 1998 MHz 3: 1998 MHz
           4: 1998 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.19.3 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1200@59.95hz, 1920x1200@59.95hz
           GLX Renderer: Mesa DRI Intel G45/G43 GLX Version: 2.1 Mesa 17.0.7
Audio:     Card Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-32-generic
Network:   Card-1: Intel 82567LF-2 Gigabit Network Connection driver: e1000e
           IF: enp0s25 state: down mac: 00:1c:c0:6f:ad:9e
           Card-2: ASUSTek USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
           driver: rtl8192cu
           IF: wlxe03f498fabc8 state: N/A mac: N/A
Drives:    HDD Total Size: 150.0GB (13.5% used)
           ID-1: /dev/sda model: WDC_WD1500HLFS size: 150.0GB
Partition: ID-1: / size: 134G used: 16G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.19GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 100.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 208 Uptime: 57 min Memory: 1671.6/3848.2MB
           Client: Shell (bash) inxi: 2.2.35 

```

---

### Post by HermanAB on 2017-08-24
So, the obvious(?) solution is not to reboot the machine.

Use suspend and resume.  The machine should come back up in a fraction of a second.

---

### Post by Perfect Storm on 2017-08-24
It's no big deal for me. It's nice though, but nothing to ruining my day.
Just observing and measure with a timer that systemd-analyze were wrong.

---

### Post by mastablasta on 2017-08-24
> **HermanAB said:**
> So, the obvious(?) solution is not to reboot the machine.


except if it is a laptop

---

### Post by Wadim_Korneev on 2017-09-02
[COLOR=#111111][FONT=Roboto]eOS is best GNU/Linux distro.[/FONT][/COLOR]

---

