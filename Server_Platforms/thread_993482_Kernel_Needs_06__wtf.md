---
title: "Kernel Needs 0:6 ?? wtf?"
date: 2008-11-25
forum: Server Platforms
---

### Post by DGortze380 on 2008-11-25
I had an Ubuntu LAMP set up in a virtual machine in Virtual Box.

Reformatted my drive.

Went to install a new LAMP Virtual Machine, now I'm getting this error message after grub:

The kernel requires the following features not present on the CPU: 0:6
Unable to boot - please use a kernel appropriate for your CPU

Nothing has changed. Still an i386 virtual machine, still the same 8.04 i386 iso. What am I missing here?

---

### Post by DGortze380 on 2008-12-01
bump...

Maybe I should have posted in virtualization? Could a mod maybe move the thread?

EDIT: Ok, no responses, and no response to the request to move the thread. Please excuse the double post, I've reposted this in Virtualization. RESPOND ONLY TO THE NEW THREAD: [http://ubuntuforums.org/showthread.php?p=6294705#post6294705](http://ubuntuforums.org/showthread.php?p=6294705#post6294705)

---

### Post by utdream on 2008-12-31
I ran into this error when trying to boot ubuntu server 8.04 from a Sun xVM instance (VirtualBox). I'm running VirtualBox 2.1, and in order to get ubuntu to boot properly, I had to edit the properties of the VM instance to "Enable PAE/NX". Once I did that, ubuntu server 8.04 booted without a hitch.

Just thought I'd post this solution here in case anyone else ran into this issue and needed a fix.

Warm regards,
Jordan Michaels
Vivio Technologies
[http://www.viviotech.net/](http://www.viviotech.net/)

---

### Post by LOG123 on 2008-12-31
you need to enable PAE/NX

---

### Post by DGortze380 on 2008-12-31
> **DGortze380 said:**
> RESPOND ONLY TO THE NEW THREAD: [http://ubuntuforums.org/showthread.php?p=6294705#post6294705](http://ubuntuforums.org/showthread.php?p=6294705#post6294705)

Thanks Anyways

---

