---
title: "CIFS mount: mkdir by normal user results in root owned directory"
date: 2008-11-25
forum: Server Platforms
---

### Post by bziman on 2008-11-25
I've got a Samba/CIFS issue that hopefully one of you can help me out with... I've got samba set up on my server (and for the most part, it works). The client and server are both running Ubuntu 8.04 Server (with same issue on a 7.10 client). On the server, I have a share configured, and set writable.
```

[local]
   comment = Root Share
   browseable = no
   path = /home/local
   valid users = root
   writeable = yes

```

The /home/local directory is owned by root, but there are subfolders that belong to individual users (so I can mount the share on the client system at startup, and have each user be able to access their own space on the shared drive).  All the permissions on the directories are set properly, and I'm not mucking with sticky bits.

I'm mounting the share on the client from /etc/fstab with the following options:

```
auto,credentials=my.file,rw,setuids

```

The setuids option should cause the server to perform actions requested by the client using the effective uid and gid of the user on the client.  And for regular files it does that.

Here's the problem... when a user on the client, changes to a directory on the share (which the own and have write permissions for), and create a directory, the directory is created on the share belonging to root.

```
$ whoami
bob
$ ls -ld /path/to/share
drwxr-xr-x 1 bob bob 0 2008-11-25 10:00 /path/to/share
$ cd /path/to/share
$ touch foo
$ mkdir bar
$ ls -ltr
-rw-r--r-- 1 bob  bob  0 2008-11-25 10:20 foo
drwxr-xr-x 2 root root 0 2008-11-25 10:21 bar/
```

I don't see any reason that this configuration would not work, unless I'm missing a mount.cifs option or there is a bug in the software.  In this situation, NFS is not a workable alternative  - I would like very much to make Samba work for me.

Thanks!

---

### Post by bab1 on 2008-11-25
The use of  ```
valid users = root
```means that the only valid use is root.  Whatever the authenticated user is, it gets converted to root.  I think you need to use the sticky bit rather than setuid to preserve ownership.

For what you want to do you should look at the [homes]  directive. 

My [homes] share looks like this:
```
[homes]
        comment = Home Directories
        path = /smb/home/%S
        browseable = no
        guest ok = no
        valid users = %S +smbusers [COLOR="Red"]**<-logged in user +smbusers group**[/COLOR] 
        force group = smbusers
        writable = yes
        create mask = 770
        directory mask = 770

```

The file structure looks like this:
```
bruce@malibu:~>ls -l /smb/home
total 8
drwxrws--- 21 bruce  smbusers 4096 2008-11-19 21:26 bruce
drwxrws---  3 bill smbusers 4096 2008-09-08 17:22 bill
drwxrws---  3 carley smbusers 4096 2008-10-13 12:15 carley
drwxrws---  3 eloisa smbusers 4096 2008-06-13 08:12 eloisa
drwxrws---  3 jill smbusers 4096 2008-06-19 15:34 jill

```

---

### Post by bziman on 2008-11-26
According to the docs (man smb.conf), "valid users" is the list of users who are allowed to log in to the share.  This MUST be root, if you expect to be able to manipulate files that belong to any user.  This user (and his password) is used authenticate the client when mounting the share.  The setuids option in mount.cifs is designed so that when you can manipulate the files on the share (if they have permissions to).  Otherwise, everything gets created with default ownership and permissions, which is obviously not what we want to do.  No mundane situation should require the use of sticky bits by an admin on a package based system like Ubuntu.

---

### Post by redmk2 on 2008-11-26
wrong post

---

### Post by bab1 on 2008-11-26
Ok by me.  Mine works and yours does not.  Sticky bits are a legitimate tool used to preserve ownership.

Root can always manipulate files regardless of ownership.

---

### Post by bziman on 2008-11-26
As usual, the forums presented me with helpful "alternatives" instead of an answer to my question, so I did some more digging, and found that this is apparently an open Samba bug of fairly recent report:

[https://bugzilla.samba.org/show_bug.cgi?id=5863](https://bugzilla.samba.org/show_bug.cgi?id=5863)

Who knows when the patch will be accepted, and make it back into Ubuntu, though.

---

