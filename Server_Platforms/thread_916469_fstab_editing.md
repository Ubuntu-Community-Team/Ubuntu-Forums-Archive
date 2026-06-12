---
title: "fstab editing"
date: 2008-09-10
forum: Server Platforms
---

### Post by ukraine1988 on 2008-09-10
I am running ubuntu server 8.xx (the latest) and I have a problem with my hard drives not auto mounting at start up. Samba shares relies on those drives as well, now I also have a media server setup (gnump3d) to broadcast music over my local LAN. The problem is I have to boot up the computer and then manually click on the drives to mount them so the servers services will work. 

My drives are dual 300GB sata seagates running on a rosewill card.

drive one is my media drive: /dev/sdb1 mounted to /media/multi
drive two is my data drive:  /dev/sdc1 mounted to /media/data

what do I need to do to make these drives auto mount?
I have tried so many walk troughs and I still cant get it to work. I tried for two weeks now.

Thank you very much ahead of time.

Hardware Specs: IBM eServer xSeries 220 dual PIII 1.3GHz 2GB RAM

---

### Post by cariboo on 2008-09-10
Show us a copy of your /etc/fstab, also the output of:

```
sudo fdisk -l
```

Jim

---

### Post by ukraine1988 on 2008-09-10
My fstab file config:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

UUID=7955ee91-c7cb-4165-a4e5-15b24e0316c8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea18ea56-454f-c982-5dcb-eab5dacacf19 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




andrey@cypher:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23e723e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b592e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ada26b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18700   150207718+  83  Linux
/dev/sdc2           18701       19457     6080602+   5  Extended
/dev/sdc5           18701       19457     6080571   82  Linux swap / Solaris

---

### Post by cdtech on 2008-09-11
Just add these to your fstab file:
```

/dev/sdb1  /media/multi ext3 defaults 0 1

/dev/sdc1 /media/data ext3 defaults 0 1
```
You can replace the "/dev" with the block id by using the command:
```
blkid
```
to find the correct block id for the device.

**Update::.**
Just issue the command line "sudo mount -a" to mount the drives after you update your fstab file

---

### Post by ukraine1988 on 2008-09-11
Ok let me give it a try.

---

### Post by ukraine1988 on 2008-09-11
So here what happened so far:

I added these two lines to my fstab file:

/dev/sdb1  /media/data ext3 defaults 0 1
/dev/sdc1 /media/multi ext2 defaults 0 1

(notice that my multi drive is actually an ext2 format, found that out the hard way)

Now when the server boots it checks the drives. data mounts fine, however when multi is scanned it says that e2fsck exited with error 8 and halts the boot prompting me to log into the root maintenance shell and perform the repair manually. It doesnt help. I would check the drives in gui mode and they turn out fine. 

So am I missing something? IS there a better place to insert the mount of the drive in fstab and if you guys dont mind explainig what "blkid" is and how it works/how i should use it? :(  I am starting to think that plays a big role in this en devour.   

Please forgive my ignorance, I have been learning linux for only 3 months now and I am always open to learning. Thank you for your patience with me.

---

