---
title: "duplicity use rsync to copy files to another hard drive"
date: 2022-07-15
forum: Security
---

### Post by lance bermudez on 2022-07-15
Does this work like I think? Will this copy the home directory to the harddrive mounted at /home/3tb using rsync? I need the archive from rsync to keep the permissions.
```

PASSPHRASE="GPG_PASSWORD" duplicity --full-if-older-than 7D --encrypt-key 5263B0FA8C51F3EDEC73B92750AFE64262F13506 --verbosity 8 --gpg-options='--compress-algo=bzip2 --bzip2-compress-level=9' --rsync-options '-avPh' /home --exclude=/home/user.cache file:///home/3TB/rsyncHOME

```

---

### Post by TheFu on 2022-07-16
Duplicity embeds permissions, owner, group, and ACLs inside the 5mb chunks for backups.  If the backup is then rsync'd elsewhere, completely, those are all retained.
I use rdiff-backup, not duplicity, but something similar is used for the 3rd copy of backups.  rdiff-backup also stores owner, group, ACLs, and xattrs externally to ensure that file metadata is retained for every version.  Of course, it is best if native Linux file systems are used for the target and 3rd copy storage, not NTFS. Not exfat/fat-whatever.

source --> rdiff-backup --> target --> rsync --> 3rd copy

The main pro for rdiff-backup is that the most recent version looks like a mirror of the source, so restoring 1, 10, entire directory 15 directories or the entire backup set can be performed using cp/rsync with root/sudo to ensure permissions are retained.  After all, backups are 5% of the problem.  95% of the problem is the restore.  With duplicity, the backed up information is stored in 5mb file chunks and figuring out exactly which need to be restored really requires using one of the duplicity/dejadup/Duplicati tools.  Not so with rdiff-backup.

OTOH, rdiff-backup doesn't have internal encryption, which could be extremely important.  I just use encrypted storage for backups, that way the best tool for each task is used.

Lots of ways to solve these issues.

---

