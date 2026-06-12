---
title: "Moving Ubuntu from Hard disk to Microsoft Virtual PC"
date: 2009-05-13
forum: Virtualisation
---

### Post by nb123 on 2009-05-13
I currently have Ubuntu installed on a USB hard disk. Can I move this to a Microsoft Virtual PC file? Thanks!

---

### Post by brendan.lefoll on 2009-05-13
It's probably easier to reinstall on Virtual PC. (hint : use virtualbox instead ;-) )

---

### Post by yota on 2009-05-13
Virtual PC supports only windows as a guest operating system, please refer to [http://en.wikipedia.org/wiki/Microsoft_Virtual_PC](http://en.wikipedia.org/wiki/Microsoft_Virtual_PC) for details and for problems running linux on it.

To run Ubuntu on windows you can consider the already suggested (and free as in beer) virtualbox or the commercial vmware.

Moving from disk to virtual image is surely possible, but it takes some knowledge and patience.
The most efficient (and hard) way would be to create a virtual disk, format it, copy files from physical disk to the virtual one, reinstall grub and adjust fstab and /etc/xorg.conf on the virtual disk.

Cloning the physical disk on the virtual one would be easier, but still some minor glitches (graphic or network not working) and a bit of command line work can be expected.

In the end I would suggest to go on this route only if you have some expertise or if you are willing to learn.

Hope this helps!

---

