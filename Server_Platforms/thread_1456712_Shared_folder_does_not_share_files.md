---
title: "Shared folder does not share files"
date: 2010-04-17
forum: Server Platforms
---

### Post by kfleten on 2010-04-17
I have a shared folder on my Edubuntu 9.10 server that can be accessed from network or by any user on the server. All users can read and write to the folder - but only what they selves has written. All files created by others, is locked. 

I want that any files that is moved or copied to this folder by anyone should instantly be available to anybody. Is there a "sticky"-option or something ?

---

### Post by Morbius1 on 2010-04-17
You could add "inherit permissions" to the share definition.

As an example, Let's say the target is /home/Shared

You'd change the permissions to 777: **sudo chmod -R 0777 /home/Shared**

Then in the share definition you would add the following line:

```
inherit permissions = yes
```Then restart samba

New directories and files will inherit the mode of the parent directory.

---

