---
title: "ext4 full with raid 5"
date: 2011-06-04
forum: Server Platforms
---

### Post by gmalac on 2011-06-04
Hi,
I have installed ubuntu server LTS 10.4 on a HP MediasmartServer.
It has four disks. On the first one I have the original HPFS/NTFFS partition (left untouched), a Linux ext4 partition for / a Linux SWAP partition and the rest of this first disk (sda) is part of a RAID 5 with the three other disks.
I now have this first ext4 partion shown as full. Is there an easy way to give it more space without loosing the whole setup?
I am quite nervous for I have 2TB of data on this server and everything is so fine.
Thanks a million for any help 
Guy

---

### Post by YesWeCan on 2011-06-04
Hi. Where do you wish to reclaim disk space from?
NTFS, RAID5, swap, existing free space, an additional disk?

---

### Post by ian dobson on 2011-06-05
Hi,

Add another drive and expand your array onto it. If you have good backups you shouldn't be too nervous.

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-05
> **ian dobson said:**
> Add another drive and expand your array onto it. If you have good backups you shouldn't be too nervous.

You mean remove the RAID partition of the first disk from the array, creating a degraded array, then add a new disk partition to the array and let it rebuild? Then the old partition can be deleted and the ext4 partition extended to fill the freed space?

Very clever. :)

---

### Post by ian dobson on 2011-06-05
> **YesWeCan said:**
> You mean remove the RAID partition of the first disk from the array, creating a degraded array, then add a new disk partition to the array and let it rebuild? Then the old partition can be deleted and the ext4 partition extended to fill the freed space?

Very clever. :)

Hi,

You can grow an array by adding a new disk to it and letting it grow, or replacing each drive one after the other with larger drives then growing the array to fill the larger drives. I've done method 1 several times.

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-05
But can you migrate a RAID too?

So the OP has not run out of space on the RAID but on the / partition on the same disk as one partition of the RAID. So one solution is to remove that RAID partition and replace it somewhere else. IOW if the RAID comprises 4 partitions and you want to migrate one of those partitions to a new drive, how best to do it?

Perhaps one can simply clone the partition using dd, delete the original and hope mdadm doesn't notice. Assuming madam.conf specifies by UUID.

Another approach would be to shrink the RAID partition on the first drive assuming the RAID is not full. Is this possible?

---

### Post by YesWeCan on 2011-06-05
Considering how important RAID is the mdadm documentation is frustratingly fragmented and inconsistent. For example, I found two sources for man madam( 8 ) that had contradictory contents! Here is the relevant part from 'man mdadm' on Mint 11 (same as Ubuntu 11.04 for this purpose):

```
GROW MODE
       The GROW mode is used for changing the size or shape of an active array.  For this to work, the kernel must support the necessary  change.   Various
       types of growth are being added during 2.6 development, including restructuring a RAID5 array to have more active devices.

       Currently the only support available is to

       ·   change the "size" attribute for RAID1, RAID5 and RAID6.

       ·   increase or decrease the "raid-devices" attribute of RAID1, RAID5, and RAID6.

           change the chunk-size and layout of RAID5 and RAID6.

           convert between RAID1 and RAID5, and between RAID5 and RAID6.

       ·   add a write-intent bitmap to any array which supports these bitmaps, or remove a write-intent bitmap from such an array.

       GROW mode is not currently supported for CONTAINERS or arrays inside containers.


   SIZE CHANGES
       Normally  when  an  array  is  built  the "size" it taken from the smallest of the drives.  If all the small drives in an arrays are, one at a time,
       removed and replaced with larger drives, then you could have an array of large drives with only a small amount used.  In  this  situation,  changing
       the  "size" with "GROW" mode will allow the extra space to start being used.  If the size is increased in this way, a "resync" process will start to
       make sure the new parts of the array are synchronised.

       Note that when an array changes size, any filesystem that may be stored in the array will not automatically grow to use the space.   The  filesystem
       will need to be explicitly told to use the extra space.

       Also  the  size  of  an  array cannot be changed while it has an active bitmap.  If an array has a bitmap, it must be removed before the size can be
       changed. Once the change it complete a new bitmap can be created.


   RAID-DEVICES CHANGES
       A RAID1 array can work with any number of devices from 1 upwards (though 1 is not very useful).  There may be times which you want  to  increase  or
       decrease the number of active devices.  Note that this is different to hot-add or hot-remove which changes the number of inactive devices.

       When reducing the number of devices in a RAID1 array, the slots which are to be removed from the array must already be vacant.  That is, the devices
       which were in those slots must be failed and removed.

       When the number of devices is increased, any hot spares that are present will be activated immediately.

       Changing the number of active devices in a RAID5 or RAID6 is much more effort.  Every block in the array will need to be read and written back to  a
       new  location.   From  2.6.17,  the  Linux  Kernel  is able to increase the number of devices in a RAID5 safely, including restarting an interrupted
       "reshape".  From 2.6.31, the Linux Kernel is able to increase or decrease the number of devices in a RAID5 or RAID6.

       When decreasing the number of devices, the size of the array will also decrease.  If there was data in the array, it could get destroyed and this is
       not  reversible.  To help prevent accidents, mdadm requires that the size of the array be decreased first with mdadm --grow --array-size.  This is a
       reversible change which simply makes the end of the array inaccessible.  The integrity of any data can then be  checked  before  the  non-reversible
       reduction in the number of devices is request.

       When relocating the first few stripes on a RAID5, it is not possible to keep the data on disk completely consistent and crash-proof.  To provide the
       required safety, mdadm disables writes to the array while this "critical section" is reshaped, and takes a backup of the data that is in  that  sec&#8208;
       tion.   This  backup is normally stored in any spare devices that the array has, however it can also be stored in a separate file specified with the
       --backup-file option.  If this option is used, and the system does crash during the critical period, the same file must be passed to  --assemble  to
       restore the backup and reassemble the array.
```

