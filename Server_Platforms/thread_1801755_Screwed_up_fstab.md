---
title: "Screwed up fstab"
date: 2011-07-11
forum: Server Platforms
---

### Post by matthewm27 on 2011-07-11
I think I'm screwed and should probably just re-install Ubuntu -- which is no big deal -- but I figured I'd ask here first.

In attempt to change the options for a partition to accept ACL, I had "asl" stuck in my head (too much IMing?), and decided to put that instead. Now every time I try to boot, it tells me that I have an invalid option and won't mount that partition.

Any suggestions? I've read around, but nothing that I saw worked.

Thanks,
Matt:)

---

### Post by Lars Noodén on 2011-07-11
If you can still mount the partition manually then you can use those settings in fstab.  

As with any other system file it is a really good idea to make a copy before you start editing.  e.g. cp /etc/fstab /etc/fstab.orig

---

### Post by ajgreeny on 2011-07-11
Just boot to a live CD/USB session and edit the fstab back to what it was before.

---

### Post by matthewm27 on 2011-07-11
I can't mount it, that's the problem:/

ajgreeny, I'll try that, thanks.:)

---

