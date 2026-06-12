---
title: "xen dom0 / radeon.audio=1"
date: 2013-10-04
forum: Virtualisation
---

### Post by sivel27 on 2013-10-04
hello all,

i followed the fantastic guide by powerhouse >> [http://forums.linuxmint.com/viewtopic.php?t=112013&f=42](http://forums.linuxmint.com/viewtopic.php?t=112013&f=42) to setup vga passthrough, and it worked flawlessly !
i am only having 1 real issues:

amd radeon 6570 dom0 no hdmi sound. i tried installing the fglrx driver, but black screen in xen,
and fglrx working in non xen boot.

i edited grub to include radeon.audio=1 , updated it, and still no sound.

specs :
```
inxi -Fxi
System:    Host: htpc Kernel: 3.5.0-17-generic x86_64 (64 bit, gcc: 4.7.2) Console: tty 4 Distro: Linux Mint 14 Nadia
Machine:   Mobo: MSI model: 970A-G46 (MS-7693) version: 2.0 Bios: American Megatrends version: V2.5 date: 07/16/2013
CPU:       Single core AMD Phenom II X6 1055T (-UP-) cache: 512 KB flags: (lm nx sse sse2 sse3 sse4a) bmips: 6860.35 
           Clock Speeds: 1: 3430.176 MHz 2: 3430.176 MHz 3: 3430.176 MHz 4: 3430.176 MHz 5: 3430.176 MHz 6: 3430.176 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6570] bus-ID: 01:00.0 
           Card-2: Advanced Micro Devices [AMD] nee ATI PITCAIRN PRO [Radeon HD 7800 Series] bus-ID: 02:00.0 
           X.org: 1.13.0 drivers: ati,radeon (unloaded: fbdev,vesa) tty size: 137x24 Advanced Data: N/A out of X
Audio:     Card-1: Advanced Micro Devices [AMD] nee ATI Device aab0 driver: pciback bus-ID: 02:00.1 Sound: ALSA ver: 1.0.25
           Card-2: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series] driver: snd_hda_intel bus-ID: 01:00.1
           Card-3: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) driver: snd_hda_intel bus-ID: 00:14.2
Network:   Card: Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller 
           driver: r8169 ver: 2.3LK-NAPI port: c000 bus-ID: 05:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: d4:3d:7e:ea:35:ec
           WAN IP: 98.213.135.136 IF: vif1.0 ip: N/A ip-v6: fe80::fcff:ffff:feff:ffff 
           IF: eth0 ip: N/A ip-v6: N/A IF: xenbr0 ip: 10.10.10.7 ip-v6: fe80::d63d:7eff:feea:35ec 
           IF: virbr0 ip: 192.168.122.1 ip-v6: N/A 
Drives:    HDD Total Size: 3250.7GB (0.5% used) 1: id: /dev/sda model: TOSHIBA_MK2565GS size: 250.1GB 
           2: id: /dev/sdb model: ST3000DM001 size: 3000.6GB 
Partition: ID: / size: 15G used: 4.4G (31%) fs: ext4 ID: /boot size: 960M used: 30M (4%) fs: ext2 
           ID: /home size: 35G used: 9.6G (30%) fs: ext4 ID: swap-1 size: 5.37GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 0.0C mobo: N/A gpu: 64.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 191 Uptime: 28 min Memory: 559.0/1678.1MB Runlevel: 2 Gcc sys: 4.7.2 Client: Shell inxi: 1.8.4
```


thanks in advance,
sivel

---

