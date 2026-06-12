---
title: "issues after libc6 update on 01.25.07 - anyone else?"
date: 2007-01-25
forum: Repositories &amp; Backports
---

### Post by hikaricore on 2007-01-25
Today after updating libc6, libc6-dev, and libc6-i686 I noticed some slowdown issues in Edgy.  X hung at my nvidia screen after manually restarting gdm (which I do on a daily basis as I play WoW on a preconfigured X server after shutting every unneeded service down), I noticed a slower bootup time, and even abnormally long hanging while gnome was loading.  The version of libc6 in question is 2.4-1ubuntu12.3.  Luckily I had copies of the recent 2.4-1ubuntu12.2 in my apt-get cache and was able to reinstall the old version.

What I'm curious about is if anyone else was experiencing this issue or if it's just me.  I'm about to restart the system and see if this has any effect.  I realize this could be a sudden hardware, memory, or hard drive issue so I'm taking that into consideration.  Though it just seems like odd timing.  Ironicly enough this new version of libc6 was supposed to fix a bug :)  not cause a new one. lol

--Aaron

---

### Post by hikaricore on 2007-01-25
Update: Reboot was a quick as normal, gdm loaded faster, and gnome loaded with the snappiness I've become used to.  I tried rebooting even powering down several times earlier even allowing my hardware to cool for quite awhile before booting.  Disk, memory, and video tests all seem to run without fault so I don't think any of this was an issue.

Still just strikes me as odd that an standard update of libc6 caused such a drastic change to my system.

---

### Post by jdong on 2007-01-26
it is typically a good idea to restart after the C libraries update. It should not lead to any slowdowns typicall though, but you never know.

---

### Post by HobieCat on 2007-01-30
I had the same issue, but i upgraded today.

Here's the interesting part of dpkg.log:

2007-01-30 18:47:53 upgrade libc6-dev 2.4-1ubuntu12 2.4-1ubuntu12.3
2007-01-30 18:47:53 status half-configured libc6-dev 2.4-1ubuntu12
2007-01-30 18:47:53 status unpacked libc6-dev 2.4-1ubuntu12
2007-01-30 18:47:53 status half-installed libc6-dev 2.4-1ubuntu12
2007-01-30 18:47:54 status half-installed libc6-dev 2.4-1ubuntu12
2007-01-30 18:47:54 status unpacked libc6-dev 2.4-1ubuntu12.3
2007-01-30 18:47:54 status unpacked libc6-dev 2.4-1ubuntu12.3
2007-01-30 18:47:55 upgrade libc6 2.4-1ubuntu12 2.4-1ubuntu12.3
2007-01-30 18:47:55 status half-configured libc6 2.4-1ubuntu12
2007-01-30 18:47:55 status unpacked libc6 2.4-1ubuntu12
2007-01-30 18:47:55 status half-installed libc6 2.4-1ubuntu12
2007-01-30 18:47:56 status half-installed libc6 2.4-1ubuntu12
2007-01-30 18:47:57 status unpacked libc6 2.4-1ubuntu12.3
2007-01-30 18:47:57 status unpacked libc6 2.4-1ubuntu12.3
2007-01-30 18:47:57 status unpacked libc6 2.4-1ubuntu12.3
2007-01-30 18:47:58 status unpacked libc6 2.4-1ubuntu12.3
2007-01-30 18:47:58 status unpacked libc6 2.4-1ubuntu12.3
2007-01-30 18:47:58 status half-configured libc6 2.4-1ubuntu12.3
2007-01-30 18:47:59 status installed libc6 2.4-1ubuntu12.3
2007-01-30 18:48:01 upgrade libc6-i686 2.4-1ubuntu12 2.4-1ubuntu12.3
2007-01-30 18:48:01 status half-configured libc6-i686 2.4-1ubuntu12
2007-01-30 18:48:02 status unpacked libc6-i686 2.4-1ubuntu12
2007-01-30 18:48:02 status half-installed libc6-i686 2.4-1ubuntu12
2007-01-30 18:48:02 status half-installed libc6-i686 2.4-1ubuntu12
2007-01-30 18:48:02 status unpacked libc6-i686 2.4-1ubuntu12.3
2007-01-30 18:48:02 status unpacked libc6-i686 2.4-1ubuntu12.3
2007-01-30 18:48:02 upgrade libvolumeid0 093-0ubuntu18 093-0ubuntu18.0edgy2
2007-01-30 18:48:02 status half-configured libvolumeid0 093-0ubuntu18
2007-01-30 18:48:02 status unpacked libvolumeid0 093-0ubuntu18
2007-01-30 18:48:02 status half-installed libvolumeid0 093-0ubuntu18
2007-01-30 18:48:02 status half-installed libvolumeid0 093-0ubuntu18
2007-01-30 18:48:02 status unpacked libvolumeid0 093-0ubuntu18.0edgy2
2007-01-30 18:48:02 status unpacked libvolumeid0 093-0ubuntu18.0edgy2
2007-01-30 18:48:02 upgrade udev 093-0ubuntu18 093-0ubuntu18.0edgy2
2007-01-30 18:48:02 status half-configured udev 093-0ubuntu18
2007-01-30 18:48:02 status unpacked udev 093-0ubuntu18

Everithing worked smoothly unitl i did this upgrade... and now i'm posting form win..:(
It looks like the bad packages are more or less the same, and i don't have any package to downgrade.
I don't have only a slow system, but a completely unusable one!
I have no mouse, no keyboard and the touchpad makes the pointer jump for here to there on the screen... I can only login from the console in recovery mode.
Please, anyone out there knows and can tell me how to solve this?

 Thanks a lot.
 Giorgio

P.S. Now i'm backing up all the stuff i may need and get prepared to a full new system install because i'm in a hurry with my business.

---

### Post by HobieCat on 2007-01-30
Sorry if i reply to myself. But it looks like i've solved it!!
I guess a brief description may be of any help to someone, so here it is.

1. Downloaded from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) the following packages:
libc6_2.4-1ubuntu12.1_i386.deb
libc6-dev_2.4-1ubuntu12.1_i386.deb
libc6-i686_2.4-1ubuntu12.1_i386.deb
libvolumeid0_093-0ubuntu18_i386.deb
udev_093-0ubuntu18_i386.deb
volumeid_093-0ubuntu18_i386.deb

2. dpkg -i  for each one of them. And the system successfully downgraded 'em all.

3. reboot, but still not working. So reboot again in recovery mode and i found out that some modules could not be loaded. So a depmod -a solved this. Rebooted and everything went ok.

4. upgraded again that packages, rebooted and all seems ok!!!

hope this will help someone,

 Giorgio

---

