---
title: "Building Linux, when does it become Ubuntu?"
date: 2015-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by pgib8 on 2015-10-24
I'm building a Linux from scratch basically to run on an embedded device (ARM). I already have something working with the Xfce shell (that part I like). However I don't have access to apt-get because this Linux is using 'smart'.
Clearly it is not Ubuntu and I'm wondering how I can get there.
To build this I'm using the Yocto Project. Originally I thought that I can somehow tell the Yocto to build me Ubuntu instead of whatever it is building (which I think is called Poky reference distribution). I'm pretty sure that I can't tell Yocto to build Ubuntu, that's not how it works.
I need to find my way towards Ubuntu and I can't just download it because it's pretty much a custom hardware.

So I wonder what really makes up Ubuntu. I know I can stick with the Xfce shell and it's still considered Ubuntu (Xubuntu). So the shell doesn't define it. The next thing that comes to mind is apt-get. That's what I'm really after. apt-get allows me to install packages/libraries very easily in most cases as they have already been compiled, even for this ARM-based system.

Can I just install apt-get on whatever Linux I have right now? Also I'm curious about the Kernel. Does Ubuntu use a special Kernel that they make themselves or does it use like the official Kernel. If the Kernel isn't special, then Ubuntu is really defined through the rootfs, is that correct?

I know I'm throwing a lot at you here. I'm trying to wrap my head around some of these things.

So here is what I do know:
The Kernel I use is like an official Kernel but it is compiled specifically for my hardware. It will have many specific drivers already compiled into it.
Can I keep this Kernel the way it is and still get to Ubuntu or is that not feasible?
My Kernel is a single file, zImage I believe and resides on the boot partition. I have MLO and u-boot boot loaders that perform some basic processor configuration (like what some of the pins do), load the kernel and then pass control to it.

Any information that can help me get a better understanding will be highly appreciated.

---

### Post by QIII on 2015-10-24
It becomes Ubuntu when Canonical Ltd, its distributor in the UK, releases it.

---

### Post by PaulW2U on 2015-10-24
> **pgib8 said:**
> Clearly it is not Ubuntu and I'm wondering how I can get there.
> **QIII said:**
> It becomes Ubuntu when Canonical Ltd, its distributor in the UK, releases it.
...with thousands of patches and fixes (to Debian source) of their own. ;)

---

### Post by Bucky Ball on 2015-10-24
Which ARM processor are you actually using and what is the final outcome you are looking for? A basic xfce4 shell with apt-get and repositories and that's it? Tell us more about the project and hardware, please. :)

---

### Post by grahammechanical on 2015-10-24
What you are doing is legal because you are using Free and Open Source Software (FOSS) but I do not think that it will ever be "Ubuntu." There are different versions of Ubuntu. There is Ubuntu Desktop that runs on Linux and is built from Debian and uses the Gnome 3 Desktop Environment (DE) with the Unity Graphical User Interface (GUI). Then there is Ubuntu server which is without a DE and GUI. We also have Ubuntu Core, which is again without a DE and GUI but it uses Debian packages  and its relative Snappy Ubuntu Core which uses Snap packaging instead of Debian packaging. It also lacks a DE and GUI.

You might find either Ubuntu Core or Snappy Ubuntu Core more suitable for your needs. Both are available for ARM processors. Start with Ubuntu and it will be Ubuntu.

[https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)

