---
title: "vt-x amd-v issue"
date: 2009-03-12
forum: Virtualisation
---

### Post by sahina on 2009-03-12
I am using VirtualBox and I created a Ubuntu guest machine. Here is the configuration:

OS Type: Ubuntu
Base Memory: 3000 MB
Video Memory: 90MB
Boot Order: Floppy, CD/DVD, Hard Disk
ACPI: Enabled
IO APIC: Disabled
VT-x/AMD-V: Enabled
Nested Paging: Enabled
PAE/NX: Disabled
3D Acceleration: Enabled

When I boot the machine, I see that VT-x/AMD-V and Nested Paging show disabled on the lower right corner guest window.

I host machine is 12GB RAM, Intel Core 7 CPU.

Do you have any idea why?

Thank you in advance

---

### Post by T.J. on 2009-03-12
The Core i7 processors are pretty new, so who knows if there are bugs.

---

### Post by -Rick- on 2009-03-12
Not all motherboards (or BIOS'es?) support virtualization extensions, perhaps you could check if that is the problem.

---

### Post by the_genrl on 2010-03-14
hi i am currently having the same issue.  i'm running an AMD quad core processor that supports amd-v.  infact, the last time virtualbox was running, i remember the "VT-x/AMD-V" icon was lit.  now it's not.  ???

---

### Post by Cato2 on 2010-03-16
In both cases, have you checked in the BIOS that AMD-v / VT-x virtualization is enabled?  In some cases the BIOS doesn't have this feature.  Also, check the chipset you are using and whether that supports virtualization as well.

Finally, VMware will tell you if it can access this feature - see [http://communities.vmware.com/message/932100#932100](http://communities.vmware.com/message/932100#932100) - probably Virtualbox has something similar.

---

### Post by Seventh Reign on 2010-06-08
The problem here is that everything runs fine for months.  64 bit guests will load and run with zero issues, until Virtualbox is updated.  THEN they stop working, and nothing fixes the problem except a complete re-install of the entire host operating system.

---

