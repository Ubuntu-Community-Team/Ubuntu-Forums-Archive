---
title: "RAID 0 installation"
date: 2012-01-24
forum: Server Platforms
---

### Post by rinorho on 2012-01-24
Hi to all,
My server config, based on 10.04.3 x64 server edition, has 1 x 80 GB HD for the system and 4 x 2TB HDD for the storage. Now, I want to configure the same 4 HDD in RAID 0 array, so that the server will have 1 HD for the system and 1 x 8TB multidisk (4x2TB HDD) for the storage.
 
Is there a simple and complete guide for this operation?
I can't do a new installation and follow the guide:
 
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
 
because grub has a bug. I can install server editiond only if SATA storage controller is disabled on the BIOS (asrock n68-s-ucc). After installation is possible to enable the SATA controller! :(
 
Thanks
 
bye

---

### Post by rubylaser on 2012-01-24
> **rinorho said:**
> Hi to all,
My server config, based on 10.04.3 x64 server edition, has 1 x 80 GB HD for the system and 4 x 2TB HDD for the storage. Now, I want to configure the same 4 HDD in RAID 0 array, so that the server will have 1 HD for the system and 1 x 8TB multidisk (4x2TB HDD) for the storage.
 
Is there a simple and complete guide for this operation?
I can't do a new installation and follow the guide:
 
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
 
because grub has a bug. I can install server editiond only if SATA storage controller is disabled on the BIOS (asrock n68-s-ucc). After installation is possible to enable the SATA controller! :(
 
Thanks
 
bye

Sure, you can easily do a RAID0 array with mdadm. But you'd have to be crazy to want to use that for a storage array, especially an 8TB array :)  Losing any disk would cause a loss of all of your data.

At a minimum, you should really do a RAID 5 now (one parity drive).  The other thing you could do if you want do maximize storage space, but want to retain the data on the other drives that didn't fail is to look at[ Greyhole]("http://www.greyhole.net/") or [mhddfs]("http://romanrm.ru/en/mhddfs").

---

### Post by TFroehlich3 on 2012-01-24
> **rubylaser said:**
> Sure, you can easily do a RAID0 array with mdadm. But you'd have to be crazy to want to use that for a storage array, especially an 8TB array :) Losing any disk would cause a loss of all of your data.
 
At a minimum, you should really do a RAID 5 now (one parity drive). The other thing you could do if you want do maximize storage space, but want to retain the data on the other drives that didn't fail is to look at[ Greyhole]("http://www.greyhole.net/") or [mhddfs]("http://romanrm.ru/en/mhddfs").
 
+1
 
I would hate to see you lose 8 terabytes of data! :popcorn:

---

### Post by rinorho on 2012-01-24
Don't Worry :D
I've other 4x2TB HDD as backup!
Now I must copy the backup's files into RAID 0 array Server!
 
Is there a good guide for mdadm?
 
thans to all.
 
bye

---

### Post by rubylaser on 2012-01-24
Sure, just use my guide :) [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm")

At this step,
```
mdadm --create --verbose /dev/md0 **--level=5** --raid-devices=3 /dev/sd[bcd]1
```

Just use --level=0 instead.  All of the rest is the same regardless of the RAID level.

---

### Post by a2j on 2012-01-24
raid0 with 4 2tb drives does not make much sense. :confused:
what is the purpose, share with us, if you don't mind.

---

### Post by rinorho on 2012-01-25
> **a2j said:**
> raid0 with 4 2tb drives does not make much sense. :confused:
what is the purpose, share with us, if you don't mind.
 
I've got one HTPC W7 x64 based with 1TB HD for the system and 4 x 2 TB storage (WD20EARS) for my movie collection (ISO DVD/Blu-ray and mkv files).
 
For the backup of movie collection I assembled one file server based on ubuntu server 10.04.3 LTS edition, with 1x 80Gb HD for the system and 4 x 2 TB (WD20EARS) for the storage. (AMD X2 e240, 2x2GbDDR3 RAM other hardwares)
Now, to have 4 single HDD for the backup isn't suitable! :( I wil want just one multidisk volume as in RAID 0 array configuration.
 
Bye

---

### Post by rubylaser on 2012-01-25
> **rinorho said:**
> I've got one HTPC W7 x64 based with 1TB HD for the system and 4 x 2 TB storage (WD20EARS) for my movie collection (ISO DVD/Blu-ray and mkv files).
 
For the backup of movie collection I assembled one file server based on ubuntu server 10.04.3 LTS edition, with 1x 80Gb HD for the system and 4 x 2 TB (WD20EARS) for the storage. (AMD X2 e240, 2x2GbDDR3 RAM other hardwares)
Now, to have 4 single HDD for the backup isn't suitable! :( I wil want just one multidisk volume as in RAID 0 array configuration.
 
Bye

Personally, I would still use mhddfs instead of mdadm for this.  You'd get the benefit of one combined drive to backup to, but if a drive failed, you wouldn't lose the whole array, you'd just lose the data on that one drive.  It would make replacing a failed drive faster to resync, and in the event of a catastrophic failure on your main array, and something going wrong on this array, you wouldn't lose everything.  This type of event happens more often than you'd believe.  I see users with this problem on the forum from time to time.  

Ultimately, the choice is yours, but for reliability of your backups with no parity, mhddfs is easier to setup and will retain more data in the event of a disk failure.

---

### Post by rinorho on 2012-01-25
> **rubylaser said:**
> Personally, I would still use mhddfs instead of mdadm for this. You'd get the benefit of one combined drive to backup to, but if a drive failed, you wouldn't lose the whole array, you'd just lose the data on that one drive. It would make replacing a failed drive faster to resync, and in the event of a catastrophic failure on your main array, and something going wrong on this array, you wouldn't lose everything. This type of event happens more often than you'd believe. I see users with this problem on the forum from time to time. 
 
Ultimately, the choice is yours, but for reliability of your backups with no parity, mhddfs is easier to setup and will retain more data in the event of a disk failure.
 
I agree with You. :)
I didn't know mdadm and mhddfs; they look like better than RAID 0 array solution.
 
Is there a good and simple guide about  mhddfs? 
 
thanks
bye

---

### Post by rubylaser on 2012-01-25
Sure, I had a link in my first post in this thread, but here it is [again]("http://romanrm.ru/en/mhddfs") :)

---

### Post by rinorho on 2012-01-25
> **rubylaser said:**
> Sure, I had a link in my first post in this thread, but here it is [again]("http://romanrm.ru/en/mhddfs") :)
 
 
thanks :D

---

