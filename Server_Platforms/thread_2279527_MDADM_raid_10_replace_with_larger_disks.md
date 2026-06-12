---
title: "MDADM raid 10 replace with larger disks"
date: 2015-05-24
forum: Server Platforms
---

### Post by Jaman42 on 2015-05-24
Hi!
Is it possible to replace a disk in a raid 10 array with a larger one, let it rebuild and do the same for the rest. When all are replaced can you then grow the array?

Thanks for reading!

---

### Post by tgalati4 on 2015-05-24
The correct way to do it is to create a new RAID10 pool with new disks and then transfer your data from the old RAID10 pool to the new pool.  If anything goes wrong, presumably you still have the existing pool.

But, what you describe should work.  However, unlike Wikipedia, is sounds better in theory than in practice.

Cunningham Effect should kick in 3 .. 2  .. 1 ..

---

### Post by darkod on 2015-05-25
Yes, you can replace disks with bigger ones one by one.
As mentioned it is a better option if you can install all new disks without removing the old ones, build the new array and then copy the data.
But if you do not have an option to do that, you can replace disks one by one.

---

### Post by Jaman42 on 2015-05-25
Thanks for the answers guys, really informative. So to sum it up it would be possible but it wouldn't be the best way of doing it. However if the drives are healthy they shouldn't mind the rebuild should they?

Atm I have 4 2TB drives in raid 5, I really don't like the thought of trying to rebuild the array if one drive crashes so I was planning on building a raid 10 array instead, would have a much higher chance to rebuild putting much less stress on the disks while doing so. But then I ended up a bit short on storage room, I was trying to avoid buying larger disks, if not I would definitely go with a raid 10 setup.

So I decided to take a bit more unconventional route perhaps. I am going to build a raid 0 array with my 4 x 2TB disks

Raid 0 array you said, are you mad?

Reasons why I am doing this:
[LIST]
[*]The need for speed (not really, but it's fun)
[*]Get the most storage space possible with my current disks
[*]My OS is on a separate disk so it wouldn't be much work rebuilding it when it fails
[*]I already got a backup routine I trust
[*]I have no need for constant up time, if it's down a day or two that's fine, everything I currently work on is being live synced to 4 different units in two different geographical locations.
[/LIST]

I'm doing daily backups of the whole array to a internal drive for quick and easy access in case of a disk failure. I am also doing daily backups to a external drive that is being swapped out now and then, the 2nd external drive is always kept off site. The most important files are on top of this constantly being synced between three other units as well which leaves me with enough protection to feel comfortable.

I plan on learning more about backups, how to make sure they are kept up to date and in good condition so I could restore if I need to. I figured that if I don't feel comfortable running my disks in raid 0 I wasn't having a good enough backup routine.

---

### Post by tgalati4 on 2015-05-25
The most important thing is that you have several backups and you feel comfortable with your plan.  I would attempt your original RAID10 plan, take good notes and post your experiences in this thread as to what works and what doesn't.  RAID5 is a risky setup with large disks, something that RAID6 and RAID10 address.  But, yes, you do lose storage space, so drive count goes up to maintain the same size pool.

---

