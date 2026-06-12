---
title: "file permission"
date: 2009-11-10
forum: Server Platforms
---

### Post by jumpa72 on 2009-11-10
Hi, I'm having problem with file's writing permission.
I've a 64bit file server, running Samba 3.3.2. All the client machines are running Windows XP sp3. I've setted Samba file permissions to 776 (if I set 775 the files are hidden on Windows)
I've setted the right ACL.
I'm encountering this problem: with Autocad, in a client machine, I can't save any file! I can open it, but cannot save! if I use other programs, I can open, save, delete file! Only Autocad doesn't works. I've contacted the Autocad assistance, but they say it's not a their bug. Has anyone some ideas?
tnx

---

### Post by Lars Noodén on 2009-11-10
Would you mind showing the acl settings for the samba directory and some representative files?

```

# show directory acls
getfacl /sambadirectory

# show file acls, but don't post all 5 zillion here
getfacl /sambadirectory/*
```

You can sanitize the filenames, directory names, user names or group names if you wish.

---

### Post by jumpa72 on 2009-11-10
Here is the ACL and file permission:

File permission
```

-rwxrwxrw-+ 1 1di4  warp 580K 2009-10-01 16:03 UPL103366A - Telai.DWG
-rwxrwxrw-+ 1 1di4  warp 593K 2009-10-06 09:45 UPL103366B - Telai.DWG
-rwxrwxrw-+ 1 Robbi warp 602K 2009-10-01 13:03 UPL103366 - Telai.DWG
-rwxrwxrw-+ 1 1di4  warp 357K 2009-10-16 16:34 UPL203432A - PARTICOLARI MORSETTI.DWG
-rwxrwxrw-+ 1 1di4  warp 206K 2009-10-16 16:34 UPL203432 - PARTICOLARI MORSETTI.DWG
-rwxrwxrw-+ 1 1di4  warp 1,2M 2009-10-02 10:06 UPL203464A - Assieme Pettine di Cottura.DWG
-rwxrwxrw-+ 1 1di4  warp 1,3M 2009-10-06 09:45 UPL203464B - Assieme Pettine di Cottura.DWG

```

This is the ACL for the directory:
```

warp@1di4:/../Fusina$ getfacl Pettine\ Cottura/
# file: Pettine\040Cottura/
# owner: 1di4
# group: warp
user::rwx
group::r-x
group:warp:rwx
group:collaboratori:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:warp:rwx
default:group:collaboratori:rwx
default:mask::rwx
default:other::---

```

and this for a couple of files:
```

# file: UPL203464A\040-\040Assieme\040Pettine\040di\040Cottura.DWG
# owner: 1di4
# group: warp
user::rwx
group::rw-
group:warp:rwx
group:collaboratori:rwx
mask::rwx
other::rw-

# file: UPL203464B\040-\040Assieme\040Pettine\040di\040Cottura.DWG
# owner: 1di4
# group: warp
user::rwx
group::rw-
group:warp:rwx
group:collaboratori:rwx
mask::rwx
other::rw-

# file: UPL103366\040-\040Telai.DWG
# owner: Robbi
# group: warp
user::rwx
group::rw-
group:warp:rwx
group:collaboratori:rwx
mask::rwx
other::rw-

```

The user that cannot write the file is Robbi, which belongs to group warp.
tnx

---

