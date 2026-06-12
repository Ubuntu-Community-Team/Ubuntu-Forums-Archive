---
title: "software raid rebuild problem"
date: 2008-11-13
forum: Server Platforms
---

### Post by 241comp on 2008-11-13
I have 5 drives in software raid 5.  The array failed and I was able to reassemble by forcing it.  It reassembles and sdb, sdc, sdd and sde are OK.  sdf registers as a spare and is rebuilt.  As soon as the rebuild reaches 100%, sdb (which I believe may be the "bad" drive) drops out and sdf gets registered as a spare again even though it just completed a rebuild and should be OK.  So the raid array fails again.  And I start the process over again.  

I managed to backup most of my important files (~1TB) during the rebuild process but I have a lot of unimportant files (~1.25TB) that I would rather not lose if I don't have to and I don't have the space to back them up.  So, I believe if I could get sdf to register as OK once the rebuild is complete, I could remove sdb and replace it with a good drive and it would be rebuilt.  But because sdf gets registered as a spare drive at the end of the rebuild rather than clean, I never get the chance to do that - because I only have 3 clean drives and I need 4.  Is there a way to force sdf to be seen as clean?  Is there another process I should be following?

---

### Post by 241comp on 2008-11-14
Based on some recovery advice I received, I was able to re-create the array with the assume-clean option and mount the filesystem.  Unfortunately, the filesystems was corrupted enough that only about 5% of my files were recoverable so I was forced to restore from backups.

So, now I'm wondering if software raid is useful at all.  I had 1 bad hard drive in a raid 5 array and the array failed...  that definitely shouldn't happen.

---

