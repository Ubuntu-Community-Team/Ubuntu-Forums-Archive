---
title: "How did you partition your harddrive when installing ubuntu?"
date: 2009-12-01
forum: The Cafe
---

### Post by mahela007 on 2009-12-01
Which of these methods did you use to partition your hard drive before installing ubuntu?

---

### Post by darkod on 2009-12-01
I always use manual, nevermind if it's windows or linux. That way you control where and how big the partitions are created.
Yes, you need to read some basic info and tutorials, but I consider that a necessary step if learning to use new OS anyway.

---

### Post by mahela007 on 2009-12-01
Well, posted this thread because I've installed ubuntu 3 times (on 3 PCs) and 2 out of 3 times, I've had trouble with the partitioning stage of the ubuntu installer. The last time it said 'error in parititioning. Process aborted". I've posted about this in another thread.

---

### Post by darkod on 2009-12-01
The poll is sort of incomplete. If you used ubuntu installer it makes big difference whether you used the guided methods or manual partitioning.

---

### Post by iKonaK on 2009-12-01
None of the pool options, I use manual partitioning ::)

---

### Post by emigrant on 2009-12-01
> **mahela007 said:**
> Well, posted this thread because I've installed ubuntu 3 times (on 3 PCs) and 2 out of 3 times, I've had trouble with the partitioning stage of the ubuntu installer. The last time it said 'error in parititioning. Process aborted". I've posted about this in another thread.

i dual boot karmic with vista.
this is how i made my partitions:
in vista go to control panel> admni privileges>computer managment> diskmanagement

choose the partition you want to delete (make it free space).

run the ubuntu live cd and select the free space available for the ubuntu installation.:KS

---

### Post by overdrank on 2009-12-01
Moved to The Community Cafe

---

### Post by gn2 on 2009-12-01
Last time I did a dual-boot install was onto a Vista laptop.
I reduced the Vista partition with it's own inbuilt partitioning tool then used the manual partitioning option of the Ubuntu Alternate CD installer to create /, /home and swap partitions in the unallocated space.

Last time I did a straight Ubuntu only installation it was from a Live CD and I used manual partitioning to create /, /home and swap.

---

### Post by pi4r0n on 2009-12-01
I got 500GB HDD and as always mu laptop was already preloaded with Vista; so I decided to dual boot even that I use Ubuntu as my default OS I still need Windows for some small jobs.

So what I got is:

400 GB - Ubuntu 9.10
98 GB - Vista
2 GB - Recovery Disk

PS. I used ubuntu installer and followed the instructions in the installer.

---

### Post by mahela007 on 2009-12-01
So most of you guys seem to have used manual partitioning judging from the posts... (cos my poll is incomplete). I think that's what I'll do from now on. However, I think that this is one aspect that has to be improved. I mean, the first time a new user tries to install ubuntu, if he get's this error during installation, he'll most probably dump it.

---

### Post by wilee-nilee on 2009-12-01
I wiped my new netbook then used a custom install of W7 to half of the HD and left a open space for Karmic. I never do manual partitioning the programs are setup to auto partition and thats good enough for me.

---

### Post by Dragonbite on 2009-12-01
I used to do manual install but lately I've just been wanting to get up and running fast because it wasn't going to be one before trying something else.

My latest installation is actually Fedora 12, which I chose to encrypt the hard drive.

It laid everything out in LVM partitions so I only need to put in the passphrase once even though it is split up into partitions.

---

### Post by forrestcupp on 2009-12-01
Why go out of your way to use another method when it is already a built in step in the installation of Ubuntu?

---

### Post by alphaniner on 2009-12-01
I choose other app or live CD.  My first distro was 7.04, but I wanted to get familiar with terminal apps so I learned fdisk and mkfs.  And nowadays I format with options not available in the installer.

---

### Post by fromthehill on 2009-12-01
when I started using ubuntu I just dumped everything in one big / partition because I didn't want to have any problems with disk space on partition.
when I got used to ubuntu I splitted the disk in a / and /home disk
when switching to arch I splitted the disk in /boot / and /home

---

### Post by Dragonbite on 2009-12-01
> **fromthehill said:**
> when I started using ubuntu I just dumped everything in one big / partition because I didn't want to have any problems with disk space on partition.
when I got used to ubuntu I splitted the disk in a / and /home disk
when switching to arch I splitted the disk in /boot / and /home

I just recently had an issue where I had to run some dpkg --configure (?) command and it didn't work because I didn't give the /boo directory enough room (only 100MB).

I got around it by copying the contents of the /boot partition into the unmounted directory, ran the command and then copied the modified /boot directory back into the partition.

---

### Post by speedwell68 on 2009-12-01
I just choose use entire disk at the partioning stage of the ubuntu install.  Simples.

---

