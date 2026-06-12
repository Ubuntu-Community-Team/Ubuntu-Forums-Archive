---
title: "FreeBSD users here?"
date: 2009-05-15
forum: The Cafe
---

### Post by linsux on 2009-05-15
Anyone run a flavour of BSD here? When 7.2 came out I laughed quite a bit, because of the Linux Youths talking about it like it was another Linux distribution. I even had to send an email to a Linux news site asking them to correct their article covering it because they referred to it as "A Linux Based Operating System".

So, who uses BSD and who knows what it actually is?

---

### Post by hewbert on 2009-05-15
I've used it since around 2004.  Was my primary desktop OS for years, but recently put Ubuntu on my laptop instead.  I still use it on some other boxes though.


<3 FreeBSD.

---

### Post by ViperChief on 2009-05-15
FreeBSD is an outstanding operating system. I wouldn't recommend it on the desktop to everyone. On a server, it is definitely the best OS out there, in my opinion.

---

### Post by dragos240 on 2009-05-15
What is the difference is using BSD rather than linux, I tried it once in a VM, but nothing seemed really different, other than the kernel, what is better about it.

---

### Post by mamamia88 on 2009-05-15
i heard they don't have flash on bsd so i don't use it.

---

### Post by dragos240 on 2009-05-15
Hmm.... I bet that they can if they wanted too.

---

### Post by DeadSuperHero on 2009-05-15
Heh. I've used PC-BSD as I'm still largely unfamiliar with the handbook. It ran great on the desktop,  though. 

The PBI system had some great implementations.
It felt much, much more stable.

The only downside was that X was a little slow.

---

### Post by ViperChief on 2009-05-15
> **mamamia88 said:**
> i heard they don't have flash on bsd so i don't use it.

Not true. You can actually use Flash with Firefox in Linux compatibility mode. It works very well.

---

### Post by wsonar on 2009-05-15
maybe they it is another distro because there all on distrowatch

I got a bsdbox

---

### Post by ViperChief on 2009-05-15
> **dragos240 said:**
> What is the difference is using BSD rather than linux, I tried it once in a VM, but nothing seemed really different, other than the kernel, what is better about it.

On the outside, when using the desktop, most of the differences are under the hood. BSD is known for it's rock-hard stability. As for the kernel, Linux is a kernel and the GNU userland(hence RMS' insistence on calling it GNU/Linux), whereas BSD is an entire operating system. This is part of where the stability comes from. Everything in the OS is developed together and interact much better.

The package management system, ports, is top-notch and, in my personal opinion, unmatched.

There are several differences between Linux and BSD. I am finishing up an article for Linsux.org which will discuss these differences. I hope to finish it up in the next day or two. Once it is posted, I would be happy to link it, if the moderators here will allow me, or I will just simply let you all know it is there for public consumption.

---

### Post by chucky chuckaluck on 2009-05-15
i thought about it for a while, but the documentation was tl/dr, so i went with arch instead.

---

### Post by linsux on 2009-05-15
> **chucky chuckaluck said:**
> i thought about it for a while, but the documentation was tl/dr, so i went with arch instead.

Heh. Seeing as the documentation is one of the larger points for using FreeBSD, I couldn't really see how it's an issue. I think it's awesome, it tells you what you need to know in a clean, simple way.

---

### Post by chucky chuckaluck on 2009-05-15
> **linsux said:**
> Heh. Seeing as the documentation is one of the larger points for using FreeBSD, I couldn't really see how it's an issue. I think it's awesome, it tells you what you need to know in a clean, simple way.

i don't have the patience. playing with my computer is just a hobby. i don't really need it, except to email myself reminders to do stuff.

---

### Post by mamamia88 on 2009-05-15
> **ViperChief said:**
> Not true. You can actually use Flash with Firefox in Linux compatibility mode. It works very well.

really? maybe i'll give it a try.

---

### Post by linsux on 2009-05-15
> **mamamia88 said:**
> really? maybe i'll give it a try.

