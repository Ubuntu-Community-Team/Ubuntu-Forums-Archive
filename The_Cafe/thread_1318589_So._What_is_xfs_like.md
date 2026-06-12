---
title: "So. What is xfs like?"
date: 2009-11-07
forum: The Cafe
---

### Post by dragos240 on 2009-11-07
Since I reinstall arch about every month (not because it breaks, it's just fun.), I always change something. Instead of ext4, I chose xfs this time. What's the difference?

---

### Post by Dark Aspect on 2009-11-07
> **dragos240 said:**
> Since I reinstall arch about every month (not because it breaks, it's just fun.), I always change something. Instead of ext4, I chose xfs this time. What's the difference?

[xfs]("http://en.wikipedia.org/wiki/XFS") vs [Ext4]("http://en.wikipedia.org/wiki/Ext4")

It would appear that xfs was not designed for Linux and is slow at certain tasks.

---

### Post by benerivo on 2009-11-07
Never noticed any difference. I would have to be copying/moving 100's of files a day to actually give a damn (seriously).

---

### Post by cariboo on 2009-11-07
I went with xfs when I setup my server because of the large file bug that ext4 had. Xfs is designed to handle huge files, and is only slightly slower that ext4.

---

### Post by Grant A. on 2009-11-07
XFS is great if you're hauling around giant media files, but it's terribly slow with small ones. Plus, it doesn't journal the same way that Ext3/4 does. If you shutdown the computer improperly, you run the risk of corrupting all of your user data and home directories.

---

### Post by ubuntu-freak on 2009-11-07
I've had more problems with EXT than XFS. I've experienced a few bad shutdowns and restarts with XFS and not suffered any ill effects. A cool feature of XFS is the fact that you can defragment a single large file, or the whole drive/partition. Also, I think I'm right in saying that patches and optimizations are still added to the Linux kernel for XFS.

---

