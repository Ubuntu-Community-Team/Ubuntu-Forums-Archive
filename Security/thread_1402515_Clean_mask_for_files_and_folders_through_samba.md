---
title: "Clean mask for files and folders through samba"
date: 2010-02-09
forum: Security
---

### Post by emma_peel on 2010-02-09
Hello.

Still working on the mask of files for shared folder.

Thanks to this thread :

[http://ubuntuforums.org/showthread.php?t=1400084](http://ubuntuforums.org/showthread.php?t=1400084)

I now have a shared folder with the exact behavior I expect :

```
sudo addgroup share_group
sudo mkdir /media/volume/shared_dir
sudo chgrp share_group /media/volume/shared_dir
sudo chmod g+s /media/volume/shared_dir
sudo chmod 770 /media/volume/shared_dir
sudo setfacl -d -m group::rwx /media/volume/shared_dir
sudo setfacl -d -m other::--- /media/volume/shared_dir
emma@box:/media/volume/shared_dir$ ls -al
total 8
drwxrws---+ 2 root   share_group 4096 2010-02-09 12:53 .
drwxr-xr-x  8 root   root        4096 2010-02-09 11:58 ..
-rw-rw----+ 1 emma share_group    0 2010-02-09 12:53 test

```

By default, user from the group can modify this file. That's perfect.

I have define the share in Samba this way :

```
[share]
   comment = Shared Folder
   path = /media/volume/shared_dir
   browseable = yes
   guest ok = no
   read only = no
   hide dot file = yes
#   force group = share_group
#   create mask = 0660
#   directory mask = 0770
#   force create mask = 0660
#   force directory mask = 0770
```

When drag & dropping a file in this share, here is the default mask :

```
emma@box:/media/volume/shared_dir$ ls -al
total 192
drwxrws---+ 2 root   share_group   4096 2010-02-09 12:54 .
drwxr-xr-x  8 root   root          4096 2010-02-09 11:58 ..
-rw-rwx---+ 1 emma share_group   6148 2010-02-09 12:54 .DS_Store
-rw-rwxr--+ 1 emma share_group 176684 2009-12-21 23:33 IMG_7487.jpg

```

So the dropped file have execution rights for the group, and read access for other. I expected it to have the same rights than the file created directly using the touch command. I tried to play with the mask options, without success.

The file has been dropped from my mac, which is a Unix like OS. I guess that some authorization access are inherited from the original file, for the user and other parts.

But where does the group authorization come from ? Moreover, is is possible to define in samba a default mask, whatever the authorization of the original file ?

Thanks again for sharing your knowledge and experience !

---

### Post by emma_peel on 2010-02-11
MOUUUHAHA MOUHOUHOUHAAAAA !!!

I finally found that the permissions are copied without any modification.

There is 2 options that help changing the permission during the transfer:

```
    security mask = 0770
    force security mode = 0660

```

The first one gives the higher permission, the second one, the lowest.

So when files are copied, anybody can modify them!

---

