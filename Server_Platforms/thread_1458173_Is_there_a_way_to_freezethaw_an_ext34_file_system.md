---
title: "Is there a way to freeze/thaw an ext3/4 file system?"
date: 2010-04-19
forum: Server Platforms
---

### Post by dpcowx on 2010-04-19
Hi guys,

I'm wanting to create consistent hot snapshots of my system. To do this, I've been using the XFS file system instead of ext3 or ext4 for my root partition as I can then use the xfs_freeze utility. 

That said, I recently read on [Wikipedia]("http://en.wikipedia.org/wiki/XFS#Snapshots") that as of kernel 2.6.29, ext3/ext4 now supports the ability to freeze and thaw the file system as well. 

Are there any command line utilities to do this similar to xfs_freeze? Alternatively, how can I create a consistent hot snapshot of my root partition if it's using ext3/4 instead of xfs. I'm not a Linux guru, so please provide as much detail as possible.

System: Ubuntu Server Karmic 9.10

Thanks,
Daniel

---

### Post by foxmulder881 on 2010-04-20
I never even knew that you could do this with ext3/4. I knew ZFS on Solaris could do it, but I didn't think it was possible with Linux. For sure, correct me if I'm wrong.

---

### Post by HermanAB on 2010-04-20
Hmm, it is quite new:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c4be0c1dc4cdc37b175579be1460f15ac6495e9a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c4be0c1dc4cdc37b175579be1460f15ac6495e9a)

However, a database running on a frozen disk will likely spew many errors while your backup is running, so I'm not sure how useful this is in practice.

---

### Post by R.Bucky on 2010-04-20
I know that Percona has a hot backup utility for their MySQL fork, however nothing for the entire filesystem. useful tool...

---

### Post by tgalati4 on 2010-04-20
If you are coming from a windows background, then you might have the urge to produce hot snapshots.  Long-time linux users just backup their important data.  The reliability of linux servers reduce (or eliminate) the need for snapshots, or checkpointing, or failover, or any other strange reliability scheme.

You do need an UPS though.

If snapshots were really needed, you would have a utility already in ext3.  The fact that it doesn't exist tells you something.

---

