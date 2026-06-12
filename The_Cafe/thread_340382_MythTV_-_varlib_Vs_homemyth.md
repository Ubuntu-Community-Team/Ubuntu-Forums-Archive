---
title: "MythTV - /var/lib Vs /home/myth"
date: 2007-01-17
forum: The Cafe
---

### Post by Titus A Duxass on 2007-01-17
In the community How-To the disc is partiioned with /var/lib as the place for storing recordings, imports, etc.
I always partion mine so that MythTV user has its own /home directory i.e - /home/myth.

Is there any advantage to using the /var/lib technique?

---

### Post by wilderness wanderer on 2007-01-17
> **Titus A Duxass said:**
> In the community How-To the disc is partiioned with /var/lib as the place for storing recordings, imports, etc.
I always partion mine so that MythTV user has its own /home directory i.e - /home/myth.

Is there any advantage to using the /var/lib technique?

In my (amateurish) opinion, it won't matter where in your file system tree you choose to put the root myth directory.  What is perhaps more important is the file system being used.  By creating a separate partition for /var/lib and putting myth there, it makes it easy to use XFS for that partition while still using ext3 for the root file system.  

What I did was move some stuff off of one of my drives and then repartition it, creating an XFS partition for myth.  Where you choose to mount that partition is, I think, of less consequence. 

If you do choose to run Myth on an ext3 partition (which Ubuntu defaults to), then make sure to enable the "delete files slowly" option.

Here is an excerpt from the manual:

> Because MythTV creates very large files, a file system that does well at deleting large files is important. Numerous benchmarks show that XFS and JFS do very well at this task. You are strongly encouraged to consider one of these for your MythTV filesystem. JFS is the absolute best at deletion, so you may want to try it if XFS gives you problems. MythTV .20 also incorporates a "slow delete" feature, which progressively shrinks the file rather than attempting to delete it all at once, so if you're more comfortable with a filesystem such as ext3 (whose delete performance for large files isn't that good) you may use it rather than one of the known-good high-performance file systems. There are other ramifications to using XFS and JFS - neither offer the opportunity to shrink a filesystem; they may only be expanded.

---

### Post by teet on 2007-01-17
I agree with the above post.  I chose to use JFS instead of XFS for my partition though.  Read up on the differences in the two (I think I remember that JFS and XFS seemed to be the best formats).  I would highly advise against using EXT3...it doesn't do well with big files.

I mounted my partition at /video ...it doesn't really matter where you decide to mount it.

One word of warning:  MythTV only allows you to have 1 recording directory.  Make sure you make the directory is big enough (mine is about 140 GB out of a 200 GB disk).

-teet

---

### Post by Titus A Duxass on 2007-01-18
Thanks for the replies, interesting information.
I will adopt the XFS and /var/lib approach for my next Myth project albeit without the complicated user log-in set up.

---

### Post by gerick on 2007-01-19
> **teet said:**
> One word of warning:  MythTV only allows you to have 1 recording directory.  Make sure you make the directory is big enough (mine is about 140 GB out of a 200 GB disk).

-teet

That is why this $400 drive will be sweet in a DVR: [CinemaStar 7K1000]("http://www.hitachigst.com/portal/site/en/menuitem.6893bc7a231364ae4bda9f30eac4f0a0/")

---

