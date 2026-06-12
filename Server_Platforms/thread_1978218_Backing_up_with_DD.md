---
title: "Backing up with DD"
date: 2012-05-11
forum: Server Platforms
---

### Post by Jake.Debord on 2012-05-11
I have a server running 8 drives in raid10 with about 800gb of data. I have two spare 2tb drive in there I would like to backup the data to. I will be doing this daily and the two 2tb drives will be on a 1 day rotation. (Backup to one, send it offsite for a day, then bring it back and send the other offsite).

My question is, if I put the drive back in and run DD again will it hurt anything to have the previous backup on there, or should I wipe it before I run DD again?

---

### Post by darkod on 2012-05-11
Doesn't dd copy the empty sectors too? It might not even finish for the whole day. :)

Depending if this is only data or system files too, you might be better off with cp or something like FS Archiver.

As for dd, I am not sure, but since it copies sector by sector, it might actually hurt having the previous data. When the today backup finishes, in continuation there might be files from the previous backup.

---

### Post by Jake.Debord on 2012-05-11
I played around with it yesterday tweaking it until I got a decent transfer rate of about 115mb/s and the whole job finished in under 3 hours. So, For now this seems like it will work well until space becomes a bigger issue.

It is my understanding as well that it copies empty space also so it effectively will make another exact copy. I would just feel much more comfortable if someone could confirm it. I can wipe it before I run DD if I have to but I would rather not do that if I don't have to.

---

### Post by Catalyph on 2012-05-11
Backup using rsync, that way any unchanged data will not get rewritten, and only new data will get backed up to the drive, it would reduce your time to maybe 20 minutes depending on how much data has been changed, also if a drive crashes you life will be difficult with getting the data back using DD

---

### Post by gharris999 on 2012-05-11
> **Jake.Debord said:**
> I played around with it yesterday tweaking it until I got a decent transfer rate of about 115mb/s and the whole job finished in under 3 hours. So, For now this seems like it will work well until space becomes a bigger issue.

It is my understanding as well that it copies empty space also so it effectively will make another exact copy. I would just feel much more comfortable if someone could confirm it. I can wipe it before I run DD if I have to but I would rather not do that if I don't have to.
Yes, dd will make an exact copy, i.e. copy empty space too.  If you're going this route (vs. using rsync,) you might look at gddrescue as an alternative to dd.  My understanding is that it should produce the exact same results as dd (exact copy of a device to another device or to an image file) except that it should be better optimized in terms of block transfer sizes (i.e. should be faster) and with better error handling.

---

### Post by Jake.Debord on 2012-05-11
Okay, thanks for the information guys. I will start off with DD since I feel comfortable with it for now. I'll look at gddrescue and I thought about rsync and that is something I will be for sure doing in the future but I want to do it right and not use it to just move files on same system.

gharris999, do you think i can get faster speeds than 115mb/s with gddrescue? I'm not sure my drive can write much faster than that anyway...

---

