---
title: "Ubuntu Server 9.10 &quot;run-init&quot; /sbin/init: No such file or directory&quot;"
date: 2009-08-11
forum: Server Platforms
---

### Post by kenelbow on 2009-08-11
Hello all,
I am currently experiencing trouble getting my Ubuntu server to boot.  Yesterday I attempted to login to the server and was unable to.  I was also unable to reboot, so I ["raised a skinny elephant"]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html") to try to reboot as cleanly as possible.

Afterwards I am unable to boot, even if I choose an earlier kernel or recovery mode via GRUB.  I get the following:
[I]
kinit: No resume image, doing normal boot...
run-init: /sbin/init: No such file or directory
{    4.550.603] Kernel panic - not syncing: Attempted to kill init![/I]

My root filesystem is /dev/mapper/*MyServerName*
I booted to a live CD and checked this filesystem and /sbin/init does indeed exist.

Anyone have any idea what's going on?

---

