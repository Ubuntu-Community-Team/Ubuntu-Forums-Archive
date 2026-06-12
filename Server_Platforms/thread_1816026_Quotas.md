---
title: "Quotas"
date: 2011-08-01
forum: Server Platforms
---

### Post by mbw290 on 2011-08-01
I am so confused about my quota system.  I ran a edquota -u on user ali so the syntax was edquota -u ali then I added a hard limit on device /dev/md0

Disk quotas for user ali (uid 1002):
  Filesystem                   blocks       soft       hard     inodes     soft     hard
  /dev/sda1                        36          0     500000         10        0        0
  /dev/md0                          0          0     500000          0        0        0


then i ran quota ali and got 

Disk quotas for user ali (uid 1002): 
     Filesystem  blocks   quota   limit   grace   files   quota   limit   grace
      /dev/sda1      36       0  500000              10       0       0        


why won't the other device show?

---

