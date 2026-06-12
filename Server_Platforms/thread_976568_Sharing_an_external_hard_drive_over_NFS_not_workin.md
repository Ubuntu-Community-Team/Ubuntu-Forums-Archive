---
title: "Sharing an external hard drive over NFS not working (permissions?)"
date: 2008-11-09
forum: Server Platforms
---

### Post by mrpeenut24 on 2008-11-09
I'm trying to setup my desktop to serve NFS so that I can access my external hard drives (connected to the desktop) on my laptop.  However, whenever I mount them on my laptop via NFS, the folders are empty or protected.  I can open my home folder with no problem, so I think it has to do with the permissions the external drives are mounted with on the desktop.  Here are some relevant config files/outputs.  Let me know if something is wrong.


/etc/exports:
```

/media 192.168.1.1/24(rw,sync,no_root_squash)
/home/*user* 192.168.1.1/24(rw,sync,no_root_squash)

```mount on desktop:
```

/dev/sdd1 on /media/disk   type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=022,flush)
/dev/sdc1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=022,flush)
/dev/sdb1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-3 type reiserfs (rw,nosuid,nodev,uhelper=hal)
/dev/sdb4 on /media/disk-4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```ls -l /media on desktop:
```

drwx------  9 *user*      root 16384 1969-12-31 19:00 disk
drwx------ 25 *user*      root 32768 1969-12-31 19:00 disk-1
drwxr-xr-x 24 root      root  4096 2008-07-25 01:28 disk-2
drwxr-xr-x  5 root      root   112 2008-05-23 10:04 disk-3
drwxrwxrwx  1 root      root  4096 2008-08-19 02:44 disk-4

```mount on laptop:
```

Desktop:/media on /media/desktop-media type nfs (rw,addr=192.168.1.103)
Desktop:/home/*user* on /media/desktop-home type nfs (rw,addr=192.168.1.103)

```ls -l /media on laptop:
```

drwxr-xr-x 34 *user*   *user*   1472 2008-11-09 12:36 desktop-home
drwxr-xr-x  9 root   root   4096 2008-11-09 13:09 desktop-media

```ls -l /media/desktop-media on laptop:
```

drwx------  2 root  root  4096 2008-11-09 13:09 disk
drwx------  2 root  root  4096 2008-11-09 13:09 disk-1
drwx------  2 root  root  4096 2008-11-09 13:09 disk-2
drwx------  2 root  root  4096 2008-11-09 13:09 disk-3
drwx------  2 root  root  4096 2008-11-09 13:09 disk-4

```and each of these folders, when opened as root, show nothing.  I've tried changing the mount options (on the desktop external harddrive mountpoints) to uid=1000,gid=1000,umask=022 and it makes the permissions (755,user,root) but they're still empty.  Like I said, I can open the home folder with no problem and see everything in there, but I can't with the /media folders.  Any ideas?

It may be useful to note that the username, uid, and gid are all the same between the two computers.

---

### Post by aurelieng on 2008-11-09
I think you should try to export your /media/disk* one by one. I read once that for security reasons, NFS does not export automatically the content of mount points under the NFS mount point itself.

Alternatively, you can try with fuse/sshfs, it works well and is secure (useful if you plan to share over a wireless network or over the internet).

---

