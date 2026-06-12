---
title: "Can’t interact with the Desktop coming out of sleep"
date: 2020-09-01
forum: Ubuntu Development Version
---

### Post by Yahoé on 2020-09-01
I’m trying out Groovy on a new Dell Inspiron 15 5585 laptop (Ryzen 5 3500U).

After waking the computer from its sleep, if the screen lock option is enabled, I see the password input screen but can’t enter a password, though I can move the mouse cursor around.
If the screen lock option is not enabled, I land on the desktop, I can move the mouse around, but otherwise can’t interact with the desktop, either with the mouse or the keyboard.
I have the same issue under Gnome or Unity (I even tried to uninstall Unity to no avail).

Any idea what the problem may be here?

---

### Post by corradoventu on 2020-09-10
On my Dell Inspiron 3793 I have a similar problem: after sleep I have just a black screen and can only do power-off pressing power-off button for some seconds.

```
corrado@corrado-n4-gg-0905:~$ inxi -SCGM
System:
  Host: corrado-n4-gg-0905 Kernel: 5.8.0-18-generic x86_64 bits: 64 
  Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Laptop System: Dell product: Inspiron 3793 v: N/A 
  serial: <superuser/root required> 
  Mobo: Dell model: 0C1PF2 v: A00 serial: <superuser/root required> 
  UEFI: Dell v: 1.5.0 date: 12/17/2019 
CPU:
  Info: Quad Core model: Intel Core i5-1035G1 bits: 64 type: MT MCP 
  L2 cache: 6144 KiB 
  Speed: 610 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 1155 2: 1068 
  3: 1799 4: 2894 5: 1117 6: 1124 7: 862 8: 3195 
Graphics:
  Device-1: Intel Iris Plus Graphics G1 driver: i915 v: kernel 
  Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics (ICL GT1) v: 4.6 Mesa 20.1.5 
corrado@corrado-n4-gg-0905:~$
```

---

### Post by Yahoé on 2020-09-19
Does anyone know what may be causing this issue?

---

### Post by P-I H on 2020-09-19
Suspend works on my desktop computer.
It's an Ryzen cpu on an Asus motherboard. 
To make it work I have disabled IOMMU in bios.
I have also added "iommu=soft" in GRUB_CMDLINE_LINUX="" in /etc/default/grub
There is a bug report
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1848771](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1848771)

---

