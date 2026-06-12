---
title: "how  to copy one hard drive"
date: 2009-02-09
forum: Server Platforms
---

### Post by sfuller on 2009-02-09
i would like to know how to copy one hard drive to a second hard drive not just the file the whole thing so if one hard drive goes i can just boot from the second drive.

---

### Post by logos34 on 2009-02-09
> Cloning an entire hard disk:
[B]
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror[/B]

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


Just make sure to change the UUID of the partitions on the cloned drive so grub doesn't get confused by two / with same #

sudo tune2fs -U random /dev/sdxy

(where sdaxy = the root partition on the backup drive)

then edit /boot/grub/menu.lst and /etc/fstab

do same for /swap and any other linux partitions\

sudo blkid 

will list the partition uuids

---

### Post by HermanAB on 2009-02-09
You can also do this over a LAN using Netcat:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by windependence on 2009-02-09
Just be very careful you don't reverse the source and target as logos34 mentioned. That's why we call dd "disk destroyer". ;)

-Tim

---

### Post by anonymousnobody on 2009-02-11
> **logos34 said:**
> Just make sure to change the UUID of the partitions on the cloned drive so grub doesn't get confused by two / with same #

sudo tune2fs -U random /dev/sdxy

(where sdaxy = the root partition on the backup drive)

then edit /boot/grub/menu.lst and /etc/fstab

do same for /swap and any other linux partitions\

sudo blkid 

will list the partition uuids

do the hard drives have to be exactly the same size (if they do, do they also have be the same make/model)? if not, what if the source is smaller than the target? will dd handle the size difference or do i have to repartition?

---

### Post by windependence on 2009-02-11
Yes, IF you use the [B]conv=notrunc,noerror option. 

notrunc [/B]means do not truncate the output which writes zeros to the end of the drive after the data is written. **noerror **means what you think. dd would normally throw an error about reaching the end of the data. Basically, you're just telling it to keep going no matter what.

-Tim

---

