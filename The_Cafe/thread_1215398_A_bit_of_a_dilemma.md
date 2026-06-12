---
title: "A bit of a dilemma"
date: 2009-07-17
forum: The Cafe
---

### Post by Grant A. on 2009-07-17
Well, it's official, my puny laptop can't handle Ubuntu anymore. My problem is not that it is slow, but that it makes my CPU usage skyrocket, and that it makes my laptop run scalding hot.

Is there any relatively light-weight distribution that is well-known, trusted, and as easy to use as Ubuntu? I used to run Arch on my laptop, but I got very tired of having to maintain the thing.

Specifically, here are the things I'm looking for:

[list]
[*]Has APT
[*]Can be installed to an HDD
[*]Has repositories
[*]Uses GNOME, Fluxbox, or XFCE
[*]Has an excellent community
[*]Mono free (Not for patent/FUD reasons, but more for the reasons that mono is a **huge** package.)
[*]Does not load everything into RAM like Puppy.
[*]Fast
[*]Lightweight
[*]Stable
[*]Secure
[*]Intel i810 graphics card drivers
[*]Has flash 10 in its repositories
[*]WPA2+AES support
[*]Wireless support
[*]Excellent Documentation
[*]Low Maintenance 
[/list]

Thanks in advance for the help. :D

---

### Post by vinutux on 2009-07-17
> **Grant A. said:**
> Well, it's official, my puny laptop can't handle Ubuntu anymore. My problem is not that it is slow, but that it makes my CPU usage skyrocket, and that it makes my laptop run scalding hot.

Is there any relatively light-weight distribution that is well-known, trusted, and as easy to use as Ubuntu? I used to run Arch on my laptop, but I got very tired of having to maintain the thing.

Specifically, here are the things I'm looking for:

[list]
[*]Has APT
[*]Can be installed to an HDD
[*]Has repositories
[*]Uses GNOME, Fluxbox, or XFCE
[*]Has an excellent community
[*]Mono free (Not for patent/FUD reasons, but more for the reasons that mono is a **huge** package.)
[*]Does not load everything into RAM like Puppy.
[*]Fast
[*]Lightweight
[*]Stable
[*]Secure
[*]Intel i810 graphics card drivers
[*]Has flash 10 in its repositories
[*]WPA2+AES support
[*]Wireless support
[*]Excellent Documentation
[*]Low Maintenance 
[/list]

Thanks in advance for the help. :D


Try Xubuntu official xfce version of ubuntu **[www.xubuntu.org]("www.xubuntu.org")**

.

---

### Post by Grant A. on 2009-07-17
> **vinutux said:**
> Try Xubuntu official xfce version of ubuntu **[www.xubuntu.org]("www.xubuntu.org")**

.

Thanks, but I've tried Xubuntu before. For an XFCE distro, it's very bloated.

---

### Post by DeadSuperHero on 2009-07-17
Try WattOS: [http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by ell02 on 2009-07-17
idk if it meets mono but crunch bang is ubu based and was good.

---

### Post by vinutux on 2009-07-17
**[dreamlinux]("www.dreamlinux.com.br")** - debien based but gr8 one 

[**Fluxubuntu**]("http://fluxbuntu.org/")

**[U-lite]("http://www.u-lite.org/")** 

**[Lubuntu]("http://www.lubuntu.org/")**

[B][URL="http://opengeu.intilinux.com/Home.html"]
opengue[/URL][/B]

.

---

### Post by renzokuken on 2009-07-17
crunchbang  -  [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

based on ubuntu so has all its repos available

---

### Post by JohnFH on 2009-07-17
> **Grant A. said:**
> Well, it's official, my puny laptop can't handle Ubuntu anymore. My problem is not that it is slow, but that it makes my CPU usage skyrocket, and that it makes my laptop run scalding hot.


Have you looked into why the CPU usage is sky high rather than immediately jumping to another distro?  What's the spec of your laptop?

---

### Post by stwschool on 2009-07-17
I vote Crunchbang as it's UBU based but very very light and efficient. So, if your existing machine can run ubuntu it'll run crunchbang with the same low-maintenance but the added bonus of being fast as a fast thing.

---

### Post by stwschool on 2009-07-17
> **JohnFH said:**
> Have you looked into why the CPU usage is sky high rather than immediately jumping to another distro?  What's the spec of your laptop?
Good point.. which programs are specifically using a lot of RAM? (System -> Admin -> System Monitor to find out)

---

### Post by gnomeuser on 2009-07-17
If it ran perfectly before then it is very likely a bug. Please go and file it.

---

### Post by directhex on 2009-07-17
... if CPU use is an issue, you don't want Flash

Flash can make my i7 cry

---

### Post by urukrama on 2009-07-17
> **Grant A. said:**
> Is there any relatively light-weight distribution that is well-known, trusted, and as easy to use as Ubuntu?

Debian. Use Debian Testing if you want stable newer packages.

---

### Post by RiceMonster on 2009-07-17
Try zenwalk for a nice Xfce distro.

---

### Post by 3rdalbum on 2009-07-17
Mono is not huge. It's 36.3 megabytes installed (and a lot of those I'm sure are just dependencies for some other Mono programs I have). By contrast, libboost takes up 338 megabytes on disk if you have the development headers too.

Ubuntu should not push your CPU so hard that your computer gets hot, unless you're doing some intensive computing. I'd investigate the cause of the excessive CPU use before looking at different distributions, as it's probably just a runaway process that can be disabled.

---

### Post by malachi1990 on 2009-08-01
If you have the time to do so, install the command line only system and build up from there.  I noticed a fairly significant reduction in ram on my system (~350 on a default install to about 200 on a customized environment).

But do make sure its not a bug in a piece of software (firefox often has memory hemorrhages if you have multiple tabs open).  You may also need to make sure that any fans on your motherboard are properly attached (I had a similar problem on my laptop until the guys that fixed it told me the fan for the gpu was loose).

---

### Post by pelle.k on 2009-08-01
Jaunty doesn't activate the "ondemand" governor of the CPU like previous versions did, since powernowd is not a part of the ubuntu-desktop package any longer. You might be affected by that.
If that is the case, here is the bugreport about that , [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343354)
There is a simple solution though, install cpufrequtils or powernowd (no configuration necessary, just reboot once). It works in most cases.

---

### Post by slakkie on 2009-08-01
> **malachi1990 said:**
> If you have the time to do so, install the command line only system and build up from there.  I noticed a fairly significant reduction in ram on my system (~350 on a default install to about 200 on a customized environment).


+1 - Would be my advise as well.

---

