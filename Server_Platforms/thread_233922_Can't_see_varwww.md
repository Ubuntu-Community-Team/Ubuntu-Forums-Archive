---
title: "Can't see /var/www"
date: 2006-08-10
forum: Server Platforms
---

### Post by lugos on 2006-08-10
Hello,

I just installed Ubuntu Server 6.06 but I can't see the /var/www directory.  Did I miss something?

Any help would be greatly appreciated.

Thanks,
lugos

---

### Post by az on 2006-08-10
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The server install is just a base system.  You probably want to install the LAMP stack, or just apache2.

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by lugos on 2006-08-11
Thank you.

---

