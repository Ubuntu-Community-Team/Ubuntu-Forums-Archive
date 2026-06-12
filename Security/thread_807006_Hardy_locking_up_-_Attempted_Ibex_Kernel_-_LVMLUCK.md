---
title: "Hardy locking up - Attempted Ibex Kernel - LVM/LUCKS no longer works"
date: 2008-05-25
forum: Security
---

### Post by kevdog on 2008-05-25
I finally installed Hardy last night on a spare Acer 220 Laptop.  I'm having serious problems with the machine hard locking after random amounts of time -- minutes to hours.  Seems strangely similar to similar problems people have posted here:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996)

As recommended here:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

I downloaded and installed Ibex developing kernel version:
2.6.25.1-generic kernel. When attempted to boot however, my LVM/LUCKs encrypted disk however is no longer accessible with the password.  Booting back into the Hardy kernel however: 2.6.24.16-generic the password does work, however once again I get the lockup problems.

Any ideas on how to solve the LUCKS issue?

Small rant -- Really disappointed with the LTS Hardy release.  It is much less stable than Feisty or Gutsy.  Not sure if its a Kernel issue or simply a Hardy issue however for sure it was not thoroughly tested prior to the release.

---

