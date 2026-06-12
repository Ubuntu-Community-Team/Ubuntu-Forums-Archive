---
title: "Ubuntu 20.04.1"
date: 2020-06-15
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-06-15
Installed the development version of Ubuntu 20.04.1 on a Kingston A2000 M.2 500GB installed on a Delock PCI Express X4 Card. The installation went fine, however the existing Ubuntu 20.04 installation on a SSD disk disappeared in BIOS. It is however possible to boot from the grub menu.
You never know how grub and BIOS interact.
```
p-i@asus-b450-f:~$ inxi -Fz
System:    Kernel: 5.4.0-38-generic x86_64 bits: 64 Desktop: Gnome 3.36.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1377 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1373 2: 1374 3: 1374 4: 1375 5: 1375 6: 1372 7: 1375 
           8: 1374 9: 1375 10: 1372 11: 1370 12: 1375 13: 1372 14: 1375 15: 1371 16: 1369 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.35.0 5.4.0-38-generic LLVM 9.0.1) v: 4.6 Mesa 20.0.4 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-38-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 680.02 GiB used: 36.72 GiB (5.4%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/nvme2n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-4: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 456.96 GiB used: 36.66 GiB (8.0%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 43.6 C mobo: 38.0 C gpu: amdgpu temp: 48 C 
           Fan Speeds (RPM): cpu: 706 case-1: 914 case-2: 832 case-3: 582 gpu: amdgpu fan: 0 
Info:      Processes: 398 Uptime: 5h 04m Memory: 15.56 GiB used: 3.45 GiB (22.2%) Shell: bash inxi: 3.0.38 
p-i@asus-b450-f:~$ 

```

---

