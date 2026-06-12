---
title: "What is the difference between UFEI and EFI?"
date: 2014-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by dhruv3 on 2014-11-07
As per said, what is the difference?

---

### Post by Bucky Ball on 2014-11-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldfred on 2014-11-08
You can think of UEFI as the new BIOS as it is the startup of the system. It checks all the hardware and communicates that to the operating system for booting.

And efi is somewhat the equivalent of the MBR for starting boot of operating system, but allows many systems to share the efi partition. Each installs another folder for booting. And has a lot more room for the boot programs than MBR has.

 Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

