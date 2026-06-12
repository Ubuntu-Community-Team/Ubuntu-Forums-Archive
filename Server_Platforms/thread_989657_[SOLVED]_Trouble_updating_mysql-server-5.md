---
title: "[SOLVED] Trouble updating mysql-server-5"
date: 2008-11-21
forum: Server Platforms
---

### Post by jay019 on 2008-11-21
Hi,

Tried updating mysql from the update manager, but it is having problems updating mysql-server-5. 

The error that seems to pin point the problem is...
"Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)"

So I guess the question is, how do I give debian-sys-maint full access again. I dont remember changing anything other than the root password for mysql.

Jay

---

### Post by jay019 on 2008-11-21
Full output from update-manger / synaptic...

```

Preconfiguring packages ...
(Reading database ... 154932 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.1 (using .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld
   ...done.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by jay019 on 2008-11-22
Never mind, found it.
For anyone else stuck in my predicament...

look in /etc/mysql/deban.cnf for the default password. 
update it in mysql. 
profit.

---

### Post by PTo on 2008-11-24
Thanks for telling how you solved the problem. However, for the less experienced mysql users: how did you update the password? ;) Doesn't this change the password you chose when installing it?

---

### Post by jay019 on 2008-11-24
Good point...

To update the password I used phpmyadmin and logged on as root using the root password I set. Then I clicked on the link for "Privileges", clicked on the edit button for the "debian-sys-maint" user, then changed the password in the "Change Password" section to the password I found in /etc/mysql/deban.cnf

If anyone has any troubles fixing the same issue feel free to PM me for help.

:thumbsup:

---

