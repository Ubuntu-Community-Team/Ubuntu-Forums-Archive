---
title: "No sound on Ubuntu 10.04 Virtual Machine"
date: 2010-05-16
forum: Virtualisation
---

### Post by charles_pty on 2010-05-16
Hi all

I am using Virtual Box 3.1.6 on an Windows XP sp 3 Host, and Ubuntu 10.04 as guest.  I am not able to play any soundfile.  Could someone please help.

Kind Regards

---

### Post by dcstar on 2010-05-17
> **charles_pty said:**
> Hi all

I am using Virtual Box 3.1.6 on an Windows XP sp 3 Host, and Ubuntu 10.04 as guest.  I am not able to play any soundfile.  Could someone please help.

Kind Regards

Use the generic kernel and not the virtual kernel.

---

### Post by charles_pty on 2010-05-21
thanks very much for your reply dcstar

Attached there is the information of the kernel I am using, is it the one that you recommend to use?  Please let me know

[LIST=1]
[*]Current Operating System: Linux  ubuntu10 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC  2010 i686
[*]Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae  root=UUID=250f574c-3524-4451-a3ff-6f70e2256f81 ro quiet
[/LIST]

---

### Post by dcstar on 2010-05-25
> **charles_pty said:**
> thanks very much for your reply dcstar

Attached there is the information of the kernel I am using, is it the one that you recommend to use?  Please let me know

[LIST=1]
[*]Current Operating System: Linux  ubuntu10 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC  2010 i686
[*]Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae  root=UUID=250f574c-3524-4451-a3ff-6f70e2256f81 ro quiet
[/LIST]

You already have the generic kernel, I know the virtual kernel (really the server kernel) does not have sound support.

---

