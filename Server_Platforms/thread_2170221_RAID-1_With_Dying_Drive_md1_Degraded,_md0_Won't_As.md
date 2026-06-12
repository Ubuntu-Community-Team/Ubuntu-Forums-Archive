---
title: "RAID-1 With Dying Drive: md1 Degraded, md0 Won't Assemble. How fail/remove Bad Drive?"
date: 2013-08-25
forum: Server Platforms
---

### Post by DiagonalArg on 2013-08-25
Hi all.

I've got 2 identical disks, 2 partitions on each disk (swap/root).  One disk has failing sectors.  One pair of partitions (root/md1) I can assemble "degraded", so I know how to fail/remove the bad partition.  The other pair (swap/md0) won't allow assembly, saying the partition on the _good_ disk has no superblock; so I'm unclear on how to fail/remove the bad partition on md0... and that's supposed to be a prerequisite for taking out the old disk and adding a new one. 

```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
cannot open device /dev/sda1: Device or resource busy
/dev/sda1 has no superblock - assembly aborted.
```

Furthermore, I don't have backups, only the mirror. Is adding a new disk dependable enough, or should I mount and dd the degraded array over to another drive first?
                                                                                                     
(I'm also kind of unclear how I install grub on the new disk; so any input appreciated!)

/DA

-----------------

Ubuntu 12.04 fully updated
Tyan S3970

---

### Post by DiagonalArg on 2013-08-26
Edited to make it real short in the hope I'll get a response!

---

### Post by nerdtron on 2013-08-28
RAID-1 and one failing drive. It means that it can still boot using only a single drive right?
Turn it off and disconnect the failed hard drive, then boot. If it boots, try to poweroff and add a new disk, then, hopefully, rebuild the array.

---

### Post by DiagonalArg on 2013-09-02
@nerdtron - excellent work-around, thank you!  (Though I was kind of wondering if I should use --build instead of --assemble.  It seems that's for "legacy arrays with no superblock" ...)

Now, once done I'll need to install grub on the new disk (apprently), as it says here:
[http://serverfault.com/questions/427484/what-is-the-procedure-to-replace-a-failing-hard-drive-in-a-raid-array](http://serverfault.com/questions/427484/what-is-the-procedure-to-replace-a-failing-hard-drive-in-a-raid-array)
and here:
[http://consultancy.edvoncken.net/index.php/HOWTO_Replace_a_failing_disk_on_Linux_Software_RAID-5](http://consultancy.edvoncken.net/index.php/HOWTO_Replace_a_failing_disk_on_Linux_Software_RAID-5)

Do you have any words of wisdom on this step, particularly since I've never messed around with grub?

---

### Post by nerdtron on 2013-09-02
You still need to install grub? Isn't the grub or /boot partition included in the RAID? Then it will be rebuilt when you rebuild the array.

---

### Post by DiagonalArg on 2013-09-10
Apparently yes, according to those two threads, above.  I need to --add a device, and install grub.

---

