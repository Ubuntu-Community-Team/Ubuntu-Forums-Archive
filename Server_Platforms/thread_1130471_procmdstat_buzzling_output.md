---
title: "/proc/mdstat buzzling output"
date: 2009-04-19
forum: Server Platforms
---

### Post by geforce123 on 2009-04-19
Hello everyone,

after a power outtage, I now have the following output when i do "cat /proc/mdstat":

```
$ cat /proc/mdstat Personalities : [raid1] [raid5]
md3 : active raid5 sdc1[0] sdf1[3](S) sde1[2] sdd1[1]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md2 : active raid1 sda3[0] sdb3[2](F)
      153356416 blocks [2/1] [U_]

md1 : active raid1 sda2[0] sdb2[1]
      1951808 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      979840 blocks [2/2] [UU]

unused devices: <none>
```

Looks like only 1 partition has a problem, that's weird: md2 is sharing the same HDs with md1 and md0.

Does anyone knows or can give me some help with that please ?  How do I rebuild it ?

Thanks !
--Phil

---

### Post by geforce123 on 2009-04-22
UP ??1?!?

Please

---

