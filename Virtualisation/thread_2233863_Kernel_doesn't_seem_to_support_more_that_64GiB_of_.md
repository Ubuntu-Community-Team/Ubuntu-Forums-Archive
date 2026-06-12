---
title: "Kernel doesn't seem to support more that 64GiB of RAM"
date: 2014-07-11
forum: Virtualisation
---

### Post by narcisgarcia on 2014-07-11
I've been testing KVM-Qemu virtual machines assigning them different ammounts of memory, and everytime booting from .iso files (Lubuntu 14.04 i386, Lubuntu 14.04 amd64, Debian Live 7.5 amd64 CLI, Fedora 20 amd64 Gnome)

In all cases virtual environment starts until the Live boot manager, all distributions and variants boot if RAM is less than 65000 MiB, and in all distributions the Kernel freezes if KVM assigns 65100 MiB or more (tested with 100GiB too).

Hardware host has vmx BIOS extensions enabled and runs Debian GNU/Linux 7.5 (x86_64)

Does anybody know some workaround to Ubuntu works with more than 64GiB (in KVM-Qemu virtual machine or in a real hardware) ?

---

### Post by TheFu on 2014-07-11
There are per-process limits, a VM is just a Linux process after all.
[https://stackoverflow.com/questions/8799481/single-process-maximum-possible-memory-in-x64-linux](https://stackoverflow.com/questions/8799481/single-process-maximum-possible-memory-in-x64-linux) tries to explain.
How much physical RAM is inside the system?
How much swap does the physical system have?

---

### Post by narcisgarcia on 2014-07-11
With:
sudo sysctl --all | grep -ie 'limit'
I don't see how the limit is set.

Per process limits souldn't be the problem, because:
1. Qemu doesn't assign all requested memory to VM at start (memory is assigned with the use by VM)
2. VM starts (Live-CD boot managers work) and Qemu-KVM doesn't expose any error.

Physical system has RAM 32GiB and  Swap 200 GiB.

---

### Post by TheFu on 2014-07-11
2x the physical RAM is the default limit for KVM - read this today, but cannot recall where. Sorry. Probably in RH or KVM.org websites.

---

### Post by narcisgarcia on 2014-07-11
I insist: VM starts and Qemu-KVM doesn't expose any error.
I've tested succesfully a VM with 63 GiB of memory on a hardware host with 16GiB of physical RAM.
Are really default kernels ready for 64GiB or more RAM?
Is there the possibility to fail booting Ubuntu on a real computer with 96 GiB of physical RAM?

Here the limits documented by Red Hat (should be applicable to Debian Qemu binaries?):
[https://www.redhat.com/resourcelibrary/articles/virtualization-limits-rhel-hypervisors](https://www.redhat.com/resourcelibrary/articles/virtualization-limits-rhel-hypervisors)

---

