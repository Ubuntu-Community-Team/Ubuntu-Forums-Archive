---
title: "Slow clock in kvm"
date: 2008-03-25
forum: Virtualisation
---

### Post by kaig on 2008-03-25
I have a dual-core AMD64 box with 4GB RAM running Gutsy (server).  On it, I created three instances of KVM and installed Gutsy (server) in each of them.

But the clock in each KVM is slow by a factor of two:
```
for i in 1 2 3 4 5 6 7 8 9 10; do echo a; sleep 1; done
```
If I execute the above loop in the host and a guest, then I can see that the guest can only print five lines in ten seconds.

What could be going wrong?

Thanks,
Kai

---

### Post by jamesntse on 2008-04-03
I am using a pair of Intel Core 2 Duo processor and I have this exact problem as well. It seems to go away if I run kvm with root privileges (as opposed to the group kvm).

Some of the posting on forums/mailing list suggest passing acpi=force as a kernel boot parameter for the guest VM. That just causes my guest VMs to freeze during the boot process.

Anybody with any ideas?

Jim

---

### Post by kaig on 2008-04-04
Apologies for forgetting to respond.

I found out that the problem is the clock source.  During bootup, the kernel tells me "This clock source is slow; consider using another clocksource." or something like this.

I added "clocksource=acpi_pm" to the list of kernel parameters in /boot/grub/menu.lst, and Bob was my uncle.

---

