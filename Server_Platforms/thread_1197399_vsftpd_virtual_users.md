---
title: "vsftpd virtual users"
date: 2009-06-26
forum: Server Platforms
---

### Post by insub2 on 2009-06-26
i can't seem to find anything that is up to date/for ubuntu on how to set up virtual users for vsftpd.  what i would like to do is set up virtual users with a base folder in my webroot.  i don't really care about restricting the v.users' access because i'm just using this for development (the users are to mimic the username/password for my webhost).

---

### Post by memor2000 on 2009-06-26
Hi,

maybe this can help you:

[http://www.howtoforge.com/vsftpd_mysql_debian_etch_p2](http://www.howtoforge.com/vsftpd_mysql_debian_etch_p2)

Remember to install pam_mysql.so module if you want to store user and password into a MySQL database.

To change the base folder, set local_root parameter. For example:

local_root=/var/www

and play with folder permission (vsftpd daemon run with his own user).

---

