---
title: "Dell Ubuntu Moblin Remix Jaunty Now Available!"
date: 2009-09-24
forum: Ubuntu Moblin Remix
---

### Post by NormanFLinux on 2009-09-24
Dell is releasing on Sept. 24 - that's tomorrow folks  - a version of the Dell Mini 10V with Ubuntu Moblin Remix installed.

For those who would like to try it out on their systems, grab the UMR IMG file here:

[http://linux.dell.com/wiki/index.php/Moblin]("http://linux.dell.com/wiki/index.php/Moblin")


Be warned - the install will erase all data on your hard drive. Have fun playing with Moblin on Ubuntu! :):popcorn:

---

### Post by NormanFLinux on 2009-09-24
Installed it to my Dell Mini 10. Its ready... and wireless setup works! :)

---

### Post by PRC09 on 2009-09-24
just installed on Acer Aspire 1 D250 and everything works......altho during install the installer stated no networking hardware could be found but i installed anyway and it picked up my wireless and etho...looks pretty good.

---

### Post by NormanFLinux on 2009-09-24
Cool. Did you figure out how to change the forest default background? No luck for me so far.

---

### Post by MasterNetra on 2009-09-24
Could this run on a Dell Latitude D530 and such or is it strictly designed for mini? And is it equipped with a liveCD function?

---

### Post by NormanFLinux on 2009-09-24
The Ubuntu Moblin Remix is designed for netbooks but I imagine it could run on any Dell laptop. It does support the Broadcom wireless card in the Mini OOTB.

Its not a LiveCD. You can only do an automatic install which will wipe off your current OS from your HD. Be warned.

---

### Post by Michael.Godawski on 2009-09-24
Moved to UMR. ;)

---

### Post by NormanFLinux on 2009-09-24
Ok. I posted it in Community Cafe because it was non-tech subject - breaking news. If I have diverted the discussion, my apologies.

---

### Post by Michael.Godawski on 2009-09-25
No problem.
We like to move threads. ;)

---

### Post by brioskj on 2009-09-26
I agree with [NormanFLinux]("http://ubuntuforums.org/member.php?u=784660")...how  to change the forest default background???
I'd have a whole lot of pics to use in place of that.

---

### Post by the8thstar on 2009-09-26
Can you guys post some pics for us? I'd like to know if the GUI is specific and good looking enough to try and install it on my HP laptop.

---

### Post by michael37 on 2009-09-27
> **MasterNetra said:**
> Could this run on a Dell Latitude D530 and such or is it strictly designed for mini? And is it equipped with a liveCD function?

It may run, but I certainly don't recommend it.  Moblin and other netbook stuff runs best on [Intel Atom architecture]("http://en.wikipedia.org/wiki/Intel_Atom").

---

### Post by archiesteel on 2009-09-27
> **brioskj said:**
> I agree with [NormanFLinux]("http://ubuntuforums.org/member.php?u=784660")...how  to change the forest default background???
I'd have a whole lot of pics to use in place of that.

I couldn't find how to do it...ended up renaming the actual file (which is found in /usr/share/mutter-moblin/theme/panel/background-tile.png) then starting up a Nautilus-managed desktop by adding he following line to /etc/xdg/moblin/xinitrc :

ionice -n7 nautilus -n &

That way too convoluted for my taste...the devs need to fix this eventually

---

