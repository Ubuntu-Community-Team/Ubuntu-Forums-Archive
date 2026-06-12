---
title: "HELP--No Boot Loader!"
date: 2011-06-30
forum: Ubuntu Studio
---

### Post by anachronon on 2011-06-30
HELP!  I tried to do a fresh install on Ubuntu Studio.  But, I got as far as the disk partitioning, and it gave me no way to format the existing Linux partition (I needed to gor from ext3 to ext 4).  I ended up having to abort the procedure.

But, now, I have no boot loader, and I can't even check to see if my Windows partition is still good.  I have almost everything backed-up.  But, I am still seriously panicking.

---

### Post by drs305 on 2011-06-30
Please boot the LiveCD and download/extract and run the boot info script. Post the contents of the RESULTS.txt it generates.

This file will show us the status of your boot files and give us a good idea of how to proceed.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by anachronon on 2011-06-30
> **drs305 said:**
> Please boot the LiveCD and download/extract and run the boot info script. Post the contents of the RESULTS.txt it generates.

This file will show us the status of your boot files and give us a good idea of how to proceed.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
I already know what's wrong.  The grub loader was completely overwritten.  There simply are no boot instructions.  The Linux partition was completely erased.  I need to know if Widows is still functional.

---

### Post by drs305 on 2011-06-30
> **anachronon said:**
> I already know what's wrong.  The grub loader was completely overwritten.  There simply are no boot instructions.  The Linux partition was completely erased.  I need to know if Widows is still functional.

You can try to point the MBR back to Windows with the following (it assumes Windows flag is on the Windows partition and that the bootloader is on sda - change as necessary):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
This will partially install enough of lilo to get the MBR pointing to sda. Don't run the other commands lilo will say are necessary to fully install it.

---

### Post by anachronon on 2011-06-30
> **drs305 said:**
> You can try to point the MBR back to Windows with the following (it assumes Windows flag is on the Windows partition and that the bootloader is on sda - change as necessary):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
This will partially install enough of lilo to get the MBR pointing to sda. Don't run the other commands lilo will say are necessary to fully install it.
could not properly install lilo.  Using live CD--no access to HD for storage.  Tried running command--"command not found"

---

### Post by drs305 on 2011-06-30
Even from the LiveCD you should be able to install lilo. As far as I know lilo installs nothing on the drive during its own installation. The second command should only write to the MBR and look for the boot flag on a partition.

From the LiveCD, if you run "sudo fdisk -l" (Lowercase L) does it show your partitions.

You can try to mount your Windows partition for inspection with:
```
sudo mount /dev/sd**XY** /mnt
gksu nautilus /mnt
```
Change the **XY** to the partition you wish to explore (e.g. sda1). It should mount an ntfs partition without specifying the partition type.

---

### Post by anachronon on 2011-06-30
> **drs305 said:**
> Even from the LiveCD you should be able to install lilo. As far as I know lilo installs nothing on the drive during its own installation. The second command should only write to the MBR and look for the boot flag on a partition.

From the LiveCD, if you run "sudo fdisk -l" (Lowercase L) does it show your partitions.

You can try to mount your Windows partition for inspection with:
```
sudo mount /dev/sd**XY** /mnt
gksu nautilus /mnt
```
Change the **XY** to the partition you wish to explore (e.g. sda1). It should mount an ntfs partition without specifying the partition type.
I already mounted the drive (windows partition) manually, and checked it.  Everything appears to be there, and the file system seems undamaged.  I just can't boot, or install anything.  Also, my live CD is way out of date.

---

### Post by anachronon on 2011-06-30
One disturbing thing though--Nautilus can't find the old Linux partition.

---

### Post by drs305 on 2011-06-30
I don't know why lilo wouldn't install unless it isn't in the hardy repositories for some reason or you have a bad disc. (Just to repeat, you only run the install command, and not the liloconfig command.) 

