---
title: "sudo apt-get not working"
date: 2009-08-09
forum: Server Platforms
---

### Post by mathijsbernson on 2009-08-09
Hi there,

A couple of months ago, I built a home server running Ubuntu 9.04 server edition. It worked fine until apt-get stopped working a while ago.

Now, for instance when I try to install nmap, this is what I get:

mathijsbernson@server:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nmap

The same thing happens with all of the other packages I try to install.

When I try sudo apt-get update, it takes five hours to complete, and apt-get still won't work.
sudo apt-get clean and sudo apt-get check don't help either.
I have never changed my sources.list file.

---

### Post by garikaib on 2009-08-09
Let us have a look at the contents of your /etc/apt/sources.list file.

---

### Post by mathijsbernson on 2009-08-09
> **garikaib said:**
> Let us have a look at the contents of your /etc/apt/sources.list file.

Here it is:

```
# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

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

```

---

### Post by garfonzo on 2009-08-09
I had something like this happen too after an update. It turned out my server suddenly couldn't see the internet, and therefore apt didn't 'work'. You might want to try and ping the outside inter-tubes just to rule that out.

```
ping www.google.com
```
or use their IP address:
```
ping 64.233.167.104
```

Hopefully it is as simple as that.

Cheers

---

### Post by wojox on 2009-08-09
<snip>

---

### Post by mathijsbernson on 2009-08-09
> **garfonzo said:**
> I had something like this happen too after an update. It turned out my server suddenly couldn't see the internet, and therefore apt didn't 'work'. You might want to try and ping the outside inter-tubes just to rule that out.

```
ping www.google.com
```
or use their IP address:
```
ping 64.233.167.104
```

Hopefully it is as simple as that.

Cheers

Pinging [www.google.com](www.google.com) works fine.
I don't have a clue what's the matter with my machine. :confused:

---

### Post by wojox on 2009-08-09
Try the old:

```
sudo apt-get dist-upgrade
```

And

```
sudo aptitude
```

---

### Post by mathijsbernson on 2009-08-10
sudo apt-get dist-upgrade works, but it downloads very slow. In fact, it goes so slow that downloading the first file is going to take 17 hours. So I cancelled the process.
Should I just reinstall the entire Ubuntu server OS from the CD?

---

