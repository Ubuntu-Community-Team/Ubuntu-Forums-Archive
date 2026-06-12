---
title: "Help with Samba permissions"
date: 2009-07-30
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2009-07-30
Alright, I've posted things about this several times in the past.  Maybe someone can help now.

I am using Ubuntu 8.04 with Samba version 3.028 as a file server.  I have a folder "Jobs" that everyone can read/write to.  Inside the Jobs folder there is a confidential file that only 4 users should be able to read or write to.  My problem is that when I put those 4 users in a group (we'll call it xyz) and set the permissions so that the xyz group has 7 access and the others have 0 access, the group members still can't access the file.  I set these permissions inside Ubuntu because I can't find a place to do it in Samba.

PLEASE help me!

---

### Post by bryanl on 2009-07-30
Someone will likely come in with the details that can get rather complex. The general concept is about the difference between how Unix and Windows manage security in shared file systems.

You will need to establish the users on the samba server which are completely separate from the host system's users. The protected folder will need to be its own share with access limited to those users in smb.conf. When a client mounts that share, it will need to provide an appropriate user ID and password either in a credentials file or in the mount command.

This is in contrast to NFS where you have to keep the UID and GID numbers consistent across the network in order to use Unix style permissions on mounted shares.

---

### Post by swerdna on 2009-07-30
> **47_MasoN_47 said:**
> Alright, I've posted things about this several times in the past.  Maybe someone can help now.

I am using Ubuntu 8.04 with Samba version 3.028 as a file server.  I have a folder "Jobs" that everyone can read/write to.  Inside the Jobs folder there is a confidential file that only 4 users should be able to read or write to.  My problem is that when I put those 4 users in a group (we'll call it xyz) and set the permissions so that the xyz group has 7 access and the others have 0 access, the group members still can't access the file.  I set these permissions inside Ubuntu because I can't find a place to do it in Samba.

PLEASE help me!
Can you please post the return you get from this command in a terminal window so we can see the share and the Samba permissions you've set in smb.conf:```
testparm -s
```
and also the Linux ownership and the Linux permissions inside the shared forlder as revealed by this command:```
ls -l /path_to/shared_folder
```

Then we could advise you in context of what you've set up so far.

---

### Post by 47_MasoN_47 on 2009-07-30
[Job]
	comment = Job
	path = /home/.../Company Shares/Job
	valid users = <all user names here>
	write list = <all user names here>
	read only = No
	hosts deny = 10.20.10.226


drwxrwxrwx 25 [admin] [all users group]     4096 2009-07-28 15:55 

That's the permissions set on all the folders right now.  If I change it so that it is drwxrwx--- so that in theory only the owner and group could read/write then nobody but the owner can read/write.  The other group members can't do anything with it.

---

### Post by swerdna on 2009-07-30
[LIST=1]
[*]Change the shared directory ownership back to normal user, normal group (e.g. billy:billy).
[*]Make a special group, e.g. rwgroup, and enrol the people into rwgrp who you want to have privileged access to the special file.
[*]Make the permissions on the shared directory to be 777.
[*]Create a directory inside the shared directory called e.g. "restricted".
[*]Make "restricted" to be owned by root and to have group = rwgr
[*]chown the directory "restricted" to drwxrwx--- (sudo chmod 770)
[*]make the share like this in smb.conf:```
[Job]
comment = Job
path = /home/.../Company Shares/Job
read only = No
hosts deny = 10.20.10.226
```
[*]Put the special file inside the restricted directory.
[/LIST]

Only the Samba users who are enrolled into the privileged group can penetrate the folder "restricted".

---

