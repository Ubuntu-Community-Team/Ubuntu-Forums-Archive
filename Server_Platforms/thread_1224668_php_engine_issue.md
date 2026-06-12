---
title: "php engine issue"
date: 2009-07-27
forum: Server Platforms
---

### Post by gishaust on 2009-07-27
hi 

I have a development lamp on my desktop. Overtime I have add different modules into the php config file. Yesterday I aptitude purge the entire lamp (except ubuntu). My issue is when I installed php from aptitude  it install fine but it will not work. I think I know the reason but I don't know how to fix it. 

below is from the apache error logs. Even after a purge and re-purge I keep getting this error. I think the php engine is looking for the modules and then shutting down is this right and how do i fix it
```

[Tue Jul 28 07:13:52 2009] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/curl.so' - /usr/lib/php5/20060613+lfs/curl.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysqli.so' - /usr/lib/php5/20060613+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_mysql.so' - /usr/lib/php5/20060613+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Jul 28 07:14:02 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch configured -- resuming normal operations

```

thanks gishaust

---

### Post by komputes on 2009-07-27
[LEFT]evilhamsterman has posted a comment which worked for himself and others in the following bug:

[https://bugs.edge.launchpad.net/ubuntu/+source/php-sqlite3/+bug/281714](https://bugs.edge.launchpad.net/ubuntu/+source/php-sqlite3/+bug/281714)


> /etc/php5/conf.d has two sqlite files one named sqlite3.ini and one named sqlite.ini. I am assuming the sqlite3.ini is a remainder from hardy. I removed the sqlite3.ini file and it no longer complains.
[/LEFT]

---

### Post by gishaust on 2009-07-28
Thanks that worked

---

