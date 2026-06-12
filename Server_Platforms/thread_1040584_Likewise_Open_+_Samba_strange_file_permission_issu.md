---
title: "Likewise Open + Samba: strange file permission issue"
date: 2009-01-15
forum: Server Platforms
---

### Post by icklePhil on 2009-01-15
Hi

I know that there are a few other threads on quite similar problems here, but after reading them for a whole day and still not finding something helpful, I decided to start a new thread stating my situation...

I'm running an Ubuntu 8.04 Server in a Windows Server 2003 Domain. I managed to install Likewise Open from the Ubuntu repositories and also to join the machine to the domain successfully. To get samba to work, I followed the steps documented here:
[http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html](http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html)
So now the samba shares are visible from other Windows XP machines in the network and I can access them with domain user credentials.

ls -l of the share's parent folder (/mnt):
```

drwxrwxr-x+  8 MYDOMAIN\administrator MYDOMAIN\domain^users  4096 2009-01-15 22:11 sdb1
```

getfacl of share (/mnt/sdb1) which I applied recursively to all files and folders within:
```

# file: sdb1
# owner: MYDOMAIN\134administrator
# group: MYDOMAIN\134domain^users
user::rwx
group::rwx
group:MYDOMAIN\134domain^users:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:MYDOMAIN\134domain^users:rwx
default:mask::rwx
default:other::r-x
```

extract of smb.conf from the particular share:
```

[media]
comment = Media Files
path = /mnt/sdb1
public = no
writable = yes
browsable = yes
printable = no
inherit acls = yes
```

Samba version is 3.0.28a
Likewise Open version is I think 4.0.5 (found this with apt-cache, please tell me how to obtain the accurate version number)

The problem is now the following:
From a Windows XP machine, I connect to a share say as some domain user called "MYDOMAIN\user1".
On the share I open a subdirectory which is owned by some other domain user, maybe "MYDOMAIN\administrator".
As user1 I can successfully create a new file inside the folder, I can also edit it, but I can not rename it nor delete it.
I can also create a new directory and delete it again, but I can not rename it.

The problem doesn't occur in a directory which is already owned by user1.
The permissions which the new files get are correct (I checked with getfacl), so the samba option "inherit acls = yes" works.
The shares also work perfectly if I connect to them with a local user account from the Ubuntu machine (added local user permission to /mnt/sdb1 temporarily).
I can also log into the Ubuntu machine via ssh using the same domain users and then access these directories/files without problems.

So I think there is nothing wrong with the file system permissions, and probably also not with the share configuration. There must be something going wrong between samba and likewise services.

I would appreciate any help, if anyone needs some more extracts of log or config files, just name it.

Cheers, Phil

---

### Post by fang0654 on 2009-01-27
I had this same issue using Likewise Open 4.5.  I upgraded to the latest version (version 5) from their website, and it fixed the problem.

---

### Post by kashifharoon on 2009-06-24
I have been suffering from the same problem.  Today I finally found out that it is a bug of samba and it is resolved in version 3.3.1. 

I installed 3.3.6 and got it done.

Wish you good luck.

---

