---
title: "Is there something better than &quot;dd&quot;? (dd vs. &quot;?&quot; vs. Macrium)"
date: 2017-07-13
forum: Ubuntu, Linux and OS Chat
---

### Post by MetalMusicAddict on 2017-07-13
So professionally I use [Macrium]("https://www.macrium.com/") to copy and reimage hard drives. The 250GB drives usually take ~9mins to reimage. I wondered if I could come up with a better linux-based solution. I'm tinkering w/dd but its 3x slower. I'm figuring it is copying every bit of freespace where Macrium is not.

Here's my current line in my script:
```
exec sshpass -p pass ssh user@192.168.5.100 dd if=/media/IMAGES/DEFAULT_IMAGE.img.gz bs=1M iflag=direct | gunzip -1 - | pv -s 238G | sudo dd of=/dev/sda bs=1M oflag=direct
```

I'm looking for better "dd" options or an alternative that I can still use the same way.

Thanx.

---

### Post by TheFu on 2017-07-13
I've never used any commercial tool.

There are lots of options, depending on the required use.  Some tools understand the underlying file system and those will be much more efficient.

dd is a brute-force, byte-for-byte copy. There are great things about that, but high performance isn't one.  It also fails badly if there are any errors.  ddrescue/gddrescue handle errors better, which could be important during data cloning from failing HDDs.

For cloning disks, there are many more efficient tools.  **Clonezilla**, **partimage**, **fsarchiver** (can't remember the exact name).  Most of these deal with compressed archives.  Think ZFS has some magic too.  There are other tools as well.

Your script had overhead due to ssh, gunzip and pipes.  Networking, CPU, RAM will impact the results.

But all of this depends on the underlying file systems used.

I don't clone disks all that often - perhaps 3 times a year, so I won't pretend to see why anything faster than 8min is needed.  Most of the disks I clone onto are directly connected and the 10G for the OS takes just 1-2 minutes.  All the data gets replicated using normal restore methods from backups - which are effectively rsync commands (actually rdiff-backup, but it is almost the same).

---

### Post by MetalMusicAddict on 2017-07-14
So really I gotta find a faster method to "dd" that works over SSH and gzip (or whatever).

I'm seeing a few places that say ddrescue doesnt work over SSH. :-k

---

### Post by TheFu on 2017-07-14
PXE boot and use clonezilla.

---

### Post by sudodus on 2017-07-14
I would recommend Clonezilla too. It recognizes the file system and can tell the difference between data blocks that are used for files and metadata, and free blocks, and it copies only data blocks that are used. Clonezilla has built-in support for ssh (I often create a clonezilla image on a server via ssh). I download a Clonezilla 'stable' iso file and create a CD boot disk and a USB boot drive to boot the computer (from one of those drives depending on the computer).

---

### Post by TheFu on 2017-07-14
There are other methods commonly used in enterprises - PXE boot and cobbler to perform the bare metal installs. [https://help.ubuntu.com/community/Cobbler](https://help.ubuntu.com/community/Cobbler)  attended a talk about it. Wasn't something I could use at the time.

---

### Post by marseille2 on 2017-07-15
I gave up on cloning software from a lack patience, and bought a [Sabrent dual bay hard drive docking station]("https://www.sabrent.com/product/EC-HDD2/usb-3-0-sata-dual-bay-external-hard-drive-docking-station-2-5-3-5in-hdd-ssd-hard-drive-duplicatorcloner-function/") (very cheap btw). I popped in the old drive on one side, a new on the other, clicked a button, and waited maybe half an hour or so... then popped in the new drive into the PC and fired it up. I was shocked. It was like zero effort for maybe $25.00.

---

### Post by TheFu on 2017-07-15
> **marseille2 said:**
> I gave up on cloning software from a lack patience, and bought a [Sabrent dual bay hard drive docking station]("https://www.sabrent.com/product/EC-HDD2/usb-3-0-sata-dual-bay-external-hard-drive-docking-station-2-5-3-5in-hdd-ssd-hard-drive-duplicatorcloner-function/") (very cheap btw). I popped in the old drive on one side, a new on the other, clicked a button, and waited maybe half an hour or so... then popped in the new drive into the PC and fired it up. I was shocked. It was like zero effort for maybe $25.00.

Your requirements are completely different from the OPs.  His include network-based cloning which is very different.  BTW, I've owned a Sabrent USB3 dock device before. It died after about a year.

---

### Post by The Cog on 2017-07-15
Looking at your original post, I get the impression that the image source is a file, already gzipped. I would be tempted to try using cat instead of that first dd, just to see if that helps (not sure why you would want to use dd to read a file). 
I would probably have used zcat instead of "gunzip -1 -". Also, the -1 is pointless as that is only used during compression, you can't control the speed of decompressing something that's already been compressed.
It might be worth trying to omit the pv step just in case pv is the bottleneck.

---

### Post by MetalMusicAddict on 2017-07-17
> **The Cog said:**
> Looking at your original post, I get the impression that the image source is a file, already gzipped. I would be tempted to try using cat instead of that first dd, just to see if that helps (not sure why you would want to use dd to read a file). 
I would probably have used zcat instead of "gunzip -1 -". Also, the -1 is pointless as that is only used during compression, you can't control the speed of decompressing something that's already been compressed.
It might be worth trying to omit the pv step just in case pv is the bottleneck.

Correct. I already have the zipped images. I can always change it up though. Ill look at **cat** and yeah, the "-1" was a typo I left in the script. I just use **pv** for some visual output. Do you (or anyone) have a better suggestion to try? Even if I stick with **dd**, suggestions for better options to add (like iflag=fullblock i just found) would be cool. I'm speed testing with no **pv** now.

Ultimately, I'd like a solution i can drop in my script as Clonezilla is a big PITA to set up. :)

Thanx for the brainstorming so far.

---

