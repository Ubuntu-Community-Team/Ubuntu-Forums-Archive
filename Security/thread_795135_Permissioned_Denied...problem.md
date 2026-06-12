---
title: "Permissioned Denied...problem"
date: 2008-05-15
forum: Security
---

### Post by razlken on 2008-05-15
Hi, I've got a question more than a problem, and I'm sure that alot of people before me asked this same question;

I've been installing themes through the command terminal and that's fine. but the question i have why can't i open the folder /usr/share/themes? there is a cross over the icon and when opening it, it gives a permission denied message. i know i can simply use commands but, it just irritates me that my own computer denies me permission for simple things like copying stuff or opening a folder. is there a way to remove this kind of restriction once and for all, I'm the only user of this computer so i don't need it so please help, thanks in advance.

---

### Post by sisco311 on 2008-05-15
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can open your file browser as superuser (root). Alt+F2:
```
gksu nautilus
```I prefer to create a ***.***themes(it's prefixed with a period) directory in my home folder and copy the new themes there.(It's a hidden folder. You need to press Ctrl+H to see the hidden folders)

---

### Post by razlken on 2008-05-15
Thanks alot that is exactly what i needed...

---

