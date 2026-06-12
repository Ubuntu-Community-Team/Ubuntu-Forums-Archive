---
title: "ubuntu server to ESXi?"
date: 2013-01-22
forum: Server Platforms
---

### Post by leejewitt on 2013-01-22
Hi am planing on moving my ubuntu server to ESXI but the problem is i don’t know how.
the machine i want to use as the esxi is the ubuntu server itself,  i want to install esxi on usb. 

ubuntu config.

HDD.
1x raid 1 array 
1x OS disk
1x 1tb data
1x 500gb data

thats the problem how do i convert to a vm with all them disks a long with it and still have a data store maybe on the 1tb data disk for other servers

any ideas please

cheers

---

### Post by sandyd on 2013-01-22
> **leejewitt said:**
> Hi am planing on moving my ubuntu server to ESXI but the problem is i don’t know how.
the machine i want to use as the esxi is the ubuntu server itself, [B] i want to install esxi on usb. 
[/B]
ubuntu config.

HDD.
1x raid 1 array 
1x OS disk
1x 1tb data
1x 500gb data

thats the problem how do i convert to a vm with all them disks a long with it and still have a data store maybe on the 1tb data disk for other servers

any ideas please

cheers
Are you installing ESXi on a USB drive?
That would not be a good idea because Flash memory only has a certain number of read/write cycles before it fails.

For migrating Ubuntu to a virtual machine, see [http://anothersysadmin.wordpress.com/2007/07/03/migrating-a-linux-machine-to-a-vmware-host/](http://anothersysadmin.wordpress.com/2007/07/03/migrating-a-linux-machine-to-a-vmware-host/)

---

### Post by spynappels on 2013-01-23
> **sandyd said:**
> Are you installing ESXi on a USB drive?
That would not be a good idea because Flash memory only has a certain number of read/write cycles before it fails.

Actually, installing ESXi on a USB thumb drive works very well indeed, and is the way that many commercial servers with ESX or ESXi pre-installed come. You just need either local storage or DAS/iSCSI to store the VMs on, but running the core ESXi hypervisor from a USB stick is fine.

I've run 2 ESXi hosts at home this way for years and our entire testing lab setup (12 hosts running 60+ VMs) at work is set up this way too.

---

### Post by leejewitt on 2013-01-23
i think it would be simple if there was only 1 disk in server, but just worried how i will covert the other disks and raid array as-well, because am sure last time i tried ESXI it converts all the disks into it own fs before it can use them

---

### Post by leejewitt on 2013-01-23
think i have worked it out but need 3 tb of spare space witch o don't have because that space is it use by physical machine

---

### Post by spynappels on 2013-01-23
Do you need all those disks for a specific reason? What services do you run?

It might be simpler to back-up all data to either the smallest disk available or an external disk and use the rest of the disks to create an ESXi host with local data stores, re-install Ubuntu in a VM and restore the backed up data.

---

### Post by leejewitt on 2013-01-23
the OS runs on a 80gb HDD but the rest are just file server data really the raid array is full nearly 1tb 

but have a spare 500gb and 1 tb drive

---

### Post by leejewitt on 2013-01-23
would it be possible to just install esxi then setup a clean ubuntu vm, leave the data disks in the server still as ext4 fs then some how get the data of them to a vm disk.

slow way to do it but safer in my eyes

---

### Post by Cheesemill on 2013-01-23
> **leejewitt said:**
> the OS runs on a 80gb HDD but the rest are just file server data really the raid array is full nearly 1tb 

but have a spare 500gb and 1 tb drive


Back up the RAID and the OS to your spare 1TB drive (you should already have backups anyway).

Then install ESXi onto your USB setting up the RAID as an empty datastore in the process.

I would then reinstall the Ubuntu Server VM from scratch and configure the required services before moving the data back onto your VM.

---

### Post by leejewitt on 2013-01-23
but how would i then move the data back with the backup drive still in server can u access it with esxi or ssh. or would i have to take it out kook it up to desktop then do a network transfer

---

