---
title: "too many sda - which one to remove"
date: 2017-05-27
forum: Windows
---

### Post by thanealex on 2017-05-27
Hello people, 
I have a well-running wily on a dual-boot machine alongside an OpenSUSE. I want to remove the OpenSUSE (and eventually replace it with WIN7) however I'm not sure how to do that - there are too many sdas. I founnd this [https://ubuntuforums.org/showthread.php?t=2228951](https://ubuntuforums.org/showthread.php?t=2228951) but i want to make it simpler with less sdas. Any ideas are welcome. Thanks
[ATTACH=CONFIG]275324[/ATTACH][ATTACH=CONFIG]275325[/ATTACH][ATTACH=CONFIG]275326[/ATTACH]

---

### Post by howefield on 2017-05-27
Thread moved to the "*Windows*" forum.

Seems like an opportunity to wipe the lot and start again given that Wily is end of life and no longer supported.

---

### Post by yancek on 2017-05-27
Each sda entry has a number after it.  The numbers indicate the different partitions.  If the image you posted of GParted is run from Ubuntu, then Ubuntu is on sda8.  Not possible to tell from the info posted whether you have other data partitions or a /home partition for Ubuntu or Opensuse.  You can tell which partition Opensuse is on by booting it and running the df -h command which will show output similar to that below:

> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        58G   19G   37G  34% /


The above shows the root of the filesystem indicated by "/" is on sda7.  Check the /etc/fstab file for your other Ubuntu partitions or post it here and someone should be able to help.

---

### Post by thanealex on 2017-05-27
thanks yancek. here is the fstab file info from the Ubuntu partition I'm using:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=21795450-bcdb-4899-9493-319db58de0d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=606174f1-bada-4f90-9efb-096f283f2e56 none            swap    sw              0       0

Cant check other Ubuntu partitions as I'm not sure which ones are Ubuntus and which ones is something else.

And yes, when mounted OpenSUSE it shows:
dev/sda1 25G 4G 20G 18%
udev 2G 100K 2G 1%

 Is it safe to remove when in sda1?

---

### Post by yancek on 2017-05-27
You need to first verify that the Ubuntu Grub is your primary bootloader which you should either know or be able to tell on boot as the boot screens are very different for the two OS's.
If it is not Ubuntu Grub, install it to the MBR.

```
sudo grub-install /dev/sda
```

You have data on sda3.  If that is something you want to save, copy it to a DVD/flash drive or another hard drive.  sda6 and sda7 look like problem partitions and the GParted info shows no data.  Is that correct?  You could try creating a mount point for each partition and then mounting each to see if you can access them and if so if there is data you have and want there.  Again, copy to another source if there is data.

When you get any data you want off sda1 and/or sda3, you should be able to boot Ubuntu and delete both and leave unallocated space for a windows install or create a single partition formatted as ntfs for a windows install.

---

### Post by thanealex on 2017-05-28
Yes, GRUB Ubuntu is the primary bootloader:
[ATTACH=CONFIG]275334[/ATTACH]

There shouldn't be anything on sda3, sda6 and sda7 - can they be some Ubuntu reinstalls? I also don't need need anything from the OpenSUSE in sda1. 

