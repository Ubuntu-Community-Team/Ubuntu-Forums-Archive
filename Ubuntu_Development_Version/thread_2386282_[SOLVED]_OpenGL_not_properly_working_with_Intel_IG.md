---
title: "[SOLVED] OpenGL not properly working with Intel IGP"
date: 2018-03-03
forum: Ubuntu Development Version
---

### Post by roots on 2018-03-03
Hi all,

I'm running Ubuntu 18.04 Bionic daily with proposed updates enabled. I am using gnome-flashback (gnome-panel) with Compiz. 

I first recognised that Compiz is giving very high CPU loads according to top. At the same time, intel_gpu_top shows GPU usage at an unchanged 0%. The same happens when running glmark2: CPU usage climbs to >400% while GPU stays at 0%. Interestingly, OpenGL seems to be enabled - please see the glxinfo outputs below. Switching to todays latest oibaf drivers did not make any
difference.

Any pointers are much appreciated.

r.

---

H/W:

CPU: Core i7-7700k @ 5GHz
GPU: Using Intel IGP (HD630)
RAM: 16GB DDR4
SSD: Intel Optane

S/W:

```
$ cat /proc/version
Linux version 4.15.0-11-generic (buildd@lgw01-amd64-016) (gcc version 7.3.0 (Ubuntu 7.3.0-5ubuntu1)) #12-Ubuntu SMP Fri Feb 23 18:39:58 UTC 2018
```

```
$ lspci -nnk | grep -iA2 vga 
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 630 [8086:5912] (rev 04)   Subsystem: Gigabyte Technology Co., Ltd HD Graphics 630 [1458:d000]
        Kernel driver in use: i915
```

```
$ modinfo i915
srcversion:     4963AD5BD78D754BBD09EAF
name:           i915
vermagic:       4.15.0-11-generic SMP mod_unload 
signat:         PKCS#7
```

```
$ dpkg -l | grep xserver-xorg-video-intel 
ii  xserver-xorg-video-intel                   2:2.99.917+git20171229-1                   amd64
$ dpkg -l | grep xorg
ii  xorg                                       1:7.7+19ubuntu5                           amd64
$dpkg -l | grep mesa
ii  libegl1-mesa:amd64                         18.0.0~rc4-1ubuntu3
```

```
$ glxinfo | grep -i opengl
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 6.0, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.1.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.1 Mesa 18.1.0-devel
OpenGL shading language version string: 1.40
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```

```
$ glxinfo | grep -i direct
direct rendering: Yes
    GL_ARB_direct_state_access, GL_ARB_draw_buffers, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect,
```

---

### Post by mc4man on 2018-03-03
Well you are using llvmpipe, i.e "OpenGL renderer string: llvmpipe (LLVM 6.0, 256 bits)"
This is because you've used -proposed. Maybe it'll square away thru future updates, maybe not. Your best bet is to do a fresh install & not use -proposed

---

### Post by roots on 2018-03-03
Thanks a lot - this was spot-on. Just did a clean reinstall w/o proposed and it's working like a charm now.

T H A N K S !

r.

---

