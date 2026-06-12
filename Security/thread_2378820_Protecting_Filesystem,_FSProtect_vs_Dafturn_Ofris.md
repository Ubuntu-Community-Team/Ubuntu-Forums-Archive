---
title: "Protecting Filesystem, FSProtect vs Dafturn Ofris?"
date: 2017-11-27
forum: Security
---

### Post by 8redex8 on 2017-11-27
Hi all, I'm wondering which is better, fsprotect, or dafturn ofris? You  can freeze the filesystem with this, and unfreeze it when you need to do  updates. I think also it resets your system to the frozen state when  you reboot. Is there any other tools that do this too? Thanks! =)

---

### Post by TheFu on 2018-01-01
mount the file system as read-only. Nobody can change anything on it then.

Or use firejail --private to keep all changes in a pseudo-file system that is wiped when the program ends.

There are other overlay file systems that can be used as needed too. [https://spin.atomicobject.com/2015/03/10/protecting-ubuntu-root-filesystem/](https://spin.atomicobject.com/2015/03/10/protecting-ubuntu-root-filesystem/)

There are standard Unix techniques for all this stuff. No need for some 3rd party tool.  For example, using an LVM snapshot would be how I did it for an entire file system.  For a virtual machine, I'd use the qcow2 snapshot capability.

Of course, there are lots and lots of other choices.  "Best" is subjective.  I'd likely use tools from well-know projects that I'm already using and trusting.

---

### Post by HermanAB on 2018-01-03
I agree with the above sentiment.  Do read up on LVM, BetterFS and ZFS (BSD).

For example:

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/)

[https://www.freebsd.org/doc/handbook/zfs.html](https://www.freebsd.org/doc/handbook/zfs.html)

---

### Post by litlesam on 2018-01-03
Thanks to the posters of 2 and 3.

Can use this info for future projects.

---