And the term 'grow' is a lie as it also shrinks. Why didn't they name it 'resize'???

My interpretation is that you cannot simply add a new disk/partition and ask mdadm to replace the old one with it. You probably need to add the new one as a spare and then "fail" the old one and let it resync. Then delete the old one.

[COLOR="DarkGreen"]sudo mdadm --add /dev/md0 /dev/sdz1[/COLOR]  (this adds the new partition sdz1 as a spare)
[COLOR="DarkGreen"]sudo mdadm --fail /dev/md0 /dev/sda3[/COLOR]  (this fails the old partition sda3 causing the array to use the spare and resync automatically)

The only risk with this is that the resync fails and your data is then toast.

-------------------------------------------------------------

I decided to trial my alternative suggestion of cloning the partition using VirtualBox. It worked for me.
BTW I find VB an invaluable tool for checking how things like mdadm work. I don't trust the documentation anymore or my interpretation of it.

I started with a 3 partition RAID5 on 3 disks. I added a new disk and gave it an MBR and a ext4 partition (sde1) a little bigger than the raid partition I wanted to delete. I then copied the RAID partition (sdb1) to it:
[COLOR="DarkOliveGreen"]sudo dd if=/dev/sdb1 of=/dev/sde1 conv=noerror,sync,notrunc[/COLOR]

When it finished I checked its superblock:
[COLOR="DarkOliveGreen"]sudo mdadm --examine /dev/sde1[/COLOR]

and it was identical to that of /dev/sdb1
I deleted sdb1. You may not need to delete it but I guess you'd have to zero its superblock to avoid confusion.
I then rebooted. The boot failed to mount the array so I skipped with 'S'
Once booted I assembled the array:
[COLOR="DarkOliveGreen"]sudo mdadm --assemble /dev/md0
cat /proc/mdstat[/COLOR]

I mounted the array and all seemed well. I then updated initramfs (thx Ian):
[COLOR="DarkOliveGreen"]sudo update-initramfs -u[/COLOR]

Then rebooted. All worked fine.
I checked the integrity of the array:
[COLOR="DarkOliveGreen"]sudo -s
echo check > /sys/block/md0/md/sync_action
tail -f /var/log/syslog
[/COLOR]
All was fine.

---

### Post by gmalac on 2011-06-07
Thanks everyone for these contributions.
So my setting is four disks, with disk 2 3 4 allocated to the RAID 5 and part of disk 1 also allocated to the RAID 5
I would need to shrink the part allocated to the RAID in disk 1 and then grow the ext4 partition.
I am using webmin so I saw I could remove SATA device A partition 4
Then I should use gParted and grow the ext4
Then I should return to webmin and re-add the SATA device A partition 4 (shrinked in the meantime).
Make sense?
Thanks
Guy

---

