---
title: "Process hangs while cleaning cache"
date: 2010-12-07
forum: Server Platforms
---

### Post by smo0th on 2010-12-07
Hi there,

I have a NFS server and I'm periodically cleaning the cache by using the following lines:

```
/bin/sync; /bin/echo 1 > /proc/sys/vm/drop_caches
/bin/sync; /bin/echo 2 > /proc/sys/vm/drop_caches

```

during the last days the cleaning process gets stucked at '/bin/echo 2', here's the process data:

```
27426 root      20   0  5488  704  576 R  100  0.0 896:06.34 /bin/echo 2                         

```

the process keeps running, so I find this more strange since it's not in zombie or D state, do you have any idea what could be causing this?

---

### Post by windependence on 2010-12-07
Have you checked your system logs?
 
-Tim

---

### Post by smo0th on 2010-12-09
yes I did, there's nothing significant there that points to anything that could be causing the drop_caches process to get hung, it's weird because I have 11 more servers, another NFS included and it only happens in this one.. the difference is that I also have git, munin and apache services on this one

---

