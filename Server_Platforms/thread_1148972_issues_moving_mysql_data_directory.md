---
title: "issues moving mysql data directory"
date: 2009-05-04
forum: Server Platforms
---

### Post by bryder on 2009-05-04
Hello all,
I'm trying to move the MySQL datadir. 
In the my.cnf file I changed the line

datadir    = /var/lib/mysql

to

datadir    = /data/mysql

and I copied all the file using the following

sudo cp -Rp /var/lib/mysql /data/mysql

but when I restart the MySQL server it fails. The syslog has the following:
-------
May  4 16:49:06 extranet mysqld_safe[3283]: started
May  4 16:49:06 extranet mysqld[3286]: 090504 16:49:06 [Warning] Can't create test file /data/mysql/extranet.lower-test
May  4 16:49:06 extranet mysqld[3286]: 090504 16:49:06 [Warning] Can't create test file /data/mysql/extranet.lower-test
May  4 16:49:06 extranet kernel: [  243.597416] type=1503 audit(1241480946.286:11): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/data/mysql/extranet.lower-test" pid=3285 profile="/usr/sbin/mysqld"
May  4 16:49:06 extranet kernel: [  243.599500] type=1503 audit(1241480946.286:12): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/data/mysql/extranet.lower-test" pid=3285 profile="/usr/sbin/mysqld"
May  4 16:49:06 extranet mysqld[3286]: 090504 16:49:06  InnoDB: Operating system error number 13 in a file operation.
May  4 16:49:06 extranet mysqld[3286]: InnoDB: The error means mysqld does not have the access rights to
May  4 16:49:06 extranet mysqld[3286]: InnoDB: the directory.
May  4 16:49:06 extranet mysqld[3286]: InnoDB: File name ./ibdata1
May  4 16:49:06 extranet mysqld[3286]: InnoDB: File operation call: 'open'.
May  4 16:49:06 extranet mysqld[3286]: InnoDB: Cannot continue operation.
May  4 16:49:06 extranet kernel: [  243.677222] type=1503 audit(1241480946.366:13): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=103 name="/data/mysql/ibdata1" pid=3285 profile="/usr/sbin/mysqld"
May  4 16:49:06 extranet mysqld_safe[3293]: ended
May  4 16:49:21 extranet /etc/init.d/mysql[3443]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May  4 16:49:21 extranet /etc/init.d/mysql[3443]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May  4 16:49:21 extranet /etc/init.d/mysql[3443]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May  4 16:49:21 extranet /etc/init.d/mysql[3443]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May  4 16:49:21 extranet /etc/init.d/mysql[3443]:
------
It seems to say that the file permissions are wrong but even with chmod 777 I get the same message. This seems like it should be an easy thing to do but I can't seem to get it running. Any ideas? Thanks for any help you can give.

- Dave

---

### Post by cariboo on 2009-05-05
Just a s a point of reference about mysql permissions, have look at the screenshot. I'm running Ubuntu cli in Vbox, and haven't set up the mouse yet, so I can't copy and paste.

---

### Post by bryder on 2009-05-05
Thanks for that. I checked my permissions and they all look fine.

Here is another part of the puzzle. If I mount a drive directly onto the original data location (/var/lib/mysql) it works fine. If I then move the mount to /data/mysql it no longer works. Is there some directory sub-tree restriction in MySQL that I don't know about?

Thanks for any advice you can give.

- Dave

---

### Post by Zeosa on 2009-05-06
What are the permissions on the /data/mysql directory itself?

Should by mysql:mysql with permissions of 755

---

