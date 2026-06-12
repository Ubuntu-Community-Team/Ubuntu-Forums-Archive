---
title: "Disabling filesystem cache"
date: 2012-01-31
forum: Server Platforms
---

### Post by alhowat on 2012-01-31
Hi,

I might be missing something really obvious, but I can't work out how to disable the filesystem cache. There are plenty of articles/posts discussing how the cache can be flushed on demand, but this isn't want we want.

I need to do this so that I can absolutely rule out the influence of the file system cache in some MySQL performance tuning work. I appreciate this is not how any server would run day-to-day but I am sure there must be a way to turn it off for cases such as ours.  

Any suggestions?

Al

---

### Post by smo0th on 2012-08-08
does this helps?:

```
sync
echo 3 > /proc/sys/vm/drop_caches
```

---

