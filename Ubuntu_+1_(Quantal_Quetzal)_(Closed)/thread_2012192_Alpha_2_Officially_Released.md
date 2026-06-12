---
title: "Alpha 2 Officially Released"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-06-28
From Kate Stewart

> Welcome to the Quantal Quetzal Alpha 2 image set, which will in time
become the 12.10 release. 

Pre-releases of Quantal Quetzal are *not* encouraged for anyone 
needing a stable system or anyone who is not comfortable running 
into occasional, even frequent breakage.  They are, however, 
recommended for Ubuntu developers and those who want to help in 
testing, reporting, and fixing bugs as we work towards getting 
this release ready.    

Alpha 2 is the second in a series of milestone images that will be
released throughout the Quantal development cycle, in addition to
our daily development images.  The Alpha images are known to be 
reasonably free of showstopper CD build or installer bugs, while 
representing a very recent snapshot of Quantal.  You can download 
them here:

   [http://cdimage.ubuntu.com/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/releases/quantal/alpha-2/) 
   (Ubuntu Desktop, Server)

Additional images are also available at:

   [http://cloud-images.ubuntu.com/releases/quantal/alpha-2/](http://cloud-images.ubuntu.com/releases/quantal/alpha-2/) 
   (Ubuntu Server Cloud)
   [http://cdimage.ubuntu.com/kubuntu/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/kubuntu/releases/quantal/alpha-2/)
   (Kubuntu)
   [http://cdimage.ubuntu.com/edubuntu/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/edubuntu/releases/quantal/alpha-2/)
   (Edubuntu)
   [http://cdimage.ubuntu.com/lubuntu/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/lubuntu/releases/quantal/alpha-2/)
   (Lubuntu)
   [http://cdimage.ubuntu.com/xubuntu/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/xubuntu/releases/quantal/alpha-2/)
   (Xubuntu)
   [http://cdimage.ubuntu.com/ubuntustudio/releases/quantal/alpha-2/](http://cdimage.ubuntu.com/ubuntustudio/releases/quantal/alpha-2/)
   (Ubuntu Studio)

Alpha 2 includes a number of software updates that are ready for wider
testing.  This is an early set of images, so you should expect
some bugs.  For a more detailed description of the changes in the Alpha
2 release and the known bugs (which can save you the effort of reporting
a duplicate bug, or help you find proven workarounds), please see:

  [http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

If you're interested in following the changes as we further develop
Quantal, we suggest that you subscribe initially to the
ubuntu-devel-announce list. This is a low-traffic list (a few posts a
week) carrying announcements of approved specifications, policy changes,
alpha releases, and other interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)


Kate Stewart, on behalf of the Ubuntu release team

---

### Post by ventrical on 2012-06-28
@cariboo907

If we use zsync on earlier alpha 1s  does that suffice for alpha 2 or do we actually have to download the alpha 2 iso?

---

### Post by cariboo on 2012-06-28
The alphas are just a snapshot of the daily iso. If anything the dailies are alpha+updates after the image is frozen and called alpha X.

---

### Post by philinux on 2012-06-28
> **ventrical said:**
> @cariboo907

If we use zsync on earlier alpha 1s  does that suffice for alpha 2 or do we actually have to download the alpha 2 iso?

Only to test the ISO as a live cd usb etc. You know test ubiquity out.

---

### Post by kevpan815 on 2012-06-28
Cariboo907, I tried doing a zsync of yesterday's i386 daily-live build and it returned a 100% match, 0% change in file, is that correct? TIA.

---

### Post by cariboo on 2012-06-28
The image was frozen on Monday, so that it could be tested before release. If there had been any show stoppers, there would have a new image. From the looks of this report:

[https://wiki.ubuntu.com/QATeam/ReleaseReports/QuantalAlpha2TestReport](https://wiki.ubuntu.com/QATeam/ReleaseReports/QuantalAlpha2TestReport)

There weren't any huge problems with the Ubuntu iso.

---

### Post by ventrical on 2012-06-28
> **cariboo907 said:**
> The alphas are just a snapshot of the daily iso. If anything the dailies are alpha+updates after the image is frozen and called alpha X.


Yes.. thank you for the reminder. It was the same routine with Precise alpha series.

---

### Post by QIII on 2012-06-28
Man am I behind the power curve, here.  All I've managed to do is install about every third daily and haven't contributed much because I don't seem to have problems.

Time to brrak something on purpose.

---

### Post by sammiev on 2012-06-28
Installed the new Alpha2. The update failed on updating well creating the USB boot able stick. Then After taking the updates online after installing Alpha2 it booted into a purple screen which was fixed doing a few things with recovery and gnome. The choice selection on install should be an option as I create my own a head of time but let it run it's course which failed to install where any newbie would just use the default. Seen a lot of good stuff but it needs a little work. That's why they call it testing! :)

---

### Post by ventrical on 2012-06-28
> **QIII said:**
> Man am I behind the power curve, here.  All I've managed to do is install about every third daily and haven't contributed much because I don't seem to have problems.

Time to brrak something on purpose.

 I've been working with Kubuntu  a little bit and have been remiss in updating my Ubuntu isos. Otherwise  the dailys have been pretty well impervious to major  showstoppers and work very professionally.  It's a fine job Canonical is doing here. I'm having a riot :)

---

### Post by QIII on 2012-06-28
I just gave up and started using Precise as my daily before Beta even.

---

### Post by jerrylamos on 2012-06-28
A2 installed and running on a Acer Aspire 1 netbook and an Acer Aspire widescreen notebook.  The latter running well for an Alpha with Broadcom wireless WPA.  The netbook with intel centrino wireless N is another matter.  Last week it would hardly connect at all to WPA network, same one the Broadcom is on with no trouble.

A2 I gave up after 12 minutes waiting for the 3.5.0-2 to connect the Centrino, did ubuntu-bug.  When the report was ready used system settings network to get connected, sluggish response to mouse selections, finally connected and submitted bug.

Next A2 install will be this tower.  It had fits installing A1 with the ATI video, now running O.K. on A1 will install A2 shortly.

All three are mutli-boot.  The netbook installed A2 onto USB hard drive.  Both the netbook and the wide screen notebook using external monitor - the latter was a bear earlier in A1 now running O.K.

Full speed ahead....time for more updates soon?

Jerry

---

### Post by ventrical on 2012-06-29
Looks like alpha 2 has the ATI routines all set.(quantal-desktop-i386.iso)
2.8GHz Pentium

Nice work!

---

### Post by Curtis6767 on 2012-06-29
Still waiting to do upgrades. Getting "Partial" error for last 24hrs. Last time it sorted itself out.  I did do a partial on A-1 and that didn't seem to have any negative effects.

---

### Post by jpeddicord on 2012-06-29
Going to take the plunge on Sunday when I get back home from vacation. Excited for the the usual X-and-pretty-much-everything-else-doesn't-work phase. :D

---

### Post by philinux on 2012-06-29
> **jpeddicord said:**
> Going to take the plunge on Sunday when I get back home from vacation. Excited for the the usual X-and-pretty-much-everything-else-doesn't-work phase. :D

You'll be disappointed then it just worky. ;)

---

### Post by philinux on 2012-06-29
> **Curtis6767 said:**
> Still waiting to do upgrades. Getting "Partial" error for last 24hrs. Last time it sorted itself out.  I did do a partial on A-1 and that didn't seem to have any negative effects.

Never do a partial. See the sticky.

---

### Post by ventrical on 2012-06-29
Same opening graphics problems with older Nvidia and some Intel based graphics adapter cards. Fuzzy screen with splashy scratches.

---

### Post by anewguy on 2012-07-01
Hey, I'm new to any of this and just plain not that smart.  Do I just download the ISO and give it a go, then report problems if I have any somewhere else?

---

### Post by bennachie on 2012-07-01
YMMV, but I will often check here first to see if there is a known problem and if there are any workarounds, and file a bug only when it's clear that I've unearthed something new, or I might be able to add worthwhile detail to somebody else's bug report. You won't solve an underlying problem by posting here, but you might well solve your own problem.

---

### Post by philinux on 2012-07-01
> **anewguy said:**
> Hey, I'm new to any of this and just plain not that smart.  Do I just download the ISO and give it a go, then report problems if I have any somewhere else?

Good place to start are the stickies in this forum. Welcome aboard the testing ship. There will be choppy seas ahead. It's not all plain sailing so best to test on a spare machine, partition or usb stick.

---

### Post by VinDSL on 2012-07-01
> **anewguy said:**
> Hey, I'm new to any of this and just plain not that smart.  Do I just download the ISO and give it a go, then report problems if I have any somewhere else?
Yep, that's about the size of it.

There are different ways of reporting bugs.  Some ppl are quite adept at knowing exactly what's needed in Launchpad, but I've found it rather frustrating, because I don't know how to use it to full advantage.  Soooo, many times, my bug reports on Launchpad only amount to a "me too" -- which is also helpful when other testers are trying to confirmation a problem.  Every little bit helps.

Occasionally, I'll discover a real corker, and be the first to report it on Launchpad.  Then, it becomes magically exciting, but for the most part I just report/follow bugs in the +1 forum.  They tend to "swarm" problems here, and that's a lot of fun too.

Anyway, just dive on in.  

After you pick up the lingo (some of it unique to this forum) and figure out who the movers n' shakers are, you'll have a ball reporting bugs and doing workarounds, blah, blah, blah.

---

