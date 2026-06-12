---
title: "clean up memory"
date: 2013-09-01
forum: Server Platforms
---

### Post by learnbash on 2013-09-01
Dear folks, 

I want to ask one thing, below command to clear memory for unnecessary thing is ok or not? if we run below command just once a day with cron is it fine or not, if not then what it impact and how.

```


sync; echo 3 | sudo tee /proc/sys/vm/drop_caches


```

---

### Post by TheFu on 2013-09-02
Linux uses RAM for disk and network caching. This is to speed up the system.  Dropping those will just slow down access to files.  Unused RAM is worthless.  
There may be fringe uses where doing this makes sense, but I cannot imagine any.

Seems like a waste to me.  Linux is good at managing RAM use. Let it.

---

