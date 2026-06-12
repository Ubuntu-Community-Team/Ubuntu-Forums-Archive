---
title: "Pc-bsd?"
date: 2005-11-13
forum: The Cafe
---

### Post by YourSurrogateGod on 2005-11-13
Has anyone tried [this](http://www.pcbsd.org/) Unix distro? Just curious...

---

### Post by jdong on 2005-11-13
Yes -- interesting idea, though I strongly disagree with its packaging system (pqi) -- Try DesktopBSD instead, which is based off Ports, the unbeatable package management system of BSD. (though DesktopBSD has yet to release a version based off FreeBSD 6)

---

### Post by tseliot on 2005-11-13
[QUOTE=jdong]Yes -- interesting idea, though I strongly disagree with its packaging system (pqi) -- Try DesktopBSD instead, which is based off Ports, the unbeatable package management system of BSD. (though DesktopBSD has yet to release a version based off FreeBSD 6)[/QUOTE]
Does this mean that DesktopBSD compiles every package from source?

I've tried Gentoo and I know that it's similar to BSD. The problem is that it takes too much to compile everything (e.g. GNOME or KDE take 6 hours to compile)

---

### Post by jdong on 2005-11-13
[QUOTE=tseliot]Does this mean that DesktopBSD compiles every package from source?

I've tried Gentoo and I know that it's similar to BSD. The problem is that it takes too much to compile everything (e.g. GNOME or KDE take 6 hours to compile)[/QUOTE]

No; DesktopBSD gives you the power to compile them from source if you wish. BSD Ports also supports binary packages, and they do provide fairly up-to-date binaries for all the packages, though if you wanna stay bleeding edge you have to compile some stuff yourself.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=tseliot]Does this mean that DesktopBSD compiles every package from source?

I've tried Gentoo and I know that it's similar to BSD. The problem is that it takes too much to compile everything (e.g. GNOME or KDE take 6 hours to compile)[/QUOTE]
According to their site, DesktopBSD installs similarly to how Ubuntu would.

---

### Post by tseliot on 2005-11-13
[QUOTE=YourSurrogateGod]According to their site, DesktopBSD installs similarly to how Ubuntu would.[/QUOTE]
Well my only problem with Gentoo is that I can't leave the computer 6 hours to compile a graphical interface or to keep it up to date. I think it works ok though. BTW binaries exist also in Gentoo.

I might try DesktopBSD when I have some time, I could use it to replace Gentoo.

---

### Post by YourSurrogateGod on 2005-11-13
Kind of off-topic, but isn't it widely acclaimed that Unix based operating systems are more stable than Linux ones? Does this claim have any merit to it?

---

### Post by Omnios on 2005-11-13
I have installed it on my old P2-350 as I could not get Ubuntu to install on it. No kernal found. I prefear Ubuntu and will not install PC-BSD on my main computer but my P2 is just there for internet forum backup and to play around with. The number click install programs is limited and from what I read you can still install BSD-ports but not shure how yet. The other bsd entry Desktop bsd seems to have a port manager and im wondering how to get one to PC-BSD. Correct me if im wrong but im getting a picture where BSD is limited to what would consist of a Ubuntu system with synaptic and real difficult system to manage outside of that box.

 In the future they may develop into serios desktop contenders but generaly speaking I prefear Ubuntu over all. Just so much more customization and flexablility. I think it will boil down to software availablity in the long run as a distro can be raited by all its little nails but there are a few huge spikes and Ubuntu and Linux seems to be way in the lead.

 Basicly PC-BSD is there on my P2 unless I can find a good Linux distro that will run on a Huston teck, Ami BIOSY, sis onboard motherboard.

---

### Post by jdong on 2005-11-13
[QUOTE=YourSurrogateGod]Kind of off-topic, but isn't it widely acclaimed that Unix based operating systems are more stable than Linux ones? Does this claim have any merit to it?[/QUOTE]
I've yet to see good proof of that. BSD's and Linuxes are all highly stable, but then again there are the poorly maintained versions of Linux with experimental nature kernels that seem to soil the Linux name... ;)

I maintain both Linux and BSD servers for robotics, all under very demanding loads (build servers and backup servers especially) with excellent stability.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=jdong]I've yet to see good proof of that. BSD's and Linuxes are all highly stable, but then again there are the poorly maintained versions of Linux with experimental nature kernels that seem to soil the Linux name... ;)

I maintain both Linux and BSD servers for robotics, all under very demanding loads (build servers and backup servers especially) with excellent stability.[/QUOTE]
*shrug* I've heard such rumors in passing, so I'm not sure.

My OS professor talked about some operating systems that will continue to function (well, as best as it can given the circumstances) even if you take out a CPU out of the machine (for replacing.) Anyone heard of something like this? If so, what OS is this?

---

### Post by jdong on 2005-11-13
[QUOTE=YourSurrogateGod]*shrug* I've heard such rumors in passing, so I'm not sure.

My OS professor talked about some operating systems that will continue to function (well, as best as it can given the circumstances) even if you take out a CPU out of the machine (for replacing.) Anyone heard of something like this? If so, what OS is this?[/QUOTE]

Well, this **requires special hot-swappable CPU hardware**! Trying it with an ordinary multiprocessor mobo would send you back to Newegg buying some new parts :)

Linux also has some levels of hotplug CPU support, but notably Solaris/SPARC blades sport this trick.

Cool trick? Yes, of course. Say anything about stability? Not at all -- it's merely a feature. It doesn't mean that the OS would survive if a CPU malfunctions and spits back erroneous results.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=jdong]Well, this **requires special hot-swappable CPU hardware**! Trying it with an ordinary multiprocessor mobo would send you back to Newegg buying some new parts :)

Linux also has some levels of hotplug CPU support, but notably Solaris/SPARC blades sport this trick.

Cool trick? Yes, of course. Say anything about stability? Not at all -- it's merely a feature. It doesn't mean that the OS would survive if a CPU malfunctions and spits back erroneous results.[/QUOTE]
Thanks for clearing it up. I wish my prof had said that.

---

### Post by docboat on 2005-11-17
Yes, I have tried both PC-BSD and FreeBSD. They both look good, but I could not use them, as I could not connect to the net:

I need to connect using pppoeconf. BSD is really awkward about that, and although there is a good documentation, it really did not help me as I was unable to find out what my ethernet connection was called. When I can get the patience again I will try and sort it out - using FreeBSD, as the documentation is better.

---

