---
title: "Mysql remote access problems"
date: 2010-02-03
forum: Server Platforms
---

### Post by NickL87 on 2010-02-03
Hi

I have a mysql server setup on my laptop together with an apache server running a webapp on an address like the following:

[http://localhost/myapp](http://localhost/myapp)

which works fine, however when i access the app by ip ([http://127.0.0.1/myapp](http://127.0.0.1/myapp)) the mysql denies access and php gives an error like the following:

```
Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/nick/Public/myapp/Classes/email_support_class.php on line 101
```

The relevant part of my my.cnf file looks like the following:

```

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
```

Do any of you have an idea for what I could do to get this working?

---

### Post by NickL87 on 2010-02-04
Found the answer myself :-) It was a php code error

---

