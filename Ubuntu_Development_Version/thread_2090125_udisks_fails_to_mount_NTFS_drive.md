---
title: "udisks fails to mount NTFS drive"
date: 2012-12-01
forum: Ubuntu Development Version
---

### Post by ronacc on 2012-12-01
One of the drives on my testbox currently has a Win-8 install , udisks refuses to mount this drive , see SS . I can mount the drive from Sabayon using Dolphin .

---

### Post by jbicha on 2012-12-01
Did you read the error message? It doesn't want to mount the Windows partition because it is hibernated and there is a chance of data loss if you mount it anyway. It also tells you the command you need to run to delete the hibernation file so you can safely mount it (assuming that you didn't have anything important like unsaved documents running in Windows when it was hibernated).

Windows 8 might have some fancy technology that means that certain types of shutdown's are actually hibernates behind the scenes as a clever trick to get faster reboots.

---

### Post by ronacc on 2012-12-01
> **jbicha said:**
> Did you read the error message? It doesn't want to mount the Windows partition because it is hibernated and there is a chance of data loss if you mount it anyway. It also tells you the command you need to run to delete the hibernation file so you can safely mount it (assuming that you didn't have anything important like unsaved documents running in Windows when it was hibernated).

Windows 8 might have some fancy technology that means that certain types of shutdown's are actually hibernates behind the scenes as a clever trick to get faster reboots.

it is not hibernated . I always shutdown to complete power off . If it is an artifact of windows 8 startup files , udisks should be able to handle that .

---

### Post by oldfred on 2012-12-01
Windows 8 is always hibernated. It has standard hibernation, but  its default shutdown is also a hibernation for fast boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by ronacc on 2012-12-01
thanks for the info .

---

