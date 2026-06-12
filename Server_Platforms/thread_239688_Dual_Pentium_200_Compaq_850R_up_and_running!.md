---
title: "Dual Pentium 200 Compaq 850R up and running!"
date: 2006-08-19
forum: Server Platforms
---

### Post by kdnoel on 2006-08-19
Took a few tries but I have it up and running Samba with a Public share for my M$ machines and am very pleased. The old server has 1/2gig of ram and mirrored 18gig scsi drives. How do I know that it is using the dual pentiums? I know it should be running the smp kernal but how do I tell? Did Ubuntu server detect and install it or what?
Many thanks to this board!
:biggrin:

---

### Post by kdnoel on 2006-09-01
I did the upgrade to the kernal and problem solved. Now running both processors and samba works great!
Awesome little server if I may say so... ubuntu!

---

### Post by Uluen on 2006-09-01
[QUOTE=kdnoel]I know it should be running the smp kernal but how do I tell? Did Ubuntu server detect and install it or what?:biggrin:[/QUOTE]

```
$ cat /proc/cpuinfo
```
```
$ dmesg | grep processors
```
```
$ top
```
```
$ uname -a
```

---

### Post by etcpool on 2006-09-21
Congratulation !!!!!

---

