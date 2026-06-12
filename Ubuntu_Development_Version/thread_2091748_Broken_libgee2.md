---
title: "Broken libgee2"
date: 2012-12-06
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-12-06
After installing the newest libgee2 (0.6.7-0ubuntu1) gnome-shell DE has no panels.
So switched to gnome classic and downgraded libgee2 to 0.6.6.1-0ubuntu1 and all is well again.

Does anyone else get this with GS?

---

### Post by mc4man on 2012-12-06
ok here with 0.6.7-0ubuntu1

---

### Post by Harry33 on 2012-12-06
> **mc4man said:**
> ok here with 0.6.7-0ubuntu1

64-bit or 32-bit?
Nvidia-current or not?

---

### Post by mc4man on 2012-12-06
64 bit, nouveau (upgraded thru proposed.

(though have been getting some lockups from attempting to close a window, likely not related to gee, maybe proposed or local

Edit; same with nvidia-current updates
Edit (nothing to do with this thread, testing cap I

---

### Post by VinDSL on 2012-12-06
Everything's working quite nicely here, Harry! (GS 3.7.2)  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-6-dec-2012-0(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-dec-2012-0.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-6-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-dec-2012-1.png")[/INDENT]


```

vindsl@Zuul:~$ apt-cache policy libgee2
libgee2:
  Installed: 0.6.7-0ubuntu1
  Candidate: 0.6.7-0ubuntu1
  Version table:
 *** 0.6.7-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     0.6.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages


vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Thu Dec  6 02:20:20 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-030700rc8-generic
Gnome Release: GNOME Shell 3.7.2
Unity Release: unity 6.6.0

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
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers~quantal
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

---

### Post by Harry33 on 2012-12-06
Right, fine here too.
Perhaps the disapperaring panels of GS was not really related to libgee2.
However, the issue is gone now.

Anyways, libgee2 is not really related to gnome-shell, but rather to  libcaribou.

---

