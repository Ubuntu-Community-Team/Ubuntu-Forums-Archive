---
title: "Problems with moving mysql datadir"
date: 2008-10-11
forum: Server Platforms
---

### Post by SteinbergerNate on 2008-10-11
Ok, I've tried every howto out there on this subject and I still get a fail when I try to start mysql after moving my datadir. This is on a clean install of mysql with no new databases. 

Here's the last 10 lines of the syslog:

```
Oct 11 15:16:19 bassmannate-laptop mysqld[9415]: InnoDB: Apply batch completed
Oct 11 15:16:19 bassmannate-laptop mysqld[9415]: 081011 15:16:19  InnoDB: Started; log sequence number 0 43655
Oct 11 15:16:19 bassmannate-laptop mysqld[9415]: 081011 15:16:19 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
Oct 11 15:16:19 bassmannate-laptop mysqld_safe[9437]: ended
Oct 11 15:16:34 bassmannate-laptop /etc/init.d/mysql[9577]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 11 15:16:34 bassmannate-laptop /etc/init.d/mysql[9577]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 11 15:16:34 bassmannate-laptop /etc/init.d/mysql[9577]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 11 15:16:34 bassmannate-laptop /etc/init.d/mysql[9577]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 11 15:16:34 bassmannate-laptop /etc/init.d/mysql[9577]: 
Oct 11 15:17:02 bassmannate-laptop /USR/SBIN/CRON[9586]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

Now, I know that apparmor is not the culprit because I've changed the config file as well as shut down apparmor. If I move everything back to /var/lib/mysql and change the config files mysql loads just fine.

Edit: When I copied everything from the original directory, I preserved the privileges so mysql should be able to read and write to the new datadir.

---

### Post by cariboo on 2008-10-11
Here is a link to how one guy solved the problem:

[http://ubuntuforums.org/showthread.php?t=839386&highlight=move+mysql+db+directory](http://ubuntuforums.org/showthread.php?t=839386&highlight=move+mysql+db+directory)

Jim

---

### Post by SteinbergerNate on 2008-10-11
Nope. Same result.

---

### Post by SteinbergerNate on 2008-10-11
Ok, new update. syslog says that it can't connect to mysqld.sock so I looked and it's not anywhere on the system. I did a sudo find / -name mysql.sock and it came up empty handed. 

I also simply created the file as one thread I found suggested. Didn't work. In fact, when I went to go start mysql, the file disappeared.

---

### Post by SteinbergerNate on 2008-10-11
Yet another update. I don't know what I did but it works now.

---

### Post by moving on 2009-02-14
Hi... I'm find solutions... it's resly working fine for ubuntu...
here is two articles how to move mysql datadir
[how to move datadir in ubuntu, issue solution]("http://article.my-addr.com/?show=how_to_move_the_mysql_data_directory-ubuntu_change_datadir_issue")
and
[move datadir with using symlinks - the fastest way]("http://article.my-addr.com/?show=linux_ubuntu_change_datadir-move_mysql_database_to_other_path")

---

