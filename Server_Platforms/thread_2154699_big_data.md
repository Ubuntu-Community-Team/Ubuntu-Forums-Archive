---
title: "big data"
date: 2013-06-15
forum: Server Platforms
---

### Post by Vegan on 2013-06-15
so commodity servers with 5TB disks, racks into rows and suddenly there is a few PB of storage

what is the best choice for making them all appear as a giant single file system?

---

### Post by sandyd on 2013-06-15
Clustered NAS.
FreeNAS supports it I think

---

### Post by rubylaser on 2013-06-15
[dup]

---

### Post by rubylaser on 2013-06-15
Personally, I'd use [Ceph]("http://ceph.com/") or [Gluster]("http://www.gluster.org/").

---

### Post by Vegan on 2013-06-15
thanks guys, I was thinking about astronomy and the spectacular amount of data it gobbles up

[http://www.sdss.org/]("http://www.sdss.org/")

Wikipedia is puny compared to this amount of data.

---

