---
title: "The release ISO is availble"
date: 2019-04-18
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-04-18
[http://releases.ubuntu.com/disco/](http://releases.ubuntu.com/disco/)
```
corrado@corrado-p5-disco:~$ cat /var/log/installer/media-info
Ubuntu 19.04 "Disco Dingo" - Release amd64 (20190416)
corrado@corrado-p5-disco:~$ inxi -SCGx
System:    Host: corrado-p5-disco Kernel: 5.0.0-13-generic x86_64 bits: 64 compiler: gcc v: 8.3.0 
           Desktop: Gnome 3.32.0 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.4 driver: i915 resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 19.0.2 
           direct render: Yes 
corrado@corrado-p5-disco:~$ 



```

---

### Post by Frogs Hair on 2019-04-18
On to the next one ! :o

```
david@dual:~$ lsb_release -a   
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco
```
```
david@dual:~$ echo $XDG_CURRENT_DESKTOP
Budgie:GNOME

```

---

### Post by thenailedone on 2019-04-18
Most polished looking release of Ubuntu perhaps ever?!

---

