---
title: "[SOLVED] Mysql Login"
date: 2007-12-08
forum: Server Platforms
---

### Post by tgs1952 on 2007-12-08
Hello,

I have never had a problem with an initial login to mysql on other systems - os x fedora and windows.

However, I am completely stymied on Ubuntu.

I repeatedly get 'Access denied' @localhost whether I am using a password or not.

Thanks in advance for any help.

---

### Post by k_grdn on 2007-12-08
Hi,

What command{,s} are you logging in with?

Have you set the initial passwd?

If so give details of how?

What address are you bound to? (listening on?, netstat -pant|grep mysql  or grep bind /etc/mysql/my.cnf)


Regards,

k_grdn

---

### Post by tgs1952 on 2007-12-08
Thanks for replying:

mysql -u mysql -p

mysql -u root -p

mysql -u myusername 

mysql -u myusername -p mypassword

all of the above prefaced by 'sudo'

here is the output from the command you suggested:
<code>
netstat -pant|grep mysql or grep bind /etc/mysql/my.cnf
grep: or: No such file or directory
grep: grep: No such file or directory
grep: bind: No such file or directory
/etc/mysql/my.cnf:# - "/etc/mysql/my.cnf" to set global options,
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
/etc/mysql/my.cnf:# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)
/etc/mysql/my.cnf:# This will be passed to all mysql clients
/etc/mysql/my.cnf:# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
/etc/mysql/my.cnf:socket                = /var/run/mysqld/mysqld.sock
/etc/mysql/my.cnf:# This was formally known as [safe_mysqld]. Both versions are currently parsed.
/etc/mysql/my.cnf:[mysqld_safe]
/etc/mysql/my.cnf:socket                = /var/run/mysqld/mysqld.sock
/etc/mysql/my.cnf:[mysqld]
/etc/mysql/my.cnf:user          = mysql
/etc/mysql/my.cnf:pid-file      = /var/run/mysqld/mysqld.pid
/etc/mysql/my.cnf:socket                = /var/run/mysqld/mysqld.sock
/etc/mysql/my.cnf:datadir               = /var/lib/mysql
/etc/mysql/my.cnf:language      = /usr/share/mysql/english
/etc/mysql/my.cnf:#log          = /var/log/mysql/mysql.log
/etc/mysql/my.cnf:#log_slow_queries     = /var/log/mysql/mysql-slow.log
/etc/mysql/my.cnf:log_bin                       = /var/log/mysql/mysql-bin.log
/etc/mysql/my.cnf:# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
/etc/mysql/my.cnf:# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
/etc/mysql/my.cnf:# chroot = /var/lib/mysql/
/etc/mysql/my.cnf:# ssl-ca=/etc/mysql/cacert.pem
/etc/mysql/my.cnf:# ssl-cert=/etc/mysql/server-cert.pem
/etc/mysql/my.cnf:# ssl-key=/etc/mysql/server-key.pem
/etc/mysql/my.cnf:[mysqldump]
/etc/mysql/my.cnf:[mysql]
/etc/mysql/my.cnf:#no-auto-rehash       # faster start of mysql but no tab completition
/etc/mysql/my.cnf:# See /usr/share/doc/mysql-server-*/README.Debian for more information.
/etc/mysql/my.cnf:!includedir /etc/mysql/conf.d/
</code>

---

### Post by jpkotta on 2007-12-12
Since I don't see where the alleged solution is, I will post what worked for me.  See [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html) for more info.

Stop mysql daemon.
```
sudo /etc/init.d/mysql stop
```

Start mysql daemon with no authorization checking.
```
sudo mysqld --skip-grant-tables --user=root &
```

Reset the passwd.  Change 'newpwd' to your own very secure, random, unguessable password.  It should be in single quotes.
```
sudo mysql
mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
    -> WHERE User='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 3  Changed: 0  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

```

Kill the unauthorized daemon.
```
sudo -i
kill $(cat /var/run/mysqld/mysqld.pid)
exit
```

Restart the normal mysql daemon.
```
sudo /etc/init.d/mysql start
```

Now you should be able to log in as user 'root'.
```
sudo mysql -u root -p
```

---

### Post by grappler on 2008-01-01
Hi Henry

I wasn't the originator of this thread but I came to it after trying many "solutions" on the web that just didn't work and getting pretty frustrated and annoyed about statements in tutorials and other threads that just were not true.  

So I followed yours through - to the letter - after a complete removal (purge) and reinstall of mysql in synaptic for ubuntu gutsy.
The version of mysql is  5.0. 

Your instructions certainly went better than most and behaved as predicted - unlike others - till I tried to restart mysql at the end where I got

bill@bill-t41:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
bill@bill-t41:~$ ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

Any attempt to login at this point as root with the password I'd set failed. 
There is no mention of debian-sys-maint in /etc/mysql/my.cnf. 
However there does seem to be  file called debian.cnf which is called by a start script debian-start both in the /etc/mysql directory that has debian-sys-maint as a user.
There is also what looks like a random password set for debian-sys-maint. I tried this user and password  but this didn't work either.


Then I tried killing the daemon again and restarted just using the command 

sudo mysqld

and then logging in as root using a password I must have set up a few months ago on an earlier install. It worked! Now as I said, I'd done a complete reinstall AND  I'd removed all config files I found in my home directory so I have no idea where mysql could have found this password. 

Any answers?

Thanks

Bill

---

### Post by spinteractive on 2008-01-17
Thanks jpcotta your advice was really helpfull!

S

---

### Post by ddb9587 on 2008-01-24
Thanks, worked perfectly with no glitches!

---

### Post by tosk on 2008-01-26
Great solution. :)

Thanks!

-- Tosk

---

