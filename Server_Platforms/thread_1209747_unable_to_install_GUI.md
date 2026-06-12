---
title: "unable to install GUI"
date: 2009-07-10
forum: Server Platforms
---

### Post by Dan409 on 2009-07-10
I cannot get the GUI to install. 
Have tried the following 
sudo apt-get update
sudo apt-get install gnome-core xorg gdm
and it cannot find gnome-core

---

### Post by d_liebscher on 2009-07-11
Hi,
strange, that gnome-core package couldn't be found.
What about the standard gnome installation, is it possible to install the meta package ubuntu-desktop?

Daniel

---

### Post by druhboruch on 2009-07-11
Could you post your sources.list?

I just checked and it is available in us archive.

---

### Post by d_liebscher on 2009-07-11
Hi,

yeah, no problem, but it is x64 and german^^

```
#deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

## amarok 1.4 
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main

```Daniel

ps: ubuntu-desktop install also gnome, just with some gnome standard applications

---

### Post by lisati on 2009-07-11
Wouldn't it be easier to use something like this?
```
sudo aptitude install ubuntu-desktop
```

---

### Post by d_liebscher on 2009-07-11
Hi,

yeah, of course. (The only thing is, it will take a bit more of your disk capacity)

Daniel

PS: kubuntu-desktop installs kde and xubuntu-desktop xfce

---

### Post by fischer98 on 2009-07-11
I installed the following packages to get a base GUI installed on 9.04 server.

x-window-system-core xserver-xorg gnome-core gnome-netstatus-applet gnome-nettool gnome-system-monitor gnome-system-tools

The first three are the primary components I needed, but the others provided some useful tools.

I do not recommend installing any of the "desktop" metapackages as they contain a lot of extraneous software that is not needed on a server (email clients, games, web browsers, etc.)

---

### Post by d_liebscher on 2009-07-12
oh,

thanks fischer98, i didn't realize that this is the serverforum, sorry for that.

On a server i also think, ubuntu-desktop package is just recommendable if you want to set up an ltsp, and the users need the programs.

---

### Post by Dan409 on 2009-07-13
Let me ask this then, I am trying to build a testing VM environment, would it be better to load the a server with just the virtual utils or to load a work station and strip out all the stuff not needed. Also, the box I am building on is an IBM 1TB HHD 1 quad core and 32GB ram, 2 1GB LAN

---

### Post by d_liebscher on 2009-07-13
Hi,

No guidance, just my experiences: 

I think this depends on your working environment. 
I'm working also with an VMWare test server (2xXenon, SCSI Raid, and so on)
I'm sure, I would not like to work in same room with this equipment. 
So I'm using ssh to set up the VMWare Server. For working with VMWare Stations it is not necessary to install an desktop environment, so i decided to use a server distribution. 

Later I decidet to set up an terminal server in an seperate subnet, so I can boot from Lan everywhere from every machine and installed XFCE [if somebody would do the same: install ltsp first and VMWare Server after it, it will be more relaxed!]. 

I think the use/allocation (sry, the right english word escapes me) of your Hardware would also be better on a Server (your hardwaredescription sounds good)
I think I need not to mention that it should be a x64 version.

Finally, the decission is yours but my advice would be: take a server distribution. 

Daniel

---

### Post by Dan409 on 2009-07-13
Yes it is easier to install the Uhuntu-desktop but then you get all the office and email stuff. I might need to just clean it out after it loads.

---

