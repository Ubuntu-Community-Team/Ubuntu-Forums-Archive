---
title: "Minimum system requirements"
date: 2007-01-22
forum: The Cafe
---

### Post by Mateo on 2007-01-22
I have a couple of old computers that I was wondering if I could put Ubuntu on.  One is a pentium 2, I believe 400mhz processor.  I think it originally had Windows 95 or 98, not sure which.  I think it's an 8gig hard drive (not sure about ram).  The other has an unknown processor (i don't have either computer with me at the time), but it was from the windowsME era, I think 64meg hard drive and unknown amount of RAM memory.

I'm pretty sure the latter can run linux, but would it be able to run GNOME (or KDE, I guess).  Or would a minimal WM be necessary?  What about the older computer, could it run ubuntu at all?

---

### Post by K.Mandla on 2007-01-22
Yes and yes. :D

It'll be slow and it might seem a little sluggish, but it can be done. Put Xubuntu on the faster of the two and see how it feels. If it's still too slow, try starting from a minimal installation and build up from there. Then you'll know if the older one will do well with Ubuntu.

If both of them seem lacking, look into some lighter distros. There are some very good graphical releases that are not at all taxing on hardware resources. ;)

---

### Post by DarkN00b on 2007-01-22
I all depends on how much functionality you want out of the machine. Just for fun last week I installed Grey Cat Linux on an old 486/50MHz machine with 16 megs of ram and a 500MB hard drive. Its not good for anything but a low end server on my home network but it works.

[Grey Cat Linux]("http://www.icewalkers.com/Linux/Software/513390/Grey-Cat-Linux.html") is really stripped down, with only the most basic kernel and tools and it sort of piggybacks itself off of DOS - Meaning DOS loads and then GCL takes over after DOS boots.. Now if I could only figure out how to configure IceWM 1.0 :lolflag: . 649x480 with graphical glitches in X is usable but I'd prefer more screen real estate.

Still a Linux install that will fit on 8 floppies ain't bad.

---

### Post by Jussi Kukkonen on 2007-01-22
RAM is going to be more important than CPU speed. I'd use xubuntu if I had less than 256MB. If I had less than 128MB I'd upgrade (but xubuntu would probably run with less)

There are dozens of threads about this by the way. Search for "hardware requirements" or "minimum requirements" and read what's been said before.

---

