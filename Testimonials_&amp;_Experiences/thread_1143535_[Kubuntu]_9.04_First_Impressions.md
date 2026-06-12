---
title: "[Kubuntu] 9.04 First Impressions"
date: 2009-04-30
forum: Testimonials &amp; Experiences
---

### Post by tvdxer on 2009-04-30
I have been using Linux, on and off, since 1998 with Red Hat Linux 5.1.  That was back in the days of [ftp://sunsite.unc.edu](ftp://sunsite.unc.edu) , of FVWM and Afterstep (GNOME and KDE had just came out), and when installing a program you downloaded off your dial-up connection meant negotiating RPM hell and trying to get all the RPMs with dependencies.  It has been very interesting over the years to see the ways in which Linux has changed, as well as the way it has very much stayed the same - for better or worse.  

Winter / Spring 2008, I was using Ubuntu 8.04a, on which I installed KDE and its associated apps.  I switched back to booting the Windows XP partition of my computer for some reason I could not remember.  

So fast forward about a year and the Windows XP side of my computer becomes infected with some nasty malware that causes my search results (both in Firefox and IE, though I never use the latter) to be re-directed to stupid ad sites.  Rather than spend my time in a boring way trying to delete the malware, I instead decided to revert to Linux.  

Let me note that my system is rather old: it consists of a 2.0 GHz Pentium 4 Processor, 512 MB RAM, 80 and 60 GB hard drives, and a dying ATI Radeon 7500 64 MB graphics card (I just purchased a 256 MB FireGL card to replace it before I build a new system).  I very rarely have any trouble with hardware detection - for the most part, everything works right out of the box just as it does in XP, without having to install any drivers.  My LAN card, my CD drives, USB, etc. - the only thing that does NOT work is the digital section of an ancient ATSC TV tuner (the first model made, actually), which I plan on replacing soon with the Linux-friendly pcHDTV anyway.

First I installed Xubuntu 8 - which I didn't care for.  It wasn't especially fast - particularly with its Flash implementation - and worst of all, it had GNOME applications.  Let me say it once and for all: I can't stand GNOME's design philosophy.  In my mind, it's awful.  Take out as many options as possible to make sure the newbies don't get confused. My annoyance reached its maximum when I chose to burn a PCLinuxOS ISO and found I could not change the burn speed!  I prefer KDE any day to GNOME.

PCLinuxOS was great with a few annoyances.  For one thing, it came with a crippled version of OpenOffice.org - and I think it was 2.4, not 3.0!  I replaced it promptly with the 3.1 RC, which ran great.  The original theme was ugly, but that was fixed.  What I couldn't fix was the fact that the repository tended to contain outdated programs.  

Good and neutral observations:

1. Firefox is much, much faster than in PCLinuxOS, or most other Linux distributions I've tried.  Switching between tabs and scrolling is comparable in speed to Windows XP, or faster.  This advantage disappears when desktop effects are enabled

2. The Ubuntu repos are great as always, with around 30,000 packages available - in other words, virtually anything you need.  I saw a chart somewhere comparing available packages, and indeed Ubuntu was the winner; PCLOS, on the other hand, has a limiting 9,000 packages, some not especially new.

3. Kubuntu fonts look great, especially after the MS Core Fonts package is installed - they're about the right size, anti-aliasing is very good, you can enable subpixel rendering (for some reason that option is blocked out in PCLinuxOS's implementation of KDE).  Maybe this is a slight exaggeration, but with some patent exceptions (e.g. the Amarok 2 song title / artist display), font rendering seems almost at parity with Win XP...and IMO, Win XP's font rendering is basically perfect.

4. Ubuntu and Xubuntu try to scare you out of downloading "restricted" codecs with a dialog box when you try to play an MP3 or AVI; I'm not sure if this is a bad thing or not.  In Kubuntu it's completely different: soon after you install it the Update Manager ASKS you if you want to download them - with no legal notices.

5. The little desktop widgets are very cool; Twitter integration is excellent with KDE Twitter, 

