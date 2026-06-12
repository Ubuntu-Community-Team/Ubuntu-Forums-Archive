---
title: "kvm ubuntu boot problems"
date: 2013-03-13
forum: Virtualisation
---

### Post by chuckb1961 on 2013-03-13
We use Ubuntu for a product we currently sell.  It's Ubuntu 10.10 server and we build a new kernel for our software.   It all runs with no problem.  

We would like to make a virtual ubuntu system running on a CentOS 6.3 system for one of our customers.  

Now for the problem. I have install CentOS on a server and created a Ubuntu vm using 10.10 server and KVM.  All works fine.  When I go to install our software and new kernel it fails to boot.  I get this error:

Give up waiting for root device.  Common problem
 - Boot args (cat /proc/cmdline)
Check root delay= (did the system wait long enough? )
Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)
Alert! "/dev/mapper/xxxxxxxxxxxxx-root does not exist.  Dropping to a shell

Remember this is virtual system.   The initial load works just fine.  The kernel I am loading works just fine on a real system.  

If I go the the generic kernel that works there is a /dev/dm-0 /dev/dm-1 /dev/mapper/(three files here)  but on the boot of the new kernel there is no /dev/dm-0 /dev/dm-1 or anything under /dev/mappers.  

Any information on the would be very helpful.  
Thank you.

---

### Post by TheFu on 2013-03-14
10.10 is not supported and hasn't been supported for about a year. Migrating to 12.04 would be the first recommendation. The newer KVM is better, more feature rich and more stable.

CentOS 6.3 is fairly new, correct? The newer KVM that 12.04 provides will do much better at supporting newer client OS kernels.

It seems that you are installing CentOS using LVM.  Does the new kernel provide support for LVM?  Could the changes have broken that support?

What do the log files on both the client AND the hostOS show related to the boot process?

A work around might be to not install CentOS using LVM.

---

