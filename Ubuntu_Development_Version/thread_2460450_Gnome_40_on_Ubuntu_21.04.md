---
title: "Gnome 40 on Ubuntu 21.04"
date: 2021-04-10
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-04-10
I installed [https://launchpad.net/~shemgp/+archive/ubuntu/gnome-40](https://launchpad.net/~shemgp/+archive/ubuntu/gnome-40) ... no problem, but I'm better off with the old gnome
```
corrado@corrado-p6-hh-0410x:~$ inxi -Fx
System:    Host: corrado-p6-hh-0410x Kernel: 5.11.0-13-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
           Desktop: GNOME 40.0 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:   Type: Desktop Mobo: ASRock model: H110M-G/M.2 serial: <superuser required> UEFI: American Megatrends 
           v: P1.10 date: 05/11/2017 
CPU:       Info: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3 MiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: ARC USB 2.0 Camera type: USB driver: uvcvideo bus ID: 3-1.3:3 
           Display: wayland server: X.Org 1.21.0.99 compositor: gnome-shell driver: loaded: i915 
           note: n/a (using device driver) resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 21.0.1 direct render: Yes 
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: ASRock driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 
           Device-2: Logitech QuickCam Pro 9000 type: USB driver: snd-usb-audio,uvcvideo bus ID: 1-2:2 
           Sound Server: ALSA v: k5.11.0-13-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: kernel port: f040 bus ID: 00:1f.6 
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86 
           Device-2: D-Link DWA-121 802.11n Wireless N 150 Pico Adapter [Realtek RTL8188CUS] type: USB 
           driver: rtl8192cu bus ID: 1-5:4 
           IF: wlx48ee0c2322b8 state: down mac: 48:ee:0c:23:22:b8 
Drives:    Local Storage: total: 2.05 TiB used: 17.45 GiB (0.8%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SKC2000M8250G size: 232.89 GiB temp: 30.9 C 
           ID-2: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB 
           ID-3: /dev/sdb vendor: Hitachi model: HDS721010CLA332 size: 931.51 GiB 
Partition: ID-1: / size: 31.25 GiB used: 6.28 GiB (20.1%) fs: ext4 dev: /dev/nvme0n1p6 
           ID-2: /boot/efi size: 252 MiB used: 7.8 MiB (3.1%) fs: vfat dev: /dev/nvme0n1p1 
Swap:      ID-1: swap-1 type: partition size: 8 GiB used: 0 KiB (0.0%) dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 46.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 220 Uptime: 3h 03m Memory: 7.48 GiB used: 2.04 GiB (27.2%) Init: systemd runlevel: 5 Compilers: 
           gcc: N/A Packages: 1721 Shell: Bash v: 5.1.4 inxi: 3.3.01 
corrado@corrado-p6-hh-0410x:~$ 

```

---

