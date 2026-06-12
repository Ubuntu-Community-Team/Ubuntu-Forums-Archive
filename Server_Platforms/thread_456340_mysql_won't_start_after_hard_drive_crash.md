---
title: "mysql won't start after hard drive crash"
date: 2007-05-27
forum: Server Platforms
---

### Post by dfreer on 2007-05-27
Hi,

I just had a hard drive on my server crash, rather suddenly so I'm not able to backup the data lost :( Fortunately, the hard drive only contained a /var/log partition, and the swap partition. I have currently fixed things by:

creating a new swap partition and enabling it.
symbolically linking a folder located on another reiserfs drive to /var/log, and recreating several log files by using sudo touch /var/log/log_filename. 

Now, the problem I am having is mysql refuses to start, with this error:
```
$ sudo /etc/init.d/mysql start
Password:
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

/var/run/mysqld/mysqld.sock no longer exists, although the directory is still there. This shouldn't have been effected, since the hard drive did not contain /var/run, only /var/log

Anyways, I'm trying to figure out how to restore mysql. I could do a uninstall/install, but I want to backup the databases first, and I can't do that due to mysql not working lol. So does anyone know where the databases are stored on the hard drive, so I could just copy them to back them up? Or has anyone seen this error before and know how to fix it?

---

### Post by benmoreassynt on 2007-05-27
Have you tried restarting it through Apache instead?

sudo apache2 -k restart (if you are using the default Ubuntu install via Synaptic or apt-get)

---

### Post by dfreer on 2007-05-27
That command simply executed, didn't provide any feedback (so dunno if it worked/died). Thanks for the idea though. Not exactly sure how apache can restart it, and didn't see any documentation on what the -k argument does.

Not quite sure why it died in the first place, other than swap partition being deleted... any ideas?

Mainly, I assume it will work if I reinstall it, but I need to backup the databases first. Since mysqldump doesn't work due to the aforementioned error, I just need to know where the databases are stored (can't find my php + mysql book :( think my little brother must have lost it). EDIT: nevermind, I tried google but forgot to search this forum in particular. found they are located in /var/lib/mysql/ on the third post :) but any ideas why mysql took a dump?

---

### Post by dfreer on 2007-05-27
Ok, figured it out:

I ran sudo mysqld and it gave me some more information, mainly that it was looking for /var/log/mysql/mysql-bin.index, which of course got hosed during the hard drive crash.
simply touching the file wouldn't work, btw.

I backed up my databases, and then uninstalled mysql-server, mysql-server-5.0, mysql-client-5.0.
I then just reinstalled them and voila! Didn't even need to restore the database backup!

ubuntu ftw!

---

