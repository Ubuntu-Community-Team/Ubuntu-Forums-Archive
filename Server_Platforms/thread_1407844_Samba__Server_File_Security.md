---
title: "Samba / Server File Security"
date: 2010-02-15
forum: Server Platforms
---

### Post by baldychap on 2010-02-15
Hi All, 

I have a problem and I'm not sure where the problem lies. I'll explain...

I have Karmic Desktop running on a machine with a software RAID array. There is one folder in the array called 'DATA'. The permissions are set so the owner is 'user1' (the user that I log on to the computer with) with read/write access and there is a group called 'group1' which also has read/write access. 

I have samba running on the computer to share the DATA folder on the network. I have two users setup called 'user2' and 'user3' and these have rights to access the samba share. They are both members of 'group1'

Windows and Linux machines can connect and browse the share OK. The problem comes when they try to create folders/files or modify an existing file. 

For example, if user2 creates a folder on DATA they will not have access to the folder and cannot view it. If I browse the DATA folder from the server (logged on as user1) I can see the folder, but also cannot access it, If I look at the permissions I can see that the user ID of user2 is now the owner of the folder with create/delete files rights and the group 'user2' also has right to access the files only. 

So the problem is that any new files do not inherit permissions from the parent, as I would like, and then when user2, or user3, create files/folder neither they, or anyone else, can access them. 

I've checked samba and all the flags etc. seem to indicate that the users have full read/write access. So maybe it's a file permissions problem, but I'm not sure. 

Can anyone offer me some advice, any tips gratefully received!!

Thanks, 

Baldychap.

---

