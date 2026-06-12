---
title: "quotaon: segmentation fault"
date: 2011-01-24
forum: Server Platforms
---

### Post by brgsousa on 2011-01-24
Hi!
I'm running ubuntu server 10.10 64 bit.
1. Set quota in /etc/fstab like this:
/dev/sdb1   /var/www        reiserfs  defaults,usrquota   0       2
2. Checked quotas:
***# quotacheck -cavm***
*quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.*
3. Tryied to activate quotas using "quotaon -a" and got a segmentation fault error.

When I change filesystem to ext3 (using mkfs.ext3 and changing /etc/fstab) it works well.

So there are 2 problems, quotacheck warning about journaled quota and the segmentation fault error. How can I fix that?

Regards,
Bruno

---

