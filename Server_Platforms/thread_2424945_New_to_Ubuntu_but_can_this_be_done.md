---
title: "New to Ubuntu but can this be done?"
date: 2019-08-17
forum: Server Platforms
---

### Post by majortd-001 on 2019-08-17
Hello all,

Seems like Youtube has been throwing a lot of Ubuntu videos at me recently so I thought I would sign up and hopefully learn a few things.

Coming from a Windows and macOS user background, I'm looking to migrate some of my existing home servers from Windows and FreeBSD systems over to Linux altogether. Sadly not everything can be move over, but the majority I would like to. 

As it stands I have various setups running Raid 5 and Raid 1, but with how my servers are setup, what I'm looking at doing (as a new setup for my house) is having a dedicated boot drive and a pair of hdd's in a raid 1 array for each server. Boot drive for the main OS itself and the Raid 1 array for data storage. Easy to setup in Windows, but how much of a task would this be within Ubuntu? Please bare in mind that I've not used this before, and the reason behind going for Ubuntu as this is the most popular OS, distro (still learning here, be kind lol) so help and assistance would be easily available? Plus I just want to move away from Windows altogether running my home. Updates, yeah, let's not go there! lol

I understand that it's possible to run everything I wish to run on a single server, but personally I don't like to have all of my eggs in one basket so have always split my install and network up in case fallovers etc. 

I'm sure a question like this has been asked before so if there is a link either on this forum or on the web itself, it would be greatly appreciated if a link could be shared.


Cheers,
Tom

---

### Post by Frogs Hair on 2019-08-18
Moved to* Server Platforms*.

---

### Post by TheFu on 2019-08-18
Setting up RAID is much easier using CentOS than Ubuntu at install time.
If you want RAID only for data, not the boot or OS stuff, then it isn't too hard.  I'd suggest that you use LVM+RAID (which LVM handles) to get the enterprise storage features of LVM.  Or since you use BSD, you might want to consider using ZFS.  All the LVM/RAID/ZFS stuff is command line. No point-n-click.  LVM is pretty much like any commercial volume manager out there. PVs, VGs, and LVs.

There's this new thing called a hypervisor.  They work really well to segment different, unrelated, services into different VMs.  It is especially handy when the risk factors for 1 service is much higher than for any other service.  IMHO, using VMs is much easier and less risky than having lots of physical machines when CPU needed is tiny for most services.  You can place all the VM storage on the RAID disks easily. The guest OS doesn't know anything about the RAID, but still gets protected by the hostOS RAID.  With LVM, you can provide RAID'd block storage to the guest and have 100% complete backups safely outside the guestOS using LVM snapshots,  LVM provides enterprise storage capabilities, when you need it, but can be ignored most of the time.  [https://www.howtoforge.com/set-up-raid1-on-a-running-lvm-system-debian-etch](https://www.howtoforge.com/set-up-raid1-on-a-running-lvm-system-debian-etch) - LVM and RAID setup are pretty much identical across all Linux OSes from the shell.

---

### Post by SeijiSensei on 2019-08-19
Linux names drives as /dev/sda, /dev/sdb, /dev/sdc, etc., with the partitions on each device numbered from 1 to N.  Suppose your machine has the operating system installed on /dev/sda1, and you want to use all the space on /dev/sdb and /dev/sdc as RAID1 storage.  I use the venerable "fdisk" for Linux to create a single partition on each of the RAID devices.  I mark these partitions as "Linux RAID" using the (t)ype command and setting the partition identifier to "fd".  This tells the operating system that the devices are part of an array during boot and constructs the RAID array at that time.

Next I run the command
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

That creates the RAID1 array using sdb1 and sdc1 and assigns it the name /dev/md0.

mdadm isn't included as part of the normal desktop installation, but you can add it by running
```
sudo apt update && sudo apt install mdadm
```

Finally I format the array as ext4 with

```
sudo mkfs -t ext4 /dev/md0
```

Then all that's left is defining where to mount the array in the filesystem.  I created /media/raid for this purpose by running "sudo mkdir /media/raid", then editing the file /etc/fstab as root with sudo ("sudo nano /etc/fstab") and adding the line

```

/dev/md0     /media/raid     ext4     defaults     0 0 

```

(Actually I use the UUID for the array, a long identifier that you can see by running "sudo blkid".  So instead of /dev/md0, I have UUID=ff2902fb-c4bc-41a4-bd94-72bedf5eec32.  But either method works.)

---

### Post by majortd-001 on 2019-08-20
Apologies for the late reply back. 


