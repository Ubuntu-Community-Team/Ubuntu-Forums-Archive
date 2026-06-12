---
title: "how to grow RAID1?"
date: 2009-02-03
forum: Server Platforms
---

### Post by anon0 on 2009-02-03
let's say a Ubuntu server is running off two 40GB drives in RAID1 (say 1GB swap and 39GB /). How are you supposed to change the array into say two 80GB drives in RAID1 (1GB swap but now 79GB /), without losing data?

---

### Post by phillik747 on 2009-02-03
Haven't tried this by My howto about Raid 1 upgrade might help.

[http://ubuntuforums.org/showthread.php?t=943155]("http://ubuntuforums.org/showthread.php?t=943155")

---

### Post by anon0 on 2009-02-04
Found a guide here:
[http://mkfblog.blogspot.com/2007/11/resizing-raid1-system-partition.html](http://mkfblog.blogspot.com/2007/11/resizing-raid1-system-partition.html)

This involves booting off live CD and resizing the filesystem, a 20-step process.

---

