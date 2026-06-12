---
title: "[Ubuntu] PlayOnLinux Installation Troubles"
date: 2010-02-02
forum: Wine
---

### Post by Starblaster1234 on 2010-02-02
Hello very supportive network of programming professionals,

after typing the following:
```
sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```I recieve this error:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  playonlinux: Depends: python-wxgtk2.8 but it is not installable
E: Broken packages

```Additional Information:
I am using Ubuntu 9.10
Wine Version: 1.1.37-0ubuntu2 (wine1.2)
Versions of Python Interpreter Installed: v2.6 and v2.5

I will run any tests you would like and will be very cooperative to help us achieve a successful installation of PlayOnLinux.

I appreciate your help!

---

### Post by beastrace91 on 2010-02-02
Can I ask why you added the POL repositories? POL is in the default Ubuntu repos as of 9.10 - try removing the line you added for POL to your sources.list and then running ```
sudo apt-get update
sudo apt-get install playonlinux
```

(To edit your sources.list run **sudo gedit /etc/apt/sources.list** and simply add an # in front of the line you wish to comment out.)

Regards,
~Jeff

---

### Post by Starblaster1234 on 2010-02-02
Well, I didn't find it in the source list anyway. Contents of the .list file:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://wine.sourceforge.net/apt/ binary/
```

I ran that line of code because the playonlinux site told me to.

Either I didn't rem out the correct line or something but I'm still getting the same error -.-;

---

### Post by beastrace91 on 2010-02-03
Some times the repos have issues - try running ```
sudo apt-get update && sudo apt-get install playonlinux
```

Just tried to grab that package yours cannot find this afternoon and it appears to be working fine now: ```
jeff@eeetop:~$ sudo apt-get install python-wxgtk2.8
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-wxversion

```

~Jeff

---

### Post by Starblaster1234 on 2010-02-03
Same error

When just trying to install the one package, I get:
```
user@computername:~$ sudo apt-get install python-wxgtk2.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-wxgtk2.8 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-wxgtk2.8 has no installation candidate

```

---

### Post by beastrace91 on 2010-02-03
Its odd that your system cannot find just that package for whatever reason... At any rate you can download the .deb installer for it from [here](http://packages.ubuntu.com/karmic/python-wxgtk2.8). Just download the arch. you need of it and install it from the .deb - after that try installing POL

~Jeff

---

### Post by Starblaster1234 on 2010-02-03
When I tried to do that I got:

```
Error: Dependency is not satisfiable: python-wxversion (>= 2.8.9.1-0ubuntu6)
```

---

### Post by beastrace91 on 2010-02-03
Check on that page I linked you to for the download - there is a link to the package your system says it cannot find. Download that .deb as well and install it manually.

Rinse and repeat for any other packages it says it cannot find.

~Jeff

---

### Post by Slayer. on 2010-03-01
... They're both dependent upon each other. Or so it says when I try to open them with the .deb installer.

---