> **TheFu said:**
> Setting up RAID is much easier using CentOS than Ubuntu at install time.
If you want RAID only for data, not the boot or OS stuff, then it isn't too hard.  I'd suggest that you use LVM+RAID (which LVM handles) to get the enterprise storage features of LVM.  Or since you use BSD, you might want to consider using ZFS.  All the LVM/RAID/ZFS stuff is command line. No point-n-click.  LVM is pretty much like any commercial volume manager out there. PVs, VGs, and LVs.

There's this new thing called a hypervisor.  They work really well to segment different, unrelated, services into different VMs.  It is especially handy when the risk factors for 1 service is much higher than for any other service.  IMHO, using VMs is much easier and less risky than having lots of physical machines when CPU needed is tiny for most services.  You can place all the VM storage on the RAID disks easily. The guest OS doesn't know anything about the RAID, but still gets protected by the hostOS RAID.  With LVM, you can provide RAID'd block storage to the guest and have 100% complete backups safely outside the guestOS using LVM snapshots,  LVM provides enterprise storage capabilities, when you need it, but can be ignored most of the time.  [https://www.howtoforge.com/set-up-raid1-on-a-running-lvm-system-debian-etch](https://www.howtoforge.com/set-up-raid1-on-a-running-lvm-system-debian-etch) - LVM and RAID setup are pretty much identical across all Linux OSes from the shell.

Thanks for the reply. Will have to have a look at ZFS. Memory hungry so might need up buy some more, not a problem though.

Interesting about the hypervisor. Will have to have a look at that in more detail. Thanks for that :)


> **SeijiSensei said:**
> Linux names drives as /dev/sda, /dev/sdb, /dev/sdc, etc., with the partitions on each device numbered from 1 to N.  Suppose your machine has the operating system installed on /dev/sda1, and you want to use all the space on /dev/sdb and /dev/sdc as RAID1 storage.  I use the venerable "fdisk" for Linux to create a single partition on each of the RAID devices.  I mark these partitions as "Linux RAID" using the (t)ype command and setting the partition identifier to "fd".  This tells the operating system that the devices are part of an array during boot and constructs the RAID array at that time.

Next I run the command
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

That creates the RAID1 array using sdb1 and sdc1 and assigns it the name /dev/md0.

mdadm isn't included as part of the normal desktop installation, but you can add it by running
```
sudo apt update && sudo apt install mdadm
```

Finally I format the array as ext4 with

```
sudo mkfs -t ext4 /dev/md0
```

Then all that's left is defining where to mount the array in the filesystem.  I created /media/raid for this purpose by running "sudo mkdir /media/raid", then editing the file /etc/fstab as root with sudo ("sudo nano /etc/fstab") and adding the line

```

/dev/md0     /media/raid     ext4     defaults     0 0 

```

(Actually I use the UUID for the array, a long identifier that you can see by running "sudo blkid".  So instead of /dev/md0, I have UUID=ff2902fb-c4bc-41a4-bd94-72bedf5eec32.  But either method works.)

Many thanks for the reply. Will be having a look what you've written also. The Ubuntu install is sitting there ready so I can go through this and see what comes of it. 



Another possible route I guess is to setup 1x server running ubuntu with all of the programs required on as a raid array. Then have a separate server running ZFS to house everything else (automation, media, cloud etc) as another raid array. I guess with that I can down on the gear I need while still being protected (to a point as always). Should save on the electricity bill as well as well as keeping my server room cooler.

---

### Post by TheFu on 2019-08-20
ZFS is only a memory hog if you use advanced capabilities.  Normal stuff isn't bad.  

Hypervisors have been production ready on Linux since at least 2008.  
 
There are lots of considerations. You're probably expert enough not to need any advice.

---

### Post by majortd-001 on 2019-08-23
> **TheFu said:**
> ZFS is only a memory hog if you use advanced capabilities.  Normal stuff isn't bad.  

Hypervisors have been production ready on Linux since at least 2008.  
 
There are lots of considerations. You're probably expert enough not to need any advice.

Fair play. I was more on about how much is required per TB of disk space. 

There are lots of options to try which I'll be trying out over the next week as I plan to set everything up in a few weeks time. 

Ohh I'm no expert, far far from it lol

---

### Post by TheFu on 2019-08-23
> **majortd-001 said:**
> Fair play. I was more on about how much is required per TB of disk space. 

Those RAM estimates are only if you need the advanced stuff like deduplication or the best possible performance through heavy caching.

---

