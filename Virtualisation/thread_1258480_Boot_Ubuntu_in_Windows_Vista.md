---
title: "Boot Ubuntu in Windows Vista"
date: 2009-09-05
forum: Virtualisation
---

### Post by jtan710 on 2009-09-05
I have two partitions on my 600gb harddrive.500gb for Vista and 100gb for Ubuntu.Is there any way to boot Ubuntu in Windows from the Ubuntu partition?
Thanks in advance to anyone who helps.:D

---

### Post by dk06 on 2009-09-05
> **jtan710 said:**
> I have two partitions on my 600gb harddrive.500gb for Vista and 100gb for Ubuntu.Is there any way to boot Ubuntu in Windows from the Ubuntu partition?
Thanks in advance to anyone who helps.:D

Install the Virtualization software on your C:\ (maybe just take the default loc) then when you add machines you can tell them to save the Virtual Disk on your other partition...but I think it's best if you just use the separate partition as a data store/saved data and keep all of your active/in-use data on your C:\
[B]
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)[/B] (free- just register with your email address)
-or-
**[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)** (free- just register with your email address)
-or-
**[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)** (free- just register with your email address)

Have Fun!


edit:adding
I'm pretty sure it would work if you stored your virtual disks on your other partition but it isn't necessary and I'm not sure how windows will like it  (I haven't tried it like that but I'm pretty sure windows likes to copy CDs to the C:\ before burning them to disk(takes longer to burn)...so not sure how it likes VDs on separate partition)

I like to store my ISOs on a separate partition and when I create a Virtual Machine, I just point it to the location of the ISO for the VM's CD/DVD drive

VD = Virtual Disk (different software uses different extensions) 
VM=Virtual Machine
Virtual machines live inside the Virtual Disks (with the exception of a couple small config. files) so really a separate partition isn't necessary, you can allocate the space you want to give Ubuntu when you create the Virtual Disk (4-8 GB is usually more than enough...but can be whatever you want -or- grow dynamically as you add more to the disk)

---

