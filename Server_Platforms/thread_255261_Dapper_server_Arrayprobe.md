---
title: "Dapper server: Arrayprobe?"
date: 2006-09-11
forum: Server Platforms
---

### Post by TonioRoffo on 2006-09-11
Hi,

I've seen that "Arrayprobe" (HP hardware raid monitor) is available for Edgy.

What do I need to change (if at all possible) to run this on Dapper?

I'm on 2.6.15-23-server kernel.

I've tried downloading arrayprobe-2.0 latest, and started ./configure after unpacking it; however, configure complains about not finding my kernel sources - if I check, latest kernel sources are already installed?

Thanks for all help regarding this!

---

### Post by rastilin on 2006-09-11
The sources may be installed but is arrayprobe looking in the right directory? At least that's what gentoo needs. For Ubuntu you'll need the kernel headers, probably more important than the kernel source.

The easiest way to do it is to change all the entires in your source.list file from "dapper" to "edgy". Then run "sudo apt-get update". Upgrade your system to edgy with "sudo apt-get dist-upgrade" and install arrayprobe the normal way. That might be a bit unstable but it's probably less hassle than messing around with the source code.

---