6. Lyrics and Wikipedia integration in Amarok actually work, and it's pretty awesome to be streaming some station (that includes artist / song data in its stream) and be able to just click on the icon when you want to know the lyrics.

7. GIMP does not come installed with Kubuntu, oddly enough; however, after downloading it and associated packages from the repo, I was surprised to see more options than the PCLOS version - or probably any version I've seen before.  Granted, the packages that provided the additional functionality might be available for other distros as well.

8. Even with desktop effects enabled, I was able to open Neverball in a non-full screen sized window.  With Compiz + PCLOS, I had to always open it full-sized.

The bad things about Kubuntu:

1. Switching between windows,  as well as resizing them, is very slow, as is desktop switching - much slower than in PCLinuxOS.  Windows within applications (e.g. the GIMP Color Curves dialog) also take a long time to pop up.

2. Desktop effects (with Kwin) in Kubuntu seem much jerkier and resource-computing than in PCLinuxOS (with Compiz).  Even with my 2002-model 64M video card effects were very smooth in PCLOS / KDE 3.5; the desktop cube and expo actually made switching between virtual desktops more seamless, and it also looked really good.  Many of the same effects are available in Kubuntu with kwin, but with reduced performance.  

3. Applications take a very long time to load, even for Linux.  oowriter took 18s with Amarok and FF running, oocalc took 12s, even Konsole takes about 3s.  Also, performance of certain applications (GIMP) seems VERY subpar - at least in comparison with PCLinuxOS.

4. With 2.0, Amarok is doing a great job, especially in terms of lyrics and Wikipedia integration that actually WORKS, but Shoutcast integration remains buggy (though less buggy)

5. kdenlive is still VERY buggy (sigint'ing when you try to play back a  transition).  Video playback is even worse in it, with "jerky" audio.  

6. Dolphin is slower than Konqueror and less capable.  This is more of a KDE problem than an Ubuntu problem.

7. I'm not sure if this is just me or not, but audio in Linux (with my SB Live Value card) takes on a "tinnier" sound - not a distorted sound, just one that puts less emphasis on bass and more on treble.  I was able to partly remedy this in PCLOS by turning bass up and 

8. There were some weird X problems upon install, but I was able to remedy them by enabling XAA acceleration in my xorg.conf file.  

What's strange about Kubuntu is that some things are MUCH faster and smoother (i.e. Firefox), while others are obnoxiously slow (window switching, OO.o loading, etc.).  

Kubuntu 9.04 has the potential to be a great distribution, and its applications brilliant applications, but there are simply too many things holding it back at this point.  This seems to be a common thread throughout the history of desktop Linux - so much functionality quashed by a few bugs.  Take kdenlive, for example: it has an attractive interface, it's very capable in terms of file formats, there are a lot of effects and transitions available, etc.  If it didn't crash constantly, it would be a GREAT and very usable program.  But alas it does.  Maybe there's a fix, who knows.

Pity that the Ubuntu project does not focus its efforts on KDE and instead offer GNOME lovers a "Gubuntu" distribution.  If that were the case I think Kubuntu 9.04 might be getting some of the same praise that Ubuntu 9.04 gets.

Right now I'm downloading the OpenSUSE 11.2 preview (with KDE 4)...I'll report on that next.

---

### Post by zoniq on 2009-05-01
> **tvdxer said:**
> The bad things about Kubuntu:

1. Switching between windows,  as well as resizing them, is very slow, as is desktop switching - much slower than in PCLinuxOS.  Windows within applications (e.g. the GIMP Color Curves dialog) also take a long time to pop up.


I've been using KDE 4.2 in Kubuntu 8.10 already by adding
```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu
```
to the sources.list
It worked really good and fast, but yesterday I upgraded to 9.04 and it is super slow. It takes about half a second to switch between windows and sometimes even to open a dialog.

Any idea what they changed or activated?

---

### Post by SuperSonic4 on 2009-05-01
Have you tried the KDE version of Mandriva (which pclos is based on)? It makes kubuntu look decrepid

---

