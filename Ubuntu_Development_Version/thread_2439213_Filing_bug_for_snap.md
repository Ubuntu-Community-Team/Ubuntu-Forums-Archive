---
title: "Filing bug for snap"
date: 2020-03-24
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-03-24
On Ubuntu 20.04 snap-store in Wayland session does not start with a message 'Segmentation fault (core dumped)'
[https://forum.snapcraft.io/t/snap-store-segmentation-fault-in-wayland-session/16153/2](https://forum.snapcraft.io/t/snap-store-segmentation-fault-in-wayland-session/16153/2)
where is the dump? what documentation can i send to developers?

```
corrado@corrado-x4-ff-0315:~$ snap list
Name Version Rev Tracking Publisher Notes
core 16-2.43.3 8689 latest/stable canonical&#10003; core
core18 20200124 1668 latest/stable canonical&#10003; base
gnome-3-34-1804 0+git.2c86692 21 latest/stable/… canonical&#10003; -
gtk-common-themes 0.1-29-g45e78c5 1474 latest/stable/… canonical&#10003; -
snap-store 20200318.3b39451 308 latest/stable/… canonical&#10003; -
corrado@corrado-x4-ff-0315:~$ snap run snap-store
Segmentation fault (core dumped)
corrado@corrado-x4-ff-0315:~$
```

---

### Post by slickymaster on 2020-03-24
Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output in a thread

---

### Post by P-I H on 2020-03-24
No help, but I don't get that problem

---

### Post by corradoventu on 2020-03-24
I have the same problem on 2 different installations of Ubuntu 20.04```
corrado@corrado-p7-ff-0302:~$ snap list
Name               Version                     Rev   Tracking         Publisher   Notes
core               16-2.43.3                   8689  latest/stable    canonical&#10003;  core
core18             20200124                    1668  latest/stable    canonical&#10003;  base
gnome-3-28-1804    3.28.0-16-g27c9498.27c9498  116   latest/stable    canonical&#10003;  -
gnome-3-34-1804    0+git.2c86692               21    latest/stable/…  canonical&#10003;  -
gtk-common-themes  0.1-29-g45e78c5             1474  latest/stable/…  canonical&#10003;  -
snap-store         20200318.3b39451            308   latest/stable/…  canonical&#10003;  -
corrado@corrado-p7-ff-0302:~$ snap run snap-store
Segmentation fault (core dumped)
corrado@corrado-p7-ff-0302:~$ inxi -SCGx
System:    Host: corrado-p7-ff-0302 Kernel: 5.4.0-18-generic x86_64 bits: 64 compiler: gcc v: 9.2.1 Desktop: Gnome 3.35.91 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 801 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Display: wayland server: X.Org 1.20.7 driver: i915 resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.0.0 direct render: Yes 
corrado@corrado-p7-ff-0302:~$ 



```

---

