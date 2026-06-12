---
title: "Can't get wine to recognise a ISO file"
date: 2009-03-03
forum: Wine
---

### Post by Deathtothetraitor on 2009-03-03
I mounted the ISO file for Age of Empires in a /media/iso directory and i added that directory to Wine as a drive, but it just won't run it, even if i run it directly from the ISO file, it says "Please insert the correct Age of Empires CD in the CD drive.
Is anyone able to think of any solutions? 

Thanks in advance guys.. And yearh, i'm pretty much a linux newb, so sorry if this is really stupid.

---

### Post by handy on 2009-03-03
Perhaps you are going to have to find & use a noCD patch to get past a built in protection.

Also, you would do better in the Wine sub-forum, so I'll ask the mod's to move your thread.

---

### Post by Ripose on 2009-03-03
You have to extract the contents of the ISO to a directory on your HDD.

Wine doesn't know what an iso is, it looks for exe or msi files.

---

### Post by tyle on 2009-03-03
> **Deathtothetraitor said:**
> I mounted the ISO file for Age of Empires in a /media/iso directory and i added that directory to Wine as a drive, but it just won't run it, even if i run it directly from the ISO file, it says "Please insert the correct Age of Empires CD in the CD drive.
Is anyone able to think of any solutions?

Run winecfg, choose the "drives" tab, and register the mounted directory as a CD drive. That way wine should recognize it as a valid CD. After this you could try running the installation again.

---

