---
title: "Hard disks not spinning down"
date: 2007-07-16
forum: Server Platforms
---

### Post by Gruelius on 2007-07-16
Hey all,
I need some help with spinning down my raid array. I have 5 disks in a mdadm made raid5 array. Four of these are on a PCI to 2x IDE board and one is on the nvidia chipset controller.

I have set hdparm to spin them down after 10 minues in hdparm.conf however they all seem to be active.

SUdo hdparm -C /dev/<device> shows hdb to be active/idle and sda->d to be on standby but they are all still rip roaring!

So what can i do to save more power + disk life? I am still learning so be gentle :P
Julius

---

### Post by Mr. C. on 2007-07-16
File system activity will prevent them from spinning down.

Where is that file system mounted ?

MrC

---

### Post by Gruelius on 2007-07-16
its ext3 and the raid array is mounted in /mnt/raid5

---

### Post by Mr. C. on 2007-07-16
So, the question is, are there processes which are accessing that file system during the spin down window of time ?

The **lsof** command will give you a list of open files / directories.

The best way to test this would be to bring the system down to single user mode, mount the disk, and make sure no processes (including your shell) are accessing that file system.

MrC

---

### Post by Gruelius on 2007-07-17
julius@tuxserver:~$ lsof /dev/md0
julius@tuxserver:~$


ill try unmounting it then wait 10 mins for it to all spin down

*edit* I think it might be because they are on that IDE to pci controller. The Hd* drives spin down easily ( the root one spins straight back up! but the array one stays off untill the array is accessed ). All of the sd* drives remain as standby to hdparm which is confusing as it says its on standby even while its running the test!

I hope when i get the dedicated controller i wont have this thing to deal with :p

---

### Post by Mr. C. on 2007-07-17
The root file system will always be active - there are logs to update, the root superblock may be updated, etc.

MrC

---

