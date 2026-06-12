---
title: "File corruption when copying files over a network"
date: 2009-11-28
forum: Server Platforms
---

### Post by sturreal on 2009-11-28
I'm having a few problems with file corruption when copying from a backup over my home network to my server. The files on the backup are fine, however once I've copied them across, I'm finding that some of my videos are corrupted as is some of my music it appears to be larger files which have the problem.

My server is an intel atom machine with a pair of 500Gb discs in software raid on an EXT3 file system on Ubuntu 9.04

I'm not sure what to do at this point, I don't know the full scale of file corruption problem is there any way to do a mass file comparison to see which ones are different from their originals and so corrupt. Also what might be causing this? I can only guess it must be something to do with the raid set.

---

### Post by Denbert on 2009-11-29
> **sturreal said:**
> I'm having a few problems with file corruption when copying from a backup over my home network to my server. The files on the backup are fine, however once I've copied them across

Are you using SSH, SAMBA or FTP to transfer the files?

---

### Post by sturreal on 2009-12-01
I've tried samba and NFS both result in corrupt files. Its the files themselves that are corrupt the filesystem is fine according to fsck. 

I did later discover that I had some bad memory so I assumed that was the problem and swapped some that I know to be good and I restored my backup once again and this time i've MD5 hashed every file i'm copying and every single file above 1mb in size has failed its hash test, here are the results

WARNING: 17267 of 18837 computed checksums did NOT match

Here are the specs of the computer in question

Intel Atom 330 (Intel D945GCLF2)
1Gb DDR2 (this is ram from my desktop which is known to be good)
2x 500Gb Western Digital drives in linux software raid1 connected to (SiI 3512 raid card)
80gb western digital running as /var /home and swap
80gb Samsung drive as a backup drive

---

### Post by Denbert on 2009-12-01
> **sturreal said:**
> 
1Gb DDR2 (this is ram from my desktop which is known to be good)


try to run a memtest from a bootable Ubuntu CD

---

### Post by Vegan on 2009-12-01
I suspect you may have bad cabling. If the machine is OK, the NICs and the cable need to be cheeked to see what is the problem.

Cables are cheap, if the NIC is bad, on a notebook, you would need an external dongle, on a server, swapping the NIC is easier.

---

