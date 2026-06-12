---
title: "Reset User password"
date: 2017-02-15
forum: Server Platforms
---

### Post by agarwaldvk on 2017-02-15
Hi Everyone


I have a home network server running Ubuntu 16.04 LTS. Everything works fine. One of the usershas forgotten her password - this is the Ubuntu user password. At this point, I believe that her Ubuntu user and her Samba user password would be the same.

How do I reset her password? Also, when she changes her Ubuntu user password, how do I ensure that her Samba user password is synced with her new Ubuntu user password?

Additionally, is there a way, I as the administrator can actually see her password and tell her what her password is?


P.S.
If I were to delete this user, can I create a new user with the same username as the one just deleted and assign this new user a password?  If I can, will this newly created user with the same credentials (username) have the same file and folder permissions as the older deleted one that was deleted?


Best regards


Deepak Agarwal

---

### Post by mastablasta on 2017-02-16
you can reset the OS user password: [SIZE=2]http://www.psychocats.net/ubuntu/resetpassword
[/SIZE]
samba and users:
[SIZE=2]https://www.samba.org/samba/docs/using_samba/ch09.html
[/SIZE]
samba password aministration: 
[SIZE=2]https://www.samba.org/samba/docs/man/manpages-3/smbpasswd.8.html
[/SIZE]
samba password reset:
[SIZE=2]https://ubuntuforums.org/showthread.php?t=1687199
[/SIZE]
btw, you have a complicated setup for a home server...

---

