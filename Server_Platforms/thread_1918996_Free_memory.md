---
title: "Free memory"
date: 2012-02-02
forum: Server Platforms
---

### Post by fernandoch on 2012-02-02
How much free memory do I have in this server?

```
root@potato:~# free -m
             total       used       free     shared    buffers     cached
Mem:           497        434         62          0         52        250
-/+ buffers/cache:        130        366
Swap:          511          0        511
```

Is it 366 MB?

---

### Post by a2j on 2012-02-02
62, but 250 of it is cached

---

### Post by fernandoch on 2012-02-06
And 52 in the buffers?

---

### Post by Habitual on 2012-02-06
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

