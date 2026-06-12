---
title: "mdadm raid 5 disk failure question"
date: 2009-09-28
forum: Server Platforms
---

### Post by pegler on 2009-09-28
I have a raid 5 array with 4 disks.  2 of them are physically bad.  they both click on boot up.  My question is if I use one of the data recovery services and have them mirror one of the failed drives over to a new drive, and then plot that drive into the machine, will the array assemble correctly?

Does mdadm use some information on the drive itself to determine what array the drive belongs to, or does the os have a list of hard drives identified by serial number or something and use that info to assemble the array.

Thanks,
Matt

---

### Post by fjgaude on 2009-09-28
I've never done what you are thinking of doing. I can tell you that md, which is in the kernel, uses the special UUID that is imprinted in the drives' superblocks to assemble an array. This UUID is not the one that the kernel uses to mount drives. It's the one that's in the /etc/mdadm/mdadm.conf file.

So, you might have a chance of having the two drives be correctly assembled, but only if the data recovery process doesn't alter the indiviudal drive superblocks.

---

