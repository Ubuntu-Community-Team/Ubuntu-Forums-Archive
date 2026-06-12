---
title: "USB Mount Permission issues :-("
date: 2006-05-17
forum: Server Platforms
---

### Post by mjpowersjr on 2006-05-17
Hello,
I am using ubuntu breezy as a file server at home. I have been with ubuntu since the beginning and have really enjoyed the ride. I'm def. not a unix wiz, but ubuntu has sure taught me a lot :-) Anyway, I'm having some trouble with permissions on a usb mount point.

I have a Maxtor external hd (/dev/sdc) formatted fat32 with alot of data on it.

whenever i mount the drive (by hand, or via fstab) the permssions are set to:
drwxr-xr-x  10 root root    16K 2006-05-17 01:58 Maxtor

I have tried setting the umask=000 and umask=0000 in both fstab, and when running the following by hand: 
root@pserver:/mnt# mount -t vfat -o umask=0000 /dev/sdc1 /mnt/Maxtor/

For now I just want to 777 the mount point, and then secure it afterwards...but nothing i do changes the permissions :-/
Thanks in advance for the help.
-mike

---

### Post by Sutekh on 2006-05-17
No matter how hard you try or want it to work, chmod'ing Windows partitions will not work.

Try unmounting the partition first.  

Then change the options in the fstab.  Then mount the partition again.  Works here.

---

### Post by mjpowersjr on 2006-05-18
sutekh, 
thanks for the response, sorry I may not of been very clear (very little sleep for the past 2 weeks). when i said 'i just want to 777 the mount point' i was just saying i want to give all users full permissions for the time being. I was not actually trying to chmod the directories/files.  Also, I do umount the device before every 're-mount' .... I dont see any errors in the syslog either :-/ This is pretty odd....

---

### Post by Sutekh on 2006-05-18
That's cool, people often ask about chmod'ing FAT partitions, that's why I mentioned it.

No you shouldn't have to unmount before each re-mount. It should be just the case of making sure that the USB is unmounted before changing the fstab.
```
sudo umount /mnt/Maxtor
``` Make the changes to the fstab; the umask as you already know, and then mount it again, with the new settings
```
sudo mount /mnt/Maxtor
``` I have found that making changes to the fstab *while* the partition is mounted and then re-mounting does not change them. I find they have to unmounted, then the settings changed, then mounted again. Slight difference, but makes all the difference.

Hope it does for you too.

---