So to resume if I grasped it correctly:
1. Ubuntu is on sda8 - this should stay
2. OpenSUSE is on sda1 - this can go
3. Everything else can go (sda3, sda6, sda7 - I never mounted these drives, I'm not using them, I dont know how they appeared)
4. sda2 - is this part of the OpenSUSE? if yes, it can go too.
5. sda5 - ?
6. Once the above is done in Gparted I should see two partitions only - one for Ubuntu and one unallocated.

---

### Post by yancek on 2017-05-28
> 1. Ubuntu is on sda8 - this should stay

Yes.

> 2. OpenSUSE is on sda1 - this can go

Yes, again.

> 4. sda2 - is this part of the OpenSUSE? if yes, it can go too.

No, absolutely not.  That is an Extended partition which is just a container for your logical partitions, sda5-8 which includes your swap and Ubuntu so you can't remove it. 
You cannot delete an Extended Partition (sda2 in your case) without first deleting all the logical partitions contained within it.
Here is your problem.  Ubuntu on sda8 is a logical partition as is the swap on sda5 so you need to keep both.  If you delete a primary partition (sda1 for example) the other primary partitions (sda2, sda3) will not change.  If you delete a logical partition (sda6, sda7) then the other higher numbered partitions will change (sda8).  Your Ubuntu is on sda8 so if you delete sda6 and sda7, Ubuntu will change to sda6 and your boot files will still be pointing to sda8 and won't boot until that is changed.

Your GParted image in your initial post shows sda and sda3 as being contiguous so deleting those two and either leaving them unallocated or creating 1 55GB partition for windows should be enough to install it.  Installing windows will overwrite the Grub code in the MBR so you won't be able to boot Ubuntu until you re-install Grub to the MBR from the Ubuntu installation DVD.

I would suggest you leave sda6 and sda7 alone until after you install windows and re-install the Ubuntu Grub to the MBR.  
What you do after that with sda6 and sda7 depends on what you want to use that space for.  A Linux/Ubuntu partition, a windows data partition?  
Take a look at the Ubuntu documentation on re-installing Grub at the link below.  Section 2.2 lists several methods of doing that.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by thanealex on 2017-05-28
Understood and completed. Happened just what you said sda1 and sda3 deleted and now I have one unallocated partition of 54.88 GB. Thanks yancek for helping out.

---

### Post by yancek on 2017-05-28
Glad it worked for you.

---

### Post by thanealex on 2017-06-02
more trouble: installed successfully a WIN7 in the unallocated space, then reinstalled the GRUB (needed a boot-repair as described here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and still I cannot access the old installation. Even worse: I do not see it when running fdisk -l. 
[ATTACH=CONFIG]275406[/ATTACH]

Any ideas? I don't believe it's been wiped but i cant access it.

---

### Post by yancek on 2017-06-02
Your windows 7 installed to the correct place, creating a small boot partition plus the standard windows system partition.  You still have the Extended partition where you had Ubuntu on the logical partition but it is only showing the swap and not the Ubuntu which is a bit odd.  I would not expect either to show.  When windows installs, it probably created a new partition table and generally when windows does that, it omits any Linux partitions.  You should be able to recover an old partition table with TestDisk, software available at the link below.  If you use it, be sure to read the Step By Step instructions before beginning.  Hopefully, that will get your Ubuntu back but I'm not sure if it will include the new windows. 


[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by thanealex on 2017-06-02
clear, thanks yancek. Will try your suggestion these days. The new WIN is not yet configured so nothing much to lose.

---

### Post by yancek on 2017-06-02
I'm not sure what might have happened in your install of windows 7.  I've never installed 7 but did install windows 10 last year and it had a "Custom" install option.  I selected that and had previously created an ntfs formatted partition and marked it as active using GParted.  It installed and of course, overwrote the Grub code in the MBR but that was an easy fix.  It did not have any effect on the other 8 Linux partitions on the drive or affect the partition table.  If you need to reinstall windows again, check to see if it has a manual or Custom install option.  Good luck with it.

---

### Post by thanealex on 2017-06-04
[ATTACH=CONFIG]275457[/ATTACH][ATTACH=CONFIG]275458[/ATTACH][ATTACH=CONFIG]275459[/ATTACH][ATTACH=CONFIG]275460[/ATTACH]

TestDisk found 2 linux partitions (pic 1) - one says No file found (pic 2) and the other one says No partition ca be recovered (pic 4). Not sure if it sees the liveCD i'm booting from as Test Ubuntu without installing. Looks like a dead end street.

---

### Post by yancek on 2017-06-04
Doesn't look hopeful.  The error "filesystem may be damaged" might be repairable, emphasis on might.  Using your Ubuntu DVD/flash drive, open a terminal and run:  sudo fdisk -l to get your partitions.  If you see a Linux partition (not swap) you could try running a filesystem check on it with the command:  fsck /dev/sda?, insert partition number for the Linux partition if you find one.  If that works, you might try running testdisk again.  If not, I don't have any other ideas other than re-insalling.  Good Luck.

---

### Post by thanealex on 2017-06-04
gave TestDisk a chance to write one of the Linux partitions that I thought was the lost one (based on the size) but alas - everything is now dead. 
I'm starting from scratch; good i have archive of my stuff. 
thanks for your support yancek.

---

