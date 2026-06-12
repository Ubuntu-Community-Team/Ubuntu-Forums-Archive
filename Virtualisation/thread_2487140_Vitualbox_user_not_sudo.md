---
title: "Vitualbox user not sudo"
date: 2023-05-24
forum: Virtualisation
---

### Post by bdrmachine on 2023-05-24
I installed Ubuntu 22 on windows 11  using Virtualbox 7.  My problem is I have no super user rights.  Without the use of sudo how can I fix this?  There doesn't seem to be any options in the virtualbox install, unless I missed it.  I changed the use name and password fields so I'm not sure why I do not have sudo access.

---

### Post by Frogs Hair on 2023-05-24
Hello and welcome to the forum.

Some actions require elevated permissions, can you be more specific about the problem ?

---

### Post by MAFoElffen on 2023-05-27
Elevated User in Windows Or Ubuntu? In Ubuntu, just like in Windows... Whatevr User you create first, is an Adminimstrative User, wiith the ability to run things with elevated rights an permissions. For example, in Ubuntu, to be able to use sudo, because that user is added to the sudoer group.

---

### Post by ajgreeny on 2023-05-27
Boot into your VM of Ubuntu, open a terminal and run command ```
groups
```
Now copy back here the output you see from that command using Code Tags please.
See Code Tags in my signature below for a How-to if you don't know what Code Tags are.

---

