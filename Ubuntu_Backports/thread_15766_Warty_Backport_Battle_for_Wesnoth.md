---
title: "Warty Backport: Battle for Wesnoth"
date: 2005-02-16
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-16
**Synposis**
Backported as requested.

**Process**
Taken from debian Sid. All deps resolved using Warty packages.

**Status**

i386: Staging rev 44
amd64: Unpackaged
ppc: Unpackaged

---

### Post by techn9ne on 2005-02-17
wesnoth:
 Depends: libsdl-mixer1.2 but it is not going to be installed
  Depends: libsdl1.2debian (>1.2.7+1.2.8) but 1.2.7-7 is to be installed

---

### Post by jdong on 2005-02-17
Oops! Will fix tonight.

---

### Post by jdong on 2005-02-17
[/code]jdong@omega2:~/work/wesnoth-0.8.10 $ sudo apt-get install wesnoth -s
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  wesnoth-data
Recommended packages:
  wesnoth-music
The following NEW packages will be installed:
  wesnoth wesnoth-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst wesnoth-data (0.8.10-1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Inst wesnoth (0.8.10-1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Conf wesnoth-data (0.8.10-1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Conf wesnoth (0.8.10-1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
[/code]

I cannot reproduce your bug. Post the output of this command:
```

jdong@omega2:~/work/wesnoth-0.8.10 $ dpkg-query -l libsdl-mixer1.2 libsdl1.2debian

```

A standard Warty install should show:
```

ii  libsdl-mixer1. 1.2.5-5ubuntu1 mixer library for Simple DirectMedia Layer 1
ii  libsdl1.2debia 1.2.7-7        Simple DirectMedia Layer

```

---

### Post by techn9ne on 2005-02-17
jeremy@ecode:~ $ dpkg-query -l libsdl-mixer1.2 libsdl1.2debian
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  libsdl-mixer1. 1.2.5-5ubuntu1 mixer library for Simple DirectMedia Layer 1
ii  libsdl1.2debia 1.2.7-7        Simple DirectMedia Layer

---

### Post by techn9ne on 2005-02-17
I installed libsdl-mixer so now it says :

$ dpkg-query -l libsdl-mixer1.2 libsdl1.2debian

ii  libsdl-mixer1. 1.2.5-5ubuntu1 mixer library for Simple DirectMedia Layer 1
ii  libsdl1.2debia 1.2.7-7        Simple DirectMedia Layer

but :

$ sudo apt-get install wesnoth

The following packages have unmet dependencies:
  wesnoth: Depends: libsdl-mixer1.2 (>= 1.2.6) but 1.2.5-5ubuntu1 is to be installed
           Depends: libsdl1.2debian (> 1.2.7+1.2.8) but 1.2.7-7 is to be installed
E: Broken packages

---

### Post by jdong on 2005-02-17
Those messages definitely aren't coming from my backported copy of wesnoth... Are you sure another repository in sources.list overriding backports?

---

### Post by techn9ne on 2005-02-20
You're right. 

I cut down my reposisitory list to nothing but backport and it worked. Something else I had in there was conflicting.

---

### Post by jdong on 2005-02-20
Remember that the "~" in the backports version forces it to be older than the same version without a tilde. It's extremely likely that another repository would override Backports.

---

### Post by sparkiegeek on 2005-02-21
[Battle for Wesnoth 0.8.11 has been released](http://www.wesnoth.org/forum/viewtopic.php?t=4656) 

*grin* *whistle*

---

