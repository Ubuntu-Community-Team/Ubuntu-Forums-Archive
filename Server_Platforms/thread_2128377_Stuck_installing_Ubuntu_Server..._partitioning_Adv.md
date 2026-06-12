---
title: "Stuck installing Ubuntu Server... partitioning Advanced Format drive"
date: 2013-03-23
forum: Server Platforms
---

### Post by Asharad on 2013-03-23
I've spent the last 6 hours trying to install Ubuntu Server 12.10 x64.  I get hung at partitioning.  The install script calls "partman" which tells me my partitions are not properly aligned and instructs me to delete the partition and start over.  It gives me three options:  "Go Back", "Yes", and "No".  No matter which of the 3 options I pick, it returns me to the partman partition screen.  I can't get past this point.

I have also attempted to partition the drive prior to Ubuntu installation, by booting into GParted.  I have partitioned my drive using 1MiB alignment, and yet the Ubuntu installer is still not happy.   

Here are my system specs:
AthlonXP 64bit
4GB Ram
Western Digital 1TB WDEARS ***_Advanced Format Drive_***

The WD drive comes with jumper for "XP compatability".  If I boot without the jumper, Ubuntu only recognizes 33MB.   With the jumper installed, Ubuntu recognizes 1TB, but will not let me past the partition screen.

Any suggestions?

---

### Post by darkod on 2013-03-23
Can you boot the machine with an ubuntu desktop live cd and post the output of parted in terminal?
```
sudo parted /dev/sda unit MiB print
```

If using Gparted don't forget it sometimes uses round to cylinder which I'm not sure complies with the alignment. You may leave 1MiB at front but if the end of the partition is rounded to another unit size that doesn't help much.

Also, it's important what the logical sector size is. parted will also show you that. All Advanced Format drives have 4K physical sector but most of them still have 512B logical sector for compatibility. This is done inside the disk so to the OS it looks the same like the older disks. If you disk has 4K logical sectors it might confuse things.

Post the parted results of the partitions as they are and it will show more info.

---

### Post by Asharad on 2013-03-23
> If you disk has 4K logical sectors it might confuse things.
Oh, it's definitely confused things.  I've found a number of threads here, all which are solved.  But the solutions found aren't working for me.  Even if I get alignment at 2048 (which works for some people), the ubuntu server installer will not let me proceed because it sees a different alignment.

Model: ATA WDC WD10EARS-00M (scsi)
Disk /dev/sda/ 953870 MiB
Sector size (logical/physical) :  512B/4096B
Partition Table: GPT
#   Start     End          Size
1   61.0MiB 953870MiB 953809MiB  (rest is blank)

---

### Post by darkod on 2013-03-23
OK, the logical sector is 512B which is good. The start of the partition is at 61MiB which is high but it should still comply with 1MiB alignment.

Try this, make a new partition from live mode and then in the server installer only try using the same partition without repartitioning it. I see only one partition, do you want to use swap? Or you only need one partition on this disk?

You can create the same size 953809MiB partition with:
```
sudo parted /dev/sda
mklabel gpt
unit MiB
mkpart PAR1 1 953810
quit
```

That will create new gpt table and then one partition with label PAR1 starting at 1MiB ending at 853810MiB. You can change the PAR1 label to anything you like, you may use something descriptive like ROOT etc. When creating gpt partitions they usually have label.

See if the server installer likes this partition.

---

### Post by Asharad on 2013-03-23
OK, I'm trying again.  gparted started the new partition at sector 2048.   Ubuntu is booting.  I'll report back in a sec.

---

### Post by Asharad on 2013-03-23
Ubuntu likes that.  Ok, so what size swap is recommended?   I plan to start over.

I have 4GB ram, and 1TB. This is a headless server.  I'm thinking about 16GB for swap.  Is this ok?

---

### Post by Asharad on 2013-03-23
Thank you!

---

### Post by darkod on 2013-03-23
16GB for swap is high, but if you can spare the space go for it. I wouldn't use more than 8GB or 4GB. If the server has the need to use all of the 4GB of RAM and uses swap regularly, you need more RAM. With 4GB of memory I don't expect the server to use swap at all.

---

### Post by Asharad on 2013-03-23
Thanks.  I'll have to start over anyways.  For some reason, my HD isn't bootable.   I was installing from a USB drive.  This machine doesn't have a CD drive.  After installing ubuntu, it will only boot if the USB drive is plugged in.  I think this means that Grub got installed on the wrong device.

---

### Post by darkod on 2013-03-23
No need to completely reinstall. Boot once with the usb connected and run in terminal:
sudo grub-install /dev/sda

That should install grub on the MBR of the hdd provided the hdd is /dev/sda. After that you can boot without the usb.

---

### Post by Asharad on 2013-03-24
Thank you.  You've been great help!

---

