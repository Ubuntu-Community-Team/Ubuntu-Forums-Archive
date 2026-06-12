---
title: "Trouble recognizing dual CPUs"
date: 2007-04-09
forum: Server Platforms
---

### Post by VinceDee on 2007-04-09
I just moved the hard drive from my old Pentium 1.6 ubuntu server to a newer dual-xeon 1.8 server. Miraculously, just about everything still works (including the kde desktop). However, system monitor reports only one CPU. Other posts here seem to indicate that Ubuntu automagically recognizes the second CPU (or core) without a recompile or anything, but that's not what happened for me.

Anyone know how I can get Edgy to recognize that second CPU? 

Vince

---

### Post by capitalistpiglet on 2007-04-09
you need to use the generic kernel which supports multiple processors I assume the kernel your currently using does not support this and thats why only one processor is working. To check which kernel your using now open a terminal and type uname -r.
You can download the generic kernel from the repository using apt.

---

### Post by VinceDee on 2007-04-09
> **capitalistpiglet said:**
> you need to use the **generic kernel** which supports multiple processors I assume the kernel your currently using does not support this and thats why only one processor is working. To check which kernel your using now open a terminal and type uname -r.
You can download the generic kernel from the repository using apt.

ahh, yes. that reminded me of this thread:

[http://ubuntuforums.org/showthread.php?t=404444&highlight=2.6.15-28-386]("http://ubuntuforums.org/showthread.php?t=404444&highlight=2.6.15-28-386")

I'll have to do this later tonight when no one is using the server, but I'm pretty sure it'll work.

Thanks,

Vince

---

