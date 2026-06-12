---
title: "release candidate iso absolute fail/nvidia"
date: 2017-10-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-12
Downloaded full ISO . Did hard install on Dell Precision T3400 with Core 2 Duo (quad) and:
1. Still has bug where you cannot exit from install "remove installation and press enter" so hard boot is required.
2. Plymouth pretends to start up then locks.  No hand off to GDM .. well .. at least I am not going to wait all night for it.

Regards..
#note# this box has installed nVidia card late model. Worked just fine with  early june iso.  But then got really buggy with flickerty between plymouth and GDM startup. I don't want to use lighdm as a workaround. I want a hard and dry GDM run up with just gnome3 for testing.

Will try nomodeset.

---

### Post by dino99 on 2017-10-12
Lightdm now makes unity-settings-daemon crashing  lp:1722988 
and nvidia cards need 'nouveau' to work with wayland (nvidia driver has problem), or boot on X to workaround

---

### Post by ventrical on 2017-10-12
> **dino99 said:**
> Lightdm now makes unity-settings-daemon crashing  lp:1722988 
and nvidia cards need 'nouveau' to work with wayland (nvidia driver has problem), or boot on X to workaround

This is fresh install. No nvidia drivers.

Got commadore64 type screen with nomodeset attempt.

---

### Post by ventrical on 2017-10-12
2nd machine hard install. Same prob  with plymouth. Lock up  on plymouth screen.
unless I got a bum .iso

---

### Post by Chanath on 2017-10-12
> **ventrical said:**
> Downloaded full ISO . Did hard install on Dell Precision T3400 with Core 2 Duo (quad) and:
1. Still has bug where you cannot exit from install "remove installation and press enter" so hard boot is required.
2. Plymouth pretends to start up then locks. 


These are ubiquity problems. Not desktop related problems. Something that has to be looked into by the devs, who maintain the base system.
This happens with Xubuntu, Lubuntu, Kubuntu and Budgie too. Had been for quite some time.

---

### Post by ventrical on 2017-10-12
Point is - the release candidate is an absolute fail with exception for live session.

regards..

---

### Post by ventrical on 2017-10-12
> **Chanath said:**
> These are ubiquity problems. Not desktop related problems. Something that has to be looked into by the devs, who maintain the base system.
This happens with Xubuntu, Lubuntu, Kubuntu and Budgie too. Had been for quite some time.

Did you try release candidate?

Regards..

---

### Post by Chanath on 2017-10-12
> **ventrical said:**
> Did you try release candidate?

Regards..

No. I don't feel like checking how Gnome is doing...
The symptoms you put are installation related, so ubiquity.

---

