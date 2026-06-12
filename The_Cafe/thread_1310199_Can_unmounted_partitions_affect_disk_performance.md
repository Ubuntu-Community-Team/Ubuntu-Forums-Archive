---
title: "Can unmounted partitions affect disk performance?"
date: 2009-11-01
forum: The Cafe
---

### Post by lovinglinux on 2009-11-01
Here is the deal...

My system is running fine. I have a triple boot with two instances of Karmic and one Windows 7. All Linux partitions are ext4. My production OS is one of the Karmics that I have been using since the Beta release. The other Karmic will be used for testing, so I will upgrade to Lucid Lynx soon.  I haven't used the Windows 7 for a long time, until today.

Anyway, today I have decided to re-install the testing partition, using the final release alternate CD, instead of updating it, in preparation for Lucid. I have only formatted the root partition, since I share the /home with my production OS (different user).

I don't remember receiving any updates today, but now some disk tasks are much faster than before. For instance, when I open a text file with 80.000 lines it opens almost immediately, while this was taking about 20-30 seconds lately.

So my question is, could the fact that I have re-installed the other OS, which is in the same drive as the mbr (my production OS is on the secondary drive), influence the other Ubuntu installation? As far as I know, an unmounted partition does not affect the others. Besides it resides on another disk. Anyway, I don't really know why I had such improvement. 

I also have accessed Windows 7 after a long period without touching it. Windows seems to make a lot of noise when accessing the disk. Not "omg it will explode" noise, but is definitely more intense than Ubuntu. Is NTFS more noisy than ext4?

---

### Post by whoop on 2009-11-01
Technically I would say no. Maybe if you resized something some de-fragmentation would occur (on purpose or not), but you said you only formatted. Really strange. Are you sure the document wasn't cached or something?

As for ntfs, maybe it's more noisy because it's more fragmented (altough ntfs is much better than fat(x) it still fragments), or maybe it's more noisy because there are usually more intensive processes running on windows that perform disk I/O's like virus scanners, indexers and the likes.

---

### Post by lovinglinux on 2009-11-01
> **whoop said:**
> Technically I would say no. Maybe if you resized something some de-fragmentation would occur (on purpose or not), but you said you only formatted. Really strange. Are you sure the document wasn't cached or something?

I have cleaned up the cache before testing and the result was the same.

I doubt there was any de-fragmentation involved. Partition sizes are the same. Perhaps could be the fact that the new install also formated swap, but I hardly use swap, since I have enough memory.

> **whoop said:**
> As for ntfs, maybe it's more noisy because it's more fragmented (altough ntfs is much better than fat(x) it still fragments), or maybe it's more noisy because there are usually more intensive processes running on windows that perform disk I/O's like virus scanners, indexers and the likes.

I will disable some Windows services to see if there is any difference.

---

