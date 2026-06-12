---
title: "Ubuntu 17.10 daily"
date: 2017-06-16
forum: Ubuntu Development Version
---

### Post by kc1di on 2017-06-16
Find much to like about 17.10 developement-- Tried to do a side by side install with 16.04 but the installer always hangs at the resize partition spot.  
Select the sizes I want but the resize always fails. have not tried doing it with gparted yet.  But thought I'd throw it out there see if anyone's gotten it to work for them. 

still exploring other features but so far really encouraged by what I see.

P.S. Think most unity users would be pleased with the results of the Gnome desktop looks very nice seems quite responsive also. :)

---

### Post by ventrical on 2017-06-16
> **kc1di said:**
> Find much to like about 17.10 developement-- Tried to do a side by side install with 16.04 but the installer always hangs at the resize partition spot.  
Select the sizes I want but the resize always fails. have not tried doing it with gparted yet.  But thought I'd throw it out there see if anyone's gotten it to work for them. 

still exploring other features but so far really encouraged by what I see.

P.S. Think most unity users would be pleased with the results of the Gnome desktop looks very nice seems quite responsive also. :)

Worked here just a few days ago.

Can you provide some hardware details?

---

### Post by SurfaceUnits on 2017-06-16
WiFi isn't working on the build from yesterday. Can see the 3 WiFi networks but won't connect to any. Doesn't give an error message when an incorrect passphrase is used either. Using a basic Realtek G adapter.

---

### Post by kc1di on 2017-06-16
> **ventrical said:**
> Worked here just a few days ago.

Can you provide some hardware details?

```
Lenovo-IdeaPad-N585 Kernel: 4.8.0-54-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.5 Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO product: 20179 v: Lenovo IdeaPad N585
           Mobo: LENOVO model: Lenovo IdeaPad N585 v: 31900003WIN8 STD MLT
           Bios: LENOVO v: 6CCN93WW(V8.05) date: 10/02/2012
CPU:       Dual core AMD E1-1200 APU with Radeon HD Graphics (-MCP-)
           speed/max: 1166/1400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Wrestler [Radeon HD 7310]
           Display Server: X.Org 1.18.4 driver: N/A
           Resolution: 1366x768@60.00hz
           GLX Renderer: Gallium 0.4 on AMD PALM (DRM 2.46.0 / 4.8.0-54-generic, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 12.0.6
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
Drives:    HDD Total Size: 320.1GB (6.2% used)
Info:      Processes: 208 Uptime: 3:42 Memory: 1610.4/3521.8MB
           Client: Shell (bash) inxi: 2.2.35 
```

---

### Post by ventrical on 2017-06-16
> **kc1di said:**
> ```
Lenovo-IdeaPad-N585 Kernel: 4.8.0-54-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.5 Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO product: 20179 v: Lenovo IdeaPad N585
           Mobo: LENOVO model: Lenovo IdeaPad N585 v: 31900003WIN8 STD MLT
           Bios: LENOVO v: 6CCN93WW(V8.05) date: 10/02/2012
CPU:       Dual core AMD E1-1200 APU with Radeon HD Graphics (-MCP-)
           speed/max: 1166/1400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Wrestler [Radeon HD 7310]
           Display Server: X.Org 1.18.4 driver: N/A
           Resolution: 1366x768@60.00hz
           GLX Renderer: Gallium 0.4 on AMD PALM (DRM 2.46.0 / 4.8.0-54-generic, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 12.0.6
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
Drives:    HDD Total Size: 320.1GB (6.2% used)
Info:      Processes: 208 Uptime: 3:42 Memory: 1610.4/3521.8MB
           Client: Shell (bash) inxi: 2.2.35 
```


It may work really well from live session but will then break when installed(hardware resources?).  The topical issue about resizing and side by side install .. all I can suggest is that you try nomodeset before you install. I have had it work here several times. Also .. there may be new bugs in the daily - but highly unlikely.

If nomodeset does not work you can file a bug.

regards..

---

### Post by kc1di on 2017-06-16
Thank you ventrical 
 will file a bug report if I can't get it to work I'll just repartition the whole drive to do two new installs. 
It may now work because I originally used and extended partition not sure the partitioner can do a partition within an extended one. 
In any event will get it going, I've never had to use nomodeset on this particualar GPU.  But will give it a try .
Thanks again.

---

### Post by ventrical on 2017-06-16
> **kc1di said:**
> Thank you ventrical 
 will file a bug report if I can't get it to work I'll just repartition the whole drive to do two new installs. 
It may now work because I originally used and extended partition not sure the partitioner can do a partition within an extended one. 
In any event will get it going, I've never had to use nomodeset on this particualar GPU.  But will give it a try .
Thanks again.

I am zsycing the daily to see if I can duplicate the problem which you are working with.

regards.

---

### Post by ventrical on 2017-06-16
It resized just fine on this old HP with the daily.

```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ inxi -Fxz
System:    Host: ventrical-RK574AA-ABA-a1730n Kernel: 4.10.0-22-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: HP-Pavilion product: RK574AA-ABA a1730n
           Mobo: ASUSTek model: NODUSM3 v: 1.05
           BIOS: Phoenix v: 5.04 date: 12/15/2006
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 svm) bmips: 4008
           clock speeds: max: 2600 MHz 1: 1000 MHz 2: 1000 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 02:00.0
           Display Server: X.Org 1.19.3 drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 17.1.2 Direct Rendering: Yes
Audio:     Card-1 NVIDIA MCP51 High Definition Audio
           driver: snd_hda_intel bus-ID: 00:10.1
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 02:00.1
           Sound: Advanced Linux Sound Architecture v: k4.10.0-22-generic
Network:   Card: NVIDIA MCP51 Ethernet Controller
           driver: forcedeth port: c800 bus-ID: 00:14.0
           IF: enp0s20 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 320.1GB (1.9% used)
           ID-1: /dev/sda model: ST3320820AS size: 320.1GB
Partition: ID-1: / size: 141G used: 5.7G (5%) fs: ext4 dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 58.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 197 Uptime: 19 min Memory: 980.7/1997.4MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.11 
ventrical@ventrical-RK574AA-ABA-a1730n:~$ 

```

regards..

---

### Post by ventrical on 2017-06-16
a pic of disk layout.

---

### Post by kc1di on 2017-06-18
Went ahead and repartitioned and did the install so far working quite well. 
Cheers.

---

### Post by rrnbtter on 2017-06-18
Greetings,
I don't dual boot, but I did a reinstall from the 17.10 daily yesterday in order to clean the remnants of 17.04 from my install. Everything went smooth.  I must say that Gnome x11 and ultimately  Gnome Wayland is a very attractive and functional  desktop. This is not the horrible experience I thought it would be.

---

