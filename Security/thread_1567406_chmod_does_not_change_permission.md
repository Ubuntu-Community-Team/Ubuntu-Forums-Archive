---
title: "chmod does not change permission"
date: 2010-09-03
forum: Security
---

### Post by pedram@patexia.com on 2010-09-03
I recently installed Ubuntu 10.4 on an Intel machine. The machine also has Windows 7. So some of the partitions of the hard drive are Windows compatible (NTFS). They are all mounted when system is booted with Ubuntu and all files are accessible. However, when I try to change permission or limit access to a group, CHMOD command does not work. It doesn't return any error and everything seems to work fine but I can't change any permission. I appreciate your help.

---

### Post by akoskm on 2010-09-03
> **pedram@patexia.com said:**
> I recently installed Ubuntu 10.4 on an Intel machine. The machine also has Windows 7. So some of the partitions of the hard drive are Windows compatible (NTFS). They are all mounted when system is booted with Ubuntu and all files are accessible. However, when I try to change permission or limit access to a group, CHMOD command does not work. It doesn't return any error and everything seems to work fine but I can't change any permission. I appreciate your help.

Have you tried to chmod it as root
```

sudo chmod

```?

---

### Post by FuturePilot on 2010-09-03
NTFS has no clue what Unix permissions are. You can't chmod on an NTFS file system.

---

### Post by Morbius1 on 2010-09-03
> They are all mounted when system is booted with Ubuntu and all files are accessible.
If they automount at boot then they have entries in fstab. fstab is the only place you can change ownership or permissions of any windows filesytem.

Why not post your fstab:
```
cat /etc/fstab
```

---

### Post by pedram@patexia.com on 2010-09-03
> **Morbius1 said:**
> If they automount at boot then they have entries in fstab. fstab is the only place you can change ownership or permissions of any windows filesytem.

Why not post your fstab:
```
cat /etc/fstab
```

This is the content of fstab:


 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=4f72e9c7-1c81-4c42-bba9-76f954ee2cca	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=7202016B0201359F	/media	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda4 :
UUID=34200E05200DCF34	/media/FACTORY_IMAGE	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda6 :
UUID=00AEE1C4AEE1B278	/media/Storage	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda7 :
UUID=7C2EFC222EFBD35E	/media/Ubuntu_Sesrver	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda2 :
UUID=94D8078ED8076E34	/media/Windows_7	ntfs-3g	defaults,locale=en_US.utf8	0	0

---

### Post by Morbius1 on 2010-09-03
Let's take this one as an example:
>  UUID=94D8078ED8076E34    /media/Windows_7    ntfs-3g    defaults,locale=en_US.utf8    0    0There are three additional options you can play with to set ownership and permissions access to these:
umask, uid, and gid

Let's say I wanted to allow read / write access to all local login users and no one else:

>  UUID=94D8078ED8076E34    /media/Windows_7    ntfs-3g    defaults,[COLOR=Blue]umask=007,gid=46[/COLOR],locale=en_US.utf8    0    0umask=007 will allow owner and group read / write access and no access to anyone else.
gid=46 refers to the "plugdev" group which represents all local login users.

You could make it so that you become the owner and only you can access the partition:
>  UUID=94D8078ED8076E34    /media/Windows_7    ntfs-3g    defaults,[COLOR=Blue]umask=077,uid=1000[/COLOR],locale=en_US.utf8    0    0umask 077 will turn off all access to anyone other that the owner.
uid=1000 makes you the owner.

---

### Post by pedram@patexia.com on 2010-09-03
That means I can only change the access for the entire drive and won't be able to change permission for individual folders or files inside that drive. Is that right? Is there a way to set the file permission for files and folders?

---

### Post by bodhi.zazen on 2010-09-04
> **pedram@patexia.com said:**
> That means I can only change the access for the entire drive and won't be able to change permission for individual folders or files inside that drive

Tha is correct.

> Is that right? Is there a way to set the file permission for files and folders?

You need to back up your data and use a Linux native partition (ext4) for that , ntfs does not support linux permissions (well, there may be a way, but it is in beta and so may not work)

[http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)

---

### Post by Morbius1 on 2010-09-04
The closest thing I can think of that comes close to what you want is bindfs: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

I've never tried it with a windows filesystem though so it might work I just don't have any experience with it on an ntfs partition. You'll never get it to the file level though just the child directories.

---

