---
title: "DESPERATE help needed with failed software raid 5!"
date: 2008-11-01
forum: Server Platforms
---

### Post by psypher on 2008-11-01
Hey all.

Got a bit of a problem. Had a Gutsy install with the OS on one drive and 3 X 80GB SATA drives setup with RAID5. The OS drive failed. I replaced it and installed Intrepid. Now my 3 X 80GB drives all have no partition table.

```
sudo fdisk -l
[sudo] password for sysadmin: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000743c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24042   193117333+  83  Linux
/dev/sda2           24043       24321     2241067+   5  Extended
/dev/sda5           24043       24321     2241036   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System


```


/dev/sdd does seem to output something else, but not much?


I'm really really worried. There's no backup yet, that was the backup being moved onto a new server which is ready now.

I know the data must still be there. It's just a case of rebuilding the partition table and superblock. I really hope there is someone out there that has experience with this. Even if someone could just tell me why this would have happened. Surely the superblock and partition table was not stored on the other failed drive? It had nothing to do with this raid. 

As far as i know the raid had not failed before the other disk, although I didn't check so I'll never know. But I think that each drive always contains a copy of the superblock. If I can just recover that I'm sure I can recreate the raid with mdadm and let it resync and all will be good.

Any help would be greatly appreciated.

Thanks

---

### Post by fjgaude on 2008-11-01
Well, **gparted** and **fdisk** don't understand software raid, so forget about partition table rebuilding. It's not needed.

I believe you can assemble your array using this force command:

```
sudo mdadm --assemble -f --scan
```

If that doesn't work you should delete the etc/mdadm/mdadm.conf and remove mdadm. Reboot, re-install mdadm and then:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will automatically be created and you should be able to mount the array, if you don't already have a mount command in your /etc/fstab file.

Let us know how you are doing.

---

### Post by psypher on 2008-11-01
Bro! I could kiss you!! 

THANK YOU THANK YOU THANK YOU!!!

The 1st command didn't find any raid drives. but I did exactly what you said and the next time it picked it all up, there drives don't even need syncing. AWESOME!!

I knew the data was there. Thats one thing I can give software raid on linux credit for. To me, it's actually more resilient than hardware because you have control like this.

---

### Post by fjgaude on 2008-11-01
Well, I'm glad you got things going again... but please do get backups.

Software raid is good but takes lots of learning to know how to handle all the situations over the years you will come across.

---

### Post by Vegan on 2008-11-01
> **fjgaude said:**
> Well, I'm glad you got things going again... but please do get backups.

Software raid is good but takes lots of learning to know how to handle all the situations over the years you will come across.

I prefer hardware RAID for performance. I backup all important files to DVD, tape or another disk.

---

### Post by psypher on 2008-11-01
I know, I'm usually very strict about backups. Just this situation I was unprepared while moving the data to a new server. Backups are running right now. 


I have had some experience running a software raid on CentOS and have actually played around with RAID in VMware to see what I can and cannot do. Actually tried something like this situation I had but didn't have any problems. Wanted to know if it was possible to move software raid between servers and even distros. So I build a CentOS server with RAID in vmware and moved the raid drives to a new install of ubuntu in vmware. worked so well. Was even able to add another drive to the raid and expand the raid to include the new dics, growing my raid from 5 X 1GB discs to 6.

but now I have learned something new. thank you once again!!

---

### Post by fjgaude on 2008-11-02
So many tricks, things to learn to cover all the bases with software raid. I've moved arrays from one machine to another without issue, that why I like **md** and **mdadm**.

Things can only get better as time goes on. Ubuntu 8.10 has the latest version of mdadm, 2.6.7. Has lots of improvements to cover operator error, if you know what I mean.

---

