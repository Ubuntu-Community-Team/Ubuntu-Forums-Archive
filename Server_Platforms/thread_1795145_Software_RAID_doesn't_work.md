---
title: "Software RAID doesn't work?"
date: 2011-07-02
forum: Server Platforms
---

### Post by Beatboxx on 2011-07-02
I'm trying to put two identical disks in Raid 1 for a homeserver. I got Ubuntu 11.04 server 32 bits on a USB stick. Installated till partition menu. Now I get the question how I want to partition my disks. I choose manual, and two times entire disk, one for both. It looks like this:

[img]http://i53.tinypic.com/2gtatkm.jpg[/IMG]

(iPhone quality)

I go to configure software Raid, and select Raid 1, 2 active disks, 0 spare disks, and get this:


[img]http://i51.tinypic.com/200pra0.jpg[/IMG]

I can't choose the other 2TB partition. I think I have to configure Raid three times, one for each partition. Not?

I click the missing 2TB partition, and get this:

[img]http://i54.tinypic.com/2evf3hv.jpg[/IMG]

But I think there's no RAID device at all, I see this again when I go to Configure Software Raid, en try to delete a RAID device:


[img]http://i52.tinypic.com/eqw5jo.jpg[/IMG]

How do I get Disk 1 and Disk 2 together in Raid 1??? In this tutorial: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) I get stuck on step 2...

---

### Post by ryanrobinson on 2011-07-02
[http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)

Watch that tutorial. It's for a RAID0 config but it's exactly the same process if you were to create a RAID 1 config.

---

### Post by arrrghhh on 2011-07-02
> **ryanrobinson said:**
> [http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)

Watch that tutorial. It's for a RAID0 config but it's exactly the same process if you were to create a RAID 1 config.

RAID0 is pointless, and dangerous.  Don't use it, there's really no point.

To the OP - perhaps you don't understand RAID?  RAID1 means that you basically get one disk for the price of two.  The point is redundancy, if one of the disks fails, you still have a second disk with the identical data, allowing you to replace the bad disk.

You will lose space with RAID, no matter what.  To get the benefit of redundancy, you will not be able to all the space - hence the phrase redundancy.  That's the tradeoff... Lose some disk space at the sake of security/safety against disk failures.

---

### Post by YesWeCan on 2011-07-02
Looks like /dev/sda2 has an old mdadm superblock on it and this is why the partitioner is not letting you add it to your new RAID.
You should probably delete and recreate the partition.

---

