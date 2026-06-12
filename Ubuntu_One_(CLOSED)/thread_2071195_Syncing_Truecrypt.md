---
title: "Syncing Truecrypt"
date: 2012-10-14
forum: Ubuntu One (CLOSED)
---

### Post by PartitionTable on 2012-10-14
Hey guys,

Is it possible to have a Truecrypt container that resides inside the Ubuntu One directory?

When I mount and make changes to the container, adding and deleting files and whatnot, will they try and sync while the container is mounted, or will it only sync *after* I dismount the container?

Cheers,
P.

---

### Post by grashdur on 2012-10-30
I'd like to know more about this too. Certainly, you'd want to make sure that you've set Truecrypt to modify the time/date stamp of the volume--which is not the default setting. I personally had plenty of trouble with this in the past, so what I've been doing is leaving my TC volumes in a non-synchronized folder, and just copying them into my normal folder from time to time. Though I only remember to do so about once a week.

---

### Post by cryptotheslow on 2012-11-13
Yes it works just fine.

I keep a couple of TC container files in a directory that is then added to Ubuntu One to keep in sync.

I have TC set with the default "Preserve modification timestamp of file containers" option set on - so that date never changes.

If I mount a container and don't make any changes to the contents - Ubuntu One does nothing.

If I mount a container and do make changes to the contents, when the container is finally  dismounted in TC, Ubuntu One immediately uploads the changed container file.

I'm not sure how Ubuntu One does it, but it is clearly not working by using the Modified or Accessed dates. Maybe it keeps a hash signature of each of the synced files??

However it works, it keeps my containers in sync between 3 machines. (Although I would not suggest ever mounting the same container on more than one machine at a time - I suspect that would cause version conflicts in U1).

*edit to add:*
OK looking at the U1 logs in ~/.cache/ubuntuone/log/syncdaemon.log it is clear that U1 traps the file close event when the TC container file is closed. It then generates a hash value for the file and compares it to the one stored on U1. If the hashes are now different it uploads the file (and presumably the new hash) and also updates something called the "current generation" which is an integer it seems to increment by 1 -- I presume that is synonymous with a version number.

---

### Post by grashdur on 2012-11-22
Excellent. That really does work. Thanks, Crypto!

---

### Post by jdevora on 2013-01-10
> **cryptotheslow said:**
> Yes it works just fine.


If I mount a container and do make changes to the contents, when the container is finally  dismounted in TC, Ubuntu One immediately uploads the changed container file.


Hi,  Does Ubuntu ONE upload the WHOLE container or only the changed parts (like drop Box)? 

Cheers
 JD

---

