---
title: "Recommend filesystem - Large disk (&gt;10TB)"
date: 2012-06-07
forum: Server Platforms
---

### Post by curmudge1 on 2012-06-07
Project users are processing a lot of satellite image data, etc.  and they need a large storage space.  We have a 12+TB LUN created on the server hardware raid.  

Can someone recommend which filesystem to use, considering the size and version (12.0.4 LTS server), please?  Thinking about time to create the filesystem, and to fsck if needed.  Also, stability/robustness with this size, under hard usage.  And, minimal systems administrator time to monitor.

What about btrfs vs. ext4?  If this was Solaris 10, I would use ZFS without hesitation.

If it matters, this will run under Vmware Vsphere 5.

Don't get me started about backups, that's a question for another day.  Budget$  for backup device, etc.

Thanks,
Dave

---

### Post by thnewguy on 2012-06-07
Btrfs is still under development and doesn't have any reliable fsck tools yet, so putting your data on Btrfs is basically like playing Russian Roulette with it. (Plus Btrfs is painfully slow.) If the server must be a Linux server then ext4 is really your own option for large amounts of data. (I think ext4 will handle partitions up to 100TB these days.)

If you have some flexibility as to what OS to use, consider using something like FreeNAS, which would make setting up large ZFS pools a simple, point-n-click effort.

---

### Post by Habitual on 2012-06-07
Dave:
[http://en.wikipedia.org/wiki/Xfs](http://en.wikipedia.org/wiki/Xfs)

Other options may become glaringly apparent 5s after this post. :)

---

### Post by rubylaser on 2012-06-07
You can now create ext4 filesystems to greater than 16TB, but the tools to work with the filesystem are still under development, so that's not really a viable option for production data.  I wouldn't touch XFS personally on this either.  I've experienced corruption on two different large arrays with XFS in the past, and I just don't trust it anymore.  JFS is another option, but I don't have personal experience with that, so I can't make a recommendation either way.

With arrays larger than 16TB, I've been using ZFS.  Personally, I'd setup an Openindiana VM in ESXi with passthrough for your disk controller with a version 28 pool, and run your array from that. I don't like telling you to not use Ubuntu, but until zfsonlinux is tuned for performance and has a true stable release, I can't recommend it for production use either.

Without a good backup strategy at this point, ZFS + snapshots and it's checksumming ability are really at least some layer of protection over a standard Linux filesystem.

---

### Post by rubylaser on 2012-06-07
> **Habitual said:**
> Dave:
[http://en.wikipedia.org/wiki/Xfs](http://en.wikipedia.org/wiki/Xfs)

Other options may become glaring apparent 5s after this post. :)

Hilarious :)

---

### Post by |{urse on 2012-06-07
+1 on OpenIndiana I've always preferred solaris based distros + zfs for large (non-fake) arrays.

---

### Post by curmudge1 on 2012-06-08
Thanks for the inputs, everyone.  I think we'll break up the 12+TB into 3 x 4TB disks and use ext4, for ease of management, stability, etc.  

In case one has problems, the other two will still be available.  

And, we're thinking that a 4TB filesystem is less likely to have filesystem problems.

---

### Post by rubylaser on 2012-06-08
But, you'll have no disk parity in that situation, so any disk you lose will result in a complete loss of that data without a backup in place.  If you're only going to 12TB, I'd just build a mdadm RAID5/6 with ext4.  That will work great.  In the future if you'd like to grow, you can always pool a couple arrays together with mhddfs.

---

### Post by |{urse on 2012-06-10
just, my personal suggestion raid 6+1, hardware raid, software raids are trouble all day for me in the past.

---

### Post by rubylaser on 2012-06-11
> **|{urse said:**
> just, my personal suggestion raid 6+1, hardware raid, software raids are trouble all day for me in the past.

I like the idea of RAID6, but personally I don't like the reliance on a hardware RAID card.  If/when that card fails, your stuck finding the same card, or one that can import it's arrays.  Also, a good hardware RAID card is a pricey investment.  Modern CPUs have no problem handling the parity calculations for a RAID array with very little impact on the host.

All this being said, if the OP isn't willing to spend the time to really understand (and test beforehand) a software RAID solution, then I'd say go the hardware route as well.

---

