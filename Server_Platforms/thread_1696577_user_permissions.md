---
title: "user permissions"
date: 2011-02-27
forum: Server Platforms
---

### Post by jk111 on 2011-02-27
Hello,

I am running Ubuntu server with an SSH server installed.  How can I create an ubuntu user and give that user permissions to read and write only 1 specific folder so someone can log in through SSH using the new username and only put files in the folder I specify?

Thanks.

---

### Post by Kljuka on 2011-02-28
I don't think it is possible to limit access by changing user permissions.
You'll need to use jailkit to lock ssh user into chroot jail.

---

### Post by hawkmage on 2011-02-28
Create a group to be the group owner of the directory you want them to be able to write to.  
Create the directory with the group ownership of the group you just created and give group write access to it. 
Create the user and add the user to the group you just created.

The user will have to ability to read/write to their home directory, the directory you created and if you have any files/directories with write privileges granted to other.

If this fits your needs it is simpler that setting a chroot login.

---

