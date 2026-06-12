---
title: "[SOLVED] Windows will not acess the Internet."
date: 2008-05-22
forum: Windows
---

### Post by phread59 on 2008-05-22
Due to a horrendous error with Grub I ended up with no working OS in my machine.  I reinstalled Ubuntu on a Sata drive and reinstalled XP 64 on an old 80 gig IDE drive.  I called in and had XP reinitialized.  I have a working XP system but it will not log into the net.

I am connecting through the ethernet port on the MB.  Ubuntu is happy, logs on just fine.  XP is just throwing a fit.  I went in to connections and made sure it can see the ethernet connection.  It just will not connect up.  I am 100% sure there is a setting off somewhere, I just cannot seem to find it.  Any suggestions on where to look?  If all else fails I'll call my ISP and see if they can figure it out.

Mark Shuman

---

### Post by LaRoza on 2008-05-22
> **phread59 said:**
> 
I am connecting through the ethernet port on the MB.  Ubuntu is happy, logs on just fine.  XP is just throwing a fit.  I went in to connections and made sure it can see the ethernet connection.  It just will not connect up.  I am 100% sure there is a setting off somewhere, I just cannot seem to find it.  Any suggestions on where to look?  If all else fails I'll call my ISP and see if they can figure it out.


Windows XP may not have the ethernet drivers (that sounds really weird to most Linux users, but it is entirely possible and rather common)

You can download and install them with Ubuntu.

---

### Post by hellion0 on 2008-05-23
I'll second LaRoza's thoughts. I've had instances in the past where an ethernet card/port was unrecognized by a clean Windows install, so it's definitely a possibility.

---

### Post by ugm6hr on 2008-05-23
> **LaRoza said:**
> Windows XP may not have the ethernet drivers (that sounds really weird to most Linux users, but it is entirely possible and rather common)

You can download and install them with Ubuntu.

Did you get a Driver CD with the motherboard?  That might have the drivers.

Also - XP64 is rather poorly supported with drivers - so it feasible that the drivers don't actually exist (although I would be surprised if this applied to ethernet chipsets).

---

### Post by Tomatz on 2008-05-23
If the Ethernet connection is showing in network connections then the drivers must be installed.

Open *control panel, system, device manager* 

Find out what Ethernet card you have

Then go to the manufacturers site and download the latest drivers

Install them (obviously)



Hope that helps ;)

---

### Post by phread59 on 2008-05-23
OK guys that makes 100% sense.  I do have a disc for the motherboard with the drivers on it.  I am sure that is the issue.  Tomorrow I will hook up the drive and boot to Windows and rerun the board's disc.  That should do it.  I originally had Windows in and running before and I ran the set up disc.  So it just makes perfect sense.  Thanks for jogging my memory.

Mark Shuman

---

### Post by phread59 on 2008-05-23
Actually all of my hardware is totally supported by Windows 64.  Believe it or not I have had no issues either with software or hardware.  XP 64 had been solid for me.  Exceeded my expectations (for Windows that is).  Linux has surpassed even that.  And by a very large margin.  It is just nice to have that other totally separate and different operating system to fall back on.  I needed it after a horrid update from 7.10 to 8.04.  I like where I am now so I'll just let it go as is untill the next LTS version.

Mark Shuman

PS:  I loaded the drivers from my MB's disc and I got it working.  Redoing Windows for hours made me realize how much I hate Windows.  But it is fixed and back into a dual boot, life is good.

---

