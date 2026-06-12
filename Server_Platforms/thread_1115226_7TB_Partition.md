---
title: "7TB Partition?"
date: 2009-04-03
forum: Server Platforms
---

### Post by oyroy on 2009-04-03
So, I just put in 4 more TB-disks in my controller, so I have a total of 8TB. GParted Live couldnt grow my partition, so I did it the easy way and was just gonna reinstall the server with my new partiotion as I borrowed a couple of 1,5TB disks from a buddy for temporary backup.

Im installing from 8.10 Ubuntuserver 64-bit version, and using 3GB for SWAP, 20GB for / I have approx 7TB left for /home, but with the install it makes it a 3TB partition and 4TB left unused. Ive tried both with ext3, ReiserFS and XFS but neither will make a partition bigger then 3TB. I thought there was no limit (at least not this low) with a 64-bit system.

For testing I booted a OpenSUSE CD, but that one could not partition anything larger then 2TB, and my Gparted Live didnt manage anything bigger then the Ubuntuserver Install CD.

Can anyone give me a clue on how to make my /home fill out my 7TB partition? I rather not keep it in several partitions as its easier with one big ...

---

### Post by anderswestrup on 2009-04-03
Are you using LVM or normal partitions? My guess is that the limit you encounter is at the partition level and not the file system level.

If you use LVM you have to configure large physical extent sizes..

---

### Post by Vegan on 2009-04-03
Interesting, is the disk array have MBR or GPT partition indexing. GPT can support larger disks.

---

### Post by oyroy on 2009-04-03
Regular partitions, not LVM. Just Primary partition and ext3 was my first try. Should I use LVM or extended partition?

From earlier exoerience ubuntuserverinstall uses the GPT system. Is that a problem?

---

### Post by oyroy on 2009-04-04
So, anyone got any tips on how to fix my 7TB partition? What choises? and if it is possible to do from the ubunutuserver installcd, or if I should just install it with the 20GB / and make the 7TB partition from the server?

---

### Post by dtoronto on 2009-04-04
This issue has been addressed in another thread

[http://ubuntuforums.org/showthread.php?t=929616](http://ubuntuforums.org/showthread.php?t=929616)

hope this helps.

---

### Post by oyroy on 2009-04-05
Thanks loads for that link. Didnt find that thread when I was searching. Got it all setup now :)

Usage of /home: 37.8% of 6.25TB

:D

---

### Post by iiiears on 2009-04-05
I found this earlier this morning.
 Helpful?
 
[http://www.linuxquestions.org/questions/linux-server-73/troubleshooting-large-partition-attempt-to-access-beyond-end-of-device-676617/#post3311353](http://www.linuxquestions.org/questions/linux-server-73/troubleshooting-large-partition-attempt-to-access-beyond-end-of-device-676617/#post3311353) "

and this in Launchpad.


" mayerI said on 2009-02-11:

It was my understanding that Ubuntu on non-mac x86_64 by default can't use a GPT partition as the boot/root partition ( A kernel recompile would be needed to enable that feature [CONFIG_EFI_PARTITION?] as well as a patched grub )  "

~Best Wishes

---

### Post by speedkreature on 2009-07-27
This doesn't seem to be working on my 8.04.3 x86-64 server.  
I cannot figure out how to get parted to commit the changes and gparted will not create a GPT label.

In GParted, I select New and it prompts me with the Set Disklabel window where I drop down the Advanced menu, select gpt, then click Create, then Create again (on the next window).  After the amount of time it takes to read all the partitions on this server, I am presented with the same window as before.  Selecting new on the 7.5TB "disk" brings up the Set Disklabel window.

I've got a Promise VTrak E310F/s on an ATTO Celerity FC-42ES Fibre Channel HBA.  The array appears as a single 7.5TB disk.

I've considered (and would prefer) using lvm2, but I'll still need to be able to write a GPT label to the array first, won't I?

---

