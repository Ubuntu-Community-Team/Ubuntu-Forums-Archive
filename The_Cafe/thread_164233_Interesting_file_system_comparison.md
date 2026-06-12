---
title: "Interesting file system comparison"
date: 2006-04-22
forum: The Cafe
---

### Post by magnusbb on 2006-04-22
Today on OSNews I found an interessting file system comparison between ext3, XFS, JFS and ReiserFS (v3).

The conclusion:
> These results replicate previous observations from Piszcz (2006) about reduced disk capacity of Ext3, longer mount time of ReiserFS and longer FS creation of Ext3. Moreover, like this report, both reviews have observed that JFS is the lowest CPU-usage FS. Finally, this report appeared to be the first to show the high page faults activity of ReiserFS on most usual file operations.

While recognizing the relative merits of each filesystem, an system administrator has no choice but to install only one filesystem on his servers. Based on all testing done for this benchmark essay, XFS appears to be the most appropriate filesystem to install on a file server for home or small-business needs.

[Read the test here]("http://www.debian-administration.org/articles/388")

**Would XFS be my best bet for Dapper?**

---

