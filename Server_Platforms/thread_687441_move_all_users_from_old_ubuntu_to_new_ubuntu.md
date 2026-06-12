---
title: "move all users from old ubuntu to new ubuntu"
date: 2008-02-04
forum: Server Platforms
---

### Post by monkeyking on 2008-02-04
Hi,
I got an old ubuntu 6.10 server.
And I'm installing ubuntu 7.10 on a new harddrive.

Is there some easy way,
to add all users from the old harddrive to the new harddrive,
including their files and password?

thanks in advance

---

### Post by rickyjones on 2008-02-04
You should be able to copy /home over to get the user files. 
Next, if I remember correctly, you should be able to copy /etc/passwd and /etc/shadow/passwd over to the new server and you should be fine.

I would test this before going production, however.

-Richard

---

### Post by koenn on 2008-02-04
> **rickyjones said:**
> 
I would test this before going production, however.
-Richard
yes, and probably better only copy 'real' users from the passwd and shadow file. 
You don't know wether UID's, passwords (?), ... for service accounts are identical between two servers - if they're not you don't want them changed/overwritten.  

You may also have to look at the groups file

---

