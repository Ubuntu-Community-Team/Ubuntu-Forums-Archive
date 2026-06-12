---
title: "Apache2 Problem"
date: 2008-05-02
forum: Server Platforms
---

### Post by khaledkhal on 2008-05-02
[B]Hi All,
This is my first time to install Ubuntu [Desktop] on my desktop, and it seems that it is really a good project and I am looking forward to help out in programming.

I have a question though, I tried to install apache2 using the Terminal and entered the command:
[PHP]sudo apt-get install apache2[/PHP]
But the installation doesn't work at all and says the following:
[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2
[/PHP]

knowing that I am signed with a user name not the "root" one.
Thanks in advance![/B]

---

### Post by Dr Small on 2008-05-02
It works perfect for me. That is odd. Perhaps your sources.list file is messed up somewhere. Please post the output back of this command:
```
cat /etc/apt/sources.list
```

And this one:
```
apt-cache search apache
```

Dr Small

---

### Post by khaledkhal on 2008-05-03
Thanks Dr. Small for your help,
Here is the output of the commands

First:
```
cat /etc/apt/sources.list
```

The output is:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://eg.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Second:

```
apt-cache search apache
```

The output is:
```
libjaxp1.3-java - Java XML parser and transformer APIs (DOM, SAX, JAXP, TrAX)
libssl0.9.8 - SSL shared libraries
librpc-xml-perl - Perl module implementation of XML-RPC
libservlet2.4-java - Servlet 2.4 and JSP 2.0 Java library.
libxerces2-java - Validating XML parser for Java with DOM level 3 support
libxalan2-java - XSL Transformations (XSLT) processor in Java

```

Note that,
when I installed Ubuntu, there was a part that had to be connected to the internet but my ISP were fixing something so the internet wasn't working.

Once again,
Thanks Dr. Small.

---

### Post by andguent on 2008-05-03
Dr Small was definitely on the right track there. Your sources listing only has the CDrom available. The power of installing software on Ubuntu (and many other Linux distributions) is the ability to have the Installer pull the files you need directly from the Internet.

There are two ways to fix this. *Note that I am working on the assumption that your Internet is now back and working fine for this computer.*

**Command line method:**
* sudo nano /etc/apt/sources.list
* Add a # in front of that first 'deb cdrom' line (The cd is outdated, stop referring to it).
* Remove the # from in front of any line that starts with '#deb http'.
* Do not remove the # from in front of any line that starts with '#deb-src http', unless you want to download source code for the many software packages.
* Press Ctrl-X, then Y to save the file.

* sudo apt-get update (This should pull down files from 8-10 different places.)
* sudo apt-get install apache2


**Graphical program method:**
* Click System -> Administration -> Synaptec Package Manager
* In Synaptec, click Settings -> Repositories
* Directly on that first tab labeled "Ubuntu Software", make sure the first four are checked, uncheck the CDrom down bottom, source code can be left unchecked unless you really want it.
* Click Close, and then the Reload button on Synaptec.
* Search for apache2, click it, let it mark all dependancies, click apply.

---

