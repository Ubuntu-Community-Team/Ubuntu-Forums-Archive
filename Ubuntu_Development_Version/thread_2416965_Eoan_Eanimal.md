---
title: "Eoan Eanimal"
date: 2019-04-18
forum: Ubuntu Development Version
---

### Post by harry332 on 2019-04-18
And here starts the Ubuntu 19.10 (Eoan Eanimal):

[Distro-info-data]("https://launchpad.net/ubuntu/+source/distro-info-data/0.39ubuntu2")

* Copy data from 0.39ubuntu2:
    - Add Ubuntu 19.10 Eoan EANIMAL. (LP: [#1825379]("https://launchpad.net/bugs/1825379"))

Not the full name but "Eoan" is correct.

---

### Post by thenailedone on 2019-04-18
Not getting the six monthly post of alliteration from Mark makes me sad.

---

### Post by cpatrick08 on 2019-04-19
me too

---

### Post by dino99 on 2019-04-19
First step done:

Description:	Ubuntu Eoan EANIMAL (development branch)
Release:	19.10
Codename:	eoan

---

### Post by Frogs Hair on 2019-04-19
Distro info:

[https://bugs.launchpad.net/ubuntu/+source/distro-info-data/+bug/1825379](https://bugs.launchpad.net/ubuntu/+source/distro-info-data/+bug/1825379)

---

### Post by corradoventu on 2019-04-21
1st ISO available [http://cdimage.ubuntu.com/ubuntu/daily-live/pending/](http://cdimage.ubuntu.com/ubuntu/daily-live/pending/)

software-properties-gtk crashed with aptsources.distro.NoDistroTemplateException in get_sources(): Error: could not find a distribution template for Ubuntu/eoan

---

### Post by P-I H on 2019-04-22
Made a new installation of Ubuntu 19.04 on my nvme disk and upgraded my system test disk to Eoan

```
p-i@pi-MS-7A34:~$ inxi -F
System:
  Host: pi-MS-7A34 Kernel: 5.0.0-13-generic x86_64 bits: 64 
  Desktop: Gnome 3.32.0 Distro: Ubuntu 19.10 (Eoan EANIMAL) 
Machine:
  Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 
  serial: <root required> UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1378 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1377 2: 1375 
  3: 1375 4: 1379 5: 1374 6: 1376 7: 1376 8: 1376 9: 1377 10: 1374 11: 1378 
  12: 1373 13: 1376 14: 1375 15: 1377 16: 1377 
Graphics:
  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X] 
  driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.4 driver: amdgpu tty: N/A 
  OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.27.0 
  5.0.0-13-generic LLVM 8.0.0) 
  v: 4.5 Mesa 19.0.2 
Audio:
  Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
  Device-2: AMD Ellesmere [Radeon RX 580] driver: snd_hda_intel 
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel 
  Device-4: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
  Sound Server: ALSA v: k5.0.0-13-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: 4c:cc:6a:f4:2d:5e 
Drives:
  Local Storage: total: 689.34 GiB used: 54.83 GiB (8.0%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 250GB 
  size: 232.89 GiB 
  ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
  ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition:
  ID-1: / size: 218.57 GiB used: 54.83 GiB (25.1%) fs: ext4 dev: /dev/sdb2 
Sensors:
  System Temperatures: cpu: 39.0 C mobo: 39.0 C gpu: amdgpu temp: 33 C 
  Fan Speeds (RPM): fan-1: 504 fan-2: 571 fan-3: 972 fan-4: 0 fan-5: 770 
  fan-6: 0 gpu: amdgpu fan: 1164 
Info:
  Processes: 375 Uptime: N/A Memory: 15.67 GiB used: 1.12 GiB (7.1%) 
  Shell: bash inxi: 3.0.33 
p-i@pi-MS-7A34:~$ 

```

---

### Post by corradoventu on 2019-04-23
software-properties crash - does not start
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1825738](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1825738)
software-properties-gtk crashed with
aptsources.distro.NoDistroTemplateException in get_sources(): Error:
could not find a distribution template for Ubuntu/eoan

---

### Post by cariboo on 2019-04-23
Try adding:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eaon-proposed restricted universe main multiverse

to your sources list. I haven't tried synaptic yet, so I haven't run into the problem yet.

Set the server to the one you use.

---

### Post by corradoventu on 2019-04-23
synaptic works fine, also apt from terminal is ok, the problem is with software properties (crash at start) and Ubuntu Software (shows snaps only)

---

### Post by corradoventu on 2019-05-07
Eoan Ermine

```
corrado@corrado-p6-ee-0506:~$ inxi -S
System:    Host: corrado-p6-ee-0506 Kernel: 5.0.0-13-generic x86_64 bits: 64 
           Desktop: Gnome 3.32.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
corrado@corrado-p6-ee-0506:~$ 
```

---

### Post by harryjackson123 on 2019-05-07
[COLOR=#333333][FONT=monospace]This bug was fixed in the package distro-info-data - 0.18ubuntu0.12[/FONT][/COLOR]

---

