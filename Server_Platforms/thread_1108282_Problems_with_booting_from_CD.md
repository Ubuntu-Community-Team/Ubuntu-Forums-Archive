---
title: "Problems with booting from CD"
date: 2009-03-27
forum: Server Platforms
---

### Post by Vinni3 on 2009-03-27
I've got my server up and running, but when I tried to boot into a GParted live CD, it boots to the hard disk. I've tried forcing it to boot to CD and changing the boot priorities but this didn't work either. Has anyone else encountered this problem or is it just me.

---

### Post by IsmailBhai on 2009-03-27
while booting, press f12 and see if a CD option is listed.  if its not detecting the CD, eject the CD and let it cool down or burn it again

---

### Post by Therion on 2009-03-27
And you're sure the CD was burned as a bootable .iso image file, not a data CD?

---

### Post by sabith on 2009-03-27
Try restarting push f2 and change the order of the boot process 
by pushing f5 f6 or whatever and make sure that cd dvd rom drives boot first
and that hard drive and stuff boots last

---

### Post by Vinni3 on 2009-03-28
I've tried everything you guys suggested. Is there a way to remove the boot loader (I want to reofrmat the HDD) so that it doesn't boot to the HDD?

---

### Post by hyper_ch on 2009-03-28
did you also set in the bios to use the cd as first boot device?

---

