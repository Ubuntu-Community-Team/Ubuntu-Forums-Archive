---
title: "MySQL 5.1.26"
date: 2008-07-14
forum: Server Platforms
---

### Post by mrmonday on 2008-07-14
I'm trying to get MySQL 5.1.26 working on my server, but I can never get it to start.

```

$ sudo /etc/init.d/mysql start
Starting MySQL
 * Couldn't find MySQL manager (/usr/bin/mysqlmanager) or server (/usr/bin/mysqld_safe)

```

```

$ sudo /usr/local/mysql/5.1.26/libexec/mysqld --user=mysql
080714 14:34:30 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
libexec/mysqld: Unknown error 1146
080714 14:34:30 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
080714 14:34:30 [ERROR] libexec/mysqld: unknown option '--skip-bdb'
080714 14:34:30 [ERROR] Aborting

080714 14:34:30 [Note]

```

```

$ sudo /usr/local/mysql/5.1.26/bin/mysqld_safe --user=mysql
080714 14:33:37 mysqld_safe Logging to '/var/lib/mysql/octarineparrot.com.err'.
080714 14:33:37 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
080714 14:33:37 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

```

I've tried running these with various options, --basedir, --verbose, --debug, --log, --no-defaults and a couple of others, but can't get it to start. I've double checked all the permissions are right, and don't know what to do. Everything worked fine when I compiled from source for 5.1.25 using the exact same steps, although it seems something has changed as I can't get 5.1.25 or 5.1.26 to start.

I've been trying to get it back up for a couple of days now, so any help would be greatly appreciated. I would like to avoid using the packages from the repositories if possible (I know you're going to try and persuade me :P)...

---

### Post by mrmonday on 2008-07-14
To solve "[ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'" use --language=./share/mysql/english/.

To solve "[ERROR] libexec/mysqld: unknown option '--skip-bdb'" edit your my.cnf and comment out or remove skip-bdb. (use find / -name my.cnf if you don't know where it is)

I used my old databases, so the one about the table didn't affect me, I'm still working on the init script. (I may just give up and edit /etc/rc.local).

EDIT: The problem all along was the fact I was editing the wrong config file... *smacks head*

---

