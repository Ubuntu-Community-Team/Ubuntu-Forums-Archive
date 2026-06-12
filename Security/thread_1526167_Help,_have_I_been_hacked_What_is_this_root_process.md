---
title: "Help, have I been hacked?? What is this root process: tar -czS -c ......"
date: 2010-07-07
forum: Security
---

### Post by cpbl on 2010-07-07
(redundant post removed)

---

### Post by cpbl on 2010-07-07
My hard disk is being used intensively, and iotop says that that is because root is doing the following to a temp file in /tmp:


```
tar -czS -C / --no-recursion --ignore-failed-read --null -T /tmp/tmpABCDE

```

When I disconnect from the network, this process (and the disk usage) stops/disappears. It returns when I plug in again. The file mentioned at the end (it has a random name, not ABCDE) looks like it contains a list of many/all of my files..

Do you know what process could have been doing this? Is it sinister?

Thanks for any help (before all my sensitive info is copied away??)!
c

---

### Post by DaithiF on 2010-07-07
Hi,
looks to me like it might be Simple Backup (sbackup).  Do you have this app installed?  (System->Administration -> Simple Backup Config)

---

### Post by cariboo on 2010-07-07
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by cpbl on 2010-07-07
Yes. That could be!  
Aha... yes, indeed. Line 271 of sbackup.py looks like that. (Hm, Google didn't find it when I searched).
Thank you!!
c

---

