---
title: "smbpasswd file Where is it on my system?"
date: 2006-03-22
forum: Server Platforms
---

### Post by peanut butter on 2006-03-22
i am trying to use a program on my webserver for me to change user's passwords over the internet. its called changepassword (its on sf.net). and it wants to know where the smbpasswd file is (i want to change both the unix and samba passwords at the same time). thank you in advance for help.

---

### Post by Glut on 2006-03-22
There are a few files:
I assume it's after /etc/samba/smbpasswd
or alternatively (less likely):
 /usr/bin/smbpasswd

---

### Post by peanut butter on 2006-03-22
thats what i thought but that file dosn't exist. i go to natilius and it dosn't  exist.

---

### Post by peanut butter on 2006-03-22
this is the error i get:


SYSTEM password changed.
SAMBA password file doesn't exist!

Please notify your system administrator.

changepassword-0.9

---