[http://www.ubuntu.com/internet-of-things](http://www.ubuntu.com/internet-of-things)

Regards

---

### Post by HermanAB on 2015-10-24
It 'becomes Ubuntu' when you use Canonical trademarked files.  If you don't, then it is your own distribution and you can name it 'Pgib8 Linux', or whatever else you want.

---

### Post by pgib8 on 2015-10-24
> **Bucky Ball said:**
> Which ARM processor are you actually using and what is the final outcome you are looking for? A basic xfce4 shell with apt-get and repositories and that's it? Tell us more about the project and hardware, please. :)

You are spot on. I don't care about the shell, something light, so Xfce is perfect. I also don't care what the distribution is called, it doesn't have to be called Ubuntu. But I guess what I'm really after is the apt-get package manager. But perhaps this is one of the big ticket items that actually makes up Ubuntu. The way I see it is that Ubuntu compiles all these packages and source code so that they can be conveniently downloaded and installed through apt-get. So let's say I need to install OpenCV; I don't have to do it from scratch but I can just type something like apt-get install opencv...

The ARM chip is the OMAP4430, it's a 1GHz dual-core from TI. It's part of a Gumstix 'DuoVero' with 'Parlor' expansion board.

> **HermanAB said:**
> It 'becomes Ubuntu' when you use Canonical trademarked files. If you don't, then it is your own distribution and you can name it 'Pgib8 Linux', or whatever else you want.
I see what you guys are saying, the key being the trademarked files. That most likely means if I create 'Pgib8 Linux' I probably can't add the apt-get package manager and even if I did, it probably wouldn't be able to download packages and install them, because from where. Pgib8 Linux doesn't have any packages available, so they would have to come from Ubuntu or something like that, but Ubuntu is probably going to say that it doesn't provide packages to Pgib8 Linux and even if it did, perhaps they wouldn't run on it.

---

### Post by tgalati4 on 2015-10-24
Installing Debian packages (including Ubuntu packages) on an unsupported platform is a challenge.  

You need to build from scratch all the dependencies for both apt and dpkg to get a basic repo system.  

> tgalati4@Mint17 ~ $ apt-cache depends apt
apt
  Depends: libapt-pkg4.12
  Depends: libc6
  Depends: libgcc1
  Depends: libstdc++6
  Depends: ubuntu-keyring
  Depends: gnupg
    gnupg:i386
 |Suggests: aptitude
 |Suggests: synaptic
  Suggests: wajig
  Suggests: dpkg-dev
  Suggests: apt-doc
  Suggests: python-apt
  Conflicts: python-apt
  Conflicts: python-apt:i386
  Breaks: manpages-it
  Breaks: <manpages-it:i386>
  Breaks: manpages-pl
  Breaks: <manpages-pl:i386>
  Breaks: openjdk-6-jdk
  Breaks: openjdk-6-jdk:i386
  Breaks: <sun-java5-jdk>
  Breaks: <sun-java5-jdk:i386>
  Breaks: <sun-java6-jdk>
  Breaks: <sun-java6-jdk:i386>
  Replaces: manpages-it
  Replaces: <manpages-it:i386>
  Replaces: manpages-pl
  Replaces: <manpages-pl:i386>
  Replaces: openjdk-6-jdk
  Replaces: openjdk-6-jdk:i386
  Replaces: <sun-java5-jdk>
  Replaces: <sun-java5-jdk:i386>
  Replaces: <sun-java6-jdk>
  Replaces: <sun-java6-jdk:i386>
  Conflicts: apt:i386
tgalati4@Mint17 ~ $ apt-cache depends dpkg
dpkg
  PreDepends: libbz2-1.0
  PreDepends: libc6
  PreDepends: liblzma5
  PreDepends: libselinux1
  PreDepends: zlib1g
  PreDepends: tar
    tar:i386
  Suggests: apt
  Breaks: apt
  Breaks: apt:i386
  Breaks: aptitude
  Breaks: aptitude:i386
  Breaks: dpkg-dev
  Breaks: <dpkg-dev:i386>
  Breaks: libdpkg-perl
  Breaks: <libdpkg-perl:i386>
  Replaces: manpages-it
  Replaces: <manpages-it:i386>
  Conflicts: dpkg:i386


Then any binaries that you try to install won't work because they are compiled for x86 processors, unless someone has created a gumstick repository to pull from.  So that makes the apt system useful only for source code, which you can download through a web page, you don't need the apt system to get source code.

I would set up a RaspberryPi since it already has an XFCE/Debian system, called Raspian and apt-get works out-of-the-box. To turn that into Ubuntu requires adding some themes, desktop apps, and it probably has been done already as an ISO.

A little searching:

[http://wiki.gumstix.org/index.php?title=Debian_Root_File_System](http://wiki.gumstix.org/index.php?title=Debian_Root_File_System)

[http://www.hackgnar.com/2015/03/building-yocto-linux-images-for-gumstix.html](http://www.hackgnar.com/2015/03/building-yocto-linux-images-for-gumstix.html)

[http://johnwoconnor.blogspot.com/2009/04/installing-ubuntu-on-gumstix-overo.html](http://johnwoconnor.blogspot.com/2009/04/installing-ubuntu-on-gumstix-overo.html)

Due to the embedded nature of the gumstick, it may not be possible to get a working apt-get system on it because updates are performed on a host computer and then Yocto is used to create the embedded firmware/OS.  The RaspberryPi works as a traditional linux computer where you can perform updates directly on the system.

---

### Post by HermanAB on 2015-10-24
Note that trademarked files are mostly graphics.  Don't confuse them with copyrighted code files.  Copyrighted files with a free license can be used freely.  A distributor usually also has a clause that if you make your own distribution, then you should not use their servers and their help system for updates to your users.  I.e. you should distribute and support it yourself.

---

### Post by pgib8 on 2015-10-25
Well thank you guys for all these insights. The raspberry pi and many other embedded linux computers have a ton of support, whereas the gumstix has next to none. The only reason I'm using it is because it's very small, which is what I need.

What I will do is forget about apt-get and ubuntu and instead do it the "old-fashioned" way of downloading source, compiling it, resolving errors until it compiles (usually other stuff that needs to be compiled, which then again has other stuff that needs to be compiled), and so on. I've done this once before and eventually it leads to everything being installed that I need.

It's a lot easier to take an OS that already runs and adding things I need as opposed to taking an OS that already has everything but trying to make it run.

---

