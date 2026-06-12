---
title: "Installing Windows XP on my Ubuntu Drive"
date: 2005-07-23
forum: The Cafe
---

### Post by harrisxml on 2005-07-23
I installed Ubuntu onto my clean 80GB SATA HDD yesterday.  I do not have Windows anymore and I need it to keep my sanity while I learn how to survive in Ubuntu.  How do I install Windows XP Professional SP2 onto my Linux/Ubuntu Drive?  I would like to know things like:  How do I resize the partitions so that I can have space for my Windows install, How do I set up the dual boot, etc...  Thank you all very much.

---

### Post by jasmuz on 2005-07-23
uh? Why would you want to go back to slavery?

---

### Post by super on 2005-07-23
noo! resist the dark side!  :-P 

but if you just *have to* then:

if you already have an unused partition then just format it as fat32 (or ntfs but that is read-only in linux) and Windows should find it when you begin the installation.

if you don't have the partition set up already then use something like gpart or qtparted to resize you linux partition. (i think these are non-destructive but i could be wrong. verify this first!!) or use a boot cd with partitioning tools (eg: UltimateBootCD) and use that to resize.

---

### Post by harrisxml on 2005-07-23
Thank you for the help.  I now have dual boot Windows XP/Ubuntu Linux.

---

### Post by sargonx on 2006-08-17
After you install windows, how can you dual boot? is there a menu appearing or something?

---

