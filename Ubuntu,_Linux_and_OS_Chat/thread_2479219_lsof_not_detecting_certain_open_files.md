---
title: "lsof not detecting certain open files"
date: 2022-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by carnagelan on 2022-09-18
Hi Guys,

I have an ubuntu media server(terminal based only) at home running plex.
Plex is also the DLNA server so i can watch the movies on my tvs.

If a movie is open on the TV and i type in > lsof /dev/sdb on the server
It doenst show any files open(/dev/sdb) is the hard drive with all my movies on

Is this possible to list the open movies as i cant umount the drive and cant use the kill command as i cant see what files are open.

---

### Post by spjackson on 2022-09-19
lsof without any arguments lists all open files, but when there is an argument, it only lists those files that are open by processes which the user has access to (typically just the user's open processes). If you use sudo, it will work. If you can't or don't want to use sudo, I think the only option would be to use lsof without an argument and pipe the output to grep or similar.

---

### Post by TheFu on 2022-09-19
Use directory and file names, not device names.
Also, lsof needs sudo to work.

---

### Post by ajgreeny on 2022-09-19
Where is /dev/sdb mounted?

USB disks of all sorts usually automount when attached to **/media/*username*/disk-ident** where disk-ident may be the label of the partition on sdb or if not labelled the UUID of the partition. Use of labels makes things a lot more human friendly.

---

### Post by spjackson on 2022-09-20
That's a fair point: /dev/sdb is unlikely to be the right thing. /dev/sdb1, or /dev/sdb2, or whatever, would be more plausible.

---

### Post by TheFu on 2022-09-20
> **spjackson said:**
> That's a fair point: /dev/sdb is unlikely to be the right thing. /dev/sdb1, or /dev/sdb2, or whatever, would be more plausible.

No.  lsof doesn't work with devices, it works with file system objects ... files and directories.  The OP needs to use a directory as the grep filter.
Say I'm looking for my top-level plex media directory for movies.  On my system, that is mounted to /d/D1/M/ ... so I'd use
```
$ sudo lsof | egrep /d/D1/M
```

For reference, the df -Th looks like:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-lv_media              ext4  3.5T  3.5T   18G 100% /d/D1
```
This is because I use LVM, but if I was using straight partitions, then that would look something like:
```
/dev/sdj2                     ext4  3.5T  3.5T   18G 100% /d/D1
```
Looking a /dev/sdj2 won't work. It isn't a file system object.

---

### Post by spjackson on 2022-09-20
> **TheFu said:**
> No.  lsof doesn't work with devices, it works with file system objects ... files and directories.

Really? The man page says "If a name is the mounted-on directory of a file system or the device of  the file system, lsof will list all the files open on the file system."

But I stand corrected.

---

### Post by ajgreeny on 2022-09-20
"If a name is the **mounted-on directory of a file system** or the device of the file system, lsof will list all the files open on the file system."

That means the directory the filesystem is  mounted on,eg /mnt/movies, not the actual filesystem, eg dev/sdx1.

---

