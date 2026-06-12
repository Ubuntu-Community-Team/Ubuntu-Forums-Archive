---
title: "the reall speed..............."
date: 2005-03-21
forum: The Cafe
---

### Post by blinksilver on 2005-03-21
this seems interesting enough, how much faster is the 64bit version of UBUNTU if you have to install so much 32bit stuff, i mean firefox, flash, openoffice, mplayer, the list embodies the most important parts of day to day use in a linux OS, so what is the speed bump, if it really even exists???

almost forgot this originally, i would bet a fair bit of money that 64 bit java does not work with 32bit firefox, so there is another big one

---

### Post by blinksilver on 2005-03-21
sorry i wrote fedora, don't know what i was thinking, had a late night

---

### Post by jdong on 2005-03-21
In my experience, there is NO NOTICEABLE performance difference between the 32-bit and 64-bit versions of ANY LINUX DISTRO, on a Athlon64 3000+ ClawHammer.

It's been shown that the 64-bit Linux port has slight benchmarkable performance boosts as a server, but even heavy video encoding on my system hasn't shown any practical (2 seconds on top of 11 hours) improvement.

Due to the lack of compatibility (i.e. Flash, good Java, etc), I've chosen to stay with 32-bit Ubuntu.

---

### Post by blinksilver on 2005-03-21
was doing some research, came across this, kinda a mixed bag, and that is with the compilers optimized, and in pure enviorment, i was hoping for better, i deal with alot to run 64bits, it seems unworth it now

[http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228&mode=nocomment](http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228&mode=nocomment)

---

### Post by jdong on 2005-03-22
I don't find those numbers accurate -- when I did oggenc, the speed was approximately equal, no 10-second gap.

Unless, of course, you have this nice Gentoo AMD64 setup with GCC 3.4/4.0, but then, you gotta have a LOT of free time!

---

### Post by IdoMcFly on 2005-03-22
[QUOTE=jdong]I don't find those numbers accurate -- when I did oggenc, the speed was approximately equal, no 10-second gap.

Unless, of course, you have this nice Gentoo AMD64 setup with GCC 3.4/4.0, but then, you gotta have a LOT of free time![/QUOTE]
 +1

IMHO all the performance tweak are really useless for a normal use. The only things that can improve a lot is the DMA settings on harddrive and cd-rom drive.

Maybe the 64bits makes a performance gap for Intel processor as they emulate somehow the 32bits instruction whereas AMD has a native 32bits mode inside.

---

### Post by jdong on 2005-03-22
The advantages of 64-bit Linux are:

1. Huge stuff support -- If you have >4GB of RAM, or have 2TB+ volumes (or deal with 2GB+ files on a regular basis), 64-bit has distinct advantages.

2. Y2.038K -- When UNIX time overflows, you'll thank yourself for 64-bit.


I don't really deal with any of the two, so I'm staying 32-bit for now :)

---

### Post by blinksilver on 2005-03-22
this is really kinda disapointing, i have been running the 64bit version for a while, it seems faster, but that is because of all of it is 64bit, except for openoffice, by the way, why is there no 64bit OOo2, i know one can't be compiled, but 2

---

### Post by cdhotfire on 2005-03-22
> Huge stuff support -- If you have >4GB of RAM, or have 2TB+ volumes (or deal with 2GB+ files on a regular basis), 64-bit has distinct advantages.
people who have this are either really rich, or did not get caught (like me:D).

---

### Post by jdodson on 2005-03-22
[QUOTE=jdong]The advantages of 64-bit Linux are:

1. Huge stuff support -- If you have >4GB of RAM, or have 2TB+ volumes (or deal with 2GB+ files on a regular basis), 64-bit has distinct advantages.

2. Y2.038K -- When UNIX time overflows, you'll thank yourself for 64-bit.


I don't really deal with any of the two, so I'm staying 32-bit for now :)[/QUOTE]

thats why my 3000+ is running 32 bit.  it seems to make the most sense at the moment for my computing needs.  my 64 bit motherboard doesnt even support > 2 gig of ram anyway, WTF?  anyways, it is one of the best motherboards supported in the kernel however, everything works like a charm.  i would rather have a well supported board than > 2 gigs of ram capacity.  i have 1 gig currently.

---

### Post by poofyhairguy on 2005-03-22
[QUOTE=blinksilver]this is really kinda disapointing, i have been running the 64bit version for a while, it seems faster, but that is because of all of it is 64bit, except for openoffice, by the way, why is there no 64bit OOo2, i know one can't be compiled, but 2[/QUOTE]


Don't be disapointed. You have a chip that mops the floor with 32 bit chips in 32 mode. When the OSes of the world catch up you'll be ready. Till then appreciate how future giants wreck shop with the old generation.

---

### Post by jdong on 2005-03-22
The special thing about AMD64 chips is that they run just as blazingly fast in 32-bit mode! You aren't 'losing' anything by using 32-bit mode instead of 64-bit, except in the two cases I described, you're getting everything you've paid for.


As for the huge amounts of RAM, think about Opteron database servers ;)

---

### Post by blinksilver on 2005-03-22
thats cool, i do like, it and i mean all my hardware is supported in 64bit, the only thing i lack is windows media, and Real, in all honesty, i ignore those sites anyway, so i think i will still stick with it, but any info one the OOo2 thing,

---

### Post by jdong on 2005-03-22
OOo 2 is a monster to compile... It also doesn't compile cleanly for AMD64, and is a BEAST to fix.

There is a ~200MB patch floating around for getting OOo 1.1.x [2 ish] to compile natively under AMD64, but you lose Java and plugin compatibility.

When I ran Gentoo, I had that version installed. It was unstable, and not at all faster.

---

### Post by blinksilver on 2005-03-22
i guess i will just sit pretty and be happy, i really do like my laptop, and because of the supercoolness of ubuntu it runs very well, so i think i will enjoy what i have, thanks for the heads up, and hope that the use of windows media and real media becomes less o that we get some  64bit codecs soon, thanks for all the info, 

even though i have been doing this for since the age of 8, and know a large collection of languages and hardware, i still consider myself quite the newb, so all the help is great

---

### Post by jdong on 2005-03-22
I started using Linux around the 2.6.0-test11 days, so I'm quite a newb myself. :D

---

### Post by TravisNewman on 2005-03-22
Wow really? You seem like you know more than most who have been around much longer.
I've personally been around since pre-2.0, but just barely

---

### Post by jdong on 2005-03-22
KDE 3.1.x was when I started learning about Knoppix, 2.6.0-test11 was the first kernel I compiled, about a week after doing my first Knoppix HD install alongside an XP pre-SP1 install.

---

### Post by blinksilver on 2005-03-22
pre 2.0, my god, i was redhat 8 during the 2.4 days, i thought this would never go anywhere then, i mean the first thing i did way the try the ati drivers, that went over well, X went out everytime, i ended up reloading 4 times then quit

---

