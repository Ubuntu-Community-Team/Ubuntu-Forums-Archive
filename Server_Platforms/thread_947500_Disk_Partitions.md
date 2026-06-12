---
title: "Disk Partitions"
date: 2008-10-14
forum: Server Platforms
---

### Post by vegas588 on 2008-10-14
I want to setup a new Ubuntu server. I have two physical disks. So after creating the basic installation, how would I partition the remaining free space. I have one disk that has 55GB and one with 80GB. I want to create one big partition out of it and I am using the CD now to install Ubuntu. 

Select the 55GB, choose create a new partition, asks me for size so I choose the whole 55GB, then primary or logical??? I assume primary

please help me fill in the rest of the options.

Thanks

---

### Post by vegas588 on 2008-10-14
I set the 55GB as /home

The second disk now has 80GB free. How do I continue that /home directory onto this second disk so that it can be seen as one large 135GB disk?

---

### Post by ilrudie on 2008-10-14
You will need to setup LVM2.  Erase the home partition you have now and partition it for LVM.  Partition the second disk LVM as well.  Add the old home partition and the second disk to a single volume group and then carve an ext3 logical volume out of the new vg.   These volumes can be resized so its not necissary to make it take up all the space managed by LVM.  Instead only take up about what you need and that way if some other filesystem gets real full (like /var) you can carve out space for /var on its own logical volume and mount it up freeing up space on your root.

Check [this]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem") [debuntu.org] out for more info.

---

