---
title: "Is Raid 5 recovery possible?"
date: 2010-04-20
forum: Server Platforms
---

### Post by siDDis on 2010-04-20
I have 10 disks in raid 5, yesterday two of them failed(most likey one since theyre both using the same IDE channel with master/slave setup).

One of these disk shows now up as a spare, the other one as a faulty spare. I've tried several alternatives to add the spare back to the array(re created the array, zero-superblock) but it still says spare.

So now I have 8 active disks left, and I cant figure out to start the degradedarray. Most of the data doesnt matter, but there are some pictures which I really want back. Is this possible? If so, how?

Yeah I know, lessons learned, always have real backup :-(

---

### Post by BobVila on 2010-04-20
> **siDDis said:**
> I have 10 disks in raid 5, yesterday two of them failed(most likey one since theyre both using the same IDE channel with master/slave setup).

One of these disk shows now up as a spare, the other one as a faulty spare. I've tried several alternatives to add the spare back to the array(re created the array, zero-superblock) but it still says spare.

So now I have 8 active disks left, and I cant figure out to start the degradedarray. Most of the data doesnt matter, but there are some pictures which I really want back. Is this possible? If so, how?

Yeah I know, lessons learned, always have real backup :-(

Is the IDE controller bad? If so, I'd connect the drive showing up as "spare" to a known working IDE controller and see if you can reassemble the array with mdadm. Attempting to recreate the array may have been a mistake, but I'll leave that issue to minds more deeply versed in software raid to answer that question.

---

