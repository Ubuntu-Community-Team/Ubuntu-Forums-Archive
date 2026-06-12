---
title: "Help Installing Dual Boot Ubuntu on Secondary Hard Drive that has Stuff on it"
date: 2015-07-25
forum: Ubuntu/Debian BASED
---

### Post by loganhsnow on 2015-07-25
Hello, I have partitioned my disks like [so]("http://i.imgur.com/92FBWu2.png"). My plan was to install Elementary OS Freya (Based on Ubuntu) on my larger 1TB driver under the 64GB partition. When I go to install it, I get [this]("http://i.imgur.com/BTtcHNh.jpg"). My secondary disk is being detected as all free space. Is there something I have to do regarding [this]("https://en.wikipedia.org/wiki/Logical_Disk_Manager")? Thank you so much!

---

### Post by howefield on 2015-07-25
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ajgreeny on 2015-07-26
Do not make partitions in Windows that you want to use for Linux because Windows often makes dynamic partitions, great for use by Windows but useless for us as Ubuntu will probably not see them.

It is possibly worth booting to a live Ubuntu system (which it appears you have already done as your second pic seems to be the installer), but opening gparted to see what that finds on sdb, then post back here with a screenshot of that gparted window.

---

