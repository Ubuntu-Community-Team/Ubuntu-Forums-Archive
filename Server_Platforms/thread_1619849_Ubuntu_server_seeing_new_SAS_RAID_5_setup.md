---
title: "Ubuntu server seeing new SAS RAID 5 setup"
date: 2010-11-12
forum: Server Platforms
---

### Post by smiffy07 on 2010-11-12
Hi all

I'm completely new to the who Ubuntu server stuff. I'm hoping someone can help with a pretty simple query!
I have been tasked to setup an Asset Bank, I have a new HP DL360 with Ubuntu server and attached (well almost) an Infortrend SAS RAID chassis with 5 x 1TB drives installed which I have setup as RAID 5.
Server is running fine and RAID drive seems happy but I can't find anywhere that will give me the command line to mount or install the SAS drive so that Ubuntu server can see it.

Any helpers out there?

Thanks.

---

### Post by CharlesA on 2010-11-12
Run this please:

```
sudo fdisk -l
```

It's likely you need a driver for the card, but fdisk will tell you if the OS sees the array or not.

---

### Post by smiffy07 on 2010-11-12
Also, I ran a command to see if server could see it and got this back

 [COLOR=#1f497d][FONT=Calibri, Verdana, Helvetica, Arial]bright@assetbank:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1      65G  958M   61G   2% /
none                  3.0G  212K  3.0G   1% /dev
none                  3.0G     0  3.0G   0% /dev/shm
none                  3.0G   32K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
none                  3.0G     0  3.0G   0% /lib/init/rw
none                   65G  958M   61G   2% /var/lib/ureadahead/debugfs[/FONT][/COLOR]

---

### Post by smiffy07 on 2010-11-12
when i run the fdsk command I get the following:

Disk /dev/cciss/c0d0: 73.4 GB, 73372631040 bytes
255 heads, 63 sectors/track, 8920 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000922cb

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1        8552    68685824   83  Linux
/dev/cciss/c0d0p2            8552        8921     2964481    5  Extended
/dev/cciss/c0d0p5            8552        8921     2964480   82  Linux swap / Solaris

Disk /dev/sda: 3999.7 GB, 3999726043136 bytes
255 heads, 63 sectors/track, 486272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

---

### Post by CharlesA on 2010-11-12
You need to partition and format that array for it to be seen.

Use something like gparted and use a GPT partition, since it's over 2TB.

---

### Post by smiffy07 on 2010-11-12
Cool ok, thank you. So the server is actually seeing that the RAID is plugged in but it just needs a partitioned. I think I can manage that!

---

### Post by CharlesA on 2010-11-12
Yep. After it's partitioned and whatnot, you'd just need to mount it somewhere and add it to fstab if you want it to be mounted automagically.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by smiffy07 on 2010-11-12
I'm sorry to sound so dumb (like I said I'm a newbie) but could you throw me some command line to partition via gparted. I'm looking around but can't find anything I can follow.

---

### Post by CharlesA on 2010-11-12
Try using ***parted***

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by smiffy07 on 2010-11-12
Excellent, thank you....worked a treat!

---

### Post by CharlesA on 2010-11-12
Don't forget to mark the thread as solved from the thread tools menu. :)

---

