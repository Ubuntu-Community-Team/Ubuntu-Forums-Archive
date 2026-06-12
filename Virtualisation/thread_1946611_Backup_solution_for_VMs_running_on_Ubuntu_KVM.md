---
title: "Backup solution for VMs running on Ubuntu KVM"
date: 2012-03-25
forum: Virtualisation
---

### Post by ennpeehs on 2012-03-25
Hi, I am new to KVM virtualization on Ubuntu. I have come across a client who is running two Intel servers each having its own RAID 5 and installed with ubuntu 10.0.4 and KVM. Multiple VMs are running on each of the Ubuntu KVM server but so far no proper backup is setup.

Is there any well tested / reliable backup solution available to backup VMs in KVM environment, from one server on to another ? I plan to bring up VMs from another server if the 1st server go down. i.e. Want to use one physical server to backup another with simple disk backup.  

I am open any suggestions on backup solution from either free or commercial providers but preferably using some kind of easy to use GUI or simple interface.

Thanks in advance

ennpee

---

### Post by imachavel on 2012-03-25
not familiar with any vm type program that utilizes kdm, although I've heard a lot about them, that a vm can be used a web interface to utilize kdm run servers. This stuff blows my head up, if I one day know the answer believe me I'll be all over threads like these.

I would suggest manually as the safest way. Or perhaps you can just use Ubuntu backup. I'm not sure if it will work with Ubuntu as a guest, or are you running ubuntu as the host? Well, I don't know how you have all these servers configured, remember that at virtualbox.org or I think it's citrix.com for vmware, you can create an account and ask away about vms used as web servers that can configure kdm controlled servers to back up files. I use the backup program in ubuntu right now, and it backs up all my files constantly. It seems fairly simple to use, that you can select any backup device/location. I disconnected my backup drive a bit ago because when I installed ubuntu, I encrypted the drive, without remembering where to put an encrypted pass key. So everything backed up, which backs up quite well for me, has this painful habit of being encrypted library files, which does nothing for me. Sorry get so off topic, best of luck!

---

### Post by imachavel on 2012-03-25
two intel servers with raid 5 installed? Mind listing the model? Sounds pretty cool, they are blade or towers? dual socket or quad socket mainboards? I think you clarified a bit more then I gave you credit for, you want to back up the entire vdi/vmdk/imageOSfileformat? I think Ubuntu backup works just fine for that, just select the hard drive image format from the vm folder when you select what you want backed up. Obviously if you want to copy the entire host OS you need something like this:

[http://www.ehow.com/how_7184450_copy-ubuntu-another-hard-drive.html](http://www.ehow.com/how_7184450_copy-ubuntu-another-hard-drive.html)

gdrescue, while first typing sudo fdisk -l into the terminal to get your dev/sda or dev/sdb on the correct partition and boot device for the location of where your Host OS is installed

---

### Post by teeks99 on 2012-03-26
KVM Supports [live migration]("http://www.linux-kvm.org/page/Migration"), which may not be exactly what you want, but close.  

If you need this kind of redundancy, you could have the live-migrations of each machine always running on the other host.  That way if your first one goes down the backup will be ready to go in moments, but this would take a lot of resources to keep going.  

If you don't have the resources to do that, the link above mentions a feature about being able to store to a compressed file.  This sounds like the backup functionality you were referring, unfortunately I know nothing about it other than the one bullet point on the page.

My method for backups is just to run a zip tool on the .qcow2 file...then I store those off on another drive.  However, I wouldn't recommend this on a machine that is running at the time, as you could get a corrupted backup of your image.  This isn't a problem for me because I don't usually have long-running machines and can readily stop them to make backups.  However, if you don't store data on the virtual machine image, you could get it all configured how you want it, then make a copy of your image before you put it into production.  This only works if nothing changes on the VM's image while it is running though.

---

### Post by iclebyte on 2012-03-27
We have a similar setup. We have 2 KVM virtulization hosts in 2 different datacenters which do not use Live Migration.

We have a NAS in each datacenter and push backups of the KVM disk image and it's Conviture config to the NAS in the oposite datacenter. The idea being if one DC burns we can import the images and boot them on the remaining physical node.

This script copies them off while they run. When you boot the image from a backup it will run an fsck, not clean but it does work.

Hopefully the below script might help you as a starting point. This is run from cron every 2 days and rotates the backups.


- Jamie

---

### Post by zeljkojagust on 2012-03-29
What is the configuration of KVM? Does it use disk images (files) to run guests or uses LVM's? If it uses LVM's and each partition of guest OS is on a different LVM you can use snapshot feature, and if you use disk images, a good old Live CD boot and creation of dd images will do the work.

---

### Post by ennpeehs on 2012-04-02
> **zeljkojagust said:**
> What is the configuration of KVM? Does it use disk images (files) to run guests or uses LVM's? If it uses LVM's and each partition of guest OS is on a different LVM you can use snapshot feature, and if you use disk images, a good old Live CD boot and creation of dd images will do the work.

We don't have Shared storage / LVM.  VMs are running on top of disk images

---

