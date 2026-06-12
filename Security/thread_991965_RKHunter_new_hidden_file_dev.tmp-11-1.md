---
title: "RKHunter new hidden file /dev/.tmp-11-1"
date: 2008-11-24
forum: Security
---

### Post by riff raff on 2008-11-24
Suddenly rkhunter has found a new hidden file:

Warning: Hidden file found: /dev/.tmp-11-1: block special (11/1)


# ls -la /dev/.tmp-11-1
brw------- 1 root root 11, 1 2008-11-22 21:35 .tmp-11-1


# file /dev/.tmp-11-1
/dev/.tmp-11-1: block special (11/1)


I can't seem to find anything about it on Google (well, two in the French ubuntu forum). 

Has anyone seen this or something similar?


Thanks,

-mike

---

### Post by brian_p on 2008-11-24
> **riff raff said:**
> 

I can't seem to find anything about it on Google (well, two in the French ubuntu forum). 


Google with "Hidden file block special rkhunter" for more information. rkhunter is given to spewing out spurious warnings.

---

