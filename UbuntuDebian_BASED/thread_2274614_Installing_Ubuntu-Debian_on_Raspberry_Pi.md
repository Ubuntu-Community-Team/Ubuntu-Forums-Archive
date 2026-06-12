---
title: "Installing Ubuntu-Debian on Raspberry Pi"
date: 2015-04-21
forum: Ubuntu/Debian BASED
---

### Post by erotavlas on 2015-04-21
Hi,
I have a problem during the upgrade of my system (Raspbian) installed on Raspberry Pi. I do not know if the Ubuntu forum is the more appropriate to this question, but in general it is populated of well informed people. However, I can update correctly my distribution with standard command apt-get update && apt-get upgrade. After since I need some package contained in Debian repository, I added the following lines to /etc/apt/sources.list
```

deb http://mirrordirector.raspbian.org/raspbian/ jessie main
deb-src http://mirrordirector.raspbian.org/raspbian/ wheezy main

# added for extra packages
deb http://ftp.debian.org/debian/ jessie main
deb http://ftp.debian.org/debian/ wheezy main

```
and if I retype apt-get update && apt-get upgrade, I get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bash bzip2 dash diffutils findutils fuse iptables iputils-ping keyutils
  libaudiofile-dev libaudiofile1 libaudit1 libbz2-1.0 libexpat1 libffi6
  libfuse2 libgpm2 libice6 libidn11 libidn11-dev libkeyutils1 liblcms2-2
  liblzma5 libmodplug1 libncurses5 libncurses5-dev libncursesw5
  libncursesw5-dev libnewt0.52 libopencv-core2.4 libopencv-imgproc2.4
  libpng12-0 libreadline-dev libreadline6 libreadline6-dev libsdl1.2debian
  libsemanage1 libsigsegv2 libsm6 libtinfo-dev libtinfo5 libustr-1.0-1
  libwebp5 libwebpdemux1 libwebpmux1 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0
  libxcb-present0 libxcb-render0 libxcb-shm0 libxcb-sync1 libxcb1 libxcursor1
  libxdamage1 libxdmcp6 libxfixes3 libxi6 libxinerama1 libxpm4 libxrandr2
  libxrender1 libxslt1.1 libxtables10 libxtst6 libxxf86vm1 linux-libc-dev
  logrotate minidlna ncurses-bin net-tools pmount python-crypto python-urwid
  sed tar traceroute whiptail xz-utils zlib1g zlib1g-dev
81 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/12.2 MB of archives.
After this operation, 2840 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  bash dash diffutils findutils libtinfo5 libncursesw5 libncurses5-dev
  ncurses-bin libncursesw5-dev libtinfo-dev libncurses5 sed tar bzip2
  libbz2-1.0 libreadline-dev libreadline6-dev libreadline6 liblzma5 zlib1g-dev
  zlib1g libaudit1 libustr-1.0-1 libsemanage1 libnewt0.52 libgpm2 libidn11-dev
  libidn11 libkeyutils1 libaudiofile-dev libaudiofile1 libexpat1 libffi6 fuse
  libfuse2 libice6 liblcms2-2 libsm6 libopencv-imgproc2.4 libopencv-core2.4
  libpng12-0 libsdl1.2debian libsigsegv2 libxdmcp6 libxcb1 libxcb-dri2-0
  libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shm0
  libxcb-sync1 libxfixes3 libxrender1 libxcursor1 libxdamage1 libxi6
  libxinerama1 libxpm4 libxrandr2 libxslt1.1 libxtst6 libxxf86vm1 libwebp5
  libwebpdemux1 libwebpmux1 iptables libxtables10 iputils-ping logrotate
  net-tools traceroute whiptail xz-utils keyutils libmodplug1 linux-libc-dev
  minidlna pmount python-crypto python-urwid
Install these packages without verification? [y/N] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 41552 files and directories currently installed.)
Preparing to unpack .../bash_4.3-11+b1_armhf.deb ...
dpkg: error processing archive /var/cache/apt/archives/bash_4.3-11+b1_armhf.deb (--unpack):
 subprocess new pre-installation script was killed by signal (Segmentation fault)
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.3-11+b1_armhf.deb

```
It cannot upgrade bash. I already tried with 
```

sudo dpkg --force-all -i /var/cache/apt/archives/bash_4.3-11+b1_armhf.deb
sudo apt-get install bash

```
and
```

sudo apt-get clean && apt-get --reinstall bash

```
Any suggestions?
Thank you

---

### Post by Bucky Ball on 2015-04-21
*Thread moved to **Ubuntu/Debian BASED**.*

Raspbian is not one of the official Ubuntu flavours supported in the main areas here.

Where did you find these repos? Are they for Raspbian/ARM?

```
# added for extra packages
deb http://ftp.debian.org/debian/ jessie main
deb http://ftp.debian.org/debian/ wheezy main
```

---

### Post by Frogs Hair on 2015-04-21
I do run, Raspbian on my Pi , but I don't think adding various Debian repositories without error is possible. Raspbian is Debian based, but not Debian just as Ubuntu.    

You can ask questions on IRC .[http://www.raspbian.org/RaspbianIRC](http://www.raspbian.org/RaspbianIRC)

---

### Post by QIII on 2015-04-21
I also stick to the Raspian repos.  There's no guarantee software from other repos will work on ARM architecture.

---

### Post by matt_symes on 2015-04-21
Hi
> 
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) jessie main
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) wheezy main

Binary packages sourced from 2 different releases of any distribution are never a good idea and can lead to library dependency hell.

BTW: What software did you need to update/install ?

Kind regards

---

### Post by erotavlas on 2015-04-23
Hi,
thank you for your reply. I solved by using the following repositories
```

deb http://mirrordirector.raspbian.org/raspbian/ jessie main contrib non-free r$
deb http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free r$

```
that are the same of standard Raspbian where I added contrib non-free.

Thank you

---

### Post by Bucky Ball on 2015-04-23
Good news. Enjoy the little RPi beast. I dug mine out a few days ago and installed Raspbian, which I'd never tried. Must think of something to do with it one of these days (worked faultlessly with RaspBMC as a media server until superseded by an Odroid).

The wireless USB dongle that didn't work before now works out of the box in Raspbian. Might shove a USB drive into it and use it as a network server ... eventually! ;)

---

