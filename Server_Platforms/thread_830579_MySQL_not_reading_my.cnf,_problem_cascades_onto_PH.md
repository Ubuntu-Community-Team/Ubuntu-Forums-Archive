---
title: "MySQL not reading my.cnf, problem cascades onto PHP"
date: 2008-06-16
forum: Server Platforms
---

### Post by borfast on 2008-06-16
The following is happnening on Ubuntu 8.04.

I'm having a weird problem with MySQL.

Although the server reads /etc/mysql/my.cnf correctly and listens on /var/run/mysqld/mysql.sock, the client tries to read my.cnf from other locations:

> borfast@computer:/etc$ strace mysql 2>&1 | grep cnf
stat64("/etc/my.cnf", 0xbfb75f44)       = -1 ENOENT (No such file or directory)
stat64("/home/borfast/.my.cnf", 0xbfb75f44) = -1 ENOENT (No such file or directory)
stat64("/usr/local/Zend/Core/etc/my.cnf", 0xbfb75f44) = -1 ENOENT (No such file or directory)

I'm not sure why it keeps trying the Zend directory, I used to have Zend Platform installed (and yes, everything was working fine after installing it) but now it's not installed anymore - still, mysql keeps trying to read my.cnf from there.

Since it can't read my.cnf from anywhere, the client defaults to /tmp/mysql.sock as the socket location, which is not where the server is listening and results in an error:

> borfast@computer:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

I tried symlinking /etc/my.cnf to the real /etc/mysql/my.cnf and it does "solve" (it's a hack, not a solution) the problem for the command line client... but then the fun part begins.

PHP also refuses to connect to MySQL because it also tries to use the wrong socket file but guess what: phpinfo() reports the correct socket location!

I even tried explicitly setting mysql.default_socket in php.ini but no good, still the same error:
> Can't connect to local MySQL server through socket '/tmp/mysql.sock'

I've been frying my brains up for the past 5 hours, trying to get this back working but still no luck.

If someone has a clue about what is wrong here and can point me in the right direction, I'd really appreciate it.

---

### Post by Cavalierdevache on 2008-06-16
Check the permissions on both my.cnf and php.ini to make sure they are at least 600. I have had mine set to 400 after updates twice and had that same problem.

---

### Post by borfast on 2008-06-16
Thanks, Cavalierdevache.
I have checked the permissions and both files are set correctly.

But meanwhile, things have changed. This morning, when I turned the machine on again, MySQL and PHP are both working fine, as long as I don't use the mysqli extension, otherwise PHP will choke and say > Warning: mysqli_error() [function.mysqli-error]: invalid object or resource mysqli in /path/to/script on line XX

The php5-mysql deb package is installed, and it contains both the mysql and mysqli extensions, so contrarily to what I though for a moment, it's not a problem with a missing package.

I just don't get it, it was working fine just a few days ago... :(

---

### Post by borfast on 2008-06-16
I fixed it.

It was just a matter of providing mysqli.default_socket in php.ini.

But the big question remains: why does it need this now, if it didn't before?

---

### Post by phantaszm on 2008-07-31
Did you figure out a way to get mysql to look at the configuration files in /etc/mysql/ ?

The symlink trick works to some extent, but like you said, it's a hack, not a real solution.

I'm using mysql replication and this problem is causing my replication server to break.

---

### Post by borfast on 2008-07-31
Sorry, I never found a solution for this, although I'll admit that I didn't look much longer and just used the symlink hack :(

Did you have Zend Platform installed at some point? I'm asking because since Zend Platform installs a bunch of stuff that messes with some configurations (PHP's configuration, at least), perhaps the problem lies there somewhere.

Somewhere along the way I thought that maybe this was due to a broken package in universe or multiverse but I have a laptop with the exact same repositories configuration and MySQL is working just fine, so that's not the problem.

I really have no clue about what could be wrong, sorry.

---

### Post by phantaszm on 2008-08-05
Oops, didn't realize you responded. Didn't get any emails saying someone had replied ;)

Anyway, I detailed everything I've tried in this thread
[http://ubuntuforums.org/showthread.php?t=876252](http://ubuntuforums.org/showthread.php?t=876252)

But to quickly respond to your questions
- Yeah I had Zend Platform installed and then uninstalled
- It looks like I ran through the same testing procedure as you (second machine, identical repos, but Zen was never installed on this second machine)
- I even did an md5 comparison on all the shared library files on both machines
- My only guess is that it's caused by some environment variable

---

### Post by phantaszm on 2008-08-05
I've found the solution!

Documented it here
[http://ubuntuforums.org/showthread.php?t=876252](http://ubuntuforums.org/showthread.php?t=876252)

---

