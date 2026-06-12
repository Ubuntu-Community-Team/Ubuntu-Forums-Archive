---
title: "Ubuntu 18.10 daily build xorg"
date: 2018-08-16
forum: Ubuntu Development Version
---

### Post by olaf.jorgensen on 2018-08-16
Can someone answer me if  the daily builds using xorg 1.20 now?

---

### Post by dino99 on 2018-08-16
Cant be fully affirmative, but: xorg 1.20 is used into archive since 02 Jul, and the daily iso was built on 23 Jul; so using 1.20 probability seems very high.

Actual archive:
stable: 1.19.6
proposed: 1.20

Is the daily iso built with the stable or proposed ? cant tell myself.

---

### Post by olaf.jorgensen on 2018-08-16
Thanks for answer i will try it tonight

---

### Post by P-I H on 2018-08-16
My fully updated Cosmic Cuttlefish has these components, without proposed enabled
```
p-i@pi-MS-7A34:~$ inxi -F
System:
  Host: pi-MS-7A34 Kernel: 4.17.0-6-generic x86_64 bits: 64 
  Desktop: Gnome 3.29.90 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 
  serial: <root required> UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1560 MHz min/max: 1550/3000 MHz Core speeds (MHz): 1: 1546 2: 1542 
  3: 1550 4: 1541 5: 1550 6: 1548 7: 1549 8: 1550 9: 1556 10: 1542 11: 1550 
  12: 1549 13: 1552 14: 1554 15: 1550 16: 1549 
Graphics:
  Card-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X] driver: amdgpu 
  v: kernel 
  Display: x11 server: X.Org 1.19.6 driver: amdgpu tty: N/A 
  OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.25.0 
  4.17.0-6-generic LLVM 6.0.1) 
  v: 4.5 Mesa 18.1.5 
Audio:
  Card-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
  Card-2: AMD Ellesmere [Radeon RX 580] driver: snd_hda_intel 
  Card-3: AMD Family 17h HD Audio driver: snd_hda_intel 
  Card-4: Logitech Webcam C250 type: USB driver: uvcvideo,snd-usb-audio 
  Sound Server: ALSA v: k4.17.0-6-generic 
Network:
  Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: 4c:cc:6a:f4:2d:5e 
Drives:
  Local Storage: total: 689.34 GiB used: 83.52 GiB (12.1%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 250GB 
  size: 232.89 GiB 
  ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
  ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition:
  ID-1: / size: 227.74 GiB used: 83.52 GiB (36.7%) fs: ext4 
  dev: /dev/nvme0n1p2 
Sensors:
  System Temperatures: cpu: 38.0 C mobo: 35.0 C gpu: amdgpu temp: 31 C 
  Fan Speeds (RPM): fan-1: 333 fan-2: 337 fan-3: 970 fan-4: 0 fan-5: 757 
  fan-6: 0 gpu: amdgpu fan: 1170 
Info:
  Processes: 347 Uptime: N/A Memory: 15.68 GiB used: 874.8 MiB (5.4%) 
  Shell: bash inxi: 3.0.20 
p-i@pi-MS-7A34:~$

```

---

### Post by olaf.jorgensen on 2018-08-16
Ok. So its not out iet. I will install it anyway. Thanks for answers!

---

### Post by mc4man on 2018-08-16
To find out what's on the current image just read the manifest here - [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
For horses mouth on xorg-xserver  - [https://launchpad.net/ubuntu/+source/xorg-server](https://launchpad.net/ubuntu/+source/xorg-server)

---

### Post by rrnbtter on 2018-08-17
Greetings,
This is what I have. 

 Display: wayland server: X.Org 1.20.0 driver: i915  Proposed enabled (as always).

---

### Post by olaf.jorgensen on 2018-08-17
How did you get 1.20?

---

### Post by dino99 on 2018-08-17
> **olaf.jorgensen said:**
> How did you get 1.20?

via the 'proposed' archive ):P

---

### Post by rrnbtter on 2018-08-17
Greetings,

> **dino99 said:**
> via the 'proposed' archive ):P


+1

---

### Post by olaf.jorgensen on 2018-08-18
If its not to much to ask,can you tell me how to get it?

---

### Post by cariboo on 2018-08-18
Enable the proposed archive. Open Software & Updates, click the Developer Options tab and enable Pre-released updates (cosmic proposed)

---

### Post by olaf.jorgensen on 2018-08-18
Thanks found it!, its looking much better with flat theme!

---

### Post by amano on 2018-08-19
Just to clarify: Using “proposed“ on the development version of Ubuntu is highly discouraged and can lead to major breakages.

Just in case that you did not know...

---

### Post by olaf.jorgensen on 2018-08-22
Thanks for the info, but i knew :) 

My problem with ubuntu 18.4.1 and 18.10 is nvidia optimus, but the xorg 1.20 did not make any difference and as long as wayland dont work with optimus i just have to wait.

---

### Post by dino99 on 2018-08-22
> **olaf.jorgensen said:**
> Thanks for the info, but i knew :) 

My problem with ubuntu 18.4.1 and 18.10 is nvidia optimus, but the xorg 1.20 did not make any difference and as long as wayland dont work with optimus i just have to wait.

Have you tried a gnome on xorg session ?

---

### Post by mc4man on 2018-08-22
> **olaf.jorgensen said:**
> Thanks for the info, but i knew :) 

My problem with ubuntu 18.4.1 and 18.10 is nvidia optimus, but the xorg 1.20 did not make any difference and as long as wayland dont work with optimus i just have to wait.

Optimus usually works fine with xorg, as far as Wayland you may be waiting a long time..

---

### Post by olaf.jorgensen on 2018-08-24
Yes i am using xorg as main but its sluggish and lagging using firefox/ chrome after screentearing fix, i find KDE much better here, but i would like to use Gnome not KDE.

---

