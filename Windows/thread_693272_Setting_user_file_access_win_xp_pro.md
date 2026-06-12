---
title: "Setting user file access win xp pro"
date: 2008-02-10
forum: Windows
---

### Post by dynamethod on 2008-02-10
Hey there, ive created two user accounts for my winpx pro HD, an admin account and a limited user account

but i get a problem when trying to run peergaurdian 2 on the limited user account, says can only be run by an admin, however from the looks of things in the propertys etc etc of the peergaurdian exe it tells me that the limited user has access, but still wont let me run it?

baffled, any help much appreciated

---

### Post by gwoodard on 2008-02-18
Some programs may run on limited accounts but to install/uninstall them the Admin has that right only...(I made a limited account for my brother so that way he can't download any "unofficial" programs without me knowing)

---

### Post by bharadwaj on 2008-02-20
try gpedit.msc and set access or you can even try file encryption for NTFS artition

---

### Post by Existentialist on 2008-02-20
When PG2 loads, it has to load a driver since it blocks at the kernel level.  Unless you have set up the local security policy on your machine to allow limited users to install drivers you will have to run it as an administrator.

---

### Post by sayakb on 2008-02-22
First of all, click on Tools in the File menu and goto Folder Options. There, under the View tab, UNCHECK the "Use simple file sharing" checkbox. That unhides a security tab under the file property dialog.
Right click on the PG2's executable and click on the Security tab. There, click on Edit button and set the permissions for users.

---

