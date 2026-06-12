---
title: "ser user permissions"
date: 2007-07-16
forum: Server Platforms
---

### Post by dunai on 2007-07-16
hi there!

i have just installed linux at my little home-server - and now i want my friend to have a user on it, so he can have some php-testing-webpage on it :) i have created the user "chris", so he's now having the home dir /home/chris - and in here i've put the dir wwwroot - which will contain his files.

The problem is, that if he ftp to the server - then he will be able of doing "cd .." and see the other files at the server - and might also have the rights to mess up with something.

Is there anyway to permit the user, only to see the home-dir?

---

### Post by Mr. C. on 2007-07-16
Which ftp server ?

vsftpd?   See **man vsftpd.con**f and search for **chroot_local_user**.
MrC

---

