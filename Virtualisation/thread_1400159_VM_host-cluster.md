---
title: "VM host-cluster?"
date: 2010-02-06
forum: Virtualisation
---

### Post by zimmemic25 on 2010-02-06
Hi,
I'd like to run one (or more) fast (multi-core,much RAM) VMs on many slow (single-core, less RAM) hosts.
I googled for hours now, but i did only find cluster systems where you run many VMs on many hosts (eg. one VM per host).
But because I have around 5 PCs with 2gHz CPU and 512MB ram each, and i want to run a much faster VM, that isn't the right solution.
So does anyone know if there is such a VM Host on a single system image-like setup, or how I could build one?
Thanks in advance.

PS. As example:
Hardware:
- 5* 2gHz 512MB
Software:
- that host system
Virtual Hardware:
- 1* 2gHz (5-cored) 2.5GB (would be less because of overhead)
Virtual Machines eg.:
- 1* Ubuntu Karmic for desktop use (2gHz triple-core 1.5GB)
- 1* Ubuntu Server minimal for eg rendering or game server (2gHz dual-core 1GB)


PPS. Oh, just to say that: I'm currently using 32-bit hardware, so my final solution should be supporting 32 bit, not only 64-bit-super-mainframe-server-IBM-architecture :-D

---

### Post by zimmemic25 on 2010-02-07
[bump and additional information]:
I found out that there is a library called netlib or PVM, which can run multi-thread-programs on multiple hosts, maybe that could be used for cpu-multiplexing?

---

