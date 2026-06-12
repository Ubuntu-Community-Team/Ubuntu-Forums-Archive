---
title: "Vmware Server 2.0 won't install on kernel 2.6.27-10-server"
date: 2009-01-16
forum: Virtualisation
---

### Post by gjarboni on 2009-01-16
Hello,

I've been trying to install VMware Server 2.0 on my Ubuntu 8.10 machine running the 2.6.27-10-server kernel (for PAE support for my extra memory) and I've been running in to a problem. I installed the linux-headers-2.6.27-10-server package but the VMWare install script kept complaining that the kernel version didn't match the kernel I was running.

It turns out that in /usr/src/linux-headers-2.6.27-10-server/include/linux/utsrelease.h there's a line that looks like this:

#define UTS_RELEASE "2.6.27-7" (or something like that). 

Changing the line to:

#define UTS_RELEASE"2.6.27-10-server"

gets everything to work. Except vsock. I guess this is a bug in linux-headers-2.6.27-10-server. Right? Or did I miss something.

 the linux-header

---

### Post by Dedoimedo on 2009-01-16
Hello,

I would not play with sources, as you may break something you did not intend.

You should post this on VMware forums.

However, I'd try updating your kernel, kernel source, kernel headers before attempting to hack the sources.

Dedoimedo

---

