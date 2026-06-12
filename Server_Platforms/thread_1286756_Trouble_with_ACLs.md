---
title: "Trouble with ACLs"
date: 2009-10-09
forum: Server Platforms
---

### Post by tookey on 2009-10-09
So I have a server that is installed with Ubuntu 9.09.  I am using this machine as an ssh, samba, file server.

I have created a filesystem /data and in there several department directories.  Each directory is owned by the department groups that I have created, and all is working well.  Where I am running into a problem is when I want to use ACLs to give permission to one or two people that are not in the group that owns the file or directory.

IE...  The accouting group is owned by root:accounting 

drwxxrwxr-x+  13  root accounting   accounting

Now there is a file under accounting  (accounting/test.txt) that I want to add Kate RW access to so I use

setfacl -m u:kate:rw test.txt

when I check I see

# getfacl test.txt

#  file: test.txt
#  owner:  root
#  group:  accounting
user::rwx
user:kate:rw
group::rwx
mask::rwx
other::rx

Now when I open this file with Kate I cannot save it.  The only way to make this work is the add rw to other which completely negates what I want to accomplish.

Anyone got any ideas?

---

### Post by bartelomeus on 2009-10-09
Hi,

I have exacty the same problem with ubuntu-804-lts
Getfacl is showing rwx effectiverights for my named group in the folder, but a users who is a member of the group is still getting the " permission denied"  error when trying to create a file in the folder.
Sorry I couldn' t help you, hope someone else can. then my problem would also be resolved.

Regards Bart

---

### Post by rnodal on 2009-10-09
Just out of curiosity.

If you type
```
vim accounting/test.txt
```
Do you also get the error?

What are the default permissions for the accounting folder?

It may be related to the way kate "edit" files.

Just brainstorming :)

-r

---

