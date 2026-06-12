---
title: "MySQL reinstallation problem"
date: 2008-06-30
forum: Server Platforms
---

### Post by satimis on 2008-06-30
Hi folks,


My 2 Ubuntu boxes, 6.06 and 7.10, have been suffering on MySQL problem after upgrade.  I did rescue the 6.06 box by removing/reinstalling MySQL.  This box seems now running normal.  However to my suprise the same steps couldn't work on the 7.04 box.

On reinstallation;


# apt-get install mysql-server mysql-client```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.5MB of archives.
After unpacking 96.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
grave bugs of mysql-server-5.0 ( -> 5.0.38-0ubuntu1.4) <done>
 #480292 - CVE-2008-2079: mysql allows local users to bypass certain privilege checks (Fixed: mysql-dfsg-5.0/5.0.51a-7)
Summary:
 mysql-server-5.0(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]  n
****************************************************************************
****** Exit with an error by force in order to stop the installation. ******
****************************************************************************
E: Sub-process if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi returned an error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi

```

Can any folk shed me some light?  TIA


B.R.
satimis

---

### Post by cpetercarter on 2008-06-30
The terminal warned you of a bug in mysql-server ("allows local users to bypass certain privilege checks"), and asked you whether you wanted to continue. You typed "n" ("no"); or the terminal inserted "n" and you accepted it by pressing Enter. Is that what you meant to do?

---

### Post by satimis on 2008-06-30
> **cpetercarter said:**
> The terminal warned you of a bug in mysql-server ("allows local users to bypass certain privilege checks"), and asked you whether you wanted to continue. You typed "n" ("no"); or the terminal inserted "n" and you accepted it by pressing Enter. Is that what you meant to do?
Hi preeminent,


I typed "n" myself.  Because I have no idea what kind of bug it is.  But I don't have this bug on reinstalling MySQL on Ubuntu 6.06 box.  It surprises me.


B.R.
satimis

---

### Post by cpetercarter on 2008-06-30
A google search suggests that the bug was identified in May and fixed early in June. I do not know whether the version of mysql-server in the repositories contains the relevant patch or not, but if it doesn't I guess that an update will follow shortly.

---

### Post by satimis on 2008-06-30
> **cpetercarter said:**
> A google search suggests that the bug was identified in May and fixed early in June. I do not know whether the version of mysql-server in the repositories contains the relevant patch or not, but if it doesn't I guess that an update will follow shortly.
Hi cpetercarter,


Performed following test;


$ sudo apt-get update
No complaint

$ sudo apt-get install mysql-server mysql-client```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not installable
E: Broken packages

```

Situation is even worst than before.


$ sudo apt-get install -f

doesn't help.


satimis

---

### Post by satimis on 2008-06-30
Hi folks,


Solved the problem on reinstalling MySQL with aptitude.


$ sudo aptitude install mysql-server mysql-client```

.....
.....
Setting up libdbd-mysql-perl (3.0008-1build1) ...
Setting up mysql-client-5.0 (5.0.38-0ubuntu1.4) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1.4) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
 * Root password is blank.  To change it use:
 * /etc/init.d/mysql reset-password

Setting up mysql-client (5.0.38-0ubuntu1.4) ...
Setting up mysql-server (5.0.38-0ubuntu1.4) ...

```
Now MySQL starts without problem.


Run
$ dpkg -l | grep mysql

to compare the packages installed with those removed previously.  Found following packages missing;

mysql-admin
mysql-admin-common
libmysqlclient15-dev
php5-mysql


Run aptitude to install them.


I think the only reason of failure previously in running "apt-get install" is apt not taking care of dependencies.


$ mysql -uroot mysql```

Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.38-Ubuntu_0ubuntu1.4-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>quit
Bye

```
MySQL is working now.


$ sudo mysqladmin -u root password abcde
No complaint.


$ sudo mysqladmin -u root -h localhost password xyz```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

I doubt whether it needs running this command???


$ sudo /etc/init.d/mysql restart```

Password:
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```

MySQL is working normal now.


B.R.
satimis

---

