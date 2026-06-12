---
title: "kswapd0 100% CPU usage"
date: 2016-09-28
forum: Server Platforms
---

### Post by lister171254 on 2016-09-28
I'm running 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux on a XEN VPS and recently found that after every clam rules update (seems to use lots of memory), the kswapd daemon uses close to 99%CPU for sometimes up to 4 hours.

I found the following Bug for 15.10 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457), but have not found any bug reports for 16.04. 

Post [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457/comments/123](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457/comments/123) suggest a solution, but I'd appreciate some feedback if this should work on 16.04 too

Thanks

---

### Post by sistoviejo on 2016-10-24
Having the same issue. Usually end up crashing the whole computer and losing work.
Tried many things related to swap but have found no solution yet.

I'm using a desktop computer (no virtualized hardware at all).

Here's my kernel version:
4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
On Ubuntu 16.04.1 LTS

---

### Post by lister171254 on 2016-10-24
Can confirm that [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457/comments/123](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457/comments/123) worked on 16.04 too.

---

### Post by Illusioneer on 2017-07-02
I have been googling around for a fix and have seen reports of this bug going back to 2014.  Even Microsoft doesn't ignore critical system bugs for that long.

---

