---
title: "Partition experiment"
date: 2008-05-07
forum: The Cafe
---

### Post by pantonio on 2008-05-07
Hello,

I have to fix a problem with a mistake size of a partition (100GB for /boot!!!). It was not very easy to solve this problem... but I solve it.

It's not very frequent for me to work with partitions, only when I'm installing Linux.

I use fdisk to fix the problem, but was a bit tricky! I copy the /boot directory to /tmp (for backup) and then I delete the /boot partition. Change the activable boot partition to the / partition. Reboot.

Big problem: Boot failed! (obviously!)

Solution: linux rescue CD! I mount the / partition and restore /boot, then I restore grub and changed grub settings for kernel. Finnaly, I went to fstab file to remove /boot partition entry.

After booting normaly, I create a new 100GB partition.

Probably, there are some software better to solve this problem. After that I discover parted, and I am exciting for trying it!

I don't know if there are some other software for partition's manipulation.

Regards.

---

