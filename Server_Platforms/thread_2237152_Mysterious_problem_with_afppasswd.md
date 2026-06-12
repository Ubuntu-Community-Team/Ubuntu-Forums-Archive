---
title: "Mysterious problem with afppasswd"
date: 2014-07-31
forum: Server Platforms
---

### Post by rbnsweden on 2014-07-31
Hi.
I have another thread about smb and macs not working properly... so while I wait for someone to point me in the right direction I thought I might as well give Netatalk another try.

But I would like to use it in the same manner as samba where I add a system user, but dont add a password in the system. Instead I add one with afppasswd. But I get a error message and I have been googling like crazy to solve this... but just cant find any good answer.

This is how it looks:
root@fileserver:~# afppasswd -a rbn
Enter NEW AFP password: 
/usr/lib64/cracklib_dict.pwd.gz: No such file or directory
PWOpen: No such file or directory

Anyone know what I can to next?

//rbn

---

