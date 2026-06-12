---
title: "Increase in load average after 12.04LTS upgrade (from 11.10)"
date: 2012-05-11
forum: Server Platforms
---

### Post by rgubele on 2012-05-11
Hi All,

I'm seeing something strange after upgrading to 12.04LTS: The load average readings are dramatically higher, even though the server's load hasn't increased at all.

You can see the change clearly on this graph:

[http://ryan.gubele.net/files/1113/3679/2110/load.png](http://ryan.gubele.net/files/1113/3679/2110/load.png)

(Keep in mind, the actual load is 4x what is seen there -- so it's more like around .3-.4).

The server otherwise seems to perform fine. It's just ... weird. Was the load average calculation changed with the upgrade?

This particular server is practically unloaded. It should be pretty close to 0 all the time. It was before. Now it sticks closer to 0.3. Restarting doesn't help.

```
$ vmstat -n 1
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 3252788 174764 443796    0    0     0     1    5    4  0  0 100  0
 0  0      0 3252788 174764 443796    0    0     0    24   69   48  0  0 99  0
 0  0      0 3252788 174764 443796    0    0     0    84   51   26  0  0 100  0
 0  0      0 3252788 174764 443796    0    0     0     0   22   18  0  0 100  0
 0  0      0 3252788 174764 443796    0    0     0     0   17   36  0  0 100  0
 0  0      0 3252788 174764 443796    0    0     0     0   21   20  0  0 100  0
 0  0      0 3252788 174764 443796    0    0     0     0   27   28  0  0 100  0
 0  0      0 3252284 174764 443800    0    0     0     0  111   56  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   19   24  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   23   27  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   24   33  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   21   29  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0    56   31   44  0  0 99  1
 0  0      0 3252292 174764 443800    0    0     0     0   21   26  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   24   24  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   19   16  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   11   14  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   21   24  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   26   22  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0    20   33   52  0  0 99  1
 0  0      0 3252292 174764 443800    0    0     0     0   17   16  0  0 100  0
 0  0      0 3252292 174764 443800    0    0     0     0   18   25  0  0 100  0

```

Any thoughts?

---

### Post by d4m1r on 2012-05-11
If the 12.04 server is anything like the desktop variant (haven't updated my servers to 12.04 yet), then yes, we should expect a hike in load averages over 11.10 or 11.04.

---

### Post by rgubele on 2012-05-12
> **d4m1r said:**
> If the 12.04 server is anything like the desktop variant (haven't updated my servers to 12.04 yet), then yes, we should expect a hike in load averages over 11.10 or 11.04.

Why? Has the calculation changed or something?

---

### Post by Gyokuro on 2012-05-12
Known problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)

---

### Post by rgubele on 2012-05-12
> **Gyokuro said:**
> Known problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)

Thank you! I'll read the bug.

---

### Post by Doug S on 2012-05-12
Yes, there were changes to the load average code just prior to the kernel freeze for 12.04. The changes fix reported load averages being in error to low, sometimes massively to low, under some conditions.
 
However, and as the above referenced bug report details, now reported load averages can be too high under very low load conditions.

---

