---
title: "Are there 32bit Linux versions still supported?"
date: 2020-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2020-11-04
In a recently posted thread a Lubuntu user asked for help installing WiFi drivers on a 32 bit version of Lubuntu. It seems that the version could be 16.04 which is out of life. There is a 32 bit Lubuntu 18.04 but that reaches end of life next year. 

As a service to Linux users on old hardware that is 32 bit can we suggest a 32 bit version of Linux that is still being supported? I am putting forward Debian Stretch (Up to  end of June 2022) and Debian Buster (up to end of June 2024). The purpose of this thread is to show an upgrade path that extends the usefulness of this kind of old hardware (32 bit Motherboards).

[https://wiki.debian.org/LTS](https://wiki.debian.org/LTS)

Regards

P.S. I note that Debian consider Stretch to be an obsolete release although still supported. So, I withdraw Stretch and stand firm on Buster.

---

### Post by Irihapeti on 2020-11-04
[CentOS 7]("https://www.centos.org/download/"), until mid-2024

CentOS 8 doesn't have a 32-bit option.

---

### Post by guiverc on 2020-11-04
I'd agree with Debian Buster. I tested it on a series of x86 hardware (pentium M & pentium 4) and truthfully had fewer issues than I did with later Ubuntu 18.04 *flavors* using the GA or HWE/5.4 kernels

- it doesn't require `forcepae --forcepae` to boot on older pentium M processors, which Ubuntu 4.15 & 5.4 kernels still require
- no (amd) graphical issue on old thinkpads that seems to impact 5.4 kernel (but not 5.3 or earlier); Debian Buster just happens to use an older kernel than Ubuntu's 18.04 with HWE and thus avoids the issue; Ubuntu 18.04 is fine using GA kernel

I don't know of other alternatives, but I've not looked.  I was using Debian long before I first started exploring other GNU/Linux distros a decade ago so it's home for me.

--
Debian LTS only support specific packages, so it'll depend what you use  Debian Stretch for, whether or not you should treat it as  fully-supported (just like a Ubuntu *flavor* after the normal 3  years of supported life somewhat, with the 5 years applying only to  'main' repo. packages).  I still have Debian Stretch on some boxes, but as I  don't browse the web on them I consider it safe (*that and I'm too lazy to re-install buster; not enough disk space to bump*)

---

### Post by DuckHook on 2020-11-04
There are still a number of decent 32-bit distros out there. The perennial go&#8209;to is Puppy, but my two faves are Bodhi and CrunchBang++ (forked from CrunchBang which sadly gave up the ghost a couple of years ago). This is assuming that those inquiring about 32-bit still want to run a DE.

I've found that the conundrum with 32-bit is not the distro&#8212;of which there are still some fine ones out there&#8212;but the fact that 32-bit HW is no longer up to the task of running today's bloated apps. A modern browser will choke most 32-bit boxes thus rendering academic the question of the OS. Such boxes can be very successful as servers though.

---

### Post by Irihapeti on 2020-11-04
After playing around with various browsers on an older netbook, I've come to the conclusion that it's not the browser that's bloated, it's the internet. The days of html/css-only sites seem to be past, and an older machine will struggle with just about anything out there.

---

### Post by DuckHook on 2020-11-04
True. It's kind of a self-reinforcing feedback loop isn't it? More bloated browsers beget more bloated sites which beget even more bloated browsers begetting yet more bloated sites. It spirals round and round, teetering upwards like an inverted cone.

I've found that *noscript* helps. It's pleasantly surprising how many sites are actually more informative shorn of their jingling bells, popups and eye candy, reduced to only the raw data. That's how I now read my news sites: by turning off all scripting.

---

### Post by mastablasta on 2020-11-05
noscript still seems to take its tool as it blocks, checks and sorts the scripts that should be blocked or not.

i think it might be time to exchange the 20 year old boxes :-) 

anyway:
EDIT:* what about LXLE? Lubuntu with extended support?*

AntiX and MXLinux - but not sure of their support cycle since they are somewhat tied to Debian
Similarly BunsenLabs Linux

These options might be a bit easier for new users. Debian is quite raw. as is CentOS. a lot of stuff have to be installed after OS install.

I am not sure how these specialised ones would do like Slitaz, TinyCore. they are maybe not as fully featured and easy to use.  

32 bit is shrinking quite fast.

---

### Post by yetimon_64 on 2020-11-06
> **grahammechanical said:**
> ... 16.04 which is out of life....Standard support end of life for 16.04 is April 2021, so not quite right but only about five months left to go. With the use of ESM the end of life for 16.04 can be as far off as April 2024. [[COLOR=#0000ff]Source[/COLOR]]("https://wiki.ubuntu.com/Releases").

Cheers, yeti.

---

### Post by CelticWarrior on 2020-11-06
> [COLOR=#000000]Standard support end of life for 16.04 is April 2021[/COLOR]
Only for standard Ubuntu, flavors get 3 years only.
We're commenting here based on the assumption that no one in their right mind would be using standard Ubuntu (Unity or Gnome) in those 32-bit 2o years old machines.

---

### Post by poorguy on 2020-11-06
This might be useful.

LXDE

[https://www.lxle.net/](https://www.lxle.net/)

[https://www.lxle.net/download/](https://www.lxle.net/download/)


32 bit iso download.

[https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download](https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download)

---

### Post by kurt18947 on 2020-11-07
> **DuckHook said:**
> True. It's kind of a self-reinforcing feedback loop isn't it? More bloated browsers beget more bloated sites which beget even more bloated browsers begetting yet more bloated sites. It spirals round and round, teetering upwards like an inverted cone.

I've found that *noscript* helps. It's pleasantly surprising how many sites are actually more informative shorn of their jingling bells, popups and eye candy, reduced to only the raw data. That's how I now read my news sites: by turning off all scripting.

So true. When I first installed noscript I was amazed at how many sites want to run scripts on a site like NFL.com or CNN.com. It can require patience to figure out which scripts are required to make a site functional and which are not required/undesirable. I start with no Google and go from there. Then of course there's google maps and Recapta which require google.com to function.

---

### Post by lammert-nijhof on 2020-11-11
For 32-bits I moved to FreeBSD 12.2 (Unix), that still has FULL support for 32-bits hardware including the i486. Also the BETA for release 13 has 32-bits support, however they will stop full support for i486 and i586 class CPUs thus CPUs older than 25 years. I use FreeBSD on a 2003 Pentium 4 HT (3.0 GHz); 1.25 GB DDR4 (400MHz), 2 IDE HDDs and 2 SATA-1 HDDs. Since mid 2019 I use the system as a headless backup server for my Ryzen desktop with Ubuntu 20.04. FreeBSD boots and runs from the ZFS file system and its implementation is more advanced than Ubuntu's experimental option. I have added a GUI with XFCE; Conky and XRDP. XFCE comes with the the well known XFCE apps, including Firefox. Installation is relatively simple, but adding the GUI requires some config file changes, but that process is very well documented. They also support other GUIs like Gnome and KDE.

All disk are used in ZFS-Raid-0, so booting is relative fast and the system is also relatively responsive also with the newest Firefox. The system is powered-on for 30-60 minutes/week, so it ages say 1 week/year. It is protected from the ugly, rude outside world by a 1200W Avtek surge protector. I expect, it will live till the end of times.

---

### Post by mastablasta on 2020-11-13
FreeBSD is definitely not something i would advise to a newbie.

---

### Post by tuxed-linux on 2020-11-17
Yes, Debian and linuxmint.

---

### Post by Dennis N on 2020-11-17
MX-Linux new MX-19.3 which was just released Nov 11, has 32-bit versions available. XFCE and KDE.

---

### Post by Perfect Storm on 2020-11-19
Even my moms boyfriend is changing his old 32-bit systems with used refurb 64-bit machines.

---

### Post by mastablasta on 2020-11-19
> **Artificial Intelligence said:**
> Even my moms boyfriend is changing his old 32-bit systems with used refurb 64-bit machines.

well it's about time he too jumped on 64 bit train. :P

MX linus is also based on debina. so as long as debian support its debian is a good option. after that there are less and less easy, newbie friendly options. for desktop PC i would really advise to get a refurb 64 bit or to get a new machine. i am still on single core but at least it is 64 bit.

---

### Post by Dennis N on 2020-11-19
MX Linux:
One thing to be aware of: the MX Linux installer still does not support LVM installation, so it's a no-go for potential customers who want to use LVM.

---

### Post by bernard010 on 2021-01-05
Their is Anti-X 32 bit OS. works well on older computers it has low hardware requirements. That is what I have on my old laptop with an atom processor & 1GB memory, Runs quick. It also comes in 64 bit.
[https://sourceforge.net/projects/antix-linux/files/Final/antiX-19/](https://sourceforge.net/projects/antix-linux/files/Final/antiX-19/)
Their is Linux Mint LMDE (Debian edition) 32bit & 64bit Still looking at 4GB memory W/newer processor
[https://linuxmint.com/download_lmde.php](https://linuxmint.com/download_lmde.php)

---

