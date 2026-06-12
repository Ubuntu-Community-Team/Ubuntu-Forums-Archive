---
title: "Out of memory: Kill process .."
date: 2012-10-13
forum: Server Platforms
---

### Post by ELMIT on 2012-10-13
On a cloud instance running just a wordpress blog I receive folowing messages:

> Oct 13 17:56:42 localhost kernel: Out of memory: Kill process 5458 (apache2) score 30 or sacrifice child
Oct 13 17:56:42 localhost kernel: Killed process 5458 (apache2) total-vm:274536kB, anon-rss:17224kB, file-rss:0kB
Oct 13 18:02:42 localhost kernel: Adding 524284k swap on /dev/xvdb.  Priority:-1 extents:1 across:524284k SS

At that point the server locks up.

What does the message mean, how can I prevent?

---

### Post by sandyd on 2012-10-13
> **ELMIT said:**
> On a cloud instance running just a wordpress blog I receive folowing messages:



At that point the server locks up.

What does the message mean, how can I prevent?

That is the OOM (out of memory) killer. When you run out of RAM, it activates to kill off processes. You can adjust apache's OOM rating (for other processes to have a higher likelyhood of being killed), but I would reccomend adding more RAM instead.

---

### Post by anonymouschief on 2012-10-15
Please show us the results of running

```
free -m
```

I just want to see your system's total memory vs memory usage.

---

### Post by ELMIT on 2012-10-15
We solved the problem by upgrading the RAM on that cloud computer from 1 G to 2 G.

As I can remember the free command only shows little swapp and of course all RAM used.

---

