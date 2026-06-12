---
title: "remote restrictions"
date: 2008-09-21
forum: Server Platforms
---

### Post by rbradshaw759 on 2008-09-21
hey,

ive install and set up a webserver with ubuntu server 8.04, when i log in remotely with programs like winscp under any user i have access to every file and folder on the system, how do i restrict it so the users only have access to their home folder apart from the admin. 

when i use an ftp program like filezilla the user only has access to their home folder.

thanks.

---

### Post by pdwerryhouse on 2008-09-21
Users will be able to see the rest of the filesystem, but they won't be able to write to it, so why does that matter?

And by default, they won't be able to see any files that they shouldn't, such as /etc/shadow.

If you have any data directories that they can see that you don't want them to, then just use chmod (along with chown and chgrp) to change the permissions so that they can't get to them.

---

