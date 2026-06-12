---
title: "what architecture for packages? (i386, amd64)"
date: 2008-07-27
forum: System76 Support
---

### Post by andrewdied on 2008-07-27
I just purchased a serval performance laptop.  Do I load i386 or amd64 architecture packages?  

andrew@ubuntu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz

Is there a regular place I check this sort of thing?  Thanks for the help.

---

### Post by scragar on 2008-07-27
```
dpkg --print-architecture
```
will work, although I'm sure someone will recomend a better way, rather than falling to dpkg for the info.

---

### Post by pauper on 2008-07-28
```
uname -m
```

---

### Post by andrewdied on 2008-07-28
Interesting:

andrew@ubuntu:~$ dpkg --print-architecture
amd64
andrew@ubuntu:~$ uname -m
x86_64

If I recall correctly, Intel went and started using the AMD chipset for 64 bit, so this makes some sense.  The important thing is I need to use the amd64 packages, and not the i386 ones, if available.

Thanks, all, for the help.

---

### Post by thomasaaron on 2008-07-28
Right. AMD64 is sort of a legacy name for Ubuntu. But it is not restricted to AMD.

---

