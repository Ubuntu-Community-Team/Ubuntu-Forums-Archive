---
title: "Running an .iso in Wine"
date: 2009-03-29
forum: Wine
---

### Post by noseforsharpies on 2009-03-29
I have a Rosetta Stone collection in DVD, in .iso format. How do I use this in Wine?

---

### Post by DeMus on 2009-03-29
> **noseforsharpies said:**
> I have a Rosetta Stone collection in DVD, in .iso format. How do I use this in Wine?

Use a program like daemontools (google it) and you get a virtual cd rom based on the iso file. Now you can "look" into the iso file as if it was a cd.

---

### Post by hikaricore on 2009-03-29
You don't need tools to do this on Linux you can just mount the ISO.... 

> sudo mount -t iso9660 filename.iso /media/mountlocation -o loop

Where filename.iso is the ISO and /media/mountlocation is the place you want to mount it.

**Be aware that Canonical and the Ubuntu Forums to not advocate piracy... _if these ISOs aren't from your own DVD/CDs you will receive no further assistance._**

Also these Rosetta Stone programs are hit and miss under WINE: [http://appdb.winehq.org/appview.php?appId=1867](http://appdb.winehq.org/appview.php?appId=1867)

---

