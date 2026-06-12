---
title: "mysql error"
date: 2009-01-27
forum: Server Platforms
---

### Post by rompstar420 on 2009-01-27
Ok, I have Ubuntu 8.10 server.  Mysql doesn't want to start at boot, when I issue this command, it then works, but generates an error:

sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
root@dragonfly:/home/raymond# /usr/share/mysql/debian-start.inc.sh: line 68: /usr/bin/mysql: cannot execute binary file

when I type: mysql I get this error:

bash: /usr/bin/mysql: cannot execute binary file

So I am betting the binary is like 64 bit or something, there is something wrong messed up with it, but the instance is working because my photogallery that work using mysql for the database works without any problems.

I need to reinstall that but keep all my settings the same, how do I do that ?

---

### Post by cariboo on 2009-01-27
If you are running as root, you don't need sudo.

the error message tels you what the problem is:

> root@dragonfly:/home/raymond# /usr/share/mysql/**debian-start.inc.sh: line 68:** /usr/bin/mysql: cannot execute binary fil

I have bolded the pertinent part of the error message. The version of debian-start.inc.sh on my server only has 53 lines, so I can't check to see what the error is.

Jim

---

### Post by rompstar420 on 2009-01-27
anyways, I think my problem is that I have a 64bit/32bit mix version installed, I need to just have it all 32-bit, what is the best way to cleanly uninstall it and re-install it and keep the tables and all the settings same ?

ya, I know about sudo with root, just sometimes I am busy and don't notice that I am already logged in as root.

Thanks.

---

