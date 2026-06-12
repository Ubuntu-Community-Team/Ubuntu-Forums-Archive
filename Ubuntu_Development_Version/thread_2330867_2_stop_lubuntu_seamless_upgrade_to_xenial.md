---
title: "2 stop lubuntu seamless upgrade to xenial"
date: 2016-07-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-15
1. amd64 14.01.1 to 14.04.4 was seamless. 
2. amd64 14.04 to xenial had two stops. One was for allowing auto restart of services and second was to allow removal of obsolete software on this machine:

```


System:    Host: ventrical-System-Product-Name Kernel: 4.4.0-31-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-31-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (9.4% used)
           ID-1: /dev/sda model: WDC_WD800JD size: 80.0GB
Partition: ID-1: / size: 36G used: 4.2G (13%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 38.0C gpu: 41.0
           Fan Speeds (in rpm): cpu: 4272 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 163 Uptime: 14 min Memory: 509.4/3007.7MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.461) inxi: 2.2.35 
ventrical@ventrical-System-Product-Name:~$ 

```

regards..

---

### Post by sudodus on 2016-07-16
Please tell us also about the final result: did you get systems that work well?

---

### Post by ventrical on 2016-07-16
> **sudodus said:**
> Please tell us also about the final result: did you get systems that work well?

Honestly? No. I have yet to do the i386.

1. There are several journal.fsck/orphans verbose at bootup.
2. There is now a double-dutch flicker with the logon screen
3. When you run update-manager -d -c it now tells you that the upgrade failed and offers partial 
    upgrade. (But it actually upgraded successfully.)
4. Installed nvidia-current and broke install. Tried to recover, remove, install nouveau, but to no avail.

 I have now broke that system (with unity8 experiment)  and will try again for testing period comming up. Will also use another hdd.

 When I first joined the forums I was warned about the 'upgrade-mangler' and it looks as if this is still the case on several attemtps on installs at various stages. The upgrade needs to be guided manually.

Regards..

---

### Post by ventrical on 2016-07-16
On the same machine, i386 lubuntu install correctly detects and notifies 16.04 xenial LTS.

---

### Post by ventrical on 2016-07-16
and yet another false flag when running udate-manager -d -c for Lubuntu  i386 14.04.4

---

### Post by zika on 2016-07-16
[https://ubuntuforums.org/showthread.php?t=2330857](https://ubuntuforums.org/showthread.php?t=2330857)
(report does not work...)

---

### Post by ventrical on 2016-07-16
> **zika said:**
> [https://ubuntuforums.org/showthread.php?t=2330857](https://ubuntuforums.org/showthread.php?t=2330857)
(report does not work...)

?? what report does not work? The bug report is not good ?

---

