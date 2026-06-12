---
title: "Stuck during boot up"
date: 2020-02-03
forum: Ubuntu Development Version
---

### Post by Yahoé on 2020-02-03
Hi,

This morning, my Focal workstation gets stuck during boot up "/dev/sda/ clean".
How could I find out what is happening?
I can Ctrl-Alt-F1, log in, update the system without problem.

---

### Post by CelticWarrior on 2020-02-03
Do you have Nvidia graphics and perhaps installed the drivers using the Nvidia binaries from their website?

---

### Post by P-I H on 2020-02-03
Have a similar problem.
Boot hangs with only a cursor at top left when I rebooted the system this morning.
However I am able to boot in rescue mode.
The problem seems to be GPU related.
I got an error message that the GPU didn't support wayland. I changed to X11 in /etc/gdm3/custom.conf, but this didn't help. I have still to boot in rescue mode.
Now I get the error message "[drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting."
I also get an error message from the avahi-daemon "chroot.c: open() failed: No such file or directory"
My system
```
p-i@pi-Asus-Rog-Strix-B450-F:~$ inxi -Fz
System:    Host: pi-Asus-Rog-Strix-B450-F Kernel: 5.4.0-12-generic x86_64 bits: 64 Desktop: Gnome 3.34.3 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1375 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1375 2: 1375 3: 1375 4: 1375 5: 1375 6: 1375 7: 1377 
           8: 1375 9: 1375 10: 1375 11: 1374 12: 1375 13: 1648 14: 1375 15: 1375 16: 1375 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: N/A 
           Display: x11 server: X.Org 1.20.7 driver: ati,fbdev unloaded: modesetting,radeon,vesa resolution: 2560x1440~93Hz 
           OpenGL: renderer: llvmpipe (LLVM 9.0.1 128 bits) v: 3.3 Mesa 20.1.0-devel (git-a4e6270 2020-02-03 focal-oibaf-ppa) 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-12-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 680.02 GiB used: 87.25 GiB (12.8%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 227.74 GiB used: 87.24 GiB (38.3%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 40.0 C mobo: 35.0 C 
           Fan Speeds (RPM): cpu: 502 case-1: 884 case-2: 825 case-3: 466 
Info:      Processes: 391 Uptime: 23m Memory: 15.56 GiB used: 2.10 GiB (13.5%) Shell: bash inxi: 3.0.37 
p-i@pi-Asus-Rog-Strix-B450-F:~$ 

```

---

### Post by CelticWarrior on 2020-02-03
> **P-I H said:**
> Have a similar problem.

Similar maybe but most likely not the same hardware.
You should open your own thread.

---

### Post by P-I H on 2020-02-03
This is the development version of Ubuntu. Mostly we discuss problems of this type (in this case boot problems) in the same thread.
Booted another 20.04 system worked fine. Updated and got the same problem. Only boot in rescue mode. This time with the wrong resolution.
The system
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:
  Host: pi-MS-7A34 Kernel: 5.4.0-12-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.3 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 
  serial: <filter> UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:
  Topology: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 1377 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1377 2: 1377 
  3: 1379 4: 1375 
Graphics:
  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
  driver: N/A 
  Display: x11 server: X.Org 1.20.7 driver: ati,fbdev 
  unloaded: modesetting,radeon,vesa resolution: 1024x768~76Hz 
  OpenGL: renderer: llvmpipe (LLVM 9.0.1 128 bits) 
  v: 3.3 Mesa 20.1.0-devel (git-a4e6270 2020-02-03 focal-oibaf-ppa) 
Audio:
  Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
  Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] 
  driver: snd_hda_intel 
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-12-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 454.60 GiB used: 47.28 GiB (10.4%) 
  ID-1: /dev/sda vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
  ID-2: /dev/sdb vendor: Samsung model: SSD 830 Series size: 119.24 GiB 
  ID-3: /dev/sdc vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
Partition:
  ID-1: / size: 218.57 GiB used: 47.24 GiB (21.6%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 35.0 C mobo: 34.0 C 
  Fan Speeds (RPM): fan-1: 0 fan-2: 830 fan-3: 834 fan-4: 0 fan-5: 665 
  fan-6: 733 
Info:
  Processes: 272 Uptime: 5m Memory: 15.65 GiB used: 1.68 GiB (10.7%) 
  Shell: bash inxi: 3.0.37 
p-i@pi-MS-7A34:~$ 

```

---

### Post by Yahoé on 2020-02-03
> **CelticWarrior said:**
> Do you have Nvidia graphics and perhaps installed the drivers using the Nvidia binaries from their website?

Hi[COLOR=#000000] CelticWarrior, Thanks for your help. No, integrated graphics on a Ryzen  [/COLOR]3 3200G

---

### Post by Yahoé on 2020-02-04
I had ppa oibaf/graphics-drivers on this machine. I ppa-purged it and the desktop environment now loads just fine.

---

### Post by P-I H on 2020-02-04
Good to know. 
That's also the case with my two installations with boot problems. I made a new install on the [COLOR=#000000][FONT=&quot]pi-MS-7A34 system, [/FONT][/COLOR]that worked without problems. Will purge the oibaf-ppa on the other installation.

---

### Post by P-I H on 2020-02-07
Started and updated my other 20.04 system. The oibaf ppa is working now.

---

### Post by tontoncypher on 2020-02-09
May be Kernel issue, or graphic drivers.

---

