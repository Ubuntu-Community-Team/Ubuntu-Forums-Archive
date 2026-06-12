---
title: "chmod folder"
date: 2011-12-22
forum: Server Platforms
---

### Post by nunkstop on 2011-12-22
Hi everyone.

I created a group and list of user, and list of user is put onto that group

I created an empty folder for all user can create file in folder.

But i want file is just viewed by the user who created it and others can not.

How can i do that?

Help me :(

---

### Post by Shompol on 2011-12-23
chmod 700 filename

7 - read/write/execute for file owner
0 - for group
0 - for public

This cannot be made "by folder"
Each user is responsible for setting his own permissions with ```
umask 0077
```Another solution is to have a script with root permission to do it for users on that folder, but it would need to be started every time a user adds a file.

---

### Post by hawkmage on 2011-12-23
Just setting the perms to 700 is not going to solve the OP question.

To allow all of the users of a group to read/write in a directory you can make the directory owned by that group and then use "chmod 2770" to allow the group to access the diretoy and set the Set GID bit so that all files/directory created will be owned by the group.

---

