---
title: "kmymoney"
date: 2008-02-19
forum: West Virginia Team - US
---

### Post by rlduff@suddenlink.net on 2008-02-19
I entered much much data and then attempted to save and exit.  I am getting an error of "unable to add transactions: unknown account id.
I have tried "skill" as well as rebooting system several times and cannot get this program to shut down.  I have gone to another panel and it says it cannot open Kmymoney because another instance is running.  How do I shut this damned thing down???  :(

---

### Post by Dr. Octagon on 2008-02-19
```
ps aux | grep kmymoney
```

Run that command in a terminal and post the output please

---

### Post by rlduff@suddenlink.net on 2008-02-19
bob@bob-desktop:~$ ps aux | grep kmymoney
bob       5335  0.1  6.0  50288 31212 ?        S    17:37   0:07 kmymoney2
bob       5373  0.1  6.1  50280 31872 ?        S    17:38   0:07 kmymoney2
bob       6162  0.1  6.0  49828 31296 ?        S    17:57   0:05 kmymoney2
bob       6167  0.0  1.5  25932  8152 ?        S    17:57   0:00 kio_file [kdeinit] file /tmp/ksocket-bob/klauncherpZtmda.slave-socket /tmp/ksocket-bob/kmymoney22xkMBb.slave-socket
bob       8595  0.0  0.1   2884   816 pts/0    S+   19:02   0:00 grep kmymoney
bob@bob-desktop:~$

---

### Post by rlduff@suddenlink.net on 2008-02-19
Ran your info and it did remove one of the kmymoney's which was running.  I cannot get the other one downed.  HELP!! (PS - thanks for your help)

---

### Post by Dr. Octagon on 2008-02-19
It appears you have multiple instances of kmymoney running concurrently.  We need to determine the original instance so that it can be killed and in turn remove the other ones.

Go into a terminal and try ```
kill 6165
```

---

### Post by rlduff@suddenlink.net on 2008-02-21
I removed kmymoney from the system and then reinstalled it.  It's working fine.  I am pretty sure I tried to get two of the program running at the same time and screwed it up.  As for now, ALL IS WELL.  Thanks for your assistance. -BOB-

---

