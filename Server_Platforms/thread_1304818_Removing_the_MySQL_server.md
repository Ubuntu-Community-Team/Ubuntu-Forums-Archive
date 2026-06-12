---
title: "Removing the MySQL server"
date: 2009-10-29
forum: Server Platforms
---

### Post by 110686 on 2009-10-29
Hello,

I've caused a little problem on my Ubuntu Server...

I was working in PHPMyAdmin, when I accidentily removed all my MySQL users. So, no big deal I thought. Untill I couldn't log in PHPMyAdmin anymore. I decided to remove MySQL entirely. It appeared to be an easy problem, but even removing MySQL didn't work. 
Here is a piece of the command line:

```
stef@server1:~$ sudo apt-get remove --purge mysql-server-5.0
[sudo] password for stef:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-client-5.0
  libplrpc-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mysql-server-5.0*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 87.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 68209 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--purge):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ]
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: N                                                                             O)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Can you please help me?
Thanks anyway!

---

### Post by Xelfox on 2009-10-29
Im pretty sure this is due to the fact that removing Mysql doesn't remove the config files so doing a fresh install won't do much I will take a look at your configs in more detail but try reading around the net?

---

### Post by GarenP on 2009-12-29
I recently worked around this by manually editing the init script.

Be sure you manually kill mysql first if it's running for some reason, then find the 'stop' section in /etc/init.d/mysql and edit it out so it always returns success, e.g.:

'stop')
    exit 1
    ;;

Then uninstall/reinstall the package.

IMO the fact that this can happen and a user can be stuck being unable to uninstall/install/upgrade an existing system is a defect--this should never happen.

---

### Post by 110686 on 2009-12-30
Thanks for your help, but I actually solved it a long time ago. I was just entering the uninstall an install commands desperatly and suddenly it said: "No root password found, please enter one". I entered the same as my Ubuntu root password and it removed itself! Then I reinstalled MySQL and everything worked as expected.

---

