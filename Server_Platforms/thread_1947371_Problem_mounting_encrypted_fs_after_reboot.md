---
title: "Problem mounting encrypted fs after reboot"
date: 2012-03-26
forum: Server Platforms
---

### Post by TheMightyGirth on 2012-03-26
Hi All,

I have just restarted a box for the first time since adding and encrypting some new disks. I seem to be unable to mount them and am being told that there is no file system.

The background is;
Ubuntu 8.10 server installed with an encrypted /home and swap partition.
/home got full so I added 2 new disks
I used cryptsetup to create the encrypted device mappers
I formated the mapped devices with mke2fs -j
I edited fstab entering the mapped device
I mounted the disks and started using them.
Upon reboot, the 2 original encrypted partitions are fine but the 2 new ones are not.

Now I have to admit I am not 100% about the password I used. I think it's the same as the existing 2 but I'm not totally 100%.

So, is there a way to verify if the password I am using is correct and assuming it is, what would people suggest as a next step....

---

