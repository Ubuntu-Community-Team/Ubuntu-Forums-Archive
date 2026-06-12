---
title: "Sharing Server Virtualization Knowledge"
date: 2011-07-22
forum: Server Platforms
---

### Post by collisionystm on 2011-07-22
Just wanted to share with everyone that I successfully converted a running Server 2003 R2 terminal server virtual last night.

It is running on 10.04 in Virtualbox, and it runs like a dream.

I used disk2vhd to copy the C: Drive to a usb drive.
[http://technet.microsoft.com/en-us/sysinternals/ee656415](http://technet.microsoft.com/en-us/sysinternals/ee656415)

Once I had this image, I fired up Virtualbox 4.1 and coverted the VHD to a VDI. The drive was listed as being 12gb in size but the VDI said it was 150gb.

To fix this I booted the virtual Server 2003 with a Windows 7 Disk and expanded the partition.

Then booted back into Windows and had all 150gb to use.

I then created my additional partitions that the physical box had and copied over the files.

It works great. Just be prepared to activate windows again. I had to call the activation line. It took 10 minutes.

Anyways, Just thought I would share.

Windows Server was originally running on a Dell Poweredge. Now its living happily in VBOX =)

---

