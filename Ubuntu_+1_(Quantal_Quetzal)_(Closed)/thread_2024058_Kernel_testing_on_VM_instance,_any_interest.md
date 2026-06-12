---
title: "Kernel testing on VM instance, any interest?"
date: 2012-07-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by saphil on 2012-07-13
I saw the announcement for kernel testing and was disappointed to see that none of my hardware is under test.  I run quite a few Ubuntu instances as virtual machines in ESXi. Is there any need for testing Stable + 1 kernels in that environment?  I run Ubuntu Studio a few places and server a few others.

-Wolf

---

### Post by dino99 on 2012-07-13
a non reported bug is not a bug, as no one knows about it  :P

---

### Post by saphil on 2012-07-13
Which 12.10 kernel would you suggest I test against?

:p

---

### Post by dino99 on 2012-07-13
do your choice  :P

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

---

### Post by cariboo on 2012-07-13
> **saphil said:**
> I saw the announcement for kernel testing and was disappointed to see that none of my hardware is under test.  I run quite a few Ubuntu instances as virtual machines in ESXi. Is there any need for testing Stable + 1 kernels in that environment?  I run Ubuntu Studio a few places and server a few others.

-Wolf

Make sure you run checkbox-qt, and create a system profile, and post it at the end of the process, you will be given a link to where the system profile is located on Launchpad. Attach the link to the tests you run along with any bugs you run into.

---

### Post by balloons on 2012-07-16
Saphil, yes, you are welcome to help test the kernel even if your hardware isn't on the list :-) As caribou mentioned linking and mentioning your hardware in any bugs you find will still help the kernel team. If your planning on running 12.04 for awhile, and still want the newer kernels (bug-free) for hardware enablement or features it's a wonderful idea to help test. 

The hardware list was intended as a first pass at common hardware the kernel team wanted to make sure worked. Ideally, we want all hardware to work and therefore any bugs found we'd like to fix if possible. Thanks for offering to help.

---

