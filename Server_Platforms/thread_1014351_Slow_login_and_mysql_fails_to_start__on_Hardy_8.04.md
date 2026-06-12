---
title: "Slow login and mysql fails to start  on Hardy 8.04"
date: 2008-12-17
forum: Server Platforms
---

### Post by markmid on 2008-12-17
This server had been running smoothly until this morning when winscp was unable to login to make file transfers.  Logging in from a terminal or console was very slow.  The prompt would not return for several minutes after entering the password.  A sudo -i command would take several minutes to respond.  After logging in, the system responds quickly and a top or ps aux command does not indicate any processes are dominating the system resources.  We decided to reboot.  The reboot hung on starting mysql.  The log file shows:

Dec 17 09:56:30 prod mysqld_safe[6322]: started
Dec 17 09:56:45 prod /etc/init.d/mysql[6472]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Dec 17 09:57:45 prod mysqld[6475]: 081217  9:53:01  InnoDB: Started; log sequence number 0 43665
Dec 17 09:58:05 prod /etc/init.d/mysql[6472]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Dec 17 09:58:40 prod mysqld[6475]: 081217  9:53:01 [Note] /usr/sbin/mysqld: ready for connections.
Dec 17 09:59:20 prod /etc/init.d/mysql[6472]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Dec 17 09:59:55 prod mysqld[6475]: Version: '5.0.51a-3ubuntu5.4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Dec 17 10:00:35 prod /etc/init.d/mysql[6472]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Dec 17 10:01:36 prod /etc/init.d/mysql[6472]:

In spite of these errors, a mysql process is running and serving files to the webserver.  If I stop the mysqld, I am not able to restart it without a reboot and then I get the errors above.


I had done an apt-get upgrade on 12-10-08.  I reviewed the log files and found the following:

Starting MySQL database server mysqld       ^[[80G ^M^[[74G[ OK ]^M
 * Checking for corrupt, not cleanly closed and upgrade needing tables.^M

I also noted that some of the updates had been kept back.  So I did a dist-upgrade today.  These installed OK.  However, login remains slow and the mysql server fails on restart.

Did something change about the mysql and login configuration with the most recent updates?

Any suggestions about how to resolve these issues?

---

### Post by Drezard on 2008-12-17
Rebooted?

---

### Post by markmid on 2008-12-17
Rebooted twice.  No change.

---

### Post by markmid on 2008-12-18
Any ideas?  I sure could use some help.

---

### Post by markmid on 2008-12-18
My problem is solved.  I am not totally sure what the exact solution was.  I went through the following steps:
1.  I made a correction in the /etc/hosts file with no improvement.
2.  Network Upgrade for Ubuntu Servers (Recommended)
3.  Install update-manager-core if it is not already installed:
      sudo apt-get install update-manager-core
4.  Edit /etc/update-manager/release-upgrades and set:
      Prompt=normal
5.  Launch the upgrade tool:
      sudo do-release-upgrade
6. do-release-upgrade hung at several points, so I did
     dpkg --configure -a to restart the configuration.  mysql would hang each time I ran this and I would ctl-c past it until I got all of the packages configured except mysql.
7.  I rebooted and mysql failed on start up.  Logins continued to be slow after restarting.
8.  I ran /etc/init.d/mysql stop
    ps aux|grep mysql to make sure all mysql processes had stopped
    ran mysqld to start mysql manually.  It started OK.  I stopped it and then ran /etc/init.d/mysql start and it started OK.
9.  Logins are now back to normal.
10. I rebooted to make sure everything would work on restart and it did.

---

