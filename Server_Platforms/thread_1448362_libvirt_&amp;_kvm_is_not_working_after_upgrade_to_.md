---
title: "libvirt &amp; kvm is not working after upgrade to 9.04"
date: 2010-04-06
forum: Server Platforms
---

### Post by josir on 2010-04-06
Hi folks, 

I upgrade one of my servers from 8.04 to 9.04 and now libvirt is not working anymore.

The funny part is that the virtual machines are working perfectly because I can access them via ssh/ftp/etc.

I just can't access the libvirt interface. For example, if I issued (as root):

virsh -c qemu://system

I halts with
Connecting to uri: qemu:///system
error: failed to connect to the hypervisor

Is there a trace/debug that I can verify ?

Thanks in advance,
Josir Gomes

---

### Post by josir on 2010-04-08
Just to doc my solution to other lucky guys:

It seems that 9.04 virsh is buggy.
After I upgrade to 9.10, virsh start to work again...

---

