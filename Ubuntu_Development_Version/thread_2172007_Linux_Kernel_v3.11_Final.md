---
title: "Linux Kernel v3.11 Final"
date: 2013-09-02
forum: Ubuntu Development Version
---

### Post by The Spectre on 2013-09-02
Looks like the Final of v3.11 is out...
[https://www.kernel.org/](https://www.kernel.org/)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/)

So far it is working perfectly:-)

---

### Post by QDR06VV9 on 2013-09-02
Working Well here.
```
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
3.11.0-031100-generic

```

---

### Post by VinDSL on 2013-09-02
Working okay here, too.  But I must admit...

[Liquorix 3.10-10.dmz]("http://liquorix.net/debian/pool/main/l/linux-liquorix/") performs better (on this machine).  ;)


```
~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Tue Sep  3 03:31:45 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10-10.dmz.1-liquorix-686
Gnome Release: GNOME Shell 3.9.90
Unity Release: unity 7.1.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

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
Installed-Size: 115
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-0ubuntu1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
  Version: 9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt

Package: xserver-xorg-core
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-common
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-xephyr
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

---

### Post by Nick Payne on 2013-09-03
If you're running Virtualbox, you need (until a new version of Virtualbox is released) an updated version of dirops.c for guest additions to build successfully when installing the new kernel.

[https://www.virtualbox.org/changeset/47588/vbox/trunk/src/VBox/Additions/linux/sharedfolders/dirops.c]("https://www.virtualbox.org/changeset/47588/vbox/trunk/src/VBox/Additions/linux/sharedfolders/dirops.c")

---

### Post by The Spectre on 2013-09-03
I can confirm that there is an issue with VirtualBox 4.2.16 and Linux Kernel v3.11...

[https://www.virtualbox.org/ticket/12001](https://www.virtualbox.org/ticket/12001)

But like Nick Payne stated the fix will be in the next Maintenance Release of VirtualBox.

It is possible that the fix might already be in VirtualBox 4.3.0 Beta1... 
[http://download.virtualbox.org/virtualbox/4.3.0_BETA1/](http://download.virtualbox.org/virtualbox/4.3.0_BETA1/)

But it might be better to wait for the Maintenance Release of VirtualBox and just temporarily boot into a previous Linux Kernel whenever you want to run VirtualBox.

---

### Post by Nick Payne on 2013-09-05
I just updated dirops.c in /usr/src/virtualbox-guest-4.2.10/vboxsf as per the link I gave above, and then reinstalled the 3.11 kernel. With the updated dirops.c the install completed without error, and Virtualbox works fine under 3.11.

---

### Post by The Spectre on 2013-09-06
VirtualBox 4.2.18 was just released and it looks like it has the fix for Linux Kernel v3.11.

VirtualBox 4.2.18...
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Changelog...
[https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog)

---

