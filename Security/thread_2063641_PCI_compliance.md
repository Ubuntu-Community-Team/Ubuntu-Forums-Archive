---
title: "PCI compliance"
date: 2012-09-27
forum: Security
---

### Post by Neil948 on 2012-09-27
I have been running some software on my ubuntu server and have managed to resolve that many issues in a bid to get pci compliance up and running that i seem to have got brain freeze. :lolflag:  
I have come accross this issue:-

> Check /tmp is mounted as a filesystem** WARNING **/tmp should be mounted as a separate filesystem with the noexec,nosuid options setand i just can't see how to resolve it i have a secondary drive newly installed however it is not mounted at the min so if i can move /tmp there that would be advantageous as an extra security messure.

this is a live server so want to avoid as much down time as possible.

anyone know how to do this?

---

### Post by ooVoh9em on 2012-09-27
> **Neil948 said:**
> I have been running some software on my ubuntu server and have managed to resolve that many issues in a bid to get pci compliance up and running that i seem to have got brain freeze. :lolflag:  
I have come accross this issue:-

and i just can't see how to resolve it i have a secondary drive newly installed however it is not mounted at the min so if i can move /tmp there that would be advantageous as an extra security messure.

this is a live server so want to avoid as much down time as possible.

anyone know how to do this?

Notice: For this entire post, I assume /dev/sda3 is your new drives partition. If you don't know the location of your new drive or its partitions, you can use fdisk to figure it out:

```
 sudo fdisk -l 
```

First of all, you need to prepare the new drive. This is a pretty simple task, and you can easily do it if you follow this guide: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

If you have already finished the partitioning of the drive, you can easily format the partition with a simple command:

```
 sudo mkfs -t ext3 /dev/sda3 
```

Secondly, you will need to modify your fstab to reflect the changes you wish to make. 

```
 sudo nano /etc/fstab
```

Replace your current fstab entry for /tmp with something like the following example:

```

[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]
/dev/sda3    /tmp            ext3      noexec,nosuid  0       2
```

That will set the /tmp mount point to reflect /dev/sda3, assumes you're using the ext3 filesystem, and mounts with the options of noexec and nosuid. You simply modify this example based on what filesystem you're actually using, and other arguments that might be specific to your situation. 

Also, if you're happy with where /tmp is currently living and decide not to use the second drive for this purpose, you can just replace the defaults keyword under options to noexec,nosuid to achieve the same effect without using your new drive to house the /tmp partition.

The next time you mount the filesystem, it will be using those options. You could easily do this by issuing a remount command, and avoid having to reboot the server.

```
sudo mount -o remount /tmp
```

That should remount /tmp using /dev/sda3 as its new location, and it will be using the noexec and nosuid options that you need. If it does not remount /tmp then you can use the following command to help you diagnose the problem:

```
 sudo cat /proc/mounts
```

For more information: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Neil948 on 2012-09-27
> **troopa said:**
> Notice: For this entire post, I assume /dev/sda3 is your new drives partition. If you don't know the location of your new drive or its partitions, you can use fdisk to figure it out:

```
 sudo fdisk -l 
```First of all, you need to prepare the new drive. This is a pretty simple task, and you can easily do it if you follow this guide: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

If you have already finished the partitioning of the drive, you can easily format the partition with a simple command:

```
 sudo mkfs -t ext3 /dev/sda3 
```Secondly, you will need to modify your fstab to reflect the changes you wish to make. 

```
 sudo nano /etc/fstab
```Replace your current fstab entry for /tmp with something like the following example:

```

[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]
/dev/sda3    /tmp            ext3      noexec,nosuid  0       2
```That will set the /tmp mount point to reflect /dev/sda3, assumes you're using the ext3 filesystem, and mounts with the options of noexec and nosuid. You simply modify this example based on what filesystem you're actually using, and other arguments that might be specific to your situation. 

Also, if you're happy with where /tmp is currently living and decide not to use the second drive for this purpose, you can just replace the defaults keyword under options to noexec,nosuid to achieve the same effect without using your new drive to house the /tmp partition.

The next time you mount the filesystem, it will be using those options. You could easily do this by issuing a remount command, and avoid having to reboot the server.

```
sudo mount -o remount /tmp
```That should remount /tmp using /dev/sda3 as its new location, and it will be using the noexec and nosuid options that you need. If it does not remount /tmp then you can use the following command to help you diagnose the problem:

```
 sudo cat /proc/mounts
```For more information: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


Thank you worked a treat very easy to understand:KS

---

### Post by ooVoh9em on 2012-09-27
> **Neil948 said:**
> Thank you worked a treat very easy to understand:KS

No problem. Happy to help. Please mark this thread as SOLVED when you have a moment.

---

