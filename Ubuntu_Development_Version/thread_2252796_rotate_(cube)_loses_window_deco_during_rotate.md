---
title: "rotate (cube) loses window deco during rotate"
date: 2014-11-14
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-11-14
The current unity  loses window deco when using rotate.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841)

---

### Post by Chanath on 2014-11-15
> **mc4man said:**
> The current unity  loses window deco when using rotate.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841)

Install Gnome-flashback and test this problem.

---

### Post by ventrical on 2014-11-15
Works fine here on:

```

 *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by mc4man on 2014-11-15
> **ventrical said:**
> Works fine here on:

```

 *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```
Haswell here, have no other to test atm
(- likely caused by rev. 3882 to unity,
> [ Marco Trevisan (Treviño) ]
  * DecoratedWindow: make edges independent from borders and properly
    update them on actions changed



crappy vid showing
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv)

---

### Post by xc3RnbFO8P on 2014-11-15
Works fine here

```
Current Date/Time: Sun Nov 16 00:41:08 UTC 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.16.0-24-generic
Gnome Release: GNOME Shell 3.14.1
Unity Release: unity 7.3.1

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version string:  3.0 Mesa 10.3.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: [http://mesa3d.org/](http://mesa3d.org/)

Package: mesa-common-dev
 Version: 10.3.2-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.16.1.901-1ubuntu1

Package: xserver-common
  Installed: 2:1.16.1.901-1ubuntu1

Package: xserver-xephyr
  Installed: 2:1.16.1.901-1ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation Haswell-ULT DRAM Controller
           +-02.0  Intel Corporation Haswell-ULT Integrated Graphics Controller
           +-03.0  Intel Corporation Haswell-ULT HD Audio Controller
           +-14.0  Intel Corporation 8 Series USB xHCI HC
           +-16.0  Intel Corporation 8 Series HECI #0
           +-1b.0  Intel Corporation 8 Series HD Audio Controller
           +-1c.0-[01]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1c.2-[02]----00.0  Qualcomm Atheros AR9485 Wireless Network Adapter
           +-1d.0  Intel Corporation 8 Series USB EHCI #1
           +-1f.0  Intel Corporation 8 Series LPC Controller
           +-1f.2  Intel Corporation 8 Series SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series SMBus Controller

Display Properties:

  dimensions:    1366x768 pixels (361x203 millimeters)
  resolution:    96x96 dots per inch

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ 
```

---

### Post by ventrical on 2014-11-16
> **mc4man said:**
> Haswell here, have no other to test atm
(- likely caused by rev. 3882 to unity,


crappy vid showing
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv)

xcuse me but I thought you were using nVidia.

```

Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
   Subsystem: Lenovo Device [17aa:3801]
 NVIDIA Corporation GK107M [GeForce GT 755M] [10de:0fcd] (rev a1) (prog-if 00 [VGA controller])

```


What Intel driver are you using?

---

### Post by ventrical on 2014-11-16
> **mc4man said:**
> Haswell here, have no other to test atm
(- likely caused by rev. 3882 to unity,


crappy vid showing
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1392841/+attachment/4261547/+files/deco.ogv)

Ahhh... yes .. very bad refresh of top menu window panel. Works seamlessly here so far.

---

### Post by mc4man on 2014-11-17
confirmed, priority low, maybe it'll go away some time.

---

