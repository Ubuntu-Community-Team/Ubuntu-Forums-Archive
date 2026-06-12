---
title: "Running FTP/Samba server, need to mount folders!"
date: 2005-12-16
forum: Server Platforms
---

### Post by mattskr on 2005-12-16
Ok I have VSFTPD/Samba running my server.

I have accounts setup for everyone that will be using it. Most of the files on the server are mine, which I want to allow others access to use it, but not change it, so I have the permissions set up right, but I need to mount some of my folders, like photos and mp3's into the other users home directories, because VSFTPD does not allow symbolic links.

I can mount it by hand, but I'm looking for a way to automatically mount these folders on startup? Any ideas? I've searched the forums extensively!

---

### Post by ola on 2005-12-16
Hi

Im not quite sure if this is what you want but I'll try anyway.

If you already have the actual disk mounted somewhere (for example /mnt/hd1) and want to "share" one cataloge within there it is possible to use mount -bind

From the manpage for mount
```

Since Linux 2.4.0 it is possible to remount part of the file hierarchy somewhere else. The call is
              mount --bind olddir newdir
       After this call the same contents is accessible in two places.  One can also remount a single file (on a  single
       file).

```

If you want to make it automaticly at bootup you can put it in your /etc/fstab -file (a file that deals with where and how file systems shall be mounted) something like this:

```

/mnt/hd1        /where/to/mount/it   ext3    defaults,bind           0       0

```

If that disk is not running ext3 (filesystem) it should be changed to vfat, reiserfs or what you are running.

Hope it was what you were looking for. Be careful when you edit the fstab file since you might have problems otherwise.

---

### Post by mattskr on 2005-12-17
Yea, this was how I thought I would have to do it, does anybody know of a better way?

---

