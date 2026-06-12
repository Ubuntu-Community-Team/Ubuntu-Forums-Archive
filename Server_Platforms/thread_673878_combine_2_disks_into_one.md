---
title: "combine 2 disks into one"
date: 2008-01-21
forum: Server Platforms
---

### Post by stock99 on 2008-01-21
hi,

 I have a 700G hard disk use to store data only. Now I just brought another 700G disk and I would like to bind the two to create larger hard disk. Is there anyway to do it without formating the first disk's data? I didn't have the first disk setup as LVM,as i didn't anticipate the large data size increase.
 
 If so, can anyone give me the commandline option to do it? I only have access in ssh at the moment.

---

### Post by banewman on 2008-01-21
I did a similar thing by creating a mount point for it in the appropriate place - where do you want to add the storage?

---

### Post by HermanAB on 2008-01-21
If you need them glued together seamlessly, then you can use either LVM or RAID0 (striping).  In both cases, you need to make a backup first.

---

