---
title: "LXC Issue - Missing Kernel Module in container"
date: 2013-07-15
forum: Virtualisation
---

### Post by srhadden on 2013-07-15
My host kernel has the module 'tipc'

/lib/modules/3.2.0-33-generic/kernel/net/tipc
/lib/modules/3.2.0-33-generic/kernel/net/tipc/tipc.ko

But after I created the container, this module is missing inside the lxc container.

I'm new to lxc, but I goolged and found this file:

cat  /boot/config-3.2.0-33-generic | grep TIPC
CONFIG_TIPC=m
# CONFIG_TIPC_ADVANCED is not set
# CONFIG_TIPC_DEBUG is not set

This file says it is automatically generated. So what do I do to enable the TIPC module to be installed when I create the container?

Running Ubuntu 12.04.

Thanks!

---

### Post by srhadden on 2013-07-15
I didn't have tipc module running on the host when I started the container. Once I did that, then it was running in my container. So I didn't need to do anything other than start that process on the host.

---

