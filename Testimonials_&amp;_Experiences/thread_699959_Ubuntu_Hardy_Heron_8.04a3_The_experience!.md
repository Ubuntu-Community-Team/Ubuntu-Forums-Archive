---
title: "Ubuntu Hardy Heron 8.04a3: The experience!"
date: 2008-02-17
forum: Testimonials &amp; Experiences
---

### Post by tvdxer on 2008-02-17
About two or three weeks ago I installed Ubuntu Hardy Heron 8.04 alpha 3 on a new 80 GB EIDE hard drive I bought especially for trying out OSes on my five-year-old computer (P4 2.0 GHz, 512 MB RAM, ATI AIW 7500 video, CD-RW / DVD drives, SB Live Value, etc.).  I chose the latest development version, because, well, it might be more interesting.

Installation was a pain, not because of Ubuntu's text-mode installer (I understand the complete version has a live CD install method), but because I had the hard drives configured wrong.  After two attempts at installs, I was able to rectify the issue by making a few changes to my hard drive configuration in BIOS, and what do you know, Ubuntu loaded!

All of my hardware was recognized properly and the resolution defaulted to the 1440 x 900 of my LCD monitor, although Ubuntu wanted to use my choppy on-board sound rather than my Live! Value card.  I went the fast and easy route and disabled the motherboard audio in BIOS and Ubuntu automatically switched to my "good" sound card.

I found the initial GNOME interface attractive.  I disabled Compiz effects, thinking the system would run faster, but later I noticed little difference between no effects and full effects in the Preferences - Display dialog.  I was quite amazed that such attractive effects would (initially) work well on a system as slow and old as mine, but they did.  The only effect perhaps was slower tab-changing in Firefox.

Unfortunately, not all was good.  The Compiz effects went haywire whenever I tried to open a full-screen application, or even when I tried to look at some of the Panoramio or Wikipedia pop-ups on Google Earth.  Some of the included GNOME applications were slow (Rhythmbox, at least until I installed / started jackd, but even then) or underfeatured (the text editor, shell).  Not only that, but vlc barely even ran under GNOME, and opening the svgalib game Lincity completely crashed the system.

So, even while still under a partial trance from the very attractive GNOME + Compiz setup, I installed the kubuntu-desktop package through apt-get and have been on KDE since.  Compiz seems considerably slower in KDE, though I do not usually have it on there so it is not an issue.  Otherwise it is faster, which suprises me.  I am impressed with how far some of the KDE apps have came since I last used Linux; others I am less enchanted by (especially KSpread and KPresent).  One thing that made me happy was the fact that amarok's streaming audio and Magnatune access is nearly instant, versus the five to fifteen second wait in Rhythmbox; that VLC ran perfectly under KDE, unlike in GNOME where it was so bug-ridden as to be nearly useless, and Lincity ran fine (though it's a little dated for me).  So, for the most part KDE 3.5 fulfills my needs.  I also installed KDE 4, which runs well, but I'm not too much of a fan of the interface.  Maybe I'll change it to look like the "old" KDE, but I think I'll stick with 3.5 until 4.1 comes out.  In addition to KDE and GNOME, I also installed about 15 - 20 window managers for the fun of it; hey, we have Synaptic :)

I really like Linux (having used it on and off for almost ten years now), and barely ever boot into Windows, though I am not ready to delete my NTFS partition just yet.   But again, there have been a lot of issues, most of which I've actually enjoyed working out.  Here are things that still need work:

* Google Earth runs fairly well under Linux, maybe a bit slower than Windows, but hey, at least I don't have system reboots out of nowhere as I do when I run it under XP.  However, there's one exception: 3D buildings render EXTREMELY slow, versus at a very acceptable speed in Windows, and some messing around with the view angle happened to completely bring my X down, forcing a reboot.  However, I don't really hold this against Ubuntu, as I'm in an alpha version of the distro.

* Something is confused with hardware acceleration on my old ATI Radeon 7500.  I've heard ATI's drivers aren't quite up to nVidia's, so I'll definitely put a GeForce chip in my next machine (which hopefully I'll build soon!).  This manifests itself in 1) margins set by mouse causing vertical lines to stay in place in OpenOffice.org (until I minimize and re-maximize the window), 2) pictures not displaying in presentations in Impress when full-screen (only when "Hardware Acceleration" is turned on in OO.o, thank God), and 3) probably other things I can't think of.  I tried switching over to exa from xaa in Xorg.conf, but this caused my system to run very slow.

