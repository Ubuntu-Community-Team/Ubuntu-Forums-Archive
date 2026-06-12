---
title: "Mount a raw file as a hard drive"
date: 2008-04-19
forum: Virtualisation
---

### Post by AkuTenshi on 2008-04-19
Hi, I have a raw disk image that I can use in QEMU, but it would be helpful if i could mount that raw file as a hard drive, and edit it's contents in Ubuntu instead of inside the virtual machine. Haver tried to do  mount <image> <folder>, but get the error
 "mount: /home/ross/Vmachines/Windows/winxp is not a block device (maybe try `-o loop'?)". 
With -o loop -t vfat, it returns
"mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
Can anybody help?

---

### Post by karyonix on 2008-04-19
use losetup an specify offset to a partition in the raw disk image.
[http://bochs.sourceforge.net/doc/docbook/user/loop-device-usage.html](http://bochs.sourceforge.net/doc/docbook/user/loop-device-usage.html)

---

