---
title: "MySQL select into outfile - permissions?"
date: 2008-11-13
forum: Server Platforms
---

### Post by edpatterson on 2008-11-13
Information: trying to output queries into the /etc/squid/lists directory.
/etc/squid# ls -l
drwxrwxr-x 2 root mysql 4096 2008-10-09 10:52 lists
...

```

select * from urls where urlid >= 80 into outfile '/etc/squid/lists/urls.txt';

```
Can't create/write to file '/etc/squid/lists/eighties.txt' (Errcode: 13)
The file does not already exist. If I remove the path and just use the name 'eighties.txt' it is created in /var/lib/mysql/proxy with mysql being listed as the user and group.
Am I missing some basic file permission knowledge?

Ed

---

### Post by oneloveamaru on 2008-11-13
man mysqldump

---

### Post by DarkZen on 2009-01-28
> **edpatterson said:**
> Information: trying to output queries into the /etc/squid/lists directory.
/etc/squid# ls -l
drwxrwxr-x 2 root mysql 4096 2008-10-09 10:52 lists
...

```

select * from urls where urlid >= 80 into outfile '/etc/squid/lists/urls.txt';

```
Can't create/write to file '/etc/squid/lists/eighties.txt' (Errcode: 13)
The file does not already exist. If I remove the path and just use the name 'eighties.txt' it is created in /var/lib/mysql/proxy with mysql being listed as the user and group.
Am I missing some basic file permission knowledge?

Ed

Please check your apparmor config for mysqld (/etc/apparmor.d/usr.sbin.mysqld). Maybe something like:

/etc/squid/lists/eighties.txt w,

At the end of the file will do the trick.

---

### Post by ivomans on 2009-08-23
> **DarkZen said:**
> Please check your apparmor config for mysqld (/etc/apparmor.d/usr.sbin.mysqld). Maybe something like:

/etc/squid/lists/eighties.txt w,

At the end of the file will do the trick.

DarkZen: Thanks a lot, that solved my problem. I had same problem as reported by edpatterson.

---

### Post by hai2lp on 2010-06-12
:guitar:

Thanks guys,

I just do 
```
sudo gedit /etc/apparmor.d/usr.sbin.mysqld
```

and add 
```
 /var/www/codeigniter/assets/download/* w,
```

and
```
sudo service mysql restart
```

And that's it i can do easily SELECT INTO OUTFILE any filename

---

