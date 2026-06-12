---
title: "ubuntu 7.10 server amd64 repository ?"
date: 2007-10-26
forum: Server Platforms
---

### Post by alaya on 2007-10-26
I have installed ubuntu 7.10 server edition amd64 on the server of my school(Sun V20Z).
I want to install gnome and some other soft.
the problem is that my etc/apt/source.list contain only the cdrom source.
I try to add some other repository( like this ones in this adress:[http://ubuntuforums.org/showthread.php?t=581521]("http://ubuntuforums.org/showthread.php?t=581521"))but it does n t much (index error when I launch apt-get update).
can some body give me the right repository for my gutsy server ?
and what is the commands I have to type to install gnome ?
thank you very much for your help.

---

### Post by dantrevino on 2007-10-28
assuming you're in the US:

```

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

To install gnome:
```
sudo apt-get install ubuntu-desktop
```

Please note universe and multiverse are enabled in the above and you may not want that in a production environment.

dan

---

