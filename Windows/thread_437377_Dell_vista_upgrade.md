---
title: "Dell vista upgrade?"
date: 2007-05-08
forum: Windows
---

### Post by 67GTA on 2007-05-08
Has anyone used the Dell vista upgrade? I got a free disk with my daughter's Dell and was thinking of using it. I have her dual booting with XP and Edubuntu. Will this thing take over the whole hard drive like the XP recovery disk, or just use the existing XP partition? Will it destroy grub? It will only be for me to play with. Is it worth the trouble?

---

### Post by icechen1 on 2007-05-08
> **67GTA said:**
> Has anyone used the Dell vista upgrade? I got a free disk with my daughter's Dell and was thinking of using it. I have her dual booting with XP and Edubuntu. Will this thing take over the whole hard drive like the XP recovery disk, or just use the existing XP partition? Will it destroy grub? It will only be for me to play with. Is it worth the trouble?

I don't know but i think it will rewrite the MBR (where your grub is installed to) but you can restore by using Super Grub Disk.I don't think it will format your disk(But who knows,it is Microsoft).

---

### Post by goumples on 2007-05-09
I don't know if Vista is more partition friendly, but older versions of MS would ignore any non windows partitions and write to the whole disk.  Windows XP and before wouldn't even see linux partitions unless you manually pointed them too it.. Maybe Vista is different, but knowing Microsoft it will probably write to the whole disk.

---

### Post by LaRoza on 2007-05-10
You might not want Vista at all unless your computer has a dual core processor and at least 1 Gig of RAM.

---

### Post by Tyrax on 2007-05-11
Vista upgrade will rewrite your MBR, but it will not overwrite your linux partition. I have not encountered a version of windows that would take over the whole disk, but then again I didn't start playing with any distros until I already had Windows 2000.

---