### Post by mc4man on 2017-10-12
The best way to exit a live session remains (assuming live session is at least 30 sec old
ctrl+alt+F2
login (user name ubuntu
reboot or shutdown now command

---

### Post by ventrical on 2017-10-12
> **mc4man said:**
> The best way to exit a live session remains (assuming live session is at least 30 sec old
ctrl+alt+F2
login (user name ubuntu
reboot or shutdown now command

OK mac4man. Thanks for that.

Regards..

---

### Post by ventrical on 2017-10-13
Got a really sleek and smooth install from todays daily. Fixed is the enter/restart/reboot option after hard installation. This only seems to work on intel based graphics.(nouveau) nVidia metal still a fail with plymouth freeze up.

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.13.0-15-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0 serial: N/A
           UEFI: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) 
           arch: Haswell rev.3 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12398
           clock speeds: max: 3100 MHz 1: 3099 MHz 2: 3099 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.3 ) driver: i915
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-15-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 200.0GB (2.9% used)
           ID-1: /dev/sda model: MAXTOR_STM320082 size: 200.0GB temp: 38C
Partition: ID-1: / size: 182G used: 5.5G (4%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 207 Uptime: 8 min Memory: 1241.7/3808.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by Chanath on 2017-10-13
> **ventrical said:**
> Got a really sleek and smooth install from todays daily. Fixed is the enter/restart/reboot option after hard installation. This only seems to work on intel based graphics.(nouveau) nVidia metal still a fail with plymouth freeze up.

It only says something about the state of the daily at the time it was uploaded. The one you already have installed and got upgraded would have the same packages and configs. The installation part of the live iso is the same, while the squashfs-root is is the one that differed. If you download the next daily tomorrow, only the squashfs-root would be different. In the final release, there'd be *the final* squashfs-root, which would only stay final until the next development daily release.

---

### Post by P-I H on 2017-10-13
Installed the daily ISO on this hardware
```
p-i@pi-GA-990FXA-UD3:~$ inxi -F
System:    Host: pi-GA-990FXA-UD3 Kernel: 4.13.0-15-generic x86_64 bits: 64
           Desktop: Gnome 3.26.1
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x serial: N/A
           BIOS: Award v: F5 date: 10/13/2011
CPU:       Octa core AMD FX-8120 Eight-Core (-MCP-) cache: 16384 KB
           clock speeds: max: 4000 MHz 1: 4026 MHz 2: 4026 MHz 3: 4026 MHz
           4: 4026 MHz 5: 4026 MHz 6: 4026 MHz 7: 4026 MHz 8: 4026 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts PRO [Radeon HD 6850]
           Display Server: wayland (X.Org 1.19.4 ) driver: radeon
           Resolution: 1920x1080@59.96hz
           OpenGL: renderer: AMD BARTS (DRM 2.50.0 / 4.13.0-15-generic, LLVM 5.0.0)
           version: 3.3 Mesa 17.2.2
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Barts HDMI Audio [Radeon HD 6790/6850/6870 / 7720 OEM]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-15-generic
Network:   Card-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k
           IF: wlp3s0 state: down mac: 00:21:91:0b:5f:11
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full
           mac:
Drives:    HDD Total Size: 880.2GB (1.1% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
           ID-2: /dev/sdb model: KINGSTON_SV300S3 size: 120.0GB
           ID-3: /dev/sdc model: WDC_WD6400AAKS size: 640.1GB
Partition: ID-1: / size: 110G used: 9.2G (9%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 32.0C mobo: 29.0C gpu: 39.0
           Fan Speeds (in rpm): cpu: 1409 fan-2: 922 fan-3: 0 fan-4: 1203
Info:      Processes: 280 Uptime: 4 min Memory: 1638.8/7961.8MB
           Client: Shell (bash) inxi: 2.3.37 
p-i@pi-GA-990FXA-UD3:~$ 

```Used "Try Ubuntu without install", which started and closed OK. Ubuntu Software behaved a little bit strange. Only showed Featured Applications and Editor's Picks. Installed only showed the System extensions.

Used " Install Ubuntu", which worked OK.
Used Ubuntu Software to install Dropbox, Chromium, Psensor, GNOME Packages, Tweaks, Steam, and Kodi.
Used GNOME Packages to install lm-sensors and chrome-gnome-shell.
Used a terminal to install chrome-gnome-shell and inxi.
All installations worked OK.

Rebooted, but after reboot the Kodi session was started and not the expected Ubuntu session.

Overall a quite good experience.

---

### Post by corradoventu on 2017-10-13
1. Still has bug where you cannot exit from install "remove installation and press enter" so hard boot is required.
see my bug and subscribe: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1719191](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1719191)
problem still remain with beta: Ubuntu 17.10 "Artful Aardvark" - Beta amd64 (20171011)

---

### Post by Chanath on 2017-10-13
If anyone can code, download ubiquity and have a look at the files. Its Ubiquity that installs. I don't think anyone had looked in it for a long time. The last "to do" was mentioned in those files sometime in 2012.

---

### Post by ventrical on 2017-10-13
> **Chanath said:**
> If anyone can code, download ubiquity and have a look at the files. Its Ubiquity that installs. I don't think anyone had looked in it for a long time. The last "to do" was mentioned in those files sometime in 2012.

I am really sure this is stricktly a nVidia/gdm problem and not an ubiquity problem. I have it working just swell on radeon/intel graphics. The really bad fails I have are all on PCs with nVidia graphics.  But maybe ubiquity might be unstacking things incorrectly so you may have a point.

regards..

---

### Post by dino99 on 2017-10-13
> **Chanath said:**
> If anyone can code, download ubiquity and have a look at the files. Its Ubiquity that installs. I don't think anyone had looked in it for a long time. The last "to do" was mentioned in those files sometime in 2012.

Not so old as you said:
ubiquity (17.10.9) artful; urgency=medium
Mathieu Trudel-Lapierre <cyphermox@ubuntu.com>  Wed, 11 Oct 2017 12:06:55 -0400

---

### Post by ventrical on 2017-10-13
> **dino99 said:**
> Not so old as you said:
ubiquity (17.10.9) artful; urgency=medium
Mathieu Trudel-Lapierre <cyphermox@ubuntu.com>  Wed, 11 Oct 2017 12:06:55 -0400

@dino

I'm doing a test on nVidia box now. I think I have an idea of whats going wrong. It is totally a hardware/jockey issue.

Regards..

---

### Post by ventrical on 2017-10-13
> **corradoventu said:**
> 1. Still has bug where you cannot exit from install "remove installation and press enter" so hard boot is required.
see my bug and subscribe: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1719191](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1719191)
problem still remain with beta: Ubuntu 17.10 "Artful Aardvark" - Beta amd64 (20171011)

ON Intel graphics boxes .. no. Not here. Did you download the Oct 12 current?

regards..

---

### Post by ventrical on 2017-10-13
OK.. here is an easy fix I developed.

[https://ubuntuforums.org/showthread.php?t=2374208](https://ubuntuforums.org/showthread.php?t=2374208)

Regards..

---

### Post by Chanath on 2017-10-13
> **dino99 said:**
> Not so old as you said:
ubiquity (17.10.9) artful; urgency=medium
Mathieu Trudel-Lapierre <cyphermox@ubuntu.com>  Wed, 11 Oct 2017 12:06:55 -0400

If you care to look in the files, you'd see that some "to do" had not been looked into for a long time...

---

### Post by mc4man on 2017-10-14
no issues with hybrid nvidia so must just affect 'desktop' nvidia gpu's.
(- not saying there aren't issues with hybrid devices, just not this one..

---

### Post by ventrical on 2017-10-14
> **Chanath said:**
> These are ubiquity problems. Not desktop related problems. Something that has to be looked into by the devs, who maintain the base system.
This happens with Xubuntu, Lubuntu, Kubuntu and Budgie too. Had been for quite some time.

Many updates to ubiquity just now.

```

 ubiquity ubiquity-casper
  ubiquity-frontend-debconf ubiquity-ubuntu-artwork

```


regards..

---

### Post by Chanath on 2017-10-15
> **ventrical said:**
> Many updates to ubiquity just now.
```

 ubiquity ubiquity-casper
  ubiquity-frontend-debconf ubiquity-ubuntu-artwork

```
regards..

Ubiquity won't be in the installed distro. It only matters in the live iso. If there is a problem with the live iso not correctly going off after an installation or has a plymouth problem, then it is the problem that had to be corrected *before *releasing the distro -- a QA problem.

---