Be sure to read this: [http://www.freebsd.org/doc/en/books/handbook/](http://www.freebsd.org/doc/en/books/handbook/)

---

### Post by ViperChief on 2009-05-15
If anything, it'll give you a chance to see one of the best systems out there. FreeBSD will give you a basic CLI system. Try out PC-BSD if you want a GUI install and KDE installed out of the box.

---

### Post by linsux on 2009-05-15
> **ViperChief said:**
> If anything, it'll give you a chance to see one of the best systems out there. FreeBSD will give you a basic CLI system. Try out PC-BSD if you want a GUI install and KDE installed out of the box.

I might also mention that flash is pretty much preconfigured to work in PC-BSD.

---

### Post by ViperChief on 2009-05-15
> **linsux said:**
> I might also mention that flash is pretty much preconfigured to work in PC-BSD.

Good point. I forgot about that. It works beautifully.

---

### Post by kelvin spratt on 2009-05-15
PC-BST is a very polished system, but sound does not work correct on my Nvidia based Mobo.

---

### Post by kk0sse54 on 2009-05-15
Another dedicated BSD user here, running FreeBSD-stable as well as NetBSD 5. Regarding PC-BSD though, nice artwork but I can't say I enjoyed it too much. I'm just not a big fan of PBIs.

---

### Post by linsux on 2009-05-15
> **C!oud said:**
> Another dedicated BSD user here, running FreeBSD-stable as well as NetBSD 5. Regarding PC-BSD though, nice artwork but I can't say I enjoyed it too much. I'm just not a big fan of PBIs.

It isn't without bugs. I'm rolling my own BSD desktop again after trying PC-BSD, X would take 108% of my ram in it.

---

### Post by baseface on 2009-05-15
you dont have to use the pbis in pc-bsd. you can still use ports.

---

### Post by subdivision on 2009-05-15
That's a pretty strong endorsement.

I don't use FreeBSD, but I have tried it and liked it.

---

### Post by baseface on 2009-05-15
flash is_not_hard to get working in freebsd. theres multiple ways it can be done. NATIVE flash isnt here yet, but maybe some day.
a gui out of the box shouldnt be an issue. you can install anything from ports using the following:
```
cd /usr/ports/whatever && make install distclean
```
ports/x11-wm contains a TON of window managers that you can install and try.
configuring a freebsd system is trivial... granted you know something about your hardware.
i can install and configure a freebsd system, getting all supported hardware and a window manager running in less than 30 mins. freebsd is very simple.

---

### Post by linsux on 2009-05-15
> **baseface said:**
> flash is_not_hard to get working in freebsd. theres multiple ways it can be done. NATIVE flash isnt here yet, but maybe some day.
a gui out of the box shouldnt be an issue. you can install anything from ports using the following:
```
cd /usr/ports/whatever && make install distclean
```
ports/x11-wm contains a TON of window managers that you can install and try.
configuring a freebsd system is trivial... granted you know something about your hardware.
i can install and configure a freebsd system, getting all supported hardware and a window manager running in less than 30 mins. freebsd is very simple.

And if you don't know how, there's always that huge pile of documentation.

---

### Post by albinootje on 2009-05-15
> **linsux said:**
> Anyone run a flavour of BSD here?

I used FreeBSD on my desktop years ago, and I still use FreeBSD and m0n0wall (FreeBSD based) on a few dedicated firewall-machines.

In the past I've tested several installations of NetBSD and OpenBSD, and PCBSD (Even bought an OpenBSD cdrom-set years ago).

I've also run an "experimental" backup server with FreeBSD and ZFS (as file system for the backups) but the specs of that machine were not good enough even after tweaking the ZFS settings in FreeBSD.

---

### Post by kk0sse54 on 2009-05-15
> **baseface said:**
> you dont have to use the pbis in pc-bsd. you can still use ports.

Tue, but for me I see the pbi as the defining feature of PC-BSD. If I'm going to use ports I might as well use FreeBSD especially since I generally don't like having a gui installed by default on any OS.

---

### Post by mohitchawla on 2009-05-15
I have been waiting for my end-semester exams to get over to really start playing around with the BSDs (again). NetBSD 5, OpenBSD 4.5 & FreeBSD 7.2 ! Are you kidding me ?! This is just awesome. Its a pity that I don't run a huge server or DragonFly BSD (*with* the HAMMER of course) would've been fun to work with! Oh and the PC-BSD release too, what with flash working out of the box & other goodies, should be good. Oh well back to studying some of Knuth's. :popcorn:

---

### Post by ViperChief on 2009-05-16
I'm setting up an OpenBSD firewall/gateway right now. After that, I want to tackle NetBSD. :D I've been meaning to use it for a while but had to fix my desktop first. It needed a lot of new hardware. :( But, now it's working so the fun is back. :D

---

### Post by handy on 2009-05-16
As mentioned in another thread, I used PC-BSD approx' a couple of years ago, it was nice, & the KDE setup was the best I had seen at that time (& I'm not a KDE fan).

I couldn't do everything I needed so I moved onto more distro surfing.

I have been using wondrous FreeNAS, since the end of last year, it was simple to set up, is as reliable as can be, & does its job perfectly for me. :)

---

### Post by toupeiro on 2009-05-16
I prefer SYSV based UNIX much more.

---

### Post by Sef on 2009-05-16
> Once it is posted, I would be happy to link it, if the moderators here will allow me, or I will just simply let you all know it is there for public consumption.

a link would be fine.

---

### Post by Ptero-4 on 2009-05-17
I run a MS Linux 11.2-Milestone1/FreeBSD 7.0 dualboot in my laptop.

---

### Post by HereZiz on 2009-05-20
I like FBSD very much. Having used Gentoo on my servers I am now preparing to migrate to FBSD completely. I find the kernel much easier and more straightforward to configure, if required, and the network stack is (not just in my opinion) better performing. FBSD is bleeding edge operating system with trademark stability.

---

### Post by Pasdar on 2009-05-20
I'm a Free-Of-BSD user.

---

### Post by baseface on 2009-05-20
> **HereZiz said:**
> I like FBSD very much. Having used Gentoo on my servers I am now preparing to migrate to FBSD completely. I find the kernel much easier and more straightforward to configure, if required, and the network stack is (not just in my opinion) better performing. FBSD is bleeding edge operating system with trademark stability.
 
its only bleeding edge if you want it to be. CURRENT, STABLE, RELEASE. choose your poison.

---

### Post by HereZiz on 2009-05-20
> **baseface said:**
> its only bleeding edge if you want it to be. CURRENT, STABLE, RELEASE. choose your poison.

 True, but I meant more like in the selection of available ports.

---

### Post by baseface on 2009-05-20
if you update your ports tree frequently, then yes, ports is usually pretty recent. packages is another thing.

---

### Post by Sorivenul on 2009-06-12
BSD user here. I run FreeBSD primarily, and have been using NetBSD recently as well, but mostly for testing purposes.

I enjoy the simplicity and easy maintainability of the BSD systems. It just makes sense, to me, and the ports/pkgsrc system is terrific, especially if used properly (proper flags in mk.conf). The 8.x series of FreeBSD is just around the corner and looks very promising.

I've considered joining the Evoke (formerly Damn Small BSD) team, or rolling my own for quite some time.

---

