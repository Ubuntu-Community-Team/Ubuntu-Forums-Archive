---
title: "Resizing an EXT3 partition on an Adaptec RAID card"
date: 2007-10-02
forum: Server Platforms
---

### Post by feenster on 2007-10-02
Hi all,
I have a server that has an Adaptec RAID controller in it, running a RAID-5 array. It had 3 x 500GB disks in, and i've added a 4th disk to give 1.5TB of storage.

I've expanded the disk with the Adaptec Storage Manager, but now need to expand my partition within Ubuntu 7.04. My disk looks like this:
```
Disk /dev/sdb: 1499.8 GB, 1499872624640 bytes
255 heads, 63 sectors/track, 182349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121565   976470831   83  Linux

```

What do I need to do to safely resize the partition, without losing data? I know about **resize2fs** but i'm unclear as to what steps i should follow to make the process safe. Any help would be greatly appreciated.

Cheers,
   Matt

---

### Post by feenster on 2007-10-02
Oh, and by the way, i've tried resizing using GParted in Ubuntu, and from a Knoppix LiveCD, but the "resize" option is greyed out :( - I wondered if this was because the partition was on an Adaptec RAID controller?

Matt

---

### Post by feenster on 2007-10-03
Any ideas folks?

Matt

---

### Post by netlogic on 2007-10-03
> **feenster said:**
> Oh, and by the way, i've tried resizing using GParted in Ubuntu, and from a Knoppix LiveCD, but the "resize" option is greyed out :( - I wondered if this was because the partition was on an Adaptec RAID controller?

Matt

You cannot resize the drive if you have mounted the drive. Knoppix default is automount. Turn off automount and try it again.

---

### Post by feenster on 2007-10-04
> **netlogic said:**
> You cannot resize the drive if you have mounted the drive. Knoppix default is automount. Turn off automount and try it again.

Hi,
Thanks for the advice. I started Knoppix as **knoppix nofstab** which did the trick, but now i'm faced with another issue. 

GParted recognised the drive as having a size of **-699151672832.00 B**. It should be 1.5TB or thereabouts.

Any ideas?

Matt

---

### Post by conjur3r on 2007-10-04
This is the process I use when extening my ext3 partition on a LVM.  It should be the same for you.

# sudo umount /MOUNTPOINT
# sudo e2fsck -f /dev/sdb1
# sudo resize2fs /dev/sdb1

---

### Post by feenster on 2007-10-04
> **conjur3r said:**
> This is the process I use when extening my ext3 partition on a LVM.  It should be the same for you.

# sudo umount /MOUNTPOINT
# sudo e2fsck -f /dev/sdb1
# sudo resize2fs /dev/sdb1

Hi,
Thanks for that. Have just started an **e2fsck -f** on the partition. Hope it doesn't take too long to go through 1TB!!!

Will let you know how the resizing goes.

Cheers,
  Matt

---

### Post by psusi on 2007-10-04
Before you can resize the filesystem you have to extend the partition.  You can do this in fdisk.  I suggest you give it  a 'u' command to switch it from cylinder to sector mode, note the current start and end sector of the partition, then delete the partition, and recreate it with the exact same starting sector, and set the ending sector to the last sector on the disk.  

Save the partition table, and if you get a warning that it could not be synced, reboot.  In fact, best to reboot anyhow just to be sure.  After that, run the resize command and it will extend the filesystem to use the full size of the partition.

---

### Post by feenster on 2007-10-10
Hi,
Just wanted to report back and say thanks. Deleting and re-adding the partition worked a treat :-)

Matt

---

### Post by netlogic on 2007-10-10
> **feenster said:**
> Hi,
Thanks for the advice. I started Knoppix as **knoppix nofstab** which did the trick, but now i'm faced with another issue. 

GParted recognised the drive as having a size of **-699151672832.00 B**. It should be 1.5TB or thereabouts.

Any ideas?

Matt

I am sorry, MATT. I forgot to get to your question. These days, I average 20 to 60 responses a day on various forums. Very addicting. I am glad you found your solution, but was this number from Knoppix boot or your OS in the drive? You have to check if your modules were the same and had same level of kernel. If you were using old Knoppix, it would have been 2.4 kernel that might not had a chipset for your controller and reporting as a wrong number.

---

### Post by feenster on 2007-10-11
> **netlogic said:**
> I am sorry, MATT. I forgot to get to your question. These days, I average 20 to 60 responses a day on various forums. Very addicting. I am glad you found your solution, but was this number from Knoppix boot or your OS in the drive? You have to check if your modules were the same and had same level of kernel. If you were using old Knoppix, it would have been 2.4 kernel that might not had a chipset for your controller and reporting as a wrong number.

Hi,
Yes, i think it's an older version of Knoppix. Thanks for your reply, i'll bear it in mind for the future.

Matt

---

