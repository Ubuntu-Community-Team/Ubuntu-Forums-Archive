---
title: "HELP! with dmsetup!"
date: 2008-10-11
forum: Server Platforms
---

### Post by rkleemann on 2008-10-11
I'm fighting a losing battle with dmsetup... ;-)

I have this nasty problem where dmsetup automatically picks up a partition that I've set aside for creating swap. No matter what I do, even if I remove it from dmsetup and dmsetup no longer lists it, the kernel claims the device is busy.

In this case, I have 4 disks and all of them had a logical partition 5 (sd[abcd]5) created for swap. So when I booted, the server has no swap, and I could do nothing with /dev/sd[abcd]5 because the kernel claimed those devices were busy, and dmsetup always showed them as taken up, active, but not open (since they're really not part of any group). I would try to "free up" the partitions by using 'dmsetup remove' and even though dmsetup showed to no longer have them, I still could do no operation on them because the kernel reported them as busy.

So I went as far as deleting /dev/sd[abcd]5 via fdisk, and rebooted. Of course, now a 'dmsetup ls' no longer shows the devices as taken.

So then I go into fdisk again to create the partitions, and to my surprise, AS SOON AS THEY'RE CREATED, dmsetup claims them again, automatically! This is nuts... :-(  I wanted to create a raid0 array of the 4 partitions, so I created them as type fd but as soon as they're created, suddenly they're taken by dmsetup and the kernel prevents them from being used, formatted, mounted, or anything!

Man this is so furstrating.

---

