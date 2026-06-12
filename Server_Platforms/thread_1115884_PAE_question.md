---
title: "PAE question"
date: 2009-04-04
forum: Server Platforms
---

### Post by Al Fischer on 2009-04-04
Using an ASUS M3N that has a Pentium Mobile which does not support PAE. This machine has 1 GIG of memory. 

Have installed the 8.1 Server in two other machines that are older (AMD Athlon) and have no problems with PAE. Both have less than 1 GIG of memory.

Of course on booting the ASUS (Pentium Mobile) I get message that I need to use a different kernel that doesn't use PAE. 

Is it possible to configure this kernel (2.6.27-11-server or 2.6.27-7-server) to not _require_ PAE?

It seems strange that if have 1G or less memory, that an OS would require the ability to use more than 4 G.

---

### Post by cariboo on 2009-04-04
The Ubuntu kernels are generic, they are setup to work on a wide range of hardware, it looks like unfortunately you can't use the server kernel, but all hope is not lost, you can use a desktop kernel, and you more than likely would notice the difference.

If you can't boot with the server kernel it may be better to just to install the cli. My favorite way is to use the [mini.iso]("http://help.ubuntu.com/community/Installation/MinimalCD"), that way I can select what I want to install. At the menu, type cli at the prompt and hit enter.

Jim

---

### Post by hyper_ch on 2009-04-05
or recompile the server kernel to not use PAE. There's a nice howto on customizing your kernel on debian/ubuntu over at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by Al Fischer on 2009-04-06
Compiling a kernel at MY point of learning may be a problem. But, I will probably try it. It most likely won't be the worst thing I have tried!

I do want the server functions if at all possible.

---

### Post by cariboo on 2009-04-06
Have a look at this [page]("http:///www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"), it explains the difference between a sever kernel and the desktop kernel.

Jim

---

### Post by hyper_ch on 2009-04-07
> **Al Fischer said:**
> Compiling a kernel at MY point of learning may be a problem.
Well, debian based OSes make it rather easy to get the config of the current kernel and modify individual things. That article on howtoforge.com explains it rather well. Besides, you'll have then two different kernels installed. If your modified doesn't work (properly) then you can just go back to the other one.

> **Al Fischer said:**
> I do want the server functions if at all possible.
You can have server functions on a dekstop install/kernel. However if you want to operate a stand-alone server you don't need a desktop and you're better suited with a server kernel.

Install apache and you have a webserver installed.
Install openssh-server and you have a openssh-server installed.
Install a .... server and you have a ... server installed.

---

### Post by Al Fischer on 2009-04-08
Thank you. BOTH of the answers are great. I am more inclined to try the re-compile of a kernel and plan to try it. (and I plan to succeed!)

My immediate goal is a http server for testing webs and as a media server for home. However, the main goal is to LEARN Linux as I do see it as a viable alternative to the mess Windows is becoming. I have only been playing with Linux for 2 months and am starting to feel pretty good about it. Lots to learn.

However, I just got delayed by a Sony Vaio to fix and rebuild due to either a virus or hardware failure for the Grandson, and my wife's game machine reload. And I just picked uo a nice Sony Vaio Laptop 3.2 mhz (for free) with the typical motherboard problem to fix.(beautiful machine but broken)

---

