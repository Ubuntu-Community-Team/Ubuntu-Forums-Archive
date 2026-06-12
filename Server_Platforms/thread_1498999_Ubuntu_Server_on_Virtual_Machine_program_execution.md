---
title: "Ubuntu Server on Virtual Machine: program execution problem"
date: 2010-06-01
forum: Server Platforms
---

### Post by mr-chuck on 2010-06-01
Hi everybody

there's a problem that i can't solve in any way.

I installed Ubuntu Server 9.10 on VMware Server, and i use it to lanuch a Java program that does some stuff requiring a lot of time.

The problem is that after about 120/130 minutes starting from launch-time, the program terminate without a reason, that is, the process disappear from the list of processes in execution. The weird thing is that up to that moment everything works well, as i can see by some kind of data regarding the program, saved on a text file.

Something more weird is that, just for being sure that the problem wasn't in my code, i created a stupid program (always Java) with a counter incrementing his value up to a very high number, and printing it on a text file (about every 15 min). Result: even in this case the program terminated after the same period of time.

This does not make sense...

I'm sure that the problem does not regard RAM (1Gb is enough for a counter) or disk space (20Gb is enough for a small text file).

I got no idea of what it can be...is there anybody with any kind of opinion?

Thank you

---

