---
title: "Help with kernel recompiling"
date: 2009-03-06
forum: Server Platforms
---

### Post by carlopires on 2009-03-06
Hi,

I'm trying to add IMQ support do my kernel, so I'm recompiling my kernel (intrepid 2.6.27-11) following [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) guidelines.

I got IMQ patch applied and kernel packages recompiled with success but looking at linux-libc-dev_2.6.27-11.27_amd64.deb, xt_IMQ.h is not included. Consequently, iptables recompiling fails when searching it.

I'm new to debian packages and I couldn't understand how debian/ structure in kernel tree is configured to include xt_IMQ.h on linux-libc-dev package. Seems to be in rules.d/2-binary-arch.mk but I'm not sure.

I'd like to do this the right way. Because I want to install these packages in others machines without breaking anything, if possible.

Thanks for help.

---

