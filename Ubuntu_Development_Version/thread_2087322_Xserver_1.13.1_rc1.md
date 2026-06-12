---
title: "Xserver 1.13.1 rc1"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-11-23
The newest development version (1.13.1 rc1) of the xserver 1.13 branch
is now in the Xorg-edgers PPA.

---

### Post by zika on 2012-11-23
> **Harry33 said:**
> The newest development version (1.13.1 rc1) of the xserver 1.13 branch
is now in the Xorg-edgers PPA.
Any caveats for us that abstained xorg-edgers for a while to experience vanilla RR...?

---

### Post by Harry33 on 2012-11-24
> **zika said:**
> Any caveats for us that abstained xorg-edgers for a while to experience vanilla RR...?

Nothing special regarding this xserver dev version.
It works OK though.
However, I am using the nvidia-current (310.19) of the same edgers PPA.

---

### Post by VinDSL on 2012-11-24
> **Harry33 said:**
> It works OK though.
No problems here, either -- nVidia 304.64...  ;)

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Sat Nov 24 03:30:45 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-3-generic
Unity Release: unity 6.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

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
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.901+git20121123+server-1.13-branch.c0e68f8e-0ubuntu0ricotz~quantal

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]--+-07.0  U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem
           |            \-0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

I don't *think* it's related, but recent upgrades brought back the volume slider in the sound indicator, and so forth, and so on.

Things are starting to shape up, and Xserver Xorg Core 1.13.0.901 hasn't created any new issues, AFAIK.

---

