---
title: "Cannot access data on UFS external drive"
date: 2008-01-20
forum: Server Platforms
---

### Post by sl1ng5h0t on 2008-01-20
Successfully mounted my UFS external drive (FreeBsd) using the following command
sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdb1 /media/ufs

Able to view top level directory structure using the filemanager but get the following error message when accessing the directories.

**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "data".

Tried logging in as root but still experience the same problem.

Any leads or help will be appreciated.

---

### Post by sl1ng5h0t on 2008-01-28
The reason why I was not able to access the freebsd filesystem using the filemanager was because all the folders on the external drive were all owned by root with the permission.

drwxrwx---  3 root root  512 2007-01-30 21:17 ad0s2c_backup

While I was using a standard user account.

---

### Post by eddie91 on 2008-01-28
Yes, it is a permissions issue. I had the same problem.  The solution I chose is a bit heavy handed but works for me.  Just change the world permissions to rwx.  To fix it I put the drive back into FreeBSD box, got into the root of the drive and then used this command: 

chmod -R o+rwx *

the -R option applies the permission settings recursively to all directories and files below.  When you mount the drive again in ubuntu, you should be able to navigate around and see all files.

---

