---
title: "Backuppc and Permission denied"
date: 2008-04-25
forum: Server Platforms
---

### Post by XioNoX on 2008-04-25
I've an BackupPC server at home to backup laptops, and since I4ve update to Hardy, rsync crash with the filder .gvfs in all home directory.

The log file is more explicit :
> full backup started for directory /home/
Running: /usr/bin/ssh -q -x -l root nameofthelaptop /usr/bin/rsync --server --sender --numeric-ids --perms --owner --group -D --links --hard-links --times --block-size=2048 --recursive --delete --force --compress --ignore-errors --ignore-times . /home/
Xfer PIDs are now 6270
Got remote protocol 29
Negotiated protocol version 28
Remote[1]: rsync: readlink "/home/nameoftheonlyuser/.gvfs" failed: Permission denied (13)
Xfer PIDs are now 6270,6272
[ 2 lignes sautées ]
Parent read EOF from child: fatal error!
Done: 0 files, 0 bytes
Got fatal error during xfer (Child exited prematurely)
Backup aborted (Child exited prematurely)

This folder is dr-x------ and is own by the user and rsync run as root
More, I can't change permissions of this folder...

Thanks
XioNoX

---

### Post by tschaboo on 2008-07-28
I had the same problem when using rsnapshot. I could solve it by excluding this folder. It's important not to write a leading slash (".gvfs" not ".gvfs/"). This is discussed here: [http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/rsnapshot-24/deleted-files-still-present-in-backup-89739/](http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/rsnapshot-24/deleted-files-still-present-in-backup-89739/)

---

### Post by Yannick Le Saint kyncani on 2008-07-28
Reading the link tschaboo provided, it seems that ~/.gvfs/ is a fuse filesystem. You could use --one-file-system like I do when backing up anything ( in my case, the entire / )

---

### Post by Yannick Le Saint kyncani on 2008-07-28
Also, if you're backing up only one /home/*/ directory, why don't you run rsync with this user permissions instead of running rsync as root ? Not that it matters anyway though.

---

