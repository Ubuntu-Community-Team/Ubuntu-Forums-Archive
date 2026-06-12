---
title: "Samba: Inheriting permissions does not work"
date: 2014-09-21
forum: Server Platforms
---

### Post by silentcreek on 2014-09-21
Hi,

I set up a samba share with the option 'inherit permissions = yes'. However, that does not work as expected. The permissions are not inherited from the parent directory but resemble the standard file creation mask for that share.

Background: The share is accessible by two users which are in the same group. By default, both users should have read and write access on that share, so the file create mask is set to 0660 and the directory create mask is set to 0770. That works works fine. Within that share I'd like to have one specific subfolder, that only user1 can read&write, but user2 can only read it. I set the permissions for that specific directory accordingly and it works fine, too. But I would also like to have permissions for new files and subfolders within this directory to be inherited, rather than being the standard read/write permissions. That doesn't work. A new subdirety within that directory will still be created with the 0770 permissions instead of 0750 (and files with 0660 instead of 0640). The clients are Windows 7 clients. I didn't fiddle with acls, because the standard unix permissions are sufficient for my use.

Here's the share definition form smb.conf:
```
[PublicFolder]
path = /media/external_drive/PublicFolder/
read only = no
public = no
writeable = yes
valid users = cifsusr1 cifsusr2
create mask = 0660
directory mask = 0770
inherit permissions = yes
```

Why does inherit permissions not have the desired effect?

Thanks,

Timo

---

### Post by bab1 on 2014-09-22
> **silentcreek said:**
> Hi,

I set up a samba share with the option 'inherit permissions = yes'. However, that does not work as expected. The permissions are not inherited from the parent directory but resemble the standard file creation mask for that share.

Background: The share is accessible by two users which are in the same group. By default, both users should have read and write access on that share, so the file create mask is set to 0660 and the directory create mask is set to 0770. That works works fine. Within that share I'd like to have one specific subfolder, that only user1 can read&write, but user2 can only read it. I set the permissions for that specific directory accordingly and it works fine, too. But I would also like to have permissions for new files and subfolders within this directory to be inherited, rather than being the standard read/write permissions. That doesn't work. A new subdirety within that directory will still be created with the 0770 permissions instead of 0750 (and files with 0660 instead of 0640). The clients are Windows 7 clients. I didn't fiddle with acls, because the standard unix permissions are sufficient for my use.

Here's the share definition form smb.conf:
```
[PublicFolder]
path = /media/external_drive/PublicFolder/
read only = no
public = no
writeable = yes
valid users = cifsusr1 cifsusr2
create mask = 0660
directory mask = 0770
inherit permissions = yes
```

Why does inherit permissions not have the desired effect?

Thanks,

Timo

I don't believe you can do what you want without ACL's.  I believe the parameter inherit permissions applies to the root directory of the share only.  It looks like it is really there for use in the [homes] share.  

If you want to change the individual users permissions in a common group of a sub-directory of the share or any of the contents you should use ACL's.  If you are going to use Windows style permissions structure then you will need Windows style ACL's.

The default Linux UID/GID and permissions structure is not fine grained enough to permit users in the same group (GID) to have differing permissions.  

Personally I use different shares for different permissions structures.

---

### Post by silentcreek on 2014-09-25
Ok, thanks for the info. I enabled acls now and that works very well.
I thought about creating a seperate share for that but I don't want to create too many shares that will be mounted as drives in Windows at boot time.

Regards,

Timo

---

