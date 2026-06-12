---
title: "Touchpad Not working with 5.x kernels"
date: 2019-04-29
forum: Ubuntu Development Version
---

### Post by rimez on 2019-04-29
I recently bought a new laptop (Lenovo ideapad 530S-14ARR). While testing the 5.x series (now currently using the latest 5.1 RC) I had 1 main issue - my touchpad doesn't work. With the 4.18 it works fine. 

If I run "cat /proc/bus/input/devices > ~/devices" on the 4.18 kernel, I see the following: 
I: Bus=0018 Vendor=06cb Product=7f27 Version=0100
N: Name="MSFT0001:00 06CB:7F27 Touchpad"
P: Phys=i2c-MSFT0001:00
S: Sysfs=/devices/platform/AMDI0011:01/i2c-2/i2c-MSFT0001:00/0018:06CB:7F27.0003/input/input16
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003
B: MSC=20


But when i run the same command in 5.x, it doesn't appear at all.  Does anyone have clue how to resolve it? 


=====
From 5.x kernel: 

```
~$ inxi -Fxxxz
System:    Host: amylia Kernel: 5.0.10-050010-generic x86_64 bits: 64 gcc: 8.3.0
           Desktop: Gnome  (Gtk 3.22.30-1ubuntu2) dm: lightdm Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: LENOVO product: 81H1 v: Lenovo ideapad 530S-14ARR serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN serial: N/A
           UEFI [Legacy]: LENOVO v: 8PCN45WW date: 08/17/2018
           Chassis: type: 10 v: Lenovo ideapad 530S-14ARR serial: N/A
Battery    BAT0: charge: 43.6 Wh 99.0% condition: 44.0/45.5 Wh (97%) volts: 8.7/7.7
           model: CPT-COS L17C4PB0 Li-poly serial: <filter>status: N/A cycles: 0
CPU:       Quad core AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (-MT-MCP-) arch: Zen rev.0 cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15970
           clock speeds: min/max: 1600/2000 MHz 1: 1379 MHz 2: 1506 MHz 3: 1375 MHz 4: 1561 MHz 5: 1509 MHz
           6: 1387 MHz 7: 1367 MHz 8: 1459 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           bus-ID: 03:00.0 chip-ID: 1002:15dd
           Display Server: x11 (X.Org 1.20.1 ) drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: AMD RAVEN (DRM 3.27.0, 5.0.10-050010-generic, LLVM 8.0.0)
           version: 4.5 Mesa 19.1.0-devel (git-d946cbe 2019-04-26 bionic-oibaf-ppa) Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel bus-ID: 03:00.6 chip-ID: 1022:15e3
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de
           driver: snd_hda_intel bus-ID: 03:00.1 chip-ID: 1002:15de
           Sound: Advanced Linux Sound Architecture v: k5.0.10-050010-generic
Network:   Card-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci bus-ID: 01:00.0 chip-ID: 168c:0042
           IF: wlp1s0 state: up mac: <filter>
           Card-2: Atheros usb-ID: 001-003
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 256.1GB (39.0% used)
           ID-1: /dev/nvme0n1 model: WDC_PC_SN520_SDAPMUW size: 256.1GB serial: <filter> firmware: 20110001
Partition: ID-1: / size: 233G used: 92G (42%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 704M used: 155M (24%) fs: ext4 dev: /dev/nvme0n1p1
           ID-3: swap-1 size: 1.03GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A gpu: 49.0
Info:      Processes: 305 Uptime: 0 min Memory: 825.2/15646.7MB Init: systemd v: 237 runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191 running in guake) inxi: 2.3.56
```

---

### Post by Claus7 on 2019-05-08
Hello,

> **rimez said:**
> 
...

If I run "cat /proc/bus/input/devices > ~/devices" on the 4.18 kernel, ...

testing this command on desktop does not produce anything. The kernel version is 4.15 though. Is this command supposed to work only with laptops? 5.x kernels are already released for ubuntu 19.04. Did you have any luck with these updated versions?

Regards!

---

### Post by P-I H on 2019-05-08
Perhaps it's related to this problem
[https://phoronix.com/scan.php?page=news_item&px=AMD-MP2-I2C-Linux-5.2](https://phoronix.com/scan.php?page=news_item&px=AMD-MP2-I2C-Linux-5.2)

---

