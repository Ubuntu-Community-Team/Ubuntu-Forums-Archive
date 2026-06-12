---
title: "problem with ubuntu server"
date: 2010-07-13
forum: Server Platforms
---

### Post by jason.rgd on 2010-07-13
Recently, I got a new job at a small business company. My employers want to shift to linux and are interested after my recommendation to use the ubuntu server... I downloaded it today and tried installing ... but I was unsuccessful. I was given a very old system for testing the ubuntu server platform!! ... It booted up and all installtion procedure till formatting the hdd went on well... formatting the hdd had a problem..  it just woiuldn't format the hard disk whatever I did and I would get the error that ext4fs file system couldn't be mounted ... I switched to ext3fs and ext2fs too... on switching to ext2fs the formatting percentage would go upto 100% which was not happening in case of the other file system...  I tried installing windows xp and the disk got formatted and also xp installed but I wanna convert that maching to linux somehow and I need community help so I can spread linux in yet another office environment... used the Gparted tool... the gparted tool says that there is no  partition table on the disk and it won't allow me to create one too.

I have formatted many hard disks before and I also have installed ubuntu 10.04 lts on laptops and on desktop hardware... I'm a intermediate linux user.. but this hard disk won't allow me to do it.. its a 20.4 gb atasv2044d samsung hard disk.... can you'll help me further on this issue..

---

### Post by garfonzo on 2010-07-13
What I would try is booting from a live Ubuntu desktop CD and, from within there format the hard drives via the command line. Open a terminal and try formatting from there. 

partition the disk:
```
 fdisk /dev/<name of drive> 
```
Then format the partition:
```
mkfs -V -t ext4 -v /dev/<name of drive>1
```

The "1" is partition 1. I had three hard drives that I wanted only one partition on each disc (big data disks) so I only had one partition number "1". For you, you could start by formatting with one partition, then when that is successful try reinstalling the OS and re-create the partition table. 

The other option is re-downloading and re-burning the install disc. Perhaps it's faulty? When burning put the burn speed to low, like 4X or 10X. I've found that doing so helps avoid some errors. 

Hope this helps.

---

### Post by drdos2006 on 2010-07-13
Try as garfonzo states. It may be a faulty ISO.

My experience.....
Finally got the Western Digital 40 Gig Raptor drive to be able to accept Ubunutu OS.
It is a long story.
Ubuntu could not see the drive when I tried to install Ubuntu.
Booting from Live CD and using gParted could see the drive and partition OK. 
Reformatted to NTFS and tried re-installing Ubuntu. Still could not see the drive.

Tried 64 bit and 32 bit Ubuntu. No good. Installed Fedora 8 32 bit OK, tried re-installing Ubuntu, no good, still could not see the drive.
Installed Windows 7 64 bit OK, tried installing Ubuntu, no good, still could not see the drive.
Installed OpenSuse 32bit, now when it came to partitioning I could see that there was RAID partitions on the drive. 
All of the OS, Windows, Fedora that I tried could not see the RAID info, only OpenSuse. 
Deleted the RAID info under OpenSuse and installed Ubuntu 64bit on the 
Raptor.............

---

### Post by jason.rgd on 2010-07-14
thanks guys... for everything ... my problem is fixed... there was a problem with the RAM modules... but I just couldn't figure that out untill the RAM konked off.... This thread can be closed !!!

---

### Post by arrrghhh on 2010-07-14
> **jason.rgd said:**
> thanks guys... for everything ... my problem is fixed... there was a problem with the RAM modules... but I just couldn't figure that out untill the RAM konked off.... This thread can be closed !!!

I don't know if threads really close 'round here.  Maybe if they get out of hand...

At any rate, please mark the thread [SOLVED] by using the thread tools drop-down!

---

### Post by amaterasher on 2010-07-14
yeah!

---

