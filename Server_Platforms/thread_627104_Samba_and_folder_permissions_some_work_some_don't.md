---
title: "Samba and folder permissions? some work some don't"
date: 2007-11-29
forum: Server Platforms
---

### Post by skyspam on 2007-11-29
Alright, i'm still fairly new to linux, got all my samba stuff sorted except for one problem. I am sharing from my ubuntu 7.10 box to windows xp machines. I can access any local shares and my external hard drive, but when i share my 2nd hard drive that's in the tower, i can't get it to have access permission. I was thinking that this must be a permissions problem more than a samba problem.. but i'm still too new at linux to know where to even start with permissions.

see smb.conf file attached, chrono(hdb1) is the internal drive which doesn't have permission...
i'm a bit at a loss now..

**edit**: i tried to change the permissions using nautilus in sudo, but it just changes them back instantly. so permissions to "others" still is none, and i'm pretty sure that's the problem.

---

### Post by skyspam on 2007-11-29
ok, i ran gksudo nautilus, and when i try to change ANY of the permissions, it instantly jumps back to what you can see in this screen shot here. I want my user to be the owner of this drive.. (it's now in the wrong forum, since i wasn't sure if it was samba or not.. hey, i'm tired)
[IMG]http://img261.imageshack.us/img261/8365/screenshothdb1propertieok7.png[/IMG]

I realized i had been editing it with the drive mounted (i'm tired) but even with it unmounted, i still have the same problem

**PROBLEM HAS BEEN SOLVED, IGNORE THIS THREAD**
(can't figure out how to mark it solved)

---

### Post by ntom-taylor on 2007-11-30
Are you mounting with sudo, and then trying to access / write to files from non-sudo. This would explain permissions issues. 

Try searching for mounting without sudo. Its somthing todo with fstab or somthing.. etc

---

### Post by crouton on 2007-11-30
You should be able to mark thread as [SOLVED] by either editing the title or going to Thread Tools.

And post exactly what the resolution was, in case other people have the same experience.

---

