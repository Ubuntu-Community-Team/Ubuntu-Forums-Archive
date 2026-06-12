---
title: "Can I have a virgin sources.list please?"
date: 2005-09-20
forum: Repositories &amp; Backports
---

### Post by Vicsun on 2005-09-20
Without backing sources.list up, I edited it trying to add an extra repository, but... apparently messed up. Now * sudo apt-get install sun-j2re1.5* returns **couldn't find package**, and I can't find any sort of Java run-time environment in the package manager, even though I've uncommented universe/multiverse repositories.

---

### Post by ghostintheshell on 2005-09-20
Hi, here's mine:

```

#  ______
#_/UBUNTU\__________________________________________________

#MAIN
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary main restricted universe multiverse

#SECURITY
deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted universe

#UPDATES
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted

#  _______
#_/KUBUNTU\__________________________________________________

#KUBUNTU
#deb [http://kubuntu.org/]("http://kubuntu.org/") hoary-updates main

#KDE
deb [http://kubuntu.org/hoary-kde342]("http://kubuntu.org/hoary-kde342") hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342]("http://kubuntu.org/hoary-kde342") hoary-updates main

#KOFFICE
#deb [http://kubuntu.org/hoary-koffice141]("http://kubuntu.org/hoary-koffice141") hoary-updates main
#deb-src [http://kubuntu.org/hoary-koffice141]("http://kubuntu.org/hoary-koffice141") hoary-updates main

#  _________
#_/BACKPORTS\__________________________________________________

#STABLE
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras main universe multiverse restricted

#STAGING
#deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports-staging main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras-staging main universe multiverse restricted

#  ____
#_/MISC\__________________________________________________

#SKYPE
deb [http://download.skype.com/linux/repos/debian/]("http://download.skype.com/linux/repos/debian/") stable non-free

#WINE
deb [http://wine.sourceforge.net/apt/]("http://wine.sourceforge.net/apt/") binary/
deb-src [http://wine.sourceforge.net/apt/]("http://wine.sourceforge.net/apt/") source/

#DINTON (kubuntu support)
#deb [http://dinton.no-ip.org/]("http://dinton.no-ip.org/") kubuntu main
#deb-src [http://dinton.no-ip.org/]("http://dinton.no-ip.org/") kubuntu main

#MARILLAT (multimedia support)
#deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") stable main 
#deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") testing main
#deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main

```

---

### Post by Vicsun on 2005-09-20
Thanks, but it didn't appear to help - I guess the repositories in my sources.list weren't the problem. Has the package sun-j2re1.5 been removed from repositories?

edit: The problem appears to [definitely not be on my side](http://ubuntuforums.org/showthread.php?t=66843&page=2&pp=10&highlight=sun-j2re1.5). Both w32codecs and j2re are missing from the backport repositories for some unbeknown to anyone reason.

---

### Post by Mustard on 2005-09-20
[QUOTE=Vicsun]Thanks, but it didn't appear to help - I guess the repositories in my sources.list weren't the problem. Has the package sun-j2re1.5 been removed from repositories?

edit: The problem appears to [definitely not be on my side](http://ubuntuforums.org/showthread.php?t=66843&page=2&pp=10&highlight=sun-j2re1.5). Both w32codecs and j2re are missing from the backport repositories for some unbeknown to anyone reason.[/QUOTE]

There are some issues with some packages as they move them from the old unofficial backports to the new official backports server.

[http://www.ubuntuforums.org/showthread.php?t=52168](http://www.ubuntuforums.org/showthread.php?t=52168)

---

### Post by ghostintheshell on 2005-09-20
[QUOTE=Mez]Please foward any requests for things that arent in official backports to [email="ubuntu-backports@lists.ubuntu.com"]ubuntu-backports@lists.ubuntu.com[/email][/QUOTE]

and try with:

 ```
 deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports main universe multiverse restricted
```

---

### Post by Vicsun on 2005-09-21
[QUOTE=ghostintheshell]and try with:

 ```
 deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports main universe multiverse restricted
```[/QUOTE]

I already had the old backports when I tried. Adding the new official one didn't help either.

---

