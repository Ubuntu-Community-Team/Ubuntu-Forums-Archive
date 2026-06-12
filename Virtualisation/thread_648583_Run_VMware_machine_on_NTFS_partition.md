---
title: "Run VMware machine on NTFS partition"
date: 2007-12-23
forum: Virtualisation
---

### Post by penguin steve on 2007-12-23
Hello, i recently installed VMware Server on Ubuntu 7.04 x64 and i cannot run machines on my NTFS partition.

I have been running VMware Workstation 5.5 in Windows XP x64 for a long time and now i want to run my machines both in windows AND and in Ubuntu as i dual boot. i got VMware Server installed no problem in Ubuntu but it wont run my machines on the NTFS partition. i have the NTFS read/write tool installed and it works very nicely. i haven't had any problems with it yet. i know my problem is the NTFS as when i copy a machine from the NTFS to the EXT3 partition, it works. but i want to know if there is a workaround this as i don't want to have move my machines every time i want to use them. especially one of them that is 30GB. i am also staying away from the EXT3 read/write for windows because i don't want viruses and malware to come in from my linux install as it would almost be like a back door.

Thanks for all your help

---

### Post by theZoid on 2007-12-25
Interesting....I have my VMware Server (XP Pro) 25 gig virtual disk running off a FAT 32 shared partition, but formatted with the VD to NTFS...I was wondering if that whole partition should have been NTFS to start with?  Are you having permission problems?

---

### Post by penguin steve on 2007-12-25
no no permition problems whatsoever. just to make things clear here, this in my disk.

partition 1 ---> 180GB Windows NTFS
partition 2 ---> 10GB Shared Fat32
partition 3 ---> 100GB Linux EXT3
partition 4 ---> 2GB Linux Swap

now that i have the NTFS read/write support i no longer need partition 2. i have run several VMware machines off partition 2 no problem in both windows and linux so i know its something to do with the NTFS partition. i cant move my VMware machines onto partition 2 as it is only 10 GB. i need at least 30 and im not going to repartition my whole drive just for that. i'd like to run my machines in on partition 1 in linux and if its not possible, its not really a big deal.

other details:

in VMware server (when im in Linux) i can go find and open my machines on partition 1 but when i go click "power on" the window goes black for a few moments and then goes right back to screen 1 when the machine is powered off. it does not even get as far as the VMware boot screen.

i just want to know if there is a workaround this.

Your help is appreciated.

---

### Post by theZoid on 2007-12-25
FAT32 doesn't use permissions I believe.....you could shrink par1, del part2 and then create a larger FAT32 to replace part2 you have now...that's basically what I did to get the virtual disk out of my basic linux system....I'm open also to any other suggestions.

---

### Post by penguin steve on 2007-12-25
yes i could resize partition 1 and expand partition 2 but because i keep most of my files on windows to have access in both OS, partition 1 is beginning to fill so i don't want to shrink it. i'd almost have to go the other way and shrink partition 3 and expand partition 2 but thats not possible as data is written from the beginning and makes its way to the end of the partition. i would have to re-install Ubuntu to do that move. i just don't have time to reinstall and reconfigure everything so i don't think i will do that either. its not really a big deal anyway. i was just hoping for a patch of some kind so if there is none, i will gladly continue the way i was going about before. (boot into windows to run VM on NTFS). it would just have been nice to run them in both OS without major mods.

Thanks, if anyone knows of a patch, please post it!

---

### Post by penguin steve on 2007-12-25
actually your suggestion i modified would work as i just looked up my disk in GParted

[IMG]http://img402.imageshack.us/img402/4078/screenshot1vh0.png[/IMG]

i thought the fat32 partition was between the NTFS and EXT3. from this picture i could indeed shrink the EXT3 and expand the FAT32

oh wait i just realized fat 32 does not support files larger than 4GB and since my 30GB disk is one file, it wont work anyway so im still forced to resort to some patch

---

### Post by popch on 2007-12-26
The partition /dev/sda1 has two interesting properties in the GParted screenshot: It has an explanation mark in a yellow triangle and it does not have a mount point.

What particular situation is the exclamation mark warning of?

Where and how is the partition mounted when you try to access the VMWare files on it? Are you quite sure that the user running the VM has the admission to write to that disk?

---

### Post by theZoid on 2007-12-26
> **penguin steve said:**
> actually your suggestion i modified would work as i just looked up my disk in GParted

[IMG]http://img402.imageshack.us/img402/4078/screenshot1vh0.png[/IMG]

i thought the fat32 partition was between the NTFS and EXT3. from this picture i could indeed shrink the EXT3 and expand the FAT32

oh wait i just realized fat 32 does not support files larger than 4GB and since my 30GB disk is one file, it wont work anyway so im still forced to resort to some patch

I have a 25 gig virtual disk on my fat32....it works because vmware server splits the vitual disk up into 2gb slices...voila...and the virtual disk itself is formatted by VMware to ntfs so no file problems there :D

---

### Post by penguin steve on 2007-12-26
> The partition /dev/sda1 has two interesting properties in the GParted screenshot: It has an explanation mark in a yellow triangle and it does not have a mount point.

What particular situation is the exclamation mark warning of?

Where and how is the partition mounted when you try to access the VMWare files on it? Are you quite sure that the user running the VM has the admission to write to that disk?

i believe the reason it does not have a mount point is because i never specified one. it is automatically mounted at /media/sda1 (checked the properties of the icon on my desktop). also i looked up the status of the exclamation mark and it says "cannot find mount point". however even if there is no mount point, the partition is mounted anyway. should i specify a mount point? i have never had any problems with my mount point at /media/sda1 and i can access the NTFS partition no problem. permissions do not seem to apply on NTFS either so i havent had problems like that.

> I have a 25 gig virtual disk on my fat32....it works because vmware server splits the vitual disk up into 2gb slices...voila...and the virtual disk itself is formatted by VMware to ntfs so no file problems there

when i created my VM, i specifically told it not to separate the virtual disk into 2GB files so my disk is indeed a full single 30GB File. i now realize how dumb that was of me.

---

### Post by theZoid on 2007-12-27
I ended up reinstalling Ubuntu, expanding the linux partion, and created a new VM for XP Pro set to 30gb max, but did not allocate the space or use the 2gb slices.  Now it will expand as needed up to max of 30 gigs.  I couldn't see reserving the space if I'd never use it for a few business programs.  The virtual disk resides on my EXT3 linux partition.

EDIT:  since I know how to set up what I need (now), it didn't take 30 minutes after the install to put everything back.

---