* Amarok sometimes reports that it needs a demux plugin for a certain stream when clicking the same stream again causes audio to begin normally.  Apparently this is a xine-lib problem wihch will be rectified in the next release.  Also, Amarok was crashing a lot in the beginning, but seems to have improved considerably with regular use (and possibly an update?)

* Flash is kinda slow.

* In some of the games (X-moto, Planet Penguin Racer) I play there are mildly annoying "line" artifacts that are kind of hard to describe.

* OO.o handles Impress / PPT pres. kind of slow, especially PPT -> ODP conversion.

* Probably some other ones I don't feel like typing up right now.

Otherwise, however, I rarely ever feel any need to boot up into Windows, and now with Windows acting slower after putting a new HD in (? - perhaps due to the million shut-downs while booting up it went through before I figured my heat sink wasn't on right), I virtually always use Ubuntu (is it Kubuntu now with all the KDE stuff?).   I could write much more, and maybe I will later, but otherwise I'm happy.

---

### Post by freebeer on 2008-02-17
Thanks for sharing your experience.  Those of us who are interested in the "news" of the next release, but otherwise don't have the time or resources to try it ourselves, appreciate the write-ups.

As for the speed issues you mentioned, it is my guess (read: I don't know for sure) that since it's alpha software, there's probably many an application that's been coded and released with debugging on (so that they can track bugs).  This greatly slows down any application.  If I'm right, then upon official release, we'll see those apps "cleaned up" and running much faster.

---

### Post by tvdxer on 2008-02-17
Hmmm, maybe that's why (when I was using GNOME) I got those messages asking me if I wanted to send a report to the developer, and showing a "complete report" as being some insane size, like 5 MiB?  

Most of the apps, however, don't seem very slow.

Something I forgot to mention: From what I hear, the current standard release of Ubuntu does not have NTFS support enabled by default.  Well, it comes working in Hardy, and very well.

---

### Post by freebeer on 2008-02-17
Yeah.. that might explain it. ;)

I thought 7.10 could automatically read/write NTFS files out of the box. *shrug*

---

### Post by tvdxer on 2008-02-17
> **freebeer said:**
> Yeah.. that might explain it. ;)

I thought 7.10 could automatically read/write NTFS files out of the box. *shrug*

Maybe it does.

Actually, I have a copy of gOS 2.0 beta on this system, which is based on 7.10.  I think it does read my NTFS C:/ drive.  Unfortuantely, I can't get the thing to fill out my monitor.

---

### Post by wolfen69 on 2008-02-17
> **freebeer said:**
> Yeah.. that might explain it. ;)

I thought 7.10 could automatically read/write NTFS files out of the box. *shrug*

it does.

---

### Post by freebeer on 2008-02-18
That's what I thought but I wasn't sure as I tend to not let my Ubuntu boxes fraternize with the Not Too Friendly System.  [IMG]http://www.freebeer.is-a-geek.org/graphics/lmao2.gif[/IMG]

---

### Post by philfromns on 2008-03-07
Here's my experience. I have an Acer Aspire 3680 with broadcom wireless 802.11. and a gig of memory. First let me say that I love Ubuntu. I was running Gutsy with no problems. Took me a while to get it all configured, but once I did it ran great. So then I saw that the Hardy upgrade was available so I took the upgrade. Then things started going south. I had lots of broken packages so I went into terminal to fix that problem. Once it got that problem fixed I lost the Wifi and had to reinstall that. Then I started getting crashes and a window opening up to report the crashes. Once in while the screen would freeze or lines going across it. Overall the system was very sluggish even after I shut down Compiz. After a while the laptop would just shut down while I was surfing the net for no reason. I checked my power settings but they were normal. I thought it was the laptop itself. So after the last crash I thought I'll try Mandriva which I've always wanted to try. As with Ubuntu it took time to configure but so far I haven't had any problems with crashes or shutdowns. Hopefully I will get back to Ubuntu but for now I'll wait until the bugs get worked out of the new distro or maybe I'll go back to good old gutsy.

---

### Post by Antman on 2008-03-07
I've been running the Hardy daily snapshots and it is pretty darn good so far. The only issues I have have are with firefox3 and the way it displays some websites. Other than that, I think they have a winner.

---

### Post by Feivel on 2008-03-08
> **tvdxer said:**
> Hmmm, maybe that's why (when I was using GNOME) I got those messages asking me if I wanted to send a report to the developer, and showing a "complete report" as being some insane size, like 5 MiB?  

Most of the apps, however, don't seem very slow.

Something I forgot to mention: From what I hear, the current standard release of Ubuntu does not have NTFS support enabled by default.  Well, it comes working in Hardy, and very well.
Not unless you install the NTFS Configuration Tool...

---

