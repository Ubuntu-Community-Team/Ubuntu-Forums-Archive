---
title: "A Question About RAID5 Recovery"
date: 2007-07-02
forum: Server Platforms
---

### Post by tkambler on 2007-07-02
I am pretty new to the whole RAID thing... This is probably a pretty basic question, but one that I need to ask.

I have a server with a hardware RAID5 array that consists of three 170GB drives. I think I have everything setup as it should be... I am able to power down, pull out a random drive, and get back on-line without the missing drive without a problem.

My question is this... How do I go about getting the removed drive back on-line? I've tried placing it back in the bay and getting into my BIOS RAID config utility... It tells me that the RAID is degraded. I thought it would see that I've placed the drive back and re-build the array automatically, but it looks like it doesn't even see that I've placed the drive back.

Any thoughts?

---

### Post by Maxtorm on 2007-07-03
It depends on the RAID BIOS, but my first suspicion is that it shows as degraded while it is rebuilding the array.  Is that a possibility?  If you leave it in there overnight, has the status changed in the morning?

---

