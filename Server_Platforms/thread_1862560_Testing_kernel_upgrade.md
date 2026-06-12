---
title: "Testing kernel upgrade"
date: 2011-10-16
forum: Server Platforms
---

### Post by mwjones on 2011-10-16
Question: **How do you go about testing a new kernel for a remote system?**

I have a remote system and would like to roll out a new kernel without having to physically be present.  After some searching, it looks like the two most prominent options are:

1. ksplice
2. kexec

ksplice probably won't work in this particular instance as the system has a 2.6.xx kernel and I'd like to go to 3.0.4.  **The new 3.0.4 kernel is already configured and compiled on the remote system.**  

kexec might work as it can be used to load the new kernel image and initrd.  But I would like to be able to test the new kernel first before trying anything with kexec.  (e.g. What if the new kernel causes a kernel panic?)

The only thing I can think to do is boot a VM on a local system and drop the new kernel there.  However the hardware on my local system is different than the hardware on my remote system.  

How can I go about testing in this situation?

---

