---
title: "I  had my permissions on in my drive but i cant copy r paste on it"
date: 2008-08-06
forum: Security
---

### Post by prabhakaran1989 on 2008-08-06
i have all my other drives working fine..so try to help me to solve the problem


the contents of fstab is
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0
# /dev/hdb6
UUID=97b180aa-5856-4941-9eb5-ce2e7b338e7e  /              ext3         relatime,errors=remount-ro  0  1
# /dev/hdb7
UUID=8b8e54c7-43be-4af0-b8ac-c15d5e25453d  none           swap         sw                          0  0
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0
/dev/hda1                                  /media/hda1    ntfs         defaults                    0  0
/dev/hda5                                  /media/hda5    ntfs         defaults                    0  0
/dev/hda6                                  /media/hda6    ntfs         defaults                    0  0
/dev/hda7                                  /media/hda7    ntfs         defaults                    0  0
/dev/hdd5                                  /media/hdd5    vfat         defaults                    0  0





in the fdd5 i have the problem that i cant create folder,paste files....but in the permissions it says i can create r delete files!
wat to do?? help me ...iam new to ubuntu!!!

Advance thanks!!
~

---

### Post by hermes0710 on 2008-08-06
Add "uid=1000,gid=1000" next to defaults:

ex: /dev/hdd5 /media/hdd5 vfat defaults,uid=1000,gid=1000 0 0

---

### Post by prabhakaran1989 on 2008-08-06
> **hermes0710 said:**
> Add "uid=1000,gid=1000" next to defaults:

ex: /dev/hdd5 /media/hdd5 vfat defaults,uid=1000,gid=1000 0 0
i changed to that but also i cant copy r create files on that disk...
but before i could be able to do that(pasting,creating files)

one more doubt "on the other drives i have all the permissions without giving the command"
how it happens?

---

### Post by hermes0710 on 2008-08-06
The other drives are ntfs. Try adding "user" like before. (I am at work. When i get home i'll post you my fstab that's working)


[http://www.daniweb.com/forums/thread22358.html]("http://www.daniweb.com/forums/thread22358.html")
> 2. Windows doesn't support UNIX-style permissions, and you can only apply permissions to the entire filesystem, not to individual Windows files/folders. This is done with the "umask" option of the mount command. In /etc/fstab, change the mount entry for your Windows partition to this:

/dev/hda6 /mnt/fat vfat users,defaults,umask=000 0 0

(the "users" option allows anyone to mount/unmount the drive and overrides the default , which is that only root is allowed to mount/unmount.)

---

### Post by hermes0710 on 2008-08-06
Just to ensure that we are on the same page, after editing you fstab you must restart the pc.

---

### Post by prabhakaran1989 on 2008-08-06
> **hermes0710 said:**
> Just to ensure that we are on the same page, after editing you fstab you must restart the pc.

k thanks ..Buddy for helping me...
 i will restart d tell u wether it is working r not k....


can i ask u something personnel??
wat r u doing ? abt studying r working?

---

### Post by prabhakaran1989 on 2008-08-06
I got my problem solved ..thank u soo much ..

---

### Post by hermes0710 on 2008-08-06
Glad i helped :)

---

