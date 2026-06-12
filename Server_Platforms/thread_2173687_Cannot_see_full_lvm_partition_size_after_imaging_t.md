---
title: "Cannot see full lvm partition size after imaging to larger hard disk"
date: 2013-09-10
forum: Server Platforms
---

### Post by auroraskyes on 2013-09-10
I used Clonezilla to image my 1TB hard drive to a larger 2TB drive in my server that is running 13.04 server 64-bit. 
After the imaging a used a GParted Live CD to alter the LVM partition tables to fit the size of the new disk.
However when I run df it doesn't appear to show the space of about the 1.8 TB that I expected.

master@atlas:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/atlas-root  907G  759G  103G  89% /
udev                    4.8G  4.0K  4.8G   1% /dev
tmpfs                   1.9G  432K  1.9G   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    4.8G     0  4.8G   0% /run/shm
/dev/sda1               228M   95M  121M  44% /boot

After running the commands I could find for LVM partitions I get the below:

master@atlas:~$ sudo pvs
[sudo] password for master:
  PV         VG    Fmt  Attr PSize PFree
  /dev/sda5  atlas lvm2 a-   1.82t 931.50g
master@atlas:~$ sudo vgs
  VG    #PV #LV #SN Attr   VSize VFree
  atlas   1   2   0 wz--n- 1.82t 931.50g
master@atlas:~$ sudo lvs
  LV     VG    Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root   atlas -wi-ao 921.50g
  swap_1 atlas -wi-ao   9.77g

Attached is what I see in GParted Live.

Please let me know what I need to change to make my LVM partition fit the entire drive.

---

### Post by 1clue on 2013-09-10
Are you using a DOS partition table?  You look to be pretty close to 2g total size of recognized partitions, and if you used fdisk or a similarly old partition tool then you will be limited by that.

Another thing, the partitions themselves might be resized but you then have to resize the filesystem on it in order to get the full size.

---

### Post by auroraskyes on 2013-09-10
I used the GParted Live to modify the partitions. How do I check the type of the partition table?

How do I change a filesystem size within the LVM partition? I have done this non-LVM setups before and the filesystem tended to follow the size of the ext4 partition.

---

### Post by steeldriver on 2013-09-10
I *think* the order is

[LIST=1]
[*]unmount
[*]deactivate the volume group which the physical volume is part of (vgchange -an *vgname*)
[*]resize the physical volume (pvresize /dev/sdaX)
[*]resize the logical volume(s) (lvresize ... )
[*]reactivate the volume group (vgchange -ay *vgname*)
[*]resize the filesystem(s) (resize2fs)
[*]remount
[/LIST]

but if you throw those search terms (pvresize, lvresize, vgchange) into a web search you will probably find a proper walk through. Hope this points you in the right direction.

---

### Post by 1clue on 2013-09-10
Checking partition table type:  In gparted, select View->Device Information.  If it shows "partition table: msdos" then that's your problem.  If you show GPT then your problem is elsewhere.

Changing filesystem size:  It varies with the type of filesystem.  For ext4 it's resize2fs <device name>.  It will automatically grow to the maximum size shown for the partition.  Google is your friend.

You might want to consider doing something different than you did.  Say for example, you reformat your disk.  Add a /boot partition.  Put in the rest as LVM2, create partitions of equal or slightly larger size, then copy the devices from old to new.

The advantage of doing that is that you can resize most of the volumes(partitions) on-the-fly.  /boot can be ext2 because you don't need anything more and it won't be resizable anyway, but if you use filesystems like ext4 or xfs then you can resize the volumes on the fly without a reboot.

---

### Post by 1clue on 2013-09-10
Wow.

Steeldriver, you're doing it the hard way.

During partitioning, you need a /boot that is not on LVM.  So that's a partition.  The rest of the disk, for a simple system, can be one partition, which is of type Linux LVM.

Then you create a volume group on /dev/sda2 (in the scheme I mentioned in the previous paragraph).  Once you do that, you can add your swap and / and any other partitions you want with modest sizes, and then resize them later.  I've been doing this for years.

If you want RAID then you typically set up RAID, and set up LVM on the MD device, but the same idea.

Then, once you're running, you can lvresize the logical volume, then resize the filesystem on it.  I do this with / partition without a reboot.

---

