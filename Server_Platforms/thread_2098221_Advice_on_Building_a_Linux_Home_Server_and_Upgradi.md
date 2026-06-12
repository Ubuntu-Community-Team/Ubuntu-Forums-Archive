---
title: "Advice on Building a Linux Home Server and Upgrading Hardware in Future"
date: 2012-12-26
forum: Server Platforms
---

### Post by Zythyr on 2012-12-26
I am interested in making a home server. For few weeks I have been doing research on both Windows Server 2012 and Linux Ubuntu Server. 

I am new to Linux/Ubuntu and after last few days of research, I have understood/played around with basics of linux and the command line interface using Virtualbox. 

Before I build my server and start transferring/backing up files onto the server, I have few questions. 

Currently I am planning on installing the server on an old desktop. The BIOS doesn't have UEFI. I have the following hard drives available to use on my desktop: 1x 500GB, 2x 3TB. The desktop has 2x hard drive bays available for use. I can probably make it 3, if I disconnect the optical drive. At the moment only 1x 500GB and 1x 3TB is sufficient for me. 

My concern is building a future proof server, I want to make sure I will be able to upgrade my hardware (enclosure or add more hard  drives). I know right now my desktop is old, and only fits 2 hard drives, but in the future, I might upgrade the desktop/enclosure so I can fit more hard drives and it has UEFI support. 

I am interested in the following: 

[LIST]
[*]Having a software RAID
[*]Setup the server using LVM
[*]Possibly partitioning my 500GB to run regular Windows OS ( rare once in a while personal use) and the other partition to boot/run Ubuntu Server. Use the 3TB hard drive as storage/backup. (Yes, I know if I boot into Windows I will have to shutdown the server...)
[/LIST]
Here are the questions I have: 

[LIST]
[*]Is partitioning the 500GB hard drive for Windows and Ubuntu server possible as I mentioned above?
[*]If I change the hardware, (enclosure), can I just swap the hard drives into the new enclosure without having issues? Will the server boot up automatically with no driver issues?
[*]If I currently decide to use 500GB hard drive and 1x 3TB hard drive will I be able to use the software RAID feature?
[*]If currently I set up the server to boot from 1x 500GB hard drive, and I want to get rid of the 500GB hard drive in the future to make space for more higher capacity hard drives, will this be possible?
[/LIST]

---

### Post by 2F4U on 2012-12-26
> Is partitioning the 500GB hard drive for Windows and Ubuntu server possible as I mentioned above?

Yes, Ubuntu Server is like Ubuntu Desktop and you can run it along with other operating systems. However, due to security concerns with Windows, I wouldn't recommend running both on the same machine.

> If I change the hardware, (enclosure), can I just swap the hard drives  into the new enclosure without having issues? Will the server boot up  automatically with no driver issues?

Ubuntu usually comes with all drivers incorporated, except when you need so called proprietary drivers. If you have such drivers in the old machine but not in the new one, I would recommend to remove the drivers before switching.

> If currently I set up the server to boot from 1x 500GB hard drive, and I  want to get rid of the 500GB hard drive in the future to make space for  more higher capacity hard drives, will this be possible?

If you install the operating system on the 500 GB drive and then replace this same drive, you would have to reinstall the OS on the new drive. This is not different from any other operating system. Of course, it may be possible to use some kind of disk imaging software to move the OS from the old drive to the new one.

---

### Post by Zythyr on 2012-12-26
> **2F4U said:**
> Yes, Ubuntu Server is like Ubuntu Desktop and you can run it along with other operating systems. However, due to security concerns with Windows, I wouldn't recommend running both on the same machine.
What are some security concerns I can run into? 


> **2F4U said:**
>  Ubuntu usually comes with all drivers incorporated, except when you need so called proprietary drivers. If you have such drivers in the old machine but not in the new one, I would recommend to remove the drivers before switching.
How would I know what were the proprietary drivers installed? How would I remove the drivers before transferring the hard drive into the new machine? 

I was thinking of another approach for my server. I was thinking about making my server a Windows 2012 server, however, visualize Ubuntu Server using VirtualBox. This way, I can use the the windows server as a quick way to easily mange all my files and storage, while use the virtual Ubuntu to manage all the features such as media sharing, web server, etc... Does anyone have any suggestions/recommendations/feedback on this approach? 

If I install Windows server, will I easily be able to swap the hard drives into the new machine without having to reinstall Windows server or have issues with drivers? 

> **2F4U said:**
> 
If you install the operating system on the 500 GB drive and then replace this same drive, you would have to reinstall the OS on the new drive. This is not different from any other operating system. Of course, it may be possible to use some kind of disk imaging software to move the OS from the old drive to the new one.
Would this solution you suggested casue any problems if I have multiple partitions on the 500GB hard drive, which include LVM, unallocated, etc?

---

### Post by Zythyr on 2013-01-05
Help please!

---

### Post by spynappels on 2013-01-05
As a general rule, I would recommend against running two servers when what you want can be achieved on a single one, and running a Windows server with Ubuntu on top in a VM seems like possibly doubling the work in terms of securing and maintaining each server.

You need to consider a couple of things when deciding what you want to do in terms of which disk layout you want to use. 

[LIST]
[*]Will you want to use RAID?
[*]What are the chances of making changes to the number of disks or or the chassis/case in the short term? medium term? long term?
[*]Will you replace the 500GB HDD or simply add more?
[/LIST]

I would suggest the following for a Linux server solution:

Install the OS on a small partition (~20GB) on the 500GB HDD, with a further ~50GB partition for /var/log to avoid a runaway log filling the disk and knocking the server over.

The rest of the disk I'd make in to a Physical Volume for LVM, and the first 1TB disk would also become a Physical Volume.

Create a single Volume Group from the Physical Volumes, and in this Volume Group create as many Logical Volumes as you need and of whatever size you need, such as for the /home directory, for a /media directory and whatever other storage directories you may need.

Later when you replace the optical drive with the second 1TB HDD, you can add it to the VG as a PV too and use that space for LVs as required.

Of course, this does not take into account the possibilities of using RAID for data redundancy, or many other possibilities, but it could be a good start.

---

### Post by lykwydchykyn on 2013-01-05
What exactly do want your server to do?  Just host files?

---

