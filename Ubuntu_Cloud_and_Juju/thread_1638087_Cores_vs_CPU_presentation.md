---
title: "Cores vs CPU presentation"
date: 2010-12-05
forum: Ubuntu Cloud and Juju
---

### Post by jfreegard on 2010-12-05
Hi,

I'm looking at setting up a UEC at home on a quad core PC.  The thing is I need to run Windows 7 as a VM and I want it to make use of all 4 cores.  Is this possible or are the cores presented to the guest as a single core cpu?

MS in their ultimate wisdom only support 2 physical CPU's but each cpu is supported with multiple cores.

Thanks

---

### Post by CharlesA on 2010-12-05
Depending on what virtulization software you are using, you should be able to assign however many cores to it as you want.

As a rule of thumb: Leave 1 core for the OS.

---

### Post by kim0 on 2010-12-05
Hey there, I wouldn't really setup UEC for a "home" setup on a single machine. Your best bet is probably to install Ubuntu as the base OS, then a direct hypervisor on top. I would recommend either KVM to be managed with virt-manager, or VirtualBox OSE

If you have more specific requirements, let us know

---

