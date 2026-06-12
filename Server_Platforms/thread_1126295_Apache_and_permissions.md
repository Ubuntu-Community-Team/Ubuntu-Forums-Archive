---
title: "Apache and permissions"
date: 2009-04-15
forum: Server Platforms
---

### Post by CryptiniteDemon on 2009-04-15
Okay basically I want to make apache able to edit files in my www directory.

How do I add apache to the same group as the owner of the directory?  

And don't tell me to chmod 777. That's stupid.


I have my own server set up on my personal computer AND I have an account on a web host.

When I look at the permissions on the web host, all files have permissions where only the owner can edit.  Groups & other users just have read access.  With these settings I'm able to use the PHP fopen() and fwrite() functions just fine.

However, on my home server, using the same permissions I can't use those same functions.  Basically i want it to where I can use fopen() and fwrite() like I do on the web host.

---

### Post by JochenJung on 2009-04-16
> **CryptiniteDemon said:**
> How do I add apache to the same group as the owner of the directory?

You can find and edit information, which user is in which groups in the file /etc/group

---

