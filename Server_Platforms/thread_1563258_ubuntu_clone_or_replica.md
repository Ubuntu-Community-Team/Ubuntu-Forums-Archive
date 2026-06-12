---
title: "ubuntu clone or replica"
date: 2010-08-28
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-28
Is it possibe to clone a ubuntu system and if any changes made to one system, should be replicated to other?.
plz guide to it.

---

### Post by Revolutionary101 on 2010-08-28
Yes it is possible. To do this follow this tutorial:

[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

I hope it helps.

---

### Post by Thyagaraj on 2010-08-31
Thanks a lot!

Is there any way to automatically replicate the changes made on a system to another to use it as a backup?.
Just like duplicate.

Thank you!

---

### Post by Thyagaraj on 2010-10-19
I used the following to clone my ubuntu9.10 vbox virtual server to another HD attached logically.

```
#ddrescue -v /dev/sda /dev/sdb
```I want to schedule a cron job using "rsync" to replicate the changes made to orginal one to the cloned. But the devices /dev/sda and /dev/sdb changes after restart and it might be problem if synchronized.

```

root@Karmic9:~# fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00065bfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris

Disk /dev/sdb: 11.3 GB, 11277434880 bytes
255 heads, 63 sectors/track, 1371 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00065bfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         993     7976241   83  Linux
/dev/sdb2             994        1044      409657+   5  Extended
/dev/sdb5             994        1044      409626   82  Linux swap / Solaris

```Is there any alternate option?

---

