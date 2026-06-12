---
title: "I can use su command"
date: 2010-02-06
forum: Security
---

### Post by hoboy on 2010-02-06
I want to install java that required root priviledge.
when I open console then su i am asked for password 
when I give the password I use to login I get the following error.

chr@ubuntu:~$ su
Password: 
su: Authentication failure

---

### Post by Gadgetech on 2010-02-06
Use *sudo* before your java installation command. *sudo* works one command at a time, so you'll have to place it in front of every command that requires root privileges.

If you really want a root login shell, then use ```
sudo su
``` to become root.

---

### Post by hoboy on 2010-02-06
> **Gadgetech said:**
> Use *sudo* before your java installation command. *sudo* works one command at a time, so you'll have to place it in front of every command that requires root privileges.

If you really want a root login shell, then use ```
sudo su
``` to become root.

tks that has helped

---

### Post by lisati on 2010-02-06
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

