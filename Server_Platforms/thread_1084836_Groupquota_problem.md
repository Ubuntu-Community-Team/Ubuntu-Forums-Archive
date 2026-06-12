---
title: "Groupquota problem"
date: 2009-03-02
forum: Server Platforms
---

### Post by mrjohnsen on 2009-03-02
Hi
I'm have some problems setting up group quota on a /home partion.
The quota is working but the soft limit is acting as a hard limit. It isn't possible for the groupmembers to get pass the soft limit at all. They just get a message about it's not enough space when trying to overreach the soft limit. 

My fstab looks like this:
/dev/sdb1  /home  ext3  defaults,grpquota   0   2

repquota -g /home gives:
Group           used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --  154256       0       0              8     0     0
test1     --    4972    5000   10000             18     0     0


If I have understand soft and hard limits right, the quotasystem isn't suppose to block groupmembers before 10000 here right? 


Thanks in advance.

---

