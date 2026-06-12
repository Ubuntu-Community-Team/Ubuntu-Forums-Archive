---
title: "win xp installation aborts through virtualbox"
date: 2008-05-11
forum: Virtualisation
---

### Post by savethewabbit on 2008-05-11
i'm trying to install windows xp (from a cd) through virtualbox - i created the hard drive and everything, the cd boots and the installation starts. 
at some point, while i'm formatting the partition, though, it aborts automatically. i tried the quick format and the normal one: with the quick one it gets to 20%, with the other one it stays at 0% for a few minutes till it closes.

could it be a configuration problem or there's something wrong with the virtual hard drive? i'm sure the cd is fine because it never gave me any error and i've used it till a few weeks ago.

thanks!

---

### Post by Promaster91 on 2008-05-11
Try using this.
```

sudo virtualbox

```

I had problems with virtualbox too and that fixed it.

---

### Post by savethewabbit on 2008-05-11
thanks for the tip, although it didn't help much... it didn't abort, but still it got stuck at 20% of formatting. i let it run for about half an hour, and since it didn't move of an inch, i had to manually reboot (the mouse was too slow, it took about 2 minutes to show one single movement.  :\

---

### Post by jacek123 on 2008-11-29
i'll try to save you some time... try lowering the RAM on the vbox to about 1 gigabyte...
took me a whole day to figure it out, maybe it works for you too

---

### Post by bodhi.zazen on 2008-11-29
Windows sometimes has problems with dynamic sized hard drives, make it fixed size.

If that fails, boot the machine with a Linux iso and format the hardrive as a single FAT partition, then try installing windows.

---

### Post by darkcard on 2008-12-04
You need to lower the RAM and maybe video memory being used in your box.

---

