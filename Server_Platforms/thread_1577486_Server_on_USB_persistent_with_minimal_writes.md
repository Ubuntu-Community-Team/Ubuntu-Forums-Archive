---
title: "Server on USB persistent with minimal writes"
date: 2010-09-18
forum: Server Platforms
---

### Post by roddersg on 2010-09-18
I would like to create a USB Flash Drive with Ubuntu Server (SMB, FTP, BFS, DHCP, NFS etc) to run my NAS system (something like FreeNAS).

I am able to get it bootable, however, I would like to keep the configurations persistent, but with minimal writes to the /tmp and other directories.  (something like FreeNAS).

I would like to boot from the drive and then run my NAS using raid5, hence, I am not able to put the OS on the drives (would not like to partition them).

Can anyone point me to the right directions or have some suggestions?

---

### Post by C.S.Cameron on 2010-09-19
You should be able to make persistent partitions named casper-rw and home-rw.
These will save changes from a persistent disk image install, (usb-creator, UNetbootin)
Ext2 FS will work for these partitions.
I think these partitions can reside on a second or third flash drive.

I understand that a persistent disk image install writes to disk less often than a full install.

You need to add " persistent" to the text.cfg file.

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.

---

### Post by roddersg on 2010-09-19
Thanks for the ideas on persistency.

How about transfering some of the writeable directories to memory e.g. /tmp,/proc that only exist for the session?

---

### Post by C.S.Cameron on 2010-09-19
I was wondering about using Puppy Linux for a server, It only writes to disk at the end of a session or when instructed.

---

### Post by LightningCrash on 2010-09-19
> **roddersg said:**
> Thanks for the ideas on persistency.

How about transfering some of the writeable directories to memory e.g. /tmp,/proc that only exist for the session?

/proc is already in memory

for /tmp:

[http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html](http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html)

---

### Post by roddersg on 2010-09-20
I found another posting in another thread which also helps in the movement of the directories to minimize writing: [http://ubuntuforums.org/showthread.php?t=1101521]("http://ubuntuforums.org/showthread.php?t=1101521").

With new systems, we have plenty of RAM (In my case, I have 1 GB with an option to upgrade to 2 GB), can't we start moving some of the writeable directories there?  Also, comparing what we have in [FreeNAS]("http://freenas.org") we could have a location within the USB stick for writing of the changes.

---

### Post by LightningCrash on 2010-09-20
Side tangent: You do know that you can boot from mdadm and LVM volumes?

---

### Post by roddersg on 2010-10-29
Thanks for your suggestions, especially the last one on booting from mdadm - this took the better part of a weekend for me, as after VMWare simulation, formatting the drives for RAID etc, grub would not boot.

I found out later that the cause is my controller card SIL3116.  Although RAID was not used from the card, I had used software raid and the system refused to boot (couldn't locate the necessary files)

Still looking for that solution to boot Ubuntu Server from a thumb drive and the changeable portions on the Hard disk.

---

### Post by arnavk007 on 2010-10-29
better way boot from server cd install the server on your flash drive 
use lvm
make a raid 5 later

---

