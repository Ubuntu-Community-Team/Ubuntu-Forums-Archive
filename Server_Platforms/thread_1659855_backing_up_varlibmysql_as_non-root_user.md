---
title: "backing up /var/lib/mysql as non-root user"
date: 2011-01-04
forum: Server Platforms
---

### Post by fro1269 on 2011-01-04
Hello

I'm using Ubuntu 10.04.1 x64 server edition

I would like to backup the /var/lib/mysql directory, but as a non-root user. 

I have created a group, added a user to the group, and have done a 

chown :groupname -r /var/lib/mysql

Now as the user I can view the /var/lib/mysql directory but I can not access the /var/lib/mysql/mysql or /var/lib/mysql/phpmyadmin directory, the permissions on these directories are 700.

If I were to change the permissions on the /var/lib/mysql/mysql and /var/lib/mysql/phpmyadmin would i experience issues? If there is a better way to do it other than changing those directory permissions I would appreciate it.

---

