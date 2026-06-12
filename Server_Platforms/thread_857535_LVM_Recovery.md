---
title: "LVM Recovery"
date: 2008-07-12
forum: Server Platforms
---

### Post by spxero on 2008-07-12
Help!

I have an LVM2 setup with three 500GB's, a 300GB, and a 1TB. This morning, the first disk in the set, one of the 500's, died. It was not in a RAID, so I believe that data is just gone forever (some of which I have backups).

My question is: 
Is there a way to remove that drive from the LVM so that the LVM can be mounted?

Thanks,
Steve

---

### Post by koenn on 2008-07-12
this ?
[http://ubuntuforums.org/showthread.php?t=449711](http://ubuntuforums.org/showthread.php?t=449711)

---

### Post by spxero on 2008-07-13
> **koenn said:**
> this ?
[http://ubuntuforums.org/showthread.php?t=449711](http://ubuntuforums.org/showthread.php?t=449711)

This sort of covers what I'm trying to do. But I have errors saying that /dev/satavg/lvol0 (satavg is my vg and lvol0 is my lv) cannot be found. Is there a way to remove the drive when /dev/satavg/lvol0 is not available?

---

### Post by OttifantSir on 2008-07-14
I have only just managed to set up LVM myself, but try these:

[Activate Volume Group(s)]("http://tldp.org/HOWTO/LVM-HOWTO/activatevgs.html")

[Remove Physical Volumes From a Volume Group]("http://tldp.org/HOWTO/LVM-HOWTO/removepvsfromvg.html")

[Remove a Logical Volume]("http://tldp.org/HOWTO/LVM-HOWTO/removelv.html")

This is links to the official LVM HOWTO. You might find the answer to your question there even if these links doesn't do it for you

---