Here is a direct link for the lilo package, although I don't know if the hardy livecd has the dependencies (I would expect it does).
[http://packages.ubuntu.com/hardy/lilo]("http://packages.ubuntu.com/hardy/lilo")

You could try downloading the deb directly and see if you can install it. If you don't have a Windows CD available to repair the MBR this is the only thing I can think of. 

There was a free download of a Windows repair disk but I believe it's been removed. Perhaps someone can point you to it's location if you can't get lilo to work.

---

### Post by anachronon on 2011-06-30
Please, if you could, try to find where I can get that windows recovery CD.  my windows disk doesn't have a recovery mode.

Plus, on this ubuntu live CD, all attempts to install anything using apt-get have failed.  I'm really pulling my hair out.  I need this fixed ASAP.

Plus, why can't I see my old Linux partition anymore?

---

### Post by drs305 on 2011-06-30
The links I had to the repair disk are no longer valid. You could try searching. For booting, I think I'd go to Super Grub Disk and make a copy to boot into Windows. SGD can also boot Linux, although I don't remember if there is still a version that boots both. The linux version is now called Rescatux, but I'd first use SGD to try to get into Windows.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

For exploring for lost or improperly formatted partitions, take a look at Test Disk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by anachronon on 2011-07-03
> **drs305 said:**
> The links I had to the repair disk are no longer valid. You could try searching. For booting, I think I'd go to Super Grub Disk and make a copy to boot into Windows. SGD can also boot Linux, although I don't remember if there is still a version that boots both. The linux version is now called Rescatux, but I'd first use SGD to try to get into Windows.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

For exploring for lost or improperly formatted partitions, take a look at Test Disk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
Well, after a couple days of studying and trying different combinations of commands, I got the Windoze portion working again, using Super Grub Disk.  Thanks for all your help.  I had to recreate the entire boot sector, as well as reinstall my monitor and video-card drivers.  For some unknown reason, the Linux installer made a real mess.

I didn't need to use Test Disk though.  Once windows was going, it was able to identify all of the partitions, without any problem.

Wonder what I should next.  Should release the Linux and Swap partitions back to Windows, and then have the Linux installer create a whole new partition?  Or, should I just give up trying to get Linux on that machine, as this attempt to upgrade to v10.10 has just been one disaster after another.

---

### Post by drs305 on 2011-07-03
> **anachronon said:**
> Wonder what I should next.  Should release the Linux and Swap partitions back to Windows, and then have the Linux installer create a whole new partition?  Or, should I just give up trying to get Linux on that machine, as this attempt to upgrade to v10.10 has just been one disaster after another.

Glad you got Windows working again.

If you try to install Ubuntu again:

Since you had problems with the Ubuntu installer, you might try working with the partitions you currently have if gparted is happy with them. I'd select manual partitioning during the installation and point the installer to the existing partitions. Just make sure you designate the mount point and tick the box to format them during the install.

---

### Post by anachronon on 2011-07-04
> **drs305 said:**
> Glad you got Windows working again.

If you try to install Ubuntu again:

Since you had problems with the Ubuntu installer, you might try working with the partitions you currently have if gparted is happy with them. I'd select manual partitioning during the installation and point the installer to the existing partitions. Just make sure you designate the mount point and tick the box to format them during the install.
I tried going after the manual install again.  But, as before, the installer could not read the partition table, or find the partitions.  So, I aborted, rather than make the same mistake again.

Windows itself seems to be starting off of a jury-rigged system.  I could not access "Safe Mode" or DOS on boot-up.  I did however, manage to run "Check Disk", and the resulting log showed no physical damage (bad sectors) on the HD.  But, from the way the computer is acting, the boot sector and partition tables appear to be corrupted.

Is there a way to fix this, without having to completely reinstall the OS, as well as all of the programs, drivers, settings, calibrations, etc, etc, etc?

---

### Post by anachronon on 2011-07-05
After more study, it really seems that the best way to tackle this problem, is to return the Linux partition to Windoze, and reformat it to NTFS (basically, get things back to the way they were, before my first installation of Linux).  Then, try installing Linux again, allowing it to create and format a new partition.

Is there any intuitive software that will help me to do that?  Or, could that too easily turn into another disaster?  Any chance that such formatting and reformatting might damage my HD?  Also, there was a 2.5GB "swap" partition (before it was corrupted).  Do I need to keep that?  Or, will a new one be created, once I again go to a duel-boot system?

---

