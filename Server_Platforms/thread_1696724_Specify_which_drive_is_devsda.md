---
title: "Specify which drive is /dev/sda"
date: 2011-02-27
forum: Server Platforms
---

### Post by djfiii on 2011-02-27
Hello,

I have been running Ubuntu Server 10.10 from a 500GB SATA drive. I also have a 1TB SATA drive formatted as ntfs (primarily because it used to be a windows OS drive and I just haven't reformatted it). This has worked fine; the OS boots from the 500GB drive, grub installed to the master boot record, etc. 

On to my problem - I just bought three 2TB drives, plugged them in, fired up the system and the 500GB drive is no longer /dev/sda - one of the 2TB drives is. Is this something I can set in the OS install? Or is it a BIOS issue? Does it even matter? It seems like you should be able to set the bootable flag = yes regardless of /dev/xxx identifier, but I can no longer set the 500GB drive to bootable. Even if I don't create any partitions on the 2TB drives, one of them always gets recognized as /dev/sda, so GRUB installs there, and then the boot fails. 

My motherboard is a Gigabyte GA-MA790GP-DS4H, with six SATA 2.0 ports - labeled 0-5. I had always assumed that there was some correlation between the port number you plugged the drive into, and the /dev/xxx name the drive was assigned. That appears not to be the case. 

Any tips are appreciated.

Thanks!

David

---

### Post by doas777 on 2011-02-27
```
sudo fdisk -l
```shoudl give you the info you need.
if you want to check the mountpoints, run 
```
mount
```this problem is why ubuntu is moving to UUID's for hard disks in the /etc/fstab.
if you Identify your partition by its UUID, it doesn;t matter if your dev names change.
you can list your UUIDs by running
```
ls -l /dev/disk/by-uuid/
```

here is some info on how to use uuids in your fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Vegan on 2011-02-27
If you need drives in a specific layout you will need to identify the proper port numbers on the MB

I have noted that marked ports are not always matching the logical ones

---

### Post by djfiii on 2011-02-27
Thanks all, I got it figured out. I was trying to do it all during installation because of the easy interface to partitioning and lvm, and that is where it was hitting a wall. It kept trying to install the grub boot loader to one of the 2TB disks no matter which motherboard SATA ports the discs were plugged into.

I started over with just the 500GB drive plugged in, got the OS installed, powered down, plugged all of the other drives back in, and I was able to boot in fine this time, of course with none of the other drives configured yet. The 500GB drive is now /dev/sdc but it doesn't seem to matter. I installed lvm2 for the command line and between fdisk and that, was able to create my logical volume that way, modify fstab to create a mount point, and I'm good to go.

Thanks again for the tips.

-David

---

