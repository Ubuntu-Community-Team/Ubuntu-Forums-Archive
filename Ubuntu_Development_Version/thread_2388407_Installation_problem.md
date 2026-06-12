---
title: "Installation problem"
date: 2018-04-02
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-04-02
Installed the 30/3 ISO on my main computer.
Had to set UEFI/Legacy in bios to boot with the USB drive.
Tried first with Update 17.10, but this didn't work. Tried a second time with Erase disk and install Ubuntu, but now the installation program crashed.
Rebooted and tried with Someting else and this worked.
I only had one disk connected /dev/nvme0n1p1.
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-13-generic x86_64 bits: 64
           Desktop: Gnome 3.28.0
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3531 MHz 1: 3377 MHz 2: 3531 MHz 3: 3012 MHz
           4: 3010 MHz 5: 3007 MHz 6: 3360 MHz 7: 3012 MHz 8: 3370 MHz
           9: 3000 MHz 10: 2990 MHz 11: 3015 MHz 12: 3026 MHz 13: 3008 MHz
           14: 3031 MHz 15: 3015 MHz 16: 3028 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580]
           Display Server: x11 (X.Org 1.19.6 ) driver: amdgpu
           Resolution: 2560x1440@143.99hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-13-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-13-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
         
Drives:    HDD Total Size: 740.2GB (6.6% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 46G (21%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: 42.0C gpu: 41.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 647 fan-2: 697 fan-3: 1076 fan-4: 0 fan-5: 811
Info:      Processes: 389 Uptime: 10:13 Memory: 3519.7/16054.5MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-MS-7A34:~$
```

---

