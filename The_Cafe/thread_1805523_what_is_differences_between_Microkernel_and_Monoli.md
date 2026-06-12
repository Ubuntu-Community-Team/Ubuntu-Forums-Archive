---
title: "what is differences between Microkernel and Monolithic kernel ?"
date: 2011-07-16
forum: The Cafe
---

### Post by rsd220 on 2011-07-16
[FONT="Arial"][SIZE="3"][B]i know linux kernel is Monolithic kernel 
but i read it has many disadvantages:
1- Coding in kernel space is hard
2-Bugs in one part of the kernel have strong side effects
3-Kernels often become very huge (more than 100 MB of source code )
4-The presence of strong side effects makes the whole kernel less modular 
5-traditional design of Unix systems
 
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/OS-structure2.svg/1024px-OS-structure2.svg.png[/IMG][/B][/SIZE][/FONT]

---

### Post by grahammechanical on 2011-07-16
You seem to have a bias against monolithic kernels. Where are the points against the microkernel?

Read this link

[http://en.wikipedia.org/wiki/Microkernel](http://en.wikipedia.org/wiki/Microkernel)

Main negative? Minix (microkernel) was not developed into GNU/Minix. But Minix was modified into Linux and Linux (or GNU/Linux, if you prefer) has been developed to the point where it is a serious OS for use as a server, desktop, hand held device, embedded OS and other computer types. It can compete with the other monolithic kernel OS - Windows.

To put it another way, the microkernel OS, with applications does not exist. 

Humans make progress by stumbling along in the dark. This is why there is so little progress in so many areas of human activity. History does repeat but not by itself but by people being people.

Regards.

---

### Post by Famicube64 on 2011-07-16
All NT based Windows versions use a hybrid kernel, not monolithic. Just sayin'.

---

### Post by el_koraco on 2011-07-16
> **Famicube64 said:**
> All NT based Windows versions use a hybrid kernel, not monolithic. Just sayin'.

Did somebody claim otherwise?

---

### Post by Famicube64 on 2011-07-16
> **el_koraco said:**
> Did somebody claim otherwise?

Yes.

> It can compete with the other monolithic kernel OS - Windows.

---

### Post by el_koraco on 2011-07-16
That's what i get for reading without glasses.

---

### Post by Bachstelze on 2011-07-16
> **grahammechanical said:**
> But Minix was modified into Linux

Wrong. Linux is not a "modified" version of MINIX, it was written from scratch.

[http://en.wikipedia.org/wiki/MINIX#MINIX_and_Linux](http://en.wikipedia.org/wiki/MINIX#MINIX_and_Linux)

---

### Post by cgroza on 2011-07-16
Linux was just inspired by MINIX.

---

