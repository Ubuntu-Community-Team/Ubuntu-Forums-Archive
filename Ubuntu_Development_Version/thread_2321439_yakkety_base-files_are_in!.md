---
title: "yakkety base-files are in!"
date: 2016-04-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-04-22
For early adpoters.

```

ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
ventrical@ventrical-System-Product-Name:~$ 

```

How to:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by slickymaster on 2016-04-22
Yes```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
4.4.0-21-generic
```And with the expected, for the moment, upgrades:```
Upgrade: vim-common:amd64 (2:7.4.1689-3ubuntu1, 2:7.4.1689-3ubuntu2), distro-info-data:amd64 (0.28, 0.28ubuntu1), vim-tiny:amd64 (2:7.4.1689-3ubuntu1, 2:7.4.1689-3ubuntu2), base-files:amd64 (9.4ubuntu4, 9.6ubuntu1)
End-Date: 2016-04-22  17:30:38
```

---

### Post by ventrical on 2016-04-22
+1 ;)

---

### Post by MikeMecanic on 2016-04-22
> **ventrical said:**
> For early adpoters.
How to:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

So far, so Yak but not without errors. Just to play, thanks for the link. Sounds like a Willy first letter of retirement eligibility.

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
4.4.0-21-generic
```

---

### Post by ventrical on 2016-04-22
Enable proposed repo and update.

```

The following packages have been kept back:
  usb-modeswitch-data
The following packages will be upgraded:
  cpp-5 g++-5 gcc-5 gcc-5-base initscripts libasan2 libatomic1 libcc1-0
  libcilkrts5 libgcc-5-dev libgomp1 libitm1 liblsan0 libmpx0 libquadmath0
  libsemanage-common libsemanage1 libstdc++-5-dev libstdc++6 libtsan0
  libubsan0 sysv-rc sysvinit-utils vim-common vim-tiny
25 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 76.7 MB of archives.
After this operation, 241 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu yakkety-proposed/main amd64 sysvinit-utils amd64 2.88dsf-59.3ubuntu4 [21.5 kB]

```

---

### Post by cariboo on 2016-04-22
I'm in too
```
cariboo@skynet:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu Yakkety Yak (development branch)"
```

I had a problem after a fresh install of Xenial, with no launcher or dash, but I found a solution, and will add it to the [Common problems]("https://wiki.ubuntu.com/U%2B1/common-problems") wiki when I have time

---

### Post by sammiev on 2016-04-23
I'm in.

sam@sam-L650:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety
4.4.0-21-generic

---

### Post by cecilpierce on 2016-04-23
Anyone remember this ?

[https://www.youtube.com/watch?v=-WfDYssJMqs](https://www.youtube.com/watch?v=-WfDYssJMqs)

---

### Post by grahammechanical on 2016-04-24
I do. That song comes to mind every time I think of this code name. And I have been thinking about there being symbolism in the phrase "Don't talk back." 

Regards.

---

### Post by Irihapeti on 2016-04-24
I remember this one: [https://www.youtube.com/watch?v=OFo4xoViiWg](https://www.youtube.com/watch?v=OFo4xoViiWg)

---

### Post by PaulW2U on 2016-04-24
> **sammiev said:**
> I'm in.

sam@sam-L650:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety
4.4.0-21-generic
Me too, on one of my Xubuntu installs. It looks like that most of the updates are currently being held in -proposed for now, 125 of them as I write this.

---

### Post by oldfred on 2016-04-24
Yesterday when I looked this was still 16.04, but now it says 16.10. 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Made copy of ubuntu-16.04-desktop-amd64.iso and renamed to yakkety-desktop-amd64.iso.

zsync [http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso.zsync)

Read yakkety-desktop-amd64.iso. Target 92.1% complete.

So some changes in daily from xenial.

---

### Post by VinDSL on 2016-04-25
```
&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;  echo && echo "~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && echo -n "Browser Release: Chromium ver." && chromium-browser --product-version && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/ /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Mon Apr 25 06:35:14 UTC 2016
Distro Release: Ubuntu Yakkety Yak (development branch)
Kernel Release: Linux 4.6.0-040600rc5-generic
Gnome Release: GNOME Shell 3.18.4
Unity Release: unity 7.4.0

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 11.2.0

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

Browser Release: Chromium ver.Using PPAPI flash.
50.0.2661.75

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 99
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.3.0-1
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 11.2.0-1ubuntu2

Package: xserver-xorg-core
  Installed: 2:1.18.3-1ubuntu2

Package: xserver-common
  Installed: 2:1.18.3-1ubuntu2

Package: xserver-xephyr
  Installed: 2:1.18.3-1ubuntu2

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
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;  

```


GS is working fine !  :)


[INDENT][[IMG]http://vindsl.com/images/2016-04-24-23:58:47--scrot(650x520).png[/IMG]]("http://vindsl.com/images/2016-04-24-23:58:47--scrot.png")[/INDENT]

---

