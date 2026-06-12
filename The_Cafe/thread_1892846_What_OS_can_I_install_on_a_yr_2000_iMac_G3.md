---
title: "What OS can I install on a yr 2000 iMac G3?"
date: 2011-12-08
forum: The Cafe
---

### Post by simpleblue on 2011-12-08
I was just given an old iMac G3 which was made in the year 1999/ 2000. It boots up fine. Accepts my keyboard and even my wireless mouse connection. The only issue is that it's user is passworded so I'd like to know my options of OS's that can be installed or used on a Live CD if possible. Can Linux or BSD be installed?

Here are the stats:

IMAC DV 400MHZ/512K L2 CACHE/64MB SDRAM
10GB HD/DVD/56K MODEM/TANGERINE

Mac OS 9.2 installed

More stats here: [http://support.apple.com/kb/SP121](http://support.apple.com/kb/SP121)

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Indigo_iMac_G3_slot_loading.jpg/614px-Indigo_iMac_G3_slot_loading.jpg[/IMG]

[IMG]http://upload.wikimedia.org/wikipedia/commons/4/44/IMac_G3_Panel.jpg[/IMG]

---

### Post by wolfen69 on 2011-12-08
See if you can bump up the RAM a bit and put Debian PPC on it.

---

### Post by 3Miro on 2011-12-08
You need a distro with PPC version, check with distrowatch. Then you have to worry about the low RAM. Pick something as light as possible.

---

### Post by wolfen69 on 2011-12-08
> **3Miro said:**
> Pick something as light as possible.

That's part of the problem though. Is there anything besides Tiny Core that will run on 64mb? Any computer recycling center has tons of memory, and will sell you sticks for next to nothing. There's no reason in this day and age where someone should HAVE to endure with only 64mb. I just recently *gave* someone a bag of pc133 ram (about 25 sticks) for nothing. 

Heck, for that matter, if you live in the US, I could probably send you a stick of 256 for the cost of an envelope. At least that way you would have something halfway decent.

---

### Post by simpleblue on 2011-12-08
Thank you all for the replies, but there is another problem. I tried booting an openBSD DVD with no luck and now the DVD will not eject. Apparently Apple keyboards have an eject button but I am currently using a Windows keyboard. I cannot log into the OS so I don't have access to the eject function.

So for now I'm stuck. I'll try posting on a mac site and see what they can come up with. I might need to take the computer apart to make it eject. :s

---

### Post by BBQdave on 2011-12-08
> **simpleblue said:**
> Thank you all for the replies, but there is another problem. I tried booting an openBSD DVD with no luck and now the DVD will not eject. Apparently Apple keyboards have an eject button but I am currently using a Windows keyboard. I cannot log into the OS so I don't have access to the eject function.

So for now I'm stuck. I'll try posting on a mac site and see what they can come up with. I might need to take the computer apart to make it eject. :s

There is a tiny hole in the front by the tray.  Use a paper clip (unfolded) end to poke through the hole, and that should manually open the tray :)

---

### Post by simpleblue on 2011-12-09
> **BBQdave said:**
> There is a tiny hole in the front by the tray.  Use a paper clip (unfolded) end to poke through the hole, and that should manually open the tray :)
Are you talking about inside the computer or on the front of it? I don't see any tiny hole.

---

### Post by BBQdave on 2011-12-09
I believe you can upgrade to 1 gig of memory on that G3.  I have an old eMac G4 700MHz (768 Mb of ram) running Tiger (os 10.4).  I use it for file and print serving in my home network.  At this point that is all that I can do with it, because most GNU/Linux distro's stop developing for ppc.  Applications are out of date.  Apple has left the ppc's behind too.  BSD does not have full support for ppc anymore.

So a friendly warning:  my machine is running great, the same as when I first got it.  But the world has left the ppc behind.  Not sure if you want to invest a lot of time and energy into a dead platform.

That said, my eMac is a tank, and is still productive with in my home network (as a file and print server).  But I have not added hardware or peripherals to it in years, it is running on what I had set up when it was still supported.  So my advice, is to weigh out what you put in for what you will get out of that G3 :)

