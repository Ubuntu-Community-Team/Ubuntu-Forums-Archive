---
title: "The iso of April 3 is still defined as alpha"
date: 2019-04-03
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-04-03
The iso of April 3 is still defined as alpha in /var/log/installer/media-info Ubuntu 19.04 "Disco Dingo" - Alpha amd64 (20190403)
and an unusable examples.desktop is still present in the generated Home directory
Otherwise the installation runs smoothly on my hardware
```
corrado@corrado-p5-dd-0403:~$ inxi -SCG
System:
  Host: corrado-p5-dd-0403 Kernel: 5.0.0-8-generic x86_64 bits: 64 
  Desktop: Gnome 3.32.0 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.4 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) 
  v: 4.5 Mesa 19.0.1 
corrado@corrado-p5-dd-0403:~$ 


```

---

### Post by Frogs Hair on 2019-04-03
This is day 15 on this Ubuntu Budgie installation and it runs as well a final release.

```
david@dual:~$ inxi -SCG
System:
  Host: dual Kernel: 5.0.0-8-generic x86_64 bits: 64 Desktop: Budgie 10.5 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Quad Core model: AMD Athlon II X4 645 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 800 MHz min/max: 800/3100 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: NVIDIA GF108 [GeForce GT 730] driver: nvidia v: 390.116 
  Display: x11 server: X.Org 1.20.4 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1680x1050~60Hz 
  OpenGL: renderer: GeForce GT 730/PCIe/SSE2 v: 4.6.0 NVIDIA 390.116 
david@dual:~$ 


```

---

