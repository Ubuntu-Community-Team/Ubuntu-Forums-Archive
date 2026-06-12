---
title: "How to install Ubuntu on encrypted partitions without LVM and RAID?"
date: 2014-06-01
forum: Security
---

### Post by abcuser on 2014-06-01
Hi,
I got a new PC and I would like to install Ubuntu 14.04 Server (minimal install) and inside it only tiny windows desktop environment like IceWM to consume as little CPU and RAM as possible and VirtualBox as virtualization. Inside VirtualBox I am going to create a single Windows 7 virtual guest. I would like to have VirtualBox so I can create snapshots and/or clone of virtual machine.

I would like to encrypt disk partitions, but because this is not a server (actually it is desktop for using virtual guest) I don't want to create a LVM and RAID (I don't have a need and the knowledge to do this - also no disks for RAID - I have one 250 GB SSD disk and one 1 TB hard disk).

I have been reading an article: How to install Ubuntu 14.04 on encrypted MBR partitions [http://www.linuxbsdos.com/2014/05/28/how-to-install-ubuntu-14-04-on-encrypted-mbr-partitions/](http://www.linuxbsdos.com/2014/05/28/how-to-install-ubuntu-14-04-on-encrypted-mbr-partitions/) but the article is for Ubuntu Desktop, but I need some instructions for Ubuntu Server.

So far I have manage to create:
1. Boot partition with mount point /boot and file system ext4.
2. Root partition with "physical volume for encryption".
3. Swat partition with "physical volume for encryption".

Now I am stuck. For steps 2) I should define mount point "/" and define file system ext4 and for step 3) I should define the file system as "swap area". How to do this? Is there some step-by-step tutorial for this?
Thanks

---

