---
title: "ubuntu looking for incremental backup Solution with GPG public key encryption"
date: 2016-08-07
forum: Security
---

### Post by lance bermudez on 2016-08-07
Hi looking to backup my /home/user to external harddrive

looking for
want GPG public key encryption
incremental backups
away to get rid of any thing more than 6 months old

do not like deja dup because it wants a password
like rsync but doses not remove old and no encryption
heard of duplicity but it seems to only work over the net and I want to use external harddrive

Does any one have any ideas?

---

### Post by deadflowr on 2016-08-08
duplicity and deja-dup are the same thing basically.
deja-dup is a graphical frontend for duplicity.

But that aside, you can export the backup to a local storage device by using the file:///path-to-files way.
Example:
```
duplicity /home/me/Documents file:///media/Backups/Documents
```
add or subtract the various options you want.

---

### Post by HermanAB on 2016-08-08
Well, the file system, encryption and backup utilities are all independent of each other.

Format a USB disk with Ext4 and configure LUKS on it with cryptsetup.  Mount the disk and then make a backup with rsync or rbackup or some such.

Here is how I do it on my Mac:
[http://www.aeronetworks.ca/2015/06/mac-backups-with-rsync-to-encrypted.html](http://www.aeronetworks.ca/2015/06/mac-backups-with-rsync-to-encrypted.html)

it is the same idea on Linux.

---

