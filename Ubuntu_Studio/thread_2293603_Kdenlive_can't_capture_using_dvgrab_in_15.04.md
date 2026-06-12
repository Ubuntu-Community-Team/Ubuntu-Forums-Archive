---
title: "Kdenlive can't capture using dvgrab in 15.04"
date: 2015-09-06
forum: Ubuntu Studio
---

### Post by GeorgeKar on 2015-09-06
Recently I upgrade ubuntu studio to 15.04 from 14.04 with a middle step in 14.10.
I found a problem in kdenlive, using dvgrab. I can handle av controls but when I start capture kdenlive disconnect. I make a small program in gambas 3 and I did use dvgrab the same way as I did in kdenlive before broken, splitting my video on records and adding date and time in file name.
I have a Sony HDV  camera and for 2 years I am user of kdenlive with no problems.
Kdenlive 9,10

---

### Post by GeorgeKar on 2015-09-09
I found solution. FFmpeg have a faulty link to cuda library. Purge ffmpeg (was installed manual,  so melt and Kdenlive didn't removed), reinstall nuoveau drivers, purge any nvidia*, reinstall nvidia, do exactly installing ffmpeg from git : [https://kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source/installing-ffmpeg](https://kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source/installing-ffmpeg). Kdenlive use now an old VIA chip firewire (PCI) without ohci old drivers
```

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

ffmpeg version N-75137-g2c1ec57 Copyright (c) 2000-2015 the FFmpeg developers
built with gcc 4.9.2 (Ubuntu 4.9.2-10ubuntu13)
configuration: --prefix=/usr --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaac --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-x11grab --enable-libgsm --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-nonfree --disable-stripping --enable-avfilter --enable-libschroedinger --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3
libavutil      55.  1.100 / 55.  1.100
libavcodec     57.  1.100 / 57.  1.100
libavformat    57.  0.100 / 57.  0.100
libavdevice    57.  0.100 / 57.  0.100
libavfilter     6.  1.100 /  6.  1.100
libswscale      4.  0.100 /  4.  0.100
libswresample   2.  0.100 /  2.  0.100
libpostproc    54.  0.100 / 54.  0.100

melt --version
no more csLADSPA plugins
melt 0.9.3
Copyright (C) 2002-2013 Ushodaya Enterprises Limited

lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 610] [10de:104a] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8460]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at f8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at a800 [size=128]
    [virtual] Expansion ROM at fe880000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF119 HDMI Audio Controller [10de:0e08] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8460]
 glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 610/PCIe/SSE2
OpenGL core profile version string: 4.4.0 NVIDIA 340.76
OpenGL core profile shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.4.0 NVIDIA 340.76
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 NVIDIA 340.76 340.76
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

lsmod | grep 'firewire\|1394'
firewire_ohci          40960  0 
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core

We can see if firewire card is in devices
cd /dev && dir fw* && cd
fw0  fw1

I also make this (when I had the problem with "libcudart.so.5.5: cannot open shared object file", but supposed the fix come from nvidia driver installation)
What I see is that there is no lib64 in my system directories, only lib and lib32 and libx32, so this fix "64-bit: sudo ldconfig /usr/local/cuda/lib64" was useless.

sudo nano /etc/ld.so.conf
..and here are some lines (maybe isn't needed but works now so here is the 3 lines, need sudo ldconfig after change)
include /etc/ld.so.conf.d/*.conf
/usr/local/lib
/usr/lib/x86_64-linux-gnu






```

---

