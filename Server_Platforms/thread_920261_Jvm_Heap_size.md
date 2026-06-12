---
title: "Jvm Heap size"
date: 2008-09-15
forum: Server Platforms
---

### Post by lskkishore on 2008-09-15
Hi all,

I want to increase JVM Heap size.......

Can anyone help me to findout solution pls..


Where to change and how to increase heap size....?


Thanks in Advance

---

### Post by porchrat on 2008-09-15
do this when you run the app:

```
java -Xms<initial heap size> -Xmx<maximum heap size>
```

---

