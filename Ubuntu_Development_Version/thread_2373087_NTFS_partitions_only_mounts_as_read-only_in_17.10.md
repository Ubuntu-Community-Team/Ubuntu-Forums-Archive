---
title: "NTFS partitions only mounts as read-only in 17.10"
date: 2017-10-02
forum: Ubuntu Development Version
---

### Post by e270889o on 2017-10-02
Hello! I've noticed that my internal hdd are mounted as read only. In disk utility, the mount options are

nosuid,nodev,nofail,x-gvfs-show

It's this any beta feature for precaution? Can I force to mount as read-write? 

In 16.04 and Manjaro everything mounts right.

Thanks

---

### Post by mc4man on 2017-10-03
Might be worth mentioning whether you're mounting automatically  (fstab ) or as a user after login.  Is this seen in both available login sessions?

Edit: checking here on a user mounted ntfs (data only, not Windows), no issues, mounts read/write

---

