---
title: "how can i get libc6 2.3.2.ds1-21?"
date: 2005-07-22
forum: Repositories &amp; Backports
---

### Post by cannibalbob on 2005-07-22
I'm getting:

gtk2-engines-experience:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

deb [http://benjamin.sipsolutions.net/debian/](http://benjamin.sipsolutions.net/debian/) stable/


any help is greatly appreciated...

---

### Post by Xian on 2005-07-22
You could install the libc6 version for Breezy which is [2.3.5-1ubuntu7](http://packages.ubuntu.com/breezy/base/libc6). 
But I'm not sure I'd necessarily advise it.

---

### Post by dbee on 2005-08-25
I've got the same problem here. 

First I couldn't find j2re1.5 in the repositories, but I eventually got around that problem. Now java won't install on my system because of an outdated libc 

What's the story here then ???

PS: apart from some minor issues though, I'm a big fan of ubuntu

---

### Post by Unix_Wizard on 2005-08-25
[QUOTE=dbee]I've got the same problem here. 

First I couldn't find j2re1.5 in the repositories, but I eventually got around that problem. Now java won't install on my system because of an outdated libc 

What's the story here then ???

PS: apart from some minor issues though, I'm a big fan of ubuntu[/QUOTE]
 I converted a rpm I had left over from fedora core 3. It worked flawlessy for what I was trying to install (zsnes).

---

### Post by H4rm0ny on 2005-08-25
[QUOTE=dbee]I've got the same problem here. 

First I couldn't find j2re1.5 in the repositories, but I eventually got around that problem. Now java won't install on my system because of an outdated libc 
[/QUOTE]

Can I ask how you got around the missing j2re1.5 as I can't find it either. I have the following in my /etc/apt/sources.list
```
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
but nothing is showing up. 

I also have the same libc problem as everyone else btw. Several packages are demanding a new version than appears to be in the repositories (not touching badger with a barge pole, btw - let someone else wear the red-shirt, I say)

---

### Post by savage on 2005-08-31
see this thread [http://www.ubuntuforums.org/showthread.php?t=46861&highlight=libc6+2.3.2.ds1-21](http://www.ubuntuforums.org/showthread.php?t=46861&highlight=libc6+2.3.2.ds1-21)

---

### Post by H4rm0ny on 2005-09-03
Thanks.

I think in retrospect, I'll just wait for badger. I've now managed to resolve most of my dependency problems and I'm just have ffmpeg left, which is demanding the new libc. I'll survive without that, I suppose.

Cheers,

-H.

---

