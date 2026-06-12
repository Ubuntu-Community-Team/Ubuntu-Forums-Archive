---
title: "personal encrypted virtual drive"
date: 2008-02-23
forum: Ubuntu Brainstorm
---

### Post by napsy on 2008-02-23
So here's my idea. It would be cool to have an option to create a personal encrypted virtual volume using dm-crypt.

The user could have an option in the user preferences to create a virtual disk volume and later mount that volume. On logout the volume would be automatically umounted. And automatically mounted again on successful login. The password for the volume would be the same as the user password. The virtual disk file would be located in the user's home dir. 

This would require a modification of gdm and possibly some other modules.

---

### Post by mrsteveman1 on 2008-02-25
Do you mean simply as a file store or do you mean as a way to store the home directory?

IE the difference between truecrypt and filevault (osx).

---

