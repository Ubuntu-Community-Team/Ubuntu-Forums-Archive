---
title: "no /dev/md0 on software RAID5 with mdadm"
date: 2005-12-08
forum: Server Platforms
---

### Post by schdefan on 2005-12-08
Hello!
I create a software RAID5 system with 4 250GB SATA Seagate Barracuda drives. I bought the mass storage controller SATA 300 TX4 from Promise.
I compiled a kernel module because the sata_promise.ko didn't work for me.
I added the module called ulsata2 in my /etc/modules.
The controller is detected and so all 4 drives are available.
I created the array as /dev/md0 and formatted it with ext3. After that i mounted the array. Everything so far worked like charm. 

To simulate an error i disconnected sda1 from the array and booted again. 
After a while the system freezed because /dev/md0 was not found
> * Starting RAID Devices
mdadm:: error opening /dev/md0: No such file or directory

I started from a LiveCD and removed all symbolic links of evms, lvm and mdadm and the rebooted the system.
I started the array on console and all data were still there. So i reconnected sda1 and rebooted. 
Then i activated the array again and it it rebuiled. 

My question is:
I always have to create /dev/md0 because udev and makedev does not. So I have to do this every time i reboot.
in rcS.d i have
> S02mountvirtfs -> ../init.d/mountvirtfs
S04udev -> /etc/init.d/udev
S05mdadm-raid -> /etc/init.d/mdadm-raid
and in rc1.d
> S20makedev -> ../init.d/makedev
S25mdadm -> ../init.d/mdadm

So i think the order is correct.
What can cause this problem? Do i have to put the module ulsata2 in initrd?
But if the controller and the sata drives are detected it should work or not?

schdefan

---

### Post by schdefan on 2005-12-10
I found a solultion in the ubuntu archive:
> There is a known problem regarding timing of events at boot and udev devices not being created quickly enough. I got round it by adding a 5 second sleep at the beginning of the fsck script in /etc/init.d

And i also delete the mdadm.conf
That worked for me.

schdefan

---

