---
title: "Unable to mount hard disk drive"
date: 2008-04-28
forum: Server Platforms
---

### Post by Chilliman on 2008-04-28
i have three 20G drive on my server box 1 has the OS and the other two are for storage, i can see all three drive and are mounted to the first one but i am unable to mount the other two drives i am a newbie and am not sure what to do next can some one help me.

chilliman

---

### Post by spoown on 2008-04-28
Can you give us perhaps more information if you get any errors when you try to mount the two others drives ?

---

### Post by cdtech on 2008-04-28
> **Chilliman said:**
> i have three 20G drive on my server box 1 has the OS and the other two are for storage, i can see all three drive and are mounted to the first one but i am unable to mount the other two drives i am a newbie and am not sure what to do next can some one help me.

chilliman

This will list the available drives installed in your setup. (example:sda,sdb)
```
sudo fdisk -l
```

This will list the block ID's used by the Ubuntu OS in the fstab (though fstab works without them, I use these as suggested by Ubuntu).
```
blkid
```

This is how the drives get mounted at boot.
```
/etc/fstab
```

This is a sample /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=d4c465e8-62a9-47cd-89fc-11035d656290 / ext3 defaults,errors=remount-ro,noatime 0 1
# /dev/hdb2
UUID=77dc92d4-3448-4bc6-8582-6c04b0face4b /home ext3 defaults 0 2
# /dev/hda1
UUID=D4A0829AA082832A /media/Windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2
UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 /mnt/Edgy ext3 defaults 0 2
# /dev/hdb5
UUID=18c26e08-7085-4e50-a881-3d6d74b19c04 none swap sw 0 0
#/dev/hde1
UUID=4b0139b9-6d5e-4a00-bf38-06d1002e3325 /media/Storage ext3 defaults 0 2
#/dev/sda1
UUID=b51b9252-a78c-416f-a734-9651fe2b7a27 /media/USBDrive ext3 defaults 0 2
```

You can see how each drive is listed in the comment line (#) and the UUID is used in place of the human readable drive number.

You have to create a mount point for the drives to be mounted as seen by the hda2 drive (/mnt/edgy).

Once you create the directory for the drive to be mounted and edit the fstab file you can run (on a command line):
```
sudo mount -a
```
This will mount all filesystems (of the given types) mentioned in fstab.

hope this helps....

---

