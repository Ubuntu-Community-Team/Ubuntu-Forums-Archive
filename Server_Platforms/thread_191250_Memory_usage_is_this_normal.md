---
title: "Memory usage: is this normal ?"
date: 2006-06-07
forum: Server Platforms
---

### Post by melmoth on 2006-06-07
Hello everybody,
I'm a somewhat a linux newbie, but I recently managed to install ubuntu 5.10 as a file server. Actually, I did a server install, and in a second time installed cupsys (which I no longer use and cannot totally remove, but this is another point). The pc (a duron 1300 with 640 Mb RAM) is working just as a network storage in a windows lan via SAMBA. Except cupsys and samba, there shouldn't be any other service running, but if I do a "free" i get this :
```

             total       used       free     shared    buffers     cached
Mem:        646484     634164      12320          0     161640     422488
-/+ buffers/cache:      50036     596448
Swap:      1951888      12476    1939412

```
Is this the right behavour ? Is there anything I should check to make shure everything's working as it should ?

Thank you in advance,

Melmoth

---

### Post by cilynx on 2006-06-07
Your output of 'free' is pretty well normal.  Most of your memory lives as unused buffers/cache.  Swap almost never gets used under normal operating conditions.

Here is my laptop that I'm using right now:
```

rcw@pyth:~$ free
             total       used       free     shared    buffers     cached
Mem:        514392     444676      69716          0      11036     217240
-/+ buffers/cache:     216400     297992
Swap:      1544184          0    1544184

```
And here is one of my production servers:
```

rcw@blessed:~$ free
             total       used       free     shared    buffers     cached
Mem:        580136     556580      23556          0     131748     160516
-/+ buffers/cache:     264316     315820
Swap:       499928      38156     461772

```

---

### Post by Nonno Bassotto on 2006-06-07
Yes, it is. Linux kernel handles ram in a different way than windows does. The ram is freed when needed, in contrast with windows, where ram is freed as soon as it is no longer used. You don't have to worry unless you see a big amount of swap used.

---

### Post by LordHunter317 on 2006-06-07
No, Windows does not operate like that.

---

### Post by melmoth on 2006-06-07
Thank you all. I found strange having just a few megs of ram free in a server running just samba , but I'm happy to hear everything's ok :)

Melmoth

---

### Post by cyracks on 2006-06-07
Look at these values:

```
 admin@tricky:/$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1123        142          0         46        747
** -/+ buffers/cache:        329        936**
Swap:          980          0        980
``` 
That means 329Mb used and 936Mb free

---

