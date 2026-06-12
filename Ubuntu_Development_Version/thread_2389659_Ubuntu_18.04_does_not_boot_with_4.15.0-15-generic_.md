---
title: "Ubuntu 18.04 does not boot with 4.15.0-15-generic and 4.15.0-17-generic kernels"
date: 2018-04-19
forum: Ubuntu Development Version
---

### Post by rrohde on 2018-04-19
Hi, 

running a Dell XPS 15, now only kernel 4.15.0-13-generic works and allows me to boot. Both 4.15.0-15-generic and 4.15.0-17-generic will hang forever (with what I believe to be a 'soft CPU lockup' or along these lines message). 

The workaround is to boot either of these newer kernels into recovery mode, and then select 'normal boot'. 

I find this issue rather discouraging this close to the release of 18.04. Any ideas as to fix this issue? 

Thanks.

---

### Post by mc4man on 2018-04-19
Are you using any proprietary video drivers?

---

### Post by rrohde on 2018-04-20
No. Intel® HD Graphics 630 (Kaby Lake GT2) by default.

---

### Post by corradoventu on 2018-04-20
Probably it does bot depend on CPU or graphic, I have similar hardware and no problems:```
corrado@corrado-p8-bb-0308:~$ inxi -SCGx
System:    Host: corrado-p8-bb-0308 Kernel: 4.15.0-15-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
corrado@corrado-p8-bb-0308:~$ 

```

---

### Post by rrohde on 2018-04-20
Here's my inxi output: 

```
CPU:       Quad core Intel Core i7-7700HQ (-MT-MCP-) arch: Skylake rev.9 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 22464
           clock speeds: max: 3800 MHz 1: 3227 MHz 2: 3369 MHz 3: 3358 MHz 4: 3217 MHz 5: 3283 MHz 6: 3291 MHz
           7: 3308 MHz 8: 3423 MHz

Graphics:  Card-1: Intel Device 591b bus-ID: 00:02.0
           Card-2: NVIDIA GP107M [GeForce GTX 1050 Mobile] bus-ID: 01:00.0
           Display Server: X.Org 1.19.6 drivers: fbdev (unloaded: modesetting,vesa)
           Resolution: 1920x1080@59.93hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
```

---

### Post by rrohde on 2018-04-20
Oh, and the only non-default thing I did to my installation is use ecryptfs to encrypt my home directory and swap file (dualbooting with Windows on a single SSD prevents me from using LUKS for full disk encryption).

---