### Post by ~LoKe on 2007-01-22
[http://youtube.com/watch?v=h3Y6F1dSR8A](http://youtube.com/watch?v=h3Y6F1dSR8A)

---

### Post by Mateo on 2007-01-22
> **~LoKe said:**
> [http://youtube.com/watch?v=h3Y6F1dSR8A](http://youtube.com/watch?v=h3Y6F1dSR8A)

huh?  I can't even get beryl and a vidcap to run at the same time (slows down too much) on my pentium 4.  that's insane.  but cool I guess.

i might try to install the standard ubuntu on my older computer just to see how it performs.  i don't need it for anything, but it's just sitting in a basement in the box right now, so might as well try to make some use of it.

---

### Post by aPello on 2007-01-22
I have used a standard installation of ubuntu on a 450mhz p3 processor, 256mb ram, and it was sluggish (gnome was), needed to be using xfce or something.

And about that video of the xgl on the p2, i dont think its real.

---

### Post by PatrickMay16 on 2007-01-22
RAM is all you'd need to worry about, unless you have a REALLY slow processor (like an AMD K6-2 150MHz or something). In my experience with 128MB RAM xubuntu is a wise choice. With less than that, the only practical method of getting ubuntu working is doing a server install and installing only what you need (like X, a window manager, etc) and turning off all services except the ones you really need. I guess this could be trouble for someone just starting with linux.

---

### Post by mips on 2007-01-22
[http://fluxbuntu.org/](http://fluxbuntu.org/)  if you want a lightweigth ubuntu version

---

### Post by Mateo on 2007-01-22
Found out the newer of the two has 128mb SDRAM, so I guess xubuntu install is what i'll try.

---

### Post by Mateo on 2007-01-22
Wow, looking on ebay I didn't realize that RAM was dirt cheap now (haven't bought any in years).  My CPU is supposedly expandable to 512mb.  So.. can I buy any memory stick that is SDRAM and it will fit in my computer?  I have never upgraded ram on a computer so I don't know about compatibility and such.

---

### Post by Sunflower1970 on 2007-01-22
> **Mateo said:**
> I have a couple of old computers that I was wondering if I could put Ubuntu on.  One is a pentium 2, I believe 400mhz processor.  I think it originally had Windows 95 or 98, not sure which.  I think it's an 8gig hard drive (not sure about ram).  The other has an unknown processor (i don't have either computer with me at the time), but it was from the windowsME era, I think 64meg hard drive and unknown amount of RAM memory.

I'm pretty sure the latter can run linux, but would it be able to run GNOME (or KDE, I guess).  Or would a minimal WM be necessary?  What about the older computer, could it run ubuntu at all?

I put Ubuntu on a Pentium II 400 Mhz. I upgraded the RAM to 384MB, and it has two 15 Gig hard drives. Ubuntu's a bit slow, but runs much, much faster than the Windows 98 (first ed) on that computer.

---

### Post by Mateo on 2007-01-22
Sounds like we have similar computers.  Did you use the standard ubuntu distro, with gnome?

---

### Post by MkfIbK7a on 2007-01-22
> **Sunflower1970 said:**
> I put Ubuntu on a Pentium II 400 Mhz. I upgraded the RAM to 384MB, and it has two 15 Gig hard drives. Ubuntu's a bit slow, but runs much, much faster than the Windows 98 (first ed) on that computer.

my setup is the exact same thing but instead of gnome i use fvwm-crystal which is beautiful and extremely speedy

its in the repos

do sudo aptitude install fvwm-crystal

you will be awed at the speed

iceWM can also be good:biggrin:

---

### Post by Dr. C on 2007-01-22
I run Ubuntu Edgy on a Celeron 400 Laptop with 192 MB RAM and 2.5 MB of Video RAM. it actually runs very well, much faster that Windows XP and more stable than Windows 98. 

Ubuntu Breezy on the other hand was so extreamly slow on the same laptop as to be totaly useless. There has been a huge order of magnitude improvement over that last year as how Ubuntu performs on my Celeron 400 laptop.

---

### Post by burek on 2007-01-22
Think Openbox for a shining min. system :-)


(or tinywm)

---

### Post by jdralphs on 2007-01-29
hmmm ... i'm running a laptop with i think 2-4mb of video ram, 128mb system ram, and 400mhz k6 processor with a 10gb hdd.  i'm running ubuntu edgy, with xfce, enlightenment, and gnome.

gnome is relatively slow
xfce is faster than gnome and slower than enlightenment, but for its features, thats ok.
enlightenment/fluxbox/blackbox run pretty well

gnome runs much better after disabling any, ha, unnecessary services.

the only complaint i have is that video is unplayable.  cpu usage goes to 100% and memory/swap levels stay stable.  video and sound are out of sync and then pretty mucgh stop altogether.  any ideas?

---

### Post by Artemis3 on 2007-01-29
If you use gnome, run gconf-editor, look for apps -> metacity -> general and enable "reduced resources". This also has the benefit of getting rid of wireframe animations.
Make sure you use a light theme. If you have 2 HDs put each in a separate pata cable and make swap partitions in both. Linux can use them in parallel faster than a single one.

> the only complaint i have is that video is unplayable. cpu usage goes to 100% and memory/swap levels stay stable. video and sound are out of sync and then pretty mucgh stop altogether. any ideas?

Cpu is a major factor for compressed video playback. Try with vlc/mplayer, but don't expect h264 videos to play smooth anytime soon... Mpeg1 should work, mpeg2 and 4 maybe... Don't resize, use a low enough resolution if you can; if video is using shared memory don't assign too much to the card.

---

