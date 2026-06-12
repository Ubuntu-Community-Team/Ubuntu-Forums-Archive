---
title: "Can't get Lighttpd"
date: 2006-09-26
forum: Server Platforms
---

### Post by myst on 2006-09-26
Hi,
I'm new on Linux. I want to install the lighttpd package for ubuntu dapper via apt-get, but the apt-get install lighttpd command can't find the package. maybe I don't have configured the right sources in sources.list? but where can I get them?
Hopefully anyone here can help me with my 'nooby' ;) problem :)
greetz
myst

---

### Post by amohanty on 2006-09-26
Enable the universe repos:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)
and try again.

HTH
AM

---

### Post by myst on 2006-09-26
thx for your answer. 
I don't have a gui installed, but I added the sources to the sources.list.

When i do: apt-get update some sources dosn't work. So I can't update all sources. If I check the urls in my browser they work. :(
I can't install some packages too. e.g. If I want to install ssh, the console tells me that the package can't be downloaded, because of a connection error.

:-k 

sry for my "german-"english....

---

### Post by amohanty on 2006-09-26
Can you post the contents of your /etc/apt/source.list?

AM

---

### Post by myst on 2006-09-27
hi,
this is my sources.list

```
# 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://de.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper universe

deb http://de.archive.ubuntu.com/ubuntu/ dapper universe multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb http://security.ubuntu.com/ubuntu dapper-security universe
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by amohanty on 2006-09-28
Try removing the 'de' infront of the urls to hit the primary servers and see if it works. This is what I would suggest:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Once you are sure everything works, add the 'de.' in the front to hit the german servers again and see if that works.

HTH
AM

---

### Post by myst on 2006-09-28
Hi,
thanks for your answer. It will be the first thing I try when I'm at home today. :)

---

