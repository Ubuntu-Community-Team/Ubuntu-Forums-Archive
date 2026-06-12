---
title: "Software RAID5 on Ubuntu 8.04"
date: 2009-12-17
forum: Server Platforms
---

### Post by rputnins on 2009-12-17
Hello everyone!

I have found recently a problem - I need to install Ubuntu 8.04 server on software RAID5.

I have FSC Primergy C150 server with 4x74Gb scsi hardrives. I Managed to install Ubuntu 9.10 server using 3 drives in software RAID 5 but the server was unstable, it was crashing. I think it's not hardware problem as I have run Memtest and PC Check to test the cpu, memory and motherboard and no errors reported. I reinstalled the 9.10 several times but it kept crashing at various stages.

So I went back to 8.04 version. During the installation I choose manual disk partitioning, create primary partitions on all 3 drives (72.8Gb) and leave the rest (~700mb) on each drive for swap. I make them raid hardrives, then assign to raid 5, the create new raid and do the same with swap. For / partitions I select bootable flag, save raid info and continue installation. The installation itself goes ubnormaly slow, the copying of packages is very slow (on 9.10 was fast). After the install process I reboot the server and get error:

GRUB loading.
erro: biosdisk read error
erro: file not found
grub rescue>

I think there must be way of installing Ubuntu 8.04 on software raid5. Any ideas? Install grub2 on 8.04?

Thanks! Any ideas are more than welcome!
Rauls

---

### Post by Noah0504 on 2009-12-17
I had a similar problem installing 9.10 on a RAID 5 setup.  Essentially, what I had to do what manually install GRUB from the Ubuntu installer by pointing it to the first hard drive (sda).  After this, it should boot.  From the research I did, you may have to finish by installing GRUB on each of the other hard drives, so it knows what to do if you lose the primary drive due to failure.

I hope that made some sense.  Other than that, I used to have a setup with 8.10 and 9.04 that involved my partition scheme to be set up like follows.  4 256MB partitions, one on each of my four HDDs that was setup for RAID 1.  This was set to be /boot.  Then 4 partitions consuming the rest of the space, set up for RAID 5 and LVM or just /.  When GRUB installs, the idea is that it installs to the RAID 1 setup.

---

### Post by rputnins on 2009-12-17
The case is solved!

This howto helped solving the problem:

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

for RAID5 on Ubuntu 8.04 you need to make following changes (use the above howto as base):

after partitioning the drives (only 3 in my case) I create Raid5:

```
mdadm -v --create /dev/md0 --level=raid5 --raid-devices=3 /dev/sda2 /dev/sdb1 /dev/sdc1
```Then create file system, I used ext3:

```
mkfs.ext3 /dev/md0
```Wait for the RAID to rebuild, you can monitor this using:

```
watch cat /proc/mdstat
```After RAID is rebuilt, reboot the live cd, boot into server install cd, install and during the disk partition part use this advice from maxbash:

> Run the installer, when you are in the partitioner choose manual and be careful not to modify the partition layout. For the /dev/sda1 partition choose ext3 as the file system and set /boot on.
   Set your swap partitions to be used as swap.
  You select the type of file system you already formatted the RAID device and set the mount point. Do not choose to reformat or make partition table changes to the RAID array, because the partitioner will misconfigure it.
   Click continue on the warning about the RAID not being marked for formatting.
And that's it! For server no need to anything else. It's working for me! Finally! :-\"

---

