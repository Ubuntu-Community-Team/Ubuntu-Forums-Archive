---
title: "compiz: 3d windows"
date: 2015-08-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-08-06
For those that use such stuff, (I don't but tested fix in 14.04) it should be working shortly..

---

### Post by ventrical on 2015-08-06
thnxs
:)

---

### Post by monkeybrain20122 on 2015-08-06
Finally!!! It would have been nice if they fixed it back in 12.04 when I still used the cube (there were multiple issues with the cube back then if I recall correctly). Now that I have been using wall for a while and gotten used to it it wouldn't make a difference to me. But may test it on 14.04 just for the heck of it now that it is my backup OS (switched to 15.04 for about two months now)

---

### Post by mc4man on 2015-08-06
It's a little sketchy in 14.04, maybe it'll be better in 15.10 or 16.04
(- sometimes shows no windows, also  at certain angles shows a black vertical line or 2
Could be because I stopped updating compiz for 14.04 at 0.9.12.0+15.04.20141210.2 plus a few personal changes as I expected & recently confirmed that 16.04 will have unity7 with compiz
couple of screens from 14.04, don't know this plugin but would be better if 3d windows scaled down to cube size??

---

### Post by monkeybrain20122 on 2015-08-06
It looks a bit off. You can watch old youtube clips to see how it is supposed to look.

---

### Post by mc4man on 2015-08-06
The 'fixed' compiz is sitting in wily -proposed, currently Not installable, waiting for something or other. When it leaves -proposed or is installable without removing a bunch that would be a better test..

---

### Post by QDR06VV9 on 2015-08-06
I Like some of the effects like Wobbly windows, Close & Open windows, and Minimize effects.
On 15.04 the same results with 3D Windowed & 15.10 Even worse.
But 14.04LTS has been one of the best OS's I have to date run on my Machine.
I can not seem to break it. >(Knock on wood)
```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu _**14.04.3 LTS**_
Release:    14.04
Codename:    trusty
pulseaudio --version
pulseaudio 6.0-54-g2cfc5d
mate@mate-Aspire-M3300:~$ inxi -Fxz
System:    Host: mate-Aspire-M3300 Kernel: 4.1.3-040103-lowlatency x86_64 (64 bit, gcc: 4.8.4) 
           Desktop: MATE Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M Bios: American Megatrends version: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20741.5 
           Clock Speeds: 1: 2600.00 MHz 2: 2600.00 MHz 3: 2600.00 MHz 4: 2600.00 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GT 520/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 355.06 Direct Rendering: Yes
Audio:     Card-1: NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Creative Labs SB Audigy driver: snd_emu10k1 port: e800 bus-ID: 04:05.0 
           Sound: Advanced Linux Sound Architecture ver: k4.1.3-040103-lowlatency
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller driver: sky2 ver: 1.30 port: c800 bus-ID: 02:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 3000.6GB (37.7% used) 1: id: /dev/sda model: WDC_WD10EADS size: 1000.2GB 
           2: id: /dev/sdb model: WDC_WD20EADS size: 2000.4GB 
Partition: ID: / size: 227G used: 82G (38%) fs: ext4 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 51.0C mobo: 50.1C gpu: 0.0:51C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 240 Uptime: 8:42 Memory: 1575.8/5967.2MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 



```
So in short I am Happier Than a Tick on a Fat Dog.
Regards

---

### Post by ventrical on 2015-08-07
Working not too bad here on overclock.

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.1.0-3-generic x86_64 (64 bit gcc: 4.9.3)
           Desktop: Unity 7.3.2 (Gtk 3.16.6-1ubuntu1)
           Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5QL PRO v: Rev 1.xx
           Bios: American Megatrends v: 1004 date: 07/01/2009
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 25200
           clock speeds: max: 3150 MHz 1: 3150 MHz 2: 3150 MHz 3: 3150 MHz
           4: 3150 MHz
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98
           GLX Version: 3.0 Mesa 10.5.9 Direct Rendering: Yes
Audio:     Card Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.1.0-3-generic
Network:   Card-1: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E port: dc00 bus-ID: 02:00.0
           IF: eth2 state: down mac: <filter>
           Card-2: VIA VT6102/VT6103 [Rhine-II]
           driver: via-rhine port: e800 bus-ID: 04:02.0
           IF: eth3 state: unknown speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (8.9% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
Partition: ID-1: / size: 52G used: 7.1G (15%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 3.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 27.0C mobo: 28.0C gpu: 33.0
           Fan Speeds (in rpm): cpu: 4560 psu: 3013 sys-1: 2556
Info:      Processes: 195 Uptime: 2 min Memory: 597.1/3260.0MB
           Init: systemd runlevel: 5 Gcc sys: 4.9.3
           Client: Shell (bash 4.3.301) inxi: 2.2.16 

```

---

