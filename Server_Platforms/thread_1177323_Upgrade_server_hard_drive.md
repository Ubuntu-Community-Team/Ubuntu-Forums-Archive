---
title: "Upgrade server hard drive"
date: 2009-06-03
forum: Server Platforms
---

### Post by cmwslw on 2009-06-03
Hi! I want to upgrade my server's hard drive by completely switching the old one with a newer one. I know I could just add an additional one, but I want to use the old drive for server backups. How can I copy everything on the old drive to the new one (preserving permissions, ownership)? After I get that, I suppose I would need to change the new drive to master, switch it out with the old one, and reinstall GRUB. Also, is this a good way to do this? I'm not worried about uptime.

Thanks in advance, Cory

---

### Post by Vegan on 2009-06-03
There is an option in 9.04's CD to copy a partition, that might be what you want. After my own machine failed, I am less than enthusiastic about a second disk, but rather see the need for another server for backups.

---

### Post by jerrrys on 2009-06-03
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by smileypaul on 2009-06-03
use ddrescue.. then gparted live to resize the partition. 

It will clone what you have.

clonezilla will also do a great job.

---

### Post by cmwslw on 2009-06-03
So will clonezilla and ddrescue completely clone my drive? Will GRUB in the MBR be cloned too?

EDIT: Nevermind, I found out that clonezilla does clone the MBR. I'm running it now. Thanks for all the help guys - I hope I don't need any more concerning this :-). It's funny how many times (at least 7) it asks you to confirm.

---

### Post by ian dobson on 2009-06-03
Hi,

Why not use dd to copy the entire disk from one disk to another.

dd if=/dev/sda of=/dev/sdb

I've done this several times and it almost always works (mbr/grub)

Regards
Ian Dobson

---

### Post by Vegan on 2009-06-03
> **ian dobson said:**
> Hi,

Why not use dd to copy the entire disk from one disk to another.

dd if=/dev/sda of=/dev/sdb

I've done this several times and it almost always works (mbr/grub)

Regards
Ian Dobson

That is more or less what booting the Ubuntu CD does when you pick the option to copy a system. You can also use the partitioner to make a cloned disk copy bigger to fill the capacity of the new disk/server.

---

