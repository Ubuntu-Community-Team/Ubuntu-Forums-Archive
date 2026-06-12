---
title: "Gnome-shell and 13.10"
date: 2013-04-30
forum: Ubuntu Development Version
---

### Post by sammiev on 2013-04-30
Hi Folks, The fun has begun. Gnome-shell is broken after todays updates on 13.10 :)

---

### Post by dino99 on 2013-04-30
GS 3.8.1 (gnome3-team ppa) is not broken here on SS i386  :P

---

### Post by VinDSL on 2013-04-30
> **dino99 said:**
> GS is not broken here on SS i386  :P
Dittos...


```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Tue Apr 30 20:41:09 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.9.0-030900-generic
Gnome Release: GNOME Shell 3.8.1
Unity Release: unity 7.0.0

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
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
Version: 9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz

Package: xserver-xorg-core
  Installed: 2:1.13.3-0ubuntu6

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

vindsl@Zuul:~$
```

Never worked better, actually!  ;)

---

### Post by Harry33 on 2013-05-01
> **sammiev said:**
> Hi Folks, The fun has begun. Gnome-shell is broken after todays updates on 13.10 :)

The issue with the new gjs is fixed now.
There is a new gnome-shell version in repos.

---

### Post by sammiev on 2013-05-01
> **Harry33 said:**
> The issue with the new gjs is fixed now.
There is a new gnome-shell version in repos.

Correct you are as the new updates did fix the problem. 
Thanks

---

### Post by kevpan815 on 2013-05-01
Question for VINDSL: Is that echo && echo command Built into Ubuntu itself or is that one of your own Personal Debugging Scripts that you yourself wrote?

Edit: Never Mind, I just read the Post in his Signature and it sounds too complicated for me to attempt to install his Script as all that Programming Language is way over my head! After all my College Education was in Computer Networking NOT Programming.

---

