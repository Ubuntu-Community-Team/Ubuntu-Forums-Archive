---
title: "Nvidia driver 304.51 in 12.10"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Louisraritan on 2012-09-30
Is there a problem with the newest Nvidia driver in 12.10 beta 2?  I was using driver 304.51 in version 12.04, but after upgrade and adding the repo, it says the most current driver is 304.43.  If anyone has tried the newest, did it work?  Want to know before I try manual install, thanks.

---

### Post by MdMax on 2012-09-30
Hello !

I'm using this PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I now have version 304.51 and it's working great, especially with [X-Plane](http://www.x-plane.com/).

---

### Post by pqwoerituytrueiwoq on 2012-09-30
> **MdMax said:**
> Hello !

I'm using this PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I now have version 304.51 and it's working great, especially with [X-Plane]("http://www.x-plane.com/").
did you rig your sources to give you the packages from precise? and if so how did you get it to let you update nvidia-current

---

### Post by VinDSL on 2012-09-30
> **Louisraritan said:**
> Is there a problem with the newest Nvidia driver in 12.10 beta 2?

Want to know before I try manual install, thanks.
Working fine here...  ;)

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Installed PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Sun Sep 30 08:54:32 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc7-generic
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.51

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

Xserver Xorg Core Branch
  Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz

Installed PCI Devices:
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

### Post by pqwoerituytrueiwoq on 2012-09-30
did you install it via nvidia's .run installer?

---

### Post by VinDSL on 2012-09-30
> **pqwoerituytrueiwoq said:**
> did you install it via nvidia's .run installer?
I'm an edger's fanboi... ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-sep-2012-1.png")[/INDENT]

---

### Post by Louisraritan on 2012-10-02
Thanks for the replies, glad you had some success.  12.10 just isn't ready yet and I don't have the skillz so I went back to 12.04lts.  Looking forward to the stable release.

---

### Post by jmore9 on 2012-10-02
I googled and found a ppa and installed it and it just installed the 51 drivers.  Works fine only problem is i have to set the resolution after each reboot or boot.

---

### Post by Rukiri on 2012-10-04
Here's how to install 304.51 in any distro.

Download the driver from Nvidia.
ctrl + alt + f1
sudo service lightdm stop (only if you use lightdm)
cd Downloads
sudo sh ./NVIDIA-Linux-x86-304.51.run

reboot and you're good to go.

However, 12.10 just seems buggy and hopefully many of the bugs will be fixed before it's released as my gtx 680 worked fine in 12.04, screen issues during install until I installed 304.51.  No known PPas for 304.51 unless you want 12.04 LTS versions.  

Also not a fan of the amazon bloat.. previews are slow.. and  with 64GB of ram and on a 4.6GHZ processor.  I just don't think 12.10 is ready, I'm more interested in 13.04 and 14.04 LTS.

---

### Post by Yahoé on 2012-10-04
One can use the xorg-edgers ppa to download the latest version of nvidia-current, and nvidia-settings, 304.51 for now.
I've tested it in 12.10 & 12.04 amd64 without any problem. 

USE THIS PPA WITH CAUTION!
Read [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

For a new install or to upgrade an older version of nvidia-current:

```
 sudo add-apt-repository ppa:xorg-edgers/ppa
``````
sudo apt-get update && sudo apt-get install nvidia-current -y
```Just be careful to only update/install these two packages in this case. Afterwards be sure to deactivate the ppa from Software sources:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

To revert to the official packages, you can install the ppa-purge package and run ```
sudo ppa-purge xorg-edgers
```

---

### Post by Harry33 on 2012-10-04
Nvidia-current_304.51 and nvidia-settings_304.51 are both in QQ official repos (restricted) now.

However, xorg-edgers version works better on my Gnome-shell setup with nvidia GTX285 graphics driver.
Booting process looks better.

---

### Post by pqwoerituytrueiwoq on 2012-10-04
on my install the only package left from edgers is the [FONT=Courier New]xserver-xorg-video-nouveau[/FONT], the update manager replaced everything else automatically
running xubuntu 12.10 on my laptop
nrv somehow i overlooked ~20 packages

---

### Post by dubbelodub on 2012-10-09
I just installed the 304.51 drivers in 12.04. Seems a lot more stable to me (but still detecting incorrect EDID which didn't happen in much older drivers).. However, trying Direct X emulation (Dota 2), through the latest Wine, I get strange red colours over many of the panels and VERY slow FPS. 

Is this likely related to this driver?

---

### Post by pqwoerituytrueiwoq on 2012-10-09
are you sure it is not [FONT=Courier New]304.51.really.304.43[/FONT]?
if you want the real 304.51 without a ppa use nvidia-current-updates

---

### Post by cjcj on 2012-10-12
:mad: The diver version '304.51 realy 43' crashes Matlab when you try to plot(). It also crashes some other software such as UNetBootin when trying to open an option dialogue. The results are similar in both cases with a black screen and no cntrl-alt-backspace etc.

I suspect there are many other bits of software that it crashes. Be cautious. I'm using two screens and a Geforce GT 630 (a fairly new but 'budget' card).

---

