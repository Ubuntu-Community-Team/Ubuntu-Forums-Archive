---
title: "Unable to view file after rsync'ed to different computers but using same UID"
date: 2009-07-29
forum: Security
---

### Post by televisi on 2009-07-29
Hi All,
I've been able to rsync 1 folder from computer A to computer B through SSH. Using super user: **jo**

[COLOR=Red]**Problem: In computer A, both users (jo & kk) able to vi the file; but not the case in computer B (giving Permission Denied error);**[/COLOR]

In computer A, user details:
- **jo** UID = **1000**
- **kk** UID = **1001**
- both are included in group **kkstaff **(GID = **1001**)

in computer B, user details:
- **jo** UID = **1000**
- **kk** UID = **1001**
- included in group **kkstaff** (GID = **1001**)

Now, in computer A I have 1 file **kkFile**, with stat:
```
 
-rwxrwx--- 1 kk    kkstaff    4 Jul 29 19:37 kkFile

  File: `kkFile'
  Size: 4               Blocks: 8          IO Block: 4096   regular file
Device: fc02h/64514d    Inode: 18164547    Links: 1
Access: (**0770**/-rwxrwx---)  Uid: ( 1001/   kk)   Gid: ( 1001/ kkstaff)
Access: 2009-07-29 19:37:15.000000000 +1000
Modify: 2009-07-29 19:37:11.000000000 +1000
Change: 2009-07-29 19:37:11.000000000 +1000

```Rsync command I use to transfer the folder:
> rsync --owner --inplace --rsync-path='sudo rsync' --delete-during --timeout=0 -zaOH -e 'ssh -2 -i /RsyncPrivateKey -p 22' /data1/currentData/ 192.168.0.3:/data1/currentData/
Now, in computer B **kkFile** stat:
```
 
-rwxrwx--- 1 kk    kkstaff    4 Jul 29 19:37 kkFile

  File: `kkFile'
  Size: 4               Blocks: 8          IO Block: 4096   regular file
Device: fc02h/64514d    Inode: 15597571    Links: 1
Access: (**0770**/-rwxrwx---)  Uid: ( 1001/   kk)   Gid: ( 1001/ kkstaff)
Access: 2009-07-29 19:38:45.000000000 +1000
Modify: 2009-07-29 19:37:11.000000000 +1000
Change: 2009-07-29 19:38:45.000000000 +1000

```Do you think this has something to do with rsync rather than the folder permission itself? did I miss something here?

Thanks

---

