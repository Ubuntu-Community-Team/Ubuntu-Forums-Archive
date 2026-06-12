---
title: "minimum required permissions for a user to use mysqldump"
date: 2011-03-10
forum: Server Platforms
---

### Post by fro1269 on 2011-03-10
Hello

I am trying to setup a mysql user whose sold purpose is to dump all of the databases on the server. What are the minimum required permissions for this user to accomplish this task?

---

### Post by SeijiSensei on 2011-03-10
If you're running the task on an automated basis, you'll probably want to run the backup task as the "mysql" user and place the files it creates in /var/lib/mysql or a new subdirectory there like /var/lib/mysql/backup.  Make sure any directory you create is owned by mysql:mysql and has 0700 permission like its parent.

To run mysqldump and get everything I'm pretty sure you'll need to run MySQL as its "root" user.  See [this thread](http://ubuntuforums.org/showthread.php?t=1580676) for more details, particularly [this](http://ubuntuforums.org/showpost.php?p=9882114&postcount=5).

---

