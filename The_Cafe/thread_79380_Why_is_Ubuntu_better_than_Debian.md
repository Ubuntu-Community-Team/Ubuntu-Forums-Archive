---
title: "Why is Ubuntu better than Debian?"
date: 2005-10-20
forum: The Cafe
---

### Post by kamagurka on 2005-10-20
I am planning on slapping Ubuntu (or maybe Debian) on my computer, but I won't be using Gnome or KDE (fluxbox or openbox, most likely); does Ubuntu still give me some advantage over "normal" Debian? I mean, afaik Ubuntu is "just" a well configured Debian with a nice Gnome/KDE embedded, with basically the same package management and stuff, not?
Correct me if I'm wrong...

---

### Post by matthias_k on 2005-10-20
Ubuntu is not "better" than Debian. It targets a different audience. Debian is widely used on servers and is not a Linux distro suited for a desktop PC. That means, it doesn't have the good hardware support, great usability and ease of configuration of Ubuntu. In terms of stability, it's probably slightly more stable than Ubuntu since it has a more conservative package selection and less frequent release cycles (Debian releases "when it's done", Ubuntu releases run on a schedule which makes some releases seem "rushed out of the door").

Overall, it's really a matter of taste. You probably won't spend hours and hours in Ubuntu getting your hardware to work, you will however in Debian (it usually took me roughly two weeks to completely set up a Debian which could be considered to be suitable for day-to-day work; make that two days for Ubuntu).

Nobody forces you to use GNOME in Ubuntu, but if you won't you will miss some of the functionality, since both are tightly integrated. From my personal experience, those distros which integrate well with a certain desktop tend to be the "better" ones in terms of usability and ease of configuration. On the other hand, I know several people who love setting up a Linux "from scratch" and have to do everything themselves, without using some fancy GUI.

It really depends on what you consider to be "good" about a distro.

---

### Post by az on 2005-10-20
Ubuntu installs some proprietary drivers by default (like for some wireless cards) which are not available from Debian stable.

You probably will track newer packages with ubuntu (especially the backports) and they probably will get better security fixes than Debian Unstable.


However, if you do not have any proprietary driver needs and the packages in Sarge are fine for you, you could use that without problem.

---

### Post by matthias_k on 2005-10-20
I'd rather go with the testing branch (etch) if you decide to use Debian. It's pretty stable (Debian always had its own definition of stability; the testing branch is way more stable than the "stable" branches of other major distros...).

Anyway, my point was: Try plugging your USB stick, digicam, handy, iPod or whatever into your USB port: Debian will not recognize it without you spending hours and hours of reading HOWTOs and setting up hotplug and USB drivers manually.
With Ubuntu, all this works automagically. GNOME will even automount recognized devices and put an icon for you on the desktop so you can immediately browse the removable media. That's just one of many examples where Ubuntu outrules Debian; it just feels way more like a modern Desktop OS than Debian does (well, Debian doesn't claim to be that, that's why I dumped it on my Notebook and Desktop PC). So, ask yourself if you're more the tech-type who loves to fiddle around with drivers and hardware and system config (then go Debian), or if you're more the plug-'n'-play type (go Ubuntu).

Another good example: Notebook support.
Ubuntu comes with a fully patched stock kernel which works very well with notebooks and Centrino WLAN (WLAN worked out of the box for me). Furthermore, my Samsung X05's DSDT is buggy, so I had to fix it; this requires a kernel patch, which is already present in the Ubuntu stock kernel. This is also very convenient.

---

### Post by gunslinger on 2005-10-21
[QUOTE=matthias_k]...
Anyway, my point was: Try plugging your USB stick, digicam, handy, iPod or whatever into your USB port: Debian will not recognize it without you spending hours and hours of reading HOWTOs and setting up hotplug and USB drivers manually.
...[/QUOTE]
Erm, when was the last time you tried this in debian?
I mean the WM not console?
I was running debian sarge b4 this and both kde and gnome recognized my usb stick immediately and gnome even automounted the partitions.
Funnily enough, ubuntu 5.10 isnt doing it atm :)
--
jb

---

### Post by matthew on 2005-10-21
I've installed both. Debian does a lot less hand-holding and installs fewer things by default. It is also a lot more complicated to install and configure and I wouldn't recommend it for a newbie. Once they are running they can be made to be pretty much identical, but Ubuntu does it in a simpler fashion with Debian attending to stability and Ubuntu giving more attention to stabilizing the bleeding edge. What I mean is you are likely to find newer versions of the same program in Ubuntu, but possibly more stable versions in Debian.

I say, Ubuntu for the desktop and Debian for the server and enterprise.

---

### Post by shade11 on 2005-10-21
Ubuntu is better for home use.

---

### Post by xequence on 2005-10-21
From my experience... Ubuntu is debian, but polished up. I couldent get debian installed, but ubuntu was easy.

I am probably going to try debian again though. Infact, I am gonna get download it tommorow and install it ;)

---

