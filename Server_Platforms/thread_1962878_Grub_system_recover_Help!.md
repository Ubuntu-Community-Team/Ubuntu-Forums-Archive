---
title: "Grub system recover Help!"
date: 2012-04-21
forum: Server Platforms
---

### Post by ndberry42 on 2012-04-21
One of the servers that I manage has experienced a serious grub issue.  It is not an option to completely reinstall or even to migrate the data because it is holding 10s of TiBs of data.  I have try reinstalling grub, switching to grub2 running the 
update-initramfs -u -k [kernel ver number] command and I used boot-repair which seems to have made things much worse.

It is running 8.04 Server at the moment and I have tried to do a dist-upgrade in the hopes that it would reinstall any corrupted parts of the system but this has not worked.



Here is the output from the boot-repair live cd.

[http://paste.ubuntu.com/940144/](http://paste.ubuntu.com/940144/)

Please help I am running out of ideas.

---

### Post by darkod on 2012-04-21
You have both menu.lst and grub.cfg which means a mix of grub1 and grub2.

Not sure how much damage the dist-upgrade might have done, the script says you are still running 8.04. On top of that, on the MBR of the disk you have syslinux bootloader.

Have you tried to chroot into the system, purge all grub1 and grub2 and reinstall them?
Note that the package for grub1 is called grub, and for grub2 is grub-pc.

If you need more detailed commands, just ask.

---

