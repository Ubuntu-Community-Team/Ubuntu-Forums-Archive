---
title: "data security through password in external hdd"
date: 2009-08-17
forum: Security
---

### Post by bilol on 2009-08-17
Hi all,
 Is it possible to hide the content of a folder through password in an external hdd? In case of folders residing in the internal hdd's Linux partition, we can make it secure through '**chown**' and '**chmod**'.Is similar kind of operations are possible in external hdd? Please note that I do not want to encrypt the data within that folder.
Need your valuable suggestions.....

---

### Post by cdenley on 2009-08-17
You can apply security permissions on any native Linux filesystem (ext3, reiserfs, xfs, etc.). Linux file permissions are not supported on fat32 or ntfs. You can change the permissions used for the entire filesystem at mount time, though.

---

### Post by bilol on 2009-08-18
Thanks cdenley,
I want to lock my folder in external hdd by root password(No encryption).Such that in any m/c it require a password to open the folder.
**Is it possible?**
For experimental purpose I did the following:
(1) I unmount my usb pen drive.
(2) sudo mkfs.ext3 /dev/sdb1  # format a usb  pen drive in ext3
(3) sudo e2label /dev/sdb1 bilol # rename the pen drive to bilol
(3) mount the pen drive
(4) sudo cp secret /media/bilol # copy the *secret* file to pen drive
(5) sudo chmod 700 /media/bilol/secret # make the file accessible by root only
(6) unmount the pen drive

But everything was in vain. In other m/c the root user can open the file *secret* by giving his root password.

need your help....
Thanks in anticipation.

---

### Post by cdenley on 2009-08-18
That is correct. With Linux and every other OS, filesystem permissions can easily be bypassed with physical access. The owner is stored in the filesystem as a UID. As long as the local user has the matching UID, they have access. There is no password stored in the filesystem, and no computer-specific details. Also, root can change ownership of any file. The only way to prevent your files from being read by a root user is encryption.

---

