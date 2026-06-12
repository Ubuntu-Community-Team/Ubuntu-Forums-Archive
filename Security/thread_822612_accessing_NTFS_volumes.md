---
title: "accessing NTFS volumes"
date: 2008-06-08
forum: Security
---

### Post by andrew.co.za on 2008-06-08
I have two NTFS issues:

Firstly, when an application tries to access my internal NTFS volume it throws errors. I can bypass this by manually accessing the drive through nautilus, thereafter applications can access it without problems. For example Virtual Box will not run an OS who's virtual drive is saved on the NTFS volume... Rhythmbox will count down the total track number until it has excluded all the files on the NTFS volume... Warsow will not run at all since it's installed on the NTFS volume. I assume this is a security issue, i have tried logging in as root and setting the permissions for my user to read/write.

My second issue is that if i plug my external HDD (formatted as NTFS) into a windows PC and then bring it back to Ubuntu, Ubuntu will say unable to mount the volume because it is locked. I can fix this by taking it back to the windows PC and explicitly clicking on "safely remove drive". Is there any way to get around this without needing windows again?

---

### Post by andrew.co.za on 2008-06-29
Solutions:

1) Accessing the drive through nautilus automatically mounts it before displaying the contents.The solution is to automount it on startup:
```
sudo gedit /etc/fstab
```
then add the following line: (you might need to change it so suit your volume)
```
/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0
```

2) Force mount the volume: (again, change if needed)
```
mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force
```

---

