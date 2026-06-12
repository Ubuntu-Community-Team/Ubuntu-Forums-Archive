---
title: "Permissions problems with SMB share mounted from TrueNAS"
date: 2021-04-07
forum: Server Platforms
---

### Post by Cantello on 2021-04-07
Hi there!

I recently had to recreate a ZFS pool on my TrueNAS box. Everything went smoothly until I tried to access the shares from my Ubuntu box (Ubuntu Server 20.04 LTS) where all my docker containers reside. I could create a new folder in my mounted folder but not a folder or file inside that folder (i.e. [FONT=Courier New]/mnt/Downloads/incomplete/test[/FONT] could be created but [FONT=Courier New]/mnt/Downloads/incomplete/test.txt[/FONT] could not.

The shares are shared by TrueNAS as SMB shares with permissions of 0777 set in TrueNAS. Thery are mounted on Ubuntu via fstab with:
```
//192.168.1.11/Downloads /mnt/Downloads cifs auto,rw,noperm,credentials=/home/user/.smbcredentials,uid=1000,gid=1002,iocharset=utf8,file_mode=0644,dir_mode=0777,nounix,x-systemd.after=network-online.target 0 0
```. 
The uid & gid are the same as in TrueNAS (user/shared).

When trying to create files/folders on the share in Ubuntu I get as a result:

```
user@ubuntu:/mnt/Downloads/incomplete$ mkdir test3
user@ubuntu:/mnt/Downloads/incomplete$ dir
total 0
drwxrwxrwx 2 user shared 0 Apr  7 12:28 .
drwxrwxrwx 2 user shared 0 Apr  6 09:27 ..
drwxrwxrwx 2 user shared 0 Apr  7 12:09 test
drwxrwxrwx 2 user shared 0 Apr  7 12:28 test2
drwxrwxrwx 2 user shared 0 Apr  7 12:28 test3
user@ubuntu:/mnt/Downloads/incomplete$ cd test3
user@ubuntu:/mnt/Downloads/incomplete/test3$ dir
total 0
drwxrwxrwx 2 user shared 0 Apr  7 12:28 .
drwxrwxrwx 2 user shared 0 Apr  7 12:28 ..
user@ubuntu:/mnt/Downloads/incomplete/test3$ touch test.txt
touch: cannot touch 'test.txt': Permission denied
user@ubuntu:/mnt/Downloads/incomplete/test3$
user@ubuntu:/mnt/Downloads/incomplete$ rm -rf test
rm: cannot remove 'test': Permission denied
```

I am now a little bit stumped on why this won't work, even though I am logged in as the owner of the files/folders and even though the permissions are set to 0777 (something I normally would not do, 755 was sufficient so far).

Any ideas?

---

### Post by LHammonds on 2021-04-07
Could it be that ACL permissions are at play here on top of posix permissions?

---

### Post by TheFu on 2021-04-07
> **LHammonds said:**
> Could it be that ACL permissions are at play here on top of posix permissions?

**getfacl** and **setfacl** are how to check ACLs.

---

### Post by Cantello on 2021-04-07
YES! You both were right, I stripped all ACL permissions with [FONT=Courier New]find directory/ | setfacl -b[/FONT] and then everything worked. Strange, I created a new ZFS pool and did not set any ACL permissions. Happy that it works, though! :-)

---

### Post by Morbius1 on 2021-04-07
Never mind

---

### Post by Cantello on 2021-04-08
> **Morbius1 said:**
> Never mind

Thanks for the reply - why remove it, it was really quite helpful! :-)
(testparm is also available on freebsd/TrueNAS)

---

