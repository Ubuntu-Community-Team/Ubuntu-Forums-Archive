---
title: "Kernel/User space on 64 bit Linux implementations"
date: 2011-07-24
forum: Ubuntu Dev Link Forum
---

### Post by PoopyTheJ on 2011-07-24
Firstly I'm sorry if this is the wrong forum for this post, Mods if there is a better forum for this please feel free to move it.

I'm doing a research paper for school on the Linux OS memory management and I've found that 32 bit implementations split the available addressable RAM into a 1/3 split, 1GB for the kernel and 3GB for the user space. I'm having a really difficult time finding the same documentation for a 64bit kernel implementation. Does anyone know where I might find documentation of this? In researching windows I found a memory management Doc they put out which states the limits in a 64bit architecture to be 128GB per resource, how is this implemented in Linux, or am I horribly confused. Thanks for any assistance.

---

### Post by rvfh on 2011-09-11
I think you mean 128 TB for Windows 64-bit.
Indeed, 64-bit addressing allows 16 EB, but in reality we use only 48-bit for virtual memory, so 128 TB addressable.

In Windows, this is split 50%/50% between kernel and userspace by default.
In Linux, the default is 25%/75% between kernel and userspace, hence 32TB/96TB.

Correct me if you know better ;-)

---