[http://lowendmac.com/](http://lowendmac.com/)

---

### Post by BBQdave on 2011-12-09
> **simpleblue said:**
> Are you talking about inside the computer or on the front of it? I don't see any tiny hole.

Sorry, it should be on the front.  And I am recalling this from an iMac G3 500MHz machine I had.

---

### Post by BBQdave on 2011-12-09
Manually ejected disc from slot loading iMac G3:

[http://support.apple.com/kb/HT3007](http://support.apple.com/kb/HT3007)

---

### Post by wolfen69 on 2011-12-09
On the first imacs, the tiny pinhole was on the right side. (it came in handy)

---

### Post by simpleblue on 2011-12-09
> There is a tiny hole in the front by the tray.  Use a paper clip  (unfolded) end to poke through the hole, and that should manually open  the tray :smile:
Thanks, found it and it works!

> **BBQdave said:**
> I believe you can upgrade to 1 gig of memory on that G3.  I have an old eMac G4 700MHz (768 Mb of ram) running Tiger (os 10.4).  I use it for file and print serving in my home network.  At this point that is all that I can do with it, because most GNU/Linux distro's stop developing for ppc.  Applications are out of date.  Apple has left the ppc's behind too.  BSD does not have full support for ppc anymore.

So a friendly warning:  my machine is running great, the same as when I first got it.  But the world has left the ppc behind.  Not sure if you want to invest a lot of time and energy into a dead platform.

That said, my eMac is a tank, and is still productive with in my home network (as a file and print server).  But I have not added hardware or peripherals to it in years, it is running on what I had set up when it was still supported.  So my advice, is to weigh out what you put in for what you will get out of that G3 :)

[http://lowendmac.com/](http://lowendmac.com/)
This does not sound like good news. :S

I tried putting openBSD macppc 5.1 on it and it didn't even reach the terminal. Just had a graphic disk with a question mark on it. I'd be happy just to run the terminal and a few terminal programs but so far nothing. If anyone has an idea could you please grab me the link to the proper iso file. I'll burn it and if it works I'll take a pic for people to see.

---

### Post by mips on 2011-12-09
You need 64MB of ram to rub OpenBSD, 128MB if using X. NetBSD requires 16MB or 32MB with X.

You will have to google a bit about booting media on that machine, think it has something to do with openfirmware.

You need some more ram in that machine, the more the better.

---

### Post by dpny on 2011-12-09
IIRC, restarting while holding down the mouse button should eject the DVD.

---

### Post by wolfen69 on 2011-12-09
> **dpny said:**
> IIRC, restarting while holding down the mouse button should eject the DVD.

F12 will eject the disc.

---

### Post by BBQdave on 2011-12-09
> **simpleblue said:**
> If anyone has an idea could you please grab me the link to the proper iso file. I'll burn it and if it works I'll take a pic for people to see.

[http://www.freebsd.org/platforms/ppc.html](http://www.freebsd.org/platforms/ppc.html)

This too has me curious for the future of my eMac.  That said, it seems like all other :(nix's, the *devs* are focused on i386 and amd64 platforms, not a lot of focus on ppc's.

---

### Post by simpleblue on 2011-12-09
> **BBQdave said:**
> [http://www.freebsd.org/platforms/ppc.html](http://www.freebsd.org/platforms/ppc.html)

This too has me curious for the future of my eMac.  That said, it seems like all other :(nix's, the *devs* are focused on i386 and amd64 platforms, not a lot of focus on ppc's.
I'm not sure if my disk drive is working correctly. I can rarely get the computer to boot to the disk and when it does the computer just shows a small graphical disk in the middle of the screen with a question mark in it. This tells me very little, but I guess that's how Apple likes it. :(

I'm going to try burning the FreeBSD-8.2-RELEASE-powerpc-disc1.iso image and seeing what happens.

---

### Post by MisterGaribaldi on 2011-12-09
Hold the mouse button down when you power any Mac on. It'll eject whatever disc is in whatever drive you have.

---

### Post by BBQdave on 2011-12-09
> **simpleblue said:**
> I'm not sure if my disk drive is working correctly. I can rarely get the computer to boot to the disk and when it does the computer just shows a small graphical disk in the middle of the screen with a question mark in it. This tells me very little, but I guess that's how Apple likes it. :(

I'm going to try burning the FreeBSD-8.2-RELEASE-powerpc-disc1.iso image and seeing what happens.

That could be hardware issues, it could also be that there is no operating system installed, which would give you the *Question Mark* :(

---

### Post by simpleblue on 2011-12-09
> **BBQdave said:**
> That could be hardware issues, it could also be that there is no operating system installed, which would give you the *Question Mark* :(
I just installed openBSD successfully. At least that's what it said when I got to the end of the install, but when I boot it I get the question mark again. I've been trying to follow the instructions on the link above but gpart keeps telling me there is not space left on the device. Amazingly I was able to ping the net, so once things get working this computer will be able to surf the web. :P

---

### Post by BBQdave on 2011-12-09
> **simpleblue said:**
> I just installed openBSD successfully. At least that's what it said when I got to the end of the install, but when I boot it I get the question mark again. I've been trying to follow the instructions on the link above but gpart keeps telling me there is not space left on the device. Amazingly I was able to ping the net, so once things get working this computer will be able to surf the web. :P

10 GB hard drive should be plenty of space to work with, unless the hard drive has been replaced.  The maximum allowed on that machine is 128 GB IDE drive.  Not sure why you are getting the *not space left *message :confused:

---

