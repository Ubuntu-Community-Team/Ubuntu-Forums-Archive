---
title: "AMD-VI: Event logged [IO_PAGE_FAULT"
date: 2019-03-12
forum: Server Platforms
---

### Post by cyrils34 on 2019-03-12
Hi everyone, i got some issue with my server, after X minutes, i got the error :

 [B][FONT=Calibri][16502.713594] AMD-VI: Event logged [IO_PAGE_FAULT device=25:00.0 domain=0x000d address=0x00000000048b5000 flags=0x0050]

[/FONT][/B][FONT=Calibri]Then the server crash and i need to reboot**. **Did someone  know how to do for fix it ?[/FONT][B][FONT=Calibri]
It's a fresh installation, no update/upgrade have been made after the installation.
[/FONT][/B][FONT=Calibri][/FONT]

  This is the spec of the server :

System:    Host: Serverprod Kernel: 4.4.0-142-generic x86_64 (64 bit gcc: 5.4.0) Console: tty 0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: B450 Pro4 serial: M80-C1007700774
           Bios: American Megatrends v: P1.50 date: 11/05/2018
CPU:       Multi core AMD Ryzen 7 2700X Eight-Core (-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 118173
           clock speeds: max: 3700 MHz 1: 2200 MHz 2: 2200 MHz 3: 2200 MHz 4: 2200 MHz 5: 2200 MHz 6: 2200 MHz
           7: 2200 MHz 8: 2200 MHz 9: 2200 MHz 10: 2200 MHz 11: 2200 MHz 12: 3700 MHz 13: 2200 MHz 14: 2200 MHz
           15: 2200 MHz 16: 2200 MHz
Graphics:  Card: NVIDIA Device 1c81 bus-ID: 26:00.0
           Display Server: N/A driver: N/A tty size: 183x42 Advanced Data: N/A for root out of X
Audio:     Card-1 Advanced Micro Devices [AMD] Device 1457 driver: snd_hda_intel bus-ID: 28:00.3
           Card-2 NVIDIA Device 0fb9 driver: snd_hda_intel bus-ID: 26:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-142-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 25:00.0
           IF: enp37s0 state: up speed: 1000 Mbps duplex: full mac: 70:85:c2:bd:8b:1c
Drives:    HDD Total Size: 2000.4GB (7.1% used) ID-1: /dev/sda model: ST1000DM010 size: 1000.2GB temp: 37C
           ID-2: /dev/sdb model: ST1000DM010 size: 1000.2GB temp: 38C
Partition: ID-1: / size: 858G used: 17G (3%) fs: ext4 dev: /dev/md0
           ID-2: swap-1 size: 65.00GB used: 0.00GB (0%) fs: swap dev: /dev/sdb1
           ID-3: swap-2 size: 65.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda1
RAID:      Device-1: /dev/md0 - active components: online: sdb2[1] sda2[0]
           Info: raid: 1 report: 2/2 blocks: 913154048 chunk size: N/A bitmap: true
Sensors:   System Temperatures: cpu: N/A mobo: 37.0C
           Fan Speeds (in rpm): cpu: N/A fan-1: 0 fan-2: 2086 fan-3: 0 fan-4: 892 fan-5: 0
Info:      Processes: 233 Uptime: 33 min Memory: 436.6/32171.1MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

Thank you so much for your help or advise

---

### Post by cyrils34 on 2019-03-12
After 3 days i finally find the problem, i explain for if someone got that problem
i grep for check what device was the 25:00.0

sudo lspci -vnn | grep 25:00.0 -A

i got the result : Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

The problem is from the Driver, i've update them with this code :
sudo apt-get install r8168-dkms

After finish the install, i have restart my server then everything is working fine (until now...)

---

### Post by MasterCATZ on 2019-12-18
[33133.008684] r8169 0000:07:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0001 address=0x747f1c523e0d8cd0 flags=0x0010]

where would I get updated drivers for  r8169  ? 
 I would have thought 2 years and all the Ryzen bugs would be ironed out , this has been my most unstable PC upgrade ever ! 
almost everything has a issue

---

