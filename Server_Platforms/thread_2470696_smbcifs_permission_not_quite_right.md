---
title: "smb/cifs permission not quite right"
date: 2022-01-08
forum: Server Platforms
---

### Post by jfaberna on 2022-01-08
I have a share on an Ubuntu 20.04 LTS system I treat as a NAS. I'd like to be able to edit and save files on that NAS from other PCs on the local network. My /etc/fstab mount statement on a remote pc is as follows:
```
//192.168.0.250/anonymous /mnt/anonymous cifs defaults,user=jim,password=xxxx,uid=jim,gid=users,dir_mode=0775,file_mode=0664 0 0
```

The Nemo file manager shows group = users, owner = jim, permissions = -rw-rw-r-- for the file I want to edit.

But if use 'nano' to try to edit a file, when I save before exiting, I get permission denied
```
nano /mnt/anonymous/mythbuntu-boot-drive-critical\ files/local-bin/mythtv-database-backup.sh
```
On the NAS is have /etc/samba/smb.conf for that share setup as:
```
[Anonymous]
path = /mnt/md0/samba/anonymous
browsable =yes
writable = yes
guest ok = yes
read only = no
force group = users
force user = jim
create mask = 0774
force directory mode = 2775
valid users = @users


```What am I missing?

---

### Post by jfaberna on 2022-01-08
So it seems that all the permissions set on my smb/cifs do not matter if the file on the NAS has owner set to 'root' and group 'users' with read-only set for 'group' which is the case for the file in questions. All the other files in that directory were owned jim:users. Once I created a test file from the remote PC a file in the same directory successfully, I figured it was a specific file issue.  

So smb/cifs does not show the real owner/group. Is this a security issue??

---

### Post by MAFoElffen on 2022-01-11
It is not a security issue in the perspective that the specific permissions denied access. It would have been if it allowed.

As file/directory group/user inherited permissions go, by rule of thumb, you can add to denying levels of access, you cannot add a level to access to what is already denied.

For example: If a User is a member of a group with has limited access to something, such as read-only to a file, you cannot give that member of that group (User X) write access to that file.

To correct that, did you change 'ownership' of that one file back to Jim:users?

---

### Post by jfaberna on 2022-01-11
> **MAFoElffen said:**
> It is not a security issue in the perspective that the specific permissions denied access. It would have been if it allowed.

As file/directory group/user inherited permissions go, by rule of thumb, you can add to denying levels of access, you cannot add a level to access to what is already denied.

For example: If a User is a member of a group with has limited access to something, such as read-only to a file, you cannot give that member of that group (User X) write access to that file.

To correct that, did you change 'ownership' of that one file back to Jim:users?Correct, that fixed the file issue.  It makes sense now that I think about it. I always get in trouble when I add files to that directory from the same system that host the SMB share. If I add the files as a SMB client, it always works.

Thanks,

---

