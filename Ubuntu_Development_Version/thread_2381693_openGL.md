---
title: "openGL"
date: 2018-01-04
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-01-04
The Wayland login and my openGL renderer "Radeon RX 580 Series" disappeared after today's updates.
There will be no more gaming until this is solved.
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-041500rc3-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3711 MHz 1: 3011 MHz 2: 3019 MHz 3: 3019 MHz
           4: 3027 MHz 5: 3011 MHz 6: 3375 MHz 7: 3711 MHz 8: 3464 MHz
           9: 3013 MHz 10: 2914 MHz 11: 3004 MHz 12: 3005 MHz 13: 3002 MHz
           14: 3080 MHz 15: 3529 MHz 16: 3004 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480]
           Display Server: x11 (X.Org 1.19.5 )
           drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1920x1200@0.00hz
           OpenGL: renderer: llvmpipe (LLVM 5.0, 128 bits)
           version: 3.3 Mesa 17.2.4
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: ALSA v: k4.15.0-041500rc3-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
            
Drives:    HDD Total Size: 740.2GB (13.7% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 219G used: 95G (46%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 38.0C
           Fan Speeds (in rpm): cpu: N/A fan-1: 491 fan-2: 426 fan-3: 978 fan-4: 0 fan-5: 759
Info:      Processes: 346 Uptime: 10 min Memory: 1952.0/16056.5MB
           Client: Shell (bash) inxi: 2.3.45 
p-i@pi-MS-7A34:~$

```

inxi on the same computer with Ubuntu 17.10 looks like this
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.13.0-21-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3749 MHz 1: 3749 MHz 2: 3749 MHz 3: 3749 MHz
           4: 3749 MHz 5: 3749 MHz 6: 3749 MHz 7: 3749 MHz 8: 3749 MHz
           9: 3749 MHz 10: 3749 MHz 11: 3749 MHz 12: 3749 MHz 13: 3749 MHz
           14: 3749 MHz 15: 3749 MHz 16: 3749 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480]
           Display Server: wayland (X.Org 1.19.5 ) driver: amdgpu
           Resolution: 1920x1200@59.88hz
           OpenGL: renderer: Radeon RX 580 Series (AMD POLARIS10 / DRM 3.18.0 / 4.13.0-21-generic, LLVM 5.0.0)
           version: 4.5 Mesa 17.2.2
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Device aaf0
           driver: snd_hda_intel
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.13.0-21-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
           
Drives:    HDD Total Size: 490.1GB (24.7% used)
           ID-1: /dev/nvme0n1 model: N/A size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 113G (53%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 38.0C gpu: 31.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 502 fan-2: 414 fan-3: 983 fan-4: 0 fan-5: 794
Info:      Processes: 382 Uptime: 4 min Memory: 1667.1/16057.2MB
           Client: Shell (bash) inxi: 2.3.37 
p-i@pi-MS-7A34:~$ 

```

---

### Post by P-I H on 2018-01-05
The problem is kernel related. When I boot with the "4.13.0-17-generic x86_64" kernel the system works OK.

---

### Post by Yellow Pasque on 2018-01-05
You are still using 4.15 rc**3**? rc6 is out now. Maybe try upgrading to that first.

---

### Post by P-I H on 2018-01-06
I removed 4.15-rc3 and went back to the 4.13.0-17 kernel, which still is used in Bionic in case you don't have proposed enabled.
I will wait to try a new kernel until the problems with Meltdown and Spectre are solved.
Also there hasn't been a new Daily Build available since 3/12.

---

### Post by xeizoo on 2018-01-06
> **P-I H said:**
> I removed 4.15-rc3 and went back to the 4.13.0-17 kernel, which still is used in Bionic in case you don't have proposed enabled.
I will wait to try a new kernel until the problems with Meltdown and Spectre are solved.
Also there hasn't been a new Daily Build available since 3/12.

You would want to run the  4.14.0-14.17 kernel which is now available, it has the patch for Meltdown and Spectre and openGL is working at least on my Nvidia-box.

---

### Post by P-I H on 2018-01-08
Installed 4.15.0-041500rc7, with the patch for Meltdown and Spectre, that works OK.
Made some performance tests, with about the same results as before. 
CIV VI 20.93 turn rater
K10 max temp 55 degrees
CIV VI + Handbrake to encode the file "SES.Astra.UHD.Test.1.2160p.UHDTV.AAC.HEVC.x265-LiebeIst.mkv" using the preset "Fast 1080p30"
ETA 2.34 minutes
Average FPS 44.68
K10 max temp 75 degrees

---

### Post by Yellow Pasque on 2018-01-08
So did that kernel solve the problem with no hardware 3D accel? If so, please mark your thread solved (thread tools menu above first post).

---

