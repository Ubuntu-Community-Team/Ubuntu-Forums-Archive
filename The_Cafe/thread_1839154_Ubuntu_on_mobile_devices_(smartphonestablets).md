---
title: "Ubuntu on mobile devices (smartphones/tablets)"
date: 2011-09-05
forum: The Cafe
---

### Post by gillza on 2011-09-05
Dear All,

I beg for someone to educate me, a clueless simpleton...
Why is it so hard to install Ubuntu on mobile devices that are running Linux based OSes (WebOS/Android/Bada) and Tablets (android/webos)? I mean having a true Dual Boot option, or just replace the original OS completely.

Lets assume for simplicity that all the drivers are available... Why can't one create an sdcard with Ubuntu (or other Linux distro) on it using a PC for example and boot from it to install the OS.

Is it the lack of a boot loader that allows for that? Or what? Could someone please explain? 

Thank you!

---

### Post by gillza on 2011-09-05
Anyone?

---

### Post by akand074 on 2011-09-05
You can. There are bootloaders that allow you to run multiple Android ROMs. Theoretically you can have Ubuntu instead given the space. You'd need an ARM based build of Ubuntu, and even then you'd have to make sure it's functional with all the hardware. I've seen Ubuntu on tablets before. It's not overly difficult I'm sure some people over at the XDA forums could have Ubuntu's ARM version ported to a particular tablet.

EDIT: Quick google search of "Ubuntu tablet"

[Here's]("http://www.youtube.com/watch?v=MErL7FslBjU") a youtube video of Ubuntu running over Android through a virtual machine it seems.
[Here's]("http://www.linuxfordevices.com/c/a/News/Ekoore-Perl-Python-and-Pascal/") an actual Ubuntu tablet.

---

### Post by gillza on 2011-09-05
I see. Thank you. 
 
It's just I notice threads where Ubuntu is being "ported" on to the tablet but it actually runs within the currently installed system, be that android (through VNC) or webos/maemo (Chroot). I haven't seen one high end tablet that comes preloaded with android/webos/or whatever that has Ubuntu/Debian or other Linux distro successfully ported on it so it actually boots into it.

PS. First link Ubuntu is running within android and is accessed through VNC. 

Second is what I'm looking for. Unfortunately there are two or three tablets out there that are running Full linux natively.. And almost no handhelds (my beloved n900 and n9 that will be almost impossible to get)

---

### Post by aeiah on 2011-09-06
its worth bearing in mind that android is really nothing like a normal linux distro. the android kernel is a fork of the linux kernel, but most of the other android stuff runs inside a java vm

---

### Post by gillza on 2011-09-06
> **aeiah said:**
> its worth bearing in mind that android is really nothing like a normal linux distro. the android kernel is a fork of the linux kernel, but most of the other android stuff runs inside a java vm

Yes, that is why in the original post I say Linux based :) and that is where my dislike towards it comes from. webOS is closer to linux than android is. But still, android runs on modified linux kernel so the drivers should not be a big issue for porting ubuntu, it is more likely the bootloader. However I have found a ubuntu wiki entry where an issue is raised regarding Tegra 2 tablets:
[https://wiki.ubuntu.com/ARM/TabletList](https://wiki.ubuntu.com/ARM/TabletList)
"Problems with Tegra2: various important bits such as power management, sound and GL are provided by a user space daemon. This daemon only works with the kernel and X11 it was compiled against. Meaning unless Nvidia provides us with builds, there is no way of ever sensibly supporting this. " Sad...

---

### Post by u-noob-tu on 2011-09-06
its possible, most definitely. I remember back when I hacked windows mobile (that was before I saw the light), I heard a lot about the htc devices being hacked to run almost anything, including ubuntu. This was 2 years ago, and with the advent of dual core processors and tablets its only going to get better. I just bought an HP touchpad for $150, and I would love to see ubuntu on it (right now I've heard a lot of android stuff is happening with it).

---

### Post by woodmaster on 2011-09-06
> **u-noob-tu said:**
> its possible, most definitely. I remember back when I hacked windows mobile (that was before I saw the light), I heard a lot about the htc devices being hacked to run almost anything, including ubuntu. This was 2 years ago, and with the advent of dual core processors and tablets its only going to get better. I just bought an HP touchpad for $150, and I would love to see ubuntu on it (right now I've heard a lot of android stuff is happening with it).

I am posting from Ubuntu running in a webOS card right now.  Its fairly easy to setup.  Goto forums.precentral.net and search for Ubuntu.  On a side note, team Touchdroid got the Android touchscreen driver operational today!  Soon I hope to have 3 OS' running on this thing.  Choices are good!

---

### Post by gillza on 2011-09-07
> **woodmaster said:**
> I am posting from Ubuntu running in a webOS card right now.  Its fairly easy to setup.  Goto forums.precentral.net and search for Ubuntu.  On a side note, team Touchdroid got the Android touchscreen driver operational today!  Soon I hope to have 3 OS' running on this thing.  Choices are good!

unfortunately it will run in chroot, not true dual boot. look in the original post

---

### Post by 1clue on 2011-09-07
Why are you choosing Ubuntu?

More specifically, why are you choosing a distro which only supports Intel 32 or 64-bit architecture?

Speaking in Linux terms, Ubuntu supports less hardware than any distro I've ever tried, a conscious decision so they could make the hardware they DO support work really well and with less effort on the user's part.  Go back to Debian and you get great support for all sorts of hardware.  Go to one of the micro distros, or a source-based distro, and you can at least get all your stuff to build for your architecture without having to fight with every package.

---

### Post by gillza on 2011-09-07
> **1clue said:**
> Why are you choosing Ubuntu?

More specifically, why are you choosing a distro which only supports Intel 32 or 64-bit architecture?

Speaking in Linux terms, Ubuntu supports less hardware than any distro I've ever tried, a conscious decision so they could make the hardware they DO support work really well and with less effort on the user's part.  Go back to Debian and you get great support for all sorts of hardware.  Go to one of the micro distros, or a source-based distro, and you can at least get all your stuff to build for your architecture without having to fight with every package.

ubuntu supports arm actually. Lets stay on topic of handhelds and smartphones  here please. and do p,ease read the whole discussion i mentioned ubuntu or other linux distros.

---

