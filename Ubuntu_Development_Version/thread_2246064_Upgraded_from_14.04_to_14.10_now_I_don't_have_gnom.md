---
title: "Upgraded from 14.04 to 14.10 now I don't have gnome-shell anymore..."
date: 2014-09-28
forum: Ubuntu Development Version
---

### Post by orange2k on 2014-09-28
Yesterday I upgraded to 14.10 from 14.04 without problems, the only thing is that I can't choose to run gnome-shell anymore. The upgrade didn't include gnome-shell 3.10 to 3.12 I guess.
When I try to install from command line via "sudo apt-get install gnome-shell" I get the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 (>= 1.17) but 1.16.4-0ubuntu2 is to be installed
               Depends: gir1.2-mutter-3.0 (>= 3.12.0) but it is not going to be installed
               Depends: libcogl-pango20 (>= 1.17.4) but it is not going to be installed
               Depends: libcogl20 (>= 1.17.4) but it is not going to be installed
               Depends: libmutter0d but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Did anyone have the same problem?
What can I do?

---

### Post by zika on 2014-09-28
What gives```
sudo apt-get dist-upgrade
```?
Did You have previously PPA's active? If 'yes' which one(s) regarding GS?

---

### Post by orange2k on 2014-09-28
It installed a bunch of packages and then I tried to install gnome-shell again, and the same error message appears...

Previously I installed gnome-shell from the software center in Ubuntu 14.04 and I didn't add any extra repository to install it...

The problem remains...

---

### Post by kansasnoob on 2014-09-28
Maybe try:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

---

### Post by orange2k on 2014-09-28
> **kansasnoob said:**
> Maybe try:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

In the meantime I ended up installing Trusty again - thanks for the reply, but I am gonna stick with 14.04 for a while, Utopic Unicorn is still too buggy for my taste...

---

### Post by grahammechanical on 2014-09-30
The Ubuntu developers are not responsible for Gnome 3 shell. And it is still too early, in my opinion, to be upgrading to 14.10. I can tell you this. The Utopic software centre has Gnome 3 shell version 3.12.2 in it. It may be best to un-install Gnome 3 shell before upgrading and then re-install afterwards and not to expect the upgrade scripts to sort things out.

Regards.

---

### Post by VinDSL on 2014-10-01
> **orange2k said:**
> Yesterday I upgraded to 14.10 from 14.04 without problems, the only thing is that I can't choose to run gnome-shell anymore.[...]

Did anyone have the same problem?

GS is working fine, here...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/ /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor: Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Thu Oct  2 02:38:37 UTC 2014
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.17.0-031700rc7-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.123

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
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.3.0-0ubuntu2

Package: xserver-xorg-core
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-common
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-xephyr
  Installed: 2:1.16.0-1ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

