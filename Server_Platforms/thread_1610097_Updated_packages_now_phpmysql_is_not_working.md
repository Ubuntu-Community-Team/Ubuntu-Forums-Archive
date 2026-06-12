---
title: "Updated packages now php/mysql is not working"
date: 2010-10-31
forum: Server Platforms
---

### Post by Glencore on 2010-10-31
```
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysql.so' - /usr/lib/php5/20090626+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysqli.so' - /usr/lib/php5/20090626+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/pdo_mysql.so' - /usr/lib/php5/20090626+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sat Oct 30 23:23:58 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
```

This is the error.log from apache2.

I have checked for directories and the file it is looking for does not seem to exist. the only file in that folder is pdo.so

---

### Post by Glencore on 2010-10-31
i did the following: apt-get install php5-mysql and now the error is:

```
[Sun Oct 31 14:48:23 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/gd.so' - /usr/lib/php5/20090626+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mcrypt.so' - /usr/lib/php5/20090626+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun Oct 31 14:48:29 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by sikander3786 on 2010-10-31
Were they the regular updates that broke your php5-mysql or a version upgrade?

You are using 10.04 as I can see from your details? If correct, try

```
sudo aptitude install --reinstall php5-mysql
```

and post the output if any errors.

---

### Post by Glencore on 2010-10-31
> **sikander3786 said:**
> Were they the regular updates that broke your php5-mysql or a version upgrade?

You are using 10.04 as I can see from your details? If correct, try

```
sudo aptitude install --reinstall php5-mysql
```

and post the output if any errors.

it was apt-get upgrade

the server does seem to work because if i type:

192.168.1.6/index.php -> it loads the page

it i type 192.168.1.6 it asks me to download a file / does not show the page.

Is apache no longer defaulting documents (sorry I am used to using IIS)?

---

### Post by bingalls on 2011-11-11
I noticed a variation of this, which still happens on upgrade to 11.10 Oneiric Ocelot:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/idn.so' - /usr/lib/php5/20090626/idn.so: cannot open shared object file: No such file or directory in Unknown on line 0

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0

The problem is that Ubuntu has replaced these libraries, but does not disable the config files. Here's the solution:
:idea:
sudo bzip2 /etc/php5/conf.d/idn.ini
sudo bzip2 /etc/php5/conf.d/sqlite.ini

You can delete these files later, after testing.

---

### Post by nariub on 2011-12-27
upgraded from 11.04 to 11.10 today

overcame apparmor and mysql issues..
then noticed i was getting spammed.

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/idn.so' - /usr/lib/php5/20090626/idn.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262")

says delete or rename the extra files
the suggestion above effectively renames the files as it zips em

so i did as **bingalls** suggested and..

sudo bzip2 /etc/php5/conf.d/idn.ini
sudo bzip2 /etc/php5/conf.d/sqlite.ini

and she is now silent again.

---

