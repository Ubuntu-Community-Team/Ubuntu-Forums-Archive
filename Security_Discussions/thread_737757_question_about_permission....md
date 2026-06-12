---
title: "question about permission..."
date: 2008-03-27
forum: Security Discussions
---

### Post by Mia_tech on 2008-03-27
I've come from a windows environment, and I love linux, but eventhough I've been using linux for quite sometime now, one thing I can't really understand the way is done is permission, could someone explain how could I give an specific user rwx permision on a folder of file

thanks

---

### Post by fmartinez on 2008-03-27
> **Mia_tech said:**
> I've come from a windows environment, and I love linux, but eventhough I've been using linux for quite sometime now, one thing I can't really understand the way is done is permission, could someone explain how could I give an specific user rwx permision on a folder of file

thanks

This is a general response for a general question: 

in the current directory: $ls -la        This command gives you something that looks like this: 

drwxr-xr-x username username      #### date time name.of.file

"d"= direcotory
1st 3 letters: permissions for the user r=read w=write x=execute
next 3: permissions for the group
last 3: permissions for other (global)

1st username = owner
nxt username = group

see the man files for: chgrp, chmod, chown
ex: $man chgrp

This will help you understand how to edit permission... 
REMEMBER: Permissions are for that specified file/directory it doesn't include sub-directories like windows....

---

### Post by scottro on 2008-03-27
A friend wrote a nice little thing on it that finally made it clear to me. I have it up at [http://home.nyc.rr.com/computertaijutsu/chmod.html](http://home.nyc.rr.com/computertaijutsu/chmod.html)

You can use the -R flag (as in recursive) to make all the files currently in a directory have the permissions you want, however, new files won't necessarily observe those permissions.

---

### Post by tubasoldier on 2008-03-27
A quick and easy answer is to open a terminal and go into the folder you want to share.
Type in:
```
chmod +755
```
This will give everyone read acess.

---

### Post by Mia_tech on 2008-03-28
thanks all for the post and links, but I understand what rwx means and all that, my concern is how you go about setting it up for a specific user which is not the root, so you can not change the owner of the file , b/c then root will not be the owner anymore, am I right?.. or if you chown to declare a new owner that user becomes owner of the file along with root....or maybe if you don't want to give to much right to a user you just put him in a group and give access at the group level
hope that was too many questions

thanks

---

