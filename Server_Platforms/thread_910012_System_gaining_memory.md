---
title: "System gaining memory"
date: 2008-09-04
forum: Server Platforms
---

### Post by Wuu on 2008-09-04
i use "free -m" and it's show me used 323 mb after 10 minutes it rising about 10 mb! And it not stooping until all my ram is full loaded! I am only running Apacahe Php Mysql and game server. How can i take a look witch process is using so much memory? I don't have GUI :(

---

### Post by windependence on 2008-09-04
This is most likely normal Linux memory management. Linux will not give up memory unless and until another process needs it. In this way disk access is reduced. Unless your system is slow, I would not worry.

You can monitor memory in real time using top.

-Tim

---

### Post by kosmiciatakuja on 2008-09-04
Or better even, use atop. It's like top only has more information. For example, and this is interesting to you - shows you which process is allocating memory and how much, showing you the growth, not only the total usage. It's easy to see which process is leaking or growing with no purpose, and then investigate it. 

Keep in mind, as it's already been said above, that linux likes to use memory for cache/buffers if it is not in use by anything other. It makes sense because it speeds up your system and if any process needs the memory it gets it. So it's a win-win situation :)

hope this helps

---

### Post by schettj on 2008-09-04
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3550       3441        108          0         13       2016
-/+ buffers/cache:       1412       2137
Swap:         9656         36       9619

```

Look at the -/+ line: -/+ buffers/cache:       1412       **2137**

My 4gb ram is "full" - only 108mb free - unless you ignore the buffers/cache, then it's got 2.1GB free.

Or, put another way, free memory is wasted memory.

---

