---
title: "Problems with my ubuntu and sata drives?"
date: 2011-10-11
forum: Ubuntu Studio
---

### Post by eddie3000 on 2011-10-11
I have been driven mad lately with my ubuntu studio. 
I accidentally messed up the installation the other day and instead of trying to repair it I thought it would be a good idea to just reinstall from scratch. I also decided to give the computer a good clean inside, and to put another couple hdds I hade lying around. I would end up with a new installation, with a total of six hdds in the computer, setup as two raid 0 arrays, one for the root system and another for swap and other data. 
But it was impossible. I am no expert on the matter. I started getting all sort of problems. I didn't know what I was doing wrong. At first, the installation seemed to work until the end when I got an error saying grub wouldn't install.
The second attempt I got errors when trying to create the raid array again. I got an error message saying I needed to restart so that the partitioner could format the new raid disk, but after restarting it appeared it hadn't done anything at all. 
On the third attempt, it seemed to work, I booted into the freshly installed OS and after unpdating the kernel I got and grub prompt at startup with a message saying that there was no such disk.
On another occasion, after getting it all going again the system produced an in/out error on dev/whatever when copying the data from my backup to the raid array mounted on my /data folder. I was running the update manager at the same time, and when it told me to restart I got the grub prompt again.
On the next occasion, the same happened as the previous, I got an in/out error when copying. I checked the /data array and it could not be mounted. I rebooted and again it would not. I tried supergrubdisk2, and that couldn't detect any OS at all. 
I became suspicious when I went into the bios setup and discovered that one of my hdd wasn't present. I jiggled the cables a bit, and when I re-entered the bios setup it was present again.
I am not quite sure, but I am pretty certain that my problems are due to faulty sata connections. Is this likely? I never liked the looks of the sata connector when it first saw one, the previous ide/pata connector looked so much better (mechanically). Has anybody had this type of problems?

---

### Post by sgx on 2011-10-11
Hi, I would suggest a reinstall, using your two best drives, one for the main install, with a separate /home partition, and the second drive used for your recording destination.
The other drives can be put in $23 external cases, and used
for backups, and to install other distros for testing.
Or for a backup computer system or two.

The sata connectors, when left in peace, are a good design.

Cheers

---

