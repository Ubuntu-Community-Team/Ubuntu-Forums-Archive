---
title: "Recommend a project for a CSE student"
date: 2006-11-08
forum: The Cafe
---

### Post by nalmeth on 2006-11-08
My brother has a sweet assignment he needs to do for a computer science engineering course.

> For this assignment you will research and identify Linux kernel modification projects capable of adding value to a Linux installation. One of the greatest advantages of open source operating systems like Linux is the full availability of source code. With sufficient expertise you can customize a Linux distribution to provide very specialized functionality. Kernel hardening and other security improvements are extremely important for servers exposed to Internet for extended periods of time. Modifications for grid computing fundamentally change the behavior of the operating system. Many experiments with improving the performance of kernel subsystems eventually make their way into stable, production releases.I was showing him tdfsb running with Beryl, and he thought tdfsb would be cool to work on. I thought so too at the time, but I don't think it's especially kernel related.
Here are some recommended projects for ideas:
> Starting Points
You may use any of these well known projects as a starting point for the assignment; if you wish to implement a project that is not listed here, please have it approved by your instructor before proceeding.
[U][I]
::Kernel Hardening and System Security Modifications::

[/I][/U]** Security Enhanced Linux from the National Security Agency**
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)
Not recommended &#8211; too complex for the timeframe. This is part of all Fedora versions since Core 3.

** Linux Intrusion Detection System. The newest is for 2.6.14 kernels.**
[http://www.lids.org/](http://www.lids.org/)

** GRSecurity for Linux. Only try 2.6.17 kernels or newer.**
[http://www.grsecurity.net/](http://www.grsecurity.net/)

** Networking and Grid Computing Modifications**
NOTE: Any network related modifications will require at least two systems to demonstrate their functionality.

** The MOSIX Project &#8211; Only MOSIX2 for Grids is suitable for 2.6.x kernels**
[http://www.mosix.org/](http://www.mosix.org/)

** The OpenMOSIX Project- Only consider the Alpha 2.6.16 kernel version.**
[http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/)

**Virtualization Support**
The Xen Virtual Machine Monitor. Similar to VMWare Server.
[http://www.cl.cam.ac.uk/Research/SRG/netos/xen/](http://www.cl.cam.ac.uk/Research/SRG/netos/xen/)

_*::Performance Enhancement Modifications::*_
[B]
The Linux Real Time Application Interface &#8211; RTAI-3.4 or newer[/B]
[http://www.rtai.org](http://www.rtai.org)

** Linux Trace Toolkit Next Generation**
[http://ltt.polymtl.ca/](http://ltt.polymtl.ca/)

** Standard 2.6.17 Kernel Features**
Understand, implement and demonstrate one of the following new kernel features.
Multiprocessing Support
[ ] Symmetric multi-processing support
( ) Maximum number of CPUs (2-255) (NEW)
[ ] SMT (Hyperthreading) scheduler support
[ ] Multi-core scheduler support (NEW)
The Kernel Preemption Model:
( ) No Forced Preemption (Server)
( ) Voluntary Kernel Preemption (Desktop)
( ) Preemptible Kernel (Low-Latency Desktop)
Block Layer I/O Schedulers:
< > Anticipatory I/O scheduler
< > Deadline I/O scheduler
< > CFQ I/O scheduler
Default I/O scheduler (CFQ) --->Sweet hey? What do you think?

The first thing that came to mind was the Do'Hicky project discussed here, I think DoctorMo is behind it?? He didn't sound that exited when I mentioned it though, I think he wants something with more pizzazz.

They're running fedora 4/5/6 BTW. 

Thanks for any ideas friends!

---

### Post by DoctorMO on 2006-11-08
More pizza's? I can agree to that!

Looking for glamour won't get vital work done, but it is important to do something you enjoy doing.

Dohickey Project: Python Based client application using HAL DBus and Gtk2, uses pathed data structures for information; connects to a perl based server service for submiting reviewing and administering information. all information is available to the client via standard http to allow for easy mirroring of files.

It's not kernel related so it's not really useful for your brother but it is a good project. do you know how hard it was for me to modify my templating engine to do spaced complex structure listing? and yet no one will ever know what it really is unless they're developers.

---

### Post by nalmeth on 2006-11-08
> **DoctorMO said:**
> More pizza's? I can agree to that!

Looking for glamour won't get vital work done, but it is important to do something you enjoy doing.

Dohickey Project: Python Based client application using HAL DBus and Gtk2, uses pathed data structures for information; connects to a perl based server service for submiting reviewing and administering information. all information is available to the client via standard http to allow for easy mirroring of files.

It's not kernel related so it's not really useful for your brother but it is a good project. do you know how hard it was for me to modify my templating engine to do spaced complex structure listing? and yet no one will ever know what it really is unless they're developers.
I suppose if it's not kernel related then.. ahh too bad. I would have pressed him on it, because I like the concept. 
It's funny, I had a similar idea to Dohickey. I drew a mockup for it, pitched the idea to my brother, then realized I hadn't a clue what I was doing, and that someone who did would probably come up with it and make it work. 
Thanks DoctorMO, that was you, and you've taken the idea further than I ever envisioned. :cool:
And no, I have no idea how hard it was, but as a user I appreciate the time and effort. I hope it becomes a major success :mrgreen:

---

### Post by DoctorMO on 2006-11-08
nalmeth even as a user your still valuable. your brother may be the programmer but we always need people for various things. for instance we'll need admins who can from time to time look at a list of submisions and accept or reject changes. or people to do usability studdies, documentation, collecting hardware information, expanding data structures etc. all of this is very very useful because it frees up the programmers time to do his real job and makes the end result better because of the many minds.

If _you_ believe in the project and you understand why it's important then won't you help us?

---

### Post by nalmeth on 2006-11-08
>  If _you_ believe in the project and you understand why it's important then won't you help us?
well said :D
It was one of those ideas, and I must say it was refreshing to see someone ambitious take up the task. Perhaps time permitting there is a place for me within the project, however large or small. I can promise you that I will take a real look at the current project, I've only heard of the name and its basic goals, and what you've just outlined.
Maybe it's not what I'm after, but maybe it is. No harm in inquiring I suppose eh?

Anyway, getting back to topic, any suggestions for the kernel hacker while you're here?

---

### Post by DoctorMO on 2006-11-08
All the things in your lists are quite fancy and have resources already going into them. mainly from big vendors.

Has he had a look at HAL? it interacts with the kernel at a very low level. they do kernel patching for device discovery and various other things all the time. be worth investigating as a posible.

I'd go with the pre-emptive kernel hacking if I had to pick from the list; it's an interesting subject with lots of theory and maths thats just perfect for someone in an educational position.

---

### Post by nalmeth on 2006-11-08
Double post

---

### Post by nalmeth on 2006-11-08
Yeah, I think he could do something with HAL. At first it seems like there are less options with strictly kernel related stuff, but there's no real boundary is there? As far as security goes at least, and hardware wise, without a lot of coporate support, theres always work to be done I guess.

I think the Intrustion Detection suggestion was kind of cool.

I've heard a bit about SELINUX too, it's kind of interesting having the NSA head a project like this..

Thanks for the comments

---

### Post by rogercas on 2006-11-22
good day.

im working on a thesis related to the Linux scheduler.

i really need help. i posted it here:

[http://ubuntuforums.org/showthread.php?p=1794658](http://ubuntuforums.org/showthread.php?p=1794658)

the reason i also put it in your thread is because you mentioned 

**[ ] Multi-core scheduler support (NEW)**

thanks alot, guys.

---

