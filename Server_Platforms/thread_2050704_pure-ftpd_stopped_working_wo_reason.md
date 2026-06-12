---
title: "pure-ftpd stopped working w/o reason"
date: 2012-08-31
forum: Server Platforms
---

### Post by JBtje on 2012-08-31
Hello,
 
sinds 08/22/2012, pure-FTPD has stopped working. This while it has ran for over an year w/o problems.
The server is mostly setup like explained in [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3), so beside that pure-ftpd should run as standalone and with virtualchroot (the current default setup), nothing has changed.
 
The log shows me that the last FTP transaction was on 08/22/2012, though a new log file was created on 08/26/2012 (emty though).
I have tried restarting pure-ftpd, but not with any result.
Thus, i reinstalled pure-ftpd and restarted it...
```

root@server:/var/log/pure-ftpd# /etc/init.d/pure-ftpd start
root@server:/var/log/pure-ftpd# /etc/init.d/pure-ftpd-mysql start
Starting ftp server: Running: /usr/sbin/pure-ftpd-mysql-virtualchroot -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -H -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -b -Y 1 -A -8 UTF-8 -D -E -B

```
but, still pure-ftpd wont start (or stops directly) and does not listen to port 21.
 
How can i get pure-ftpd to get running?
**Serverinfo:** Linux ******* 2.6.32-40-server #87-Ubuntu SMP Tue Mar 6 02:10:02 UTC 2012 x86_64 GNU/Linux
with: ISPConfig Version: 3.0.3.3
 
Thank you,
JB

---

### Post by JBtje on 2012-09-03
I would find it hard to believe that noone knows how to get pure-ftpd running?
Are there any diagnostic tests i can run, any fixes i can apply, or even any other information i could provide to give more insight in the problem?
 
Thank you,
JB

---

### Post by SlugSlug on 2012-09-03
post the output of the logs

---

### Post by JBtje on 2012-09-03
Thank you for your reply!
The transfer log (which is the only log file in the /var/log/pure-ftpd/ directory, shows nothing but correct handled transfers, no errors:
```
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/blogstyle.php" 200 982
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/category.php" 200 1888
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/comments1.php" 200 3458
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/comments2.php" 200 3598
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/featured.php" 200 5375
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/includes/newsstyle.php" 200 7336
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/jquery.js" 200 31043
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/jquery.mousewheel.js" 200 2445
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/jquery.scrollable.js" 200 7109
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/slider.js" 200 1247
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/superfish.css" 200 956
82.**.**.** - ftp_blog [22/Aug/2012:16:56:34 +0200] "GET /var/www/clients/client4/web44/web/wp-content/themes/WhosWho/js/superfish.js" 200 3827
```
 
Attatched the result of: egrep -in "pure-ftpd" * > logs.txt, done in the directory /var/log/
 
I was not able to find more pure-ftpd logs.
Let me know if you need more logs.
 
JB

---

### Post by SlugSlug on 2012-09-03
try restart pureftp and then post output of 

tail -100 /var/log/messages

---

### Post by JBtje on 2012-09-03
```
root@main-server:/# service pure-ftpd restart
root@main-server:/# tail -100 /var/log/messages
Sep  2 07:59:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
root@main-server:/# /etc/init.d/pure-ftpd restart
root@main-server:/# /etc/init.d/pure-ftpd-mysql restart
Restarting ftp server: Running: /usr/sbin/pure-ftpd-mysql-virtualchroot -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -H -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -b -Y 1 -A -8 UTF-8 -D -E -B
root@main-server:/# tail -100 /var/log/messages
Sep  2 07:59:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
root@main-server:/#

```
Well.. thats not good :|
I've been unable to find a fix for this yet, however i've tried updating the system again via apt-get / aptitude. Aptitude was able to give me some new kernel files, which I installed.
After that, I tried starting pure-ftpd again:
```

root@main-server:/etc/init.d# /etc/init.d/pure-ftpd-mysql start
Starting ftp server: Running: /usr/sbin/pure-ftpd-mysql-virtualchroot -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -H -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -b -Y 1 -A -8 UTF-8 -D -E -B
root@main-server:/etc/init.d# /etc/init.d/pure-ftpd start
root@main-server:/etc/init.d# service pure-ftpd start
root@main-server:/etc/init.d# service --status-all
...
 [ - ]  pure-ftpd
 [ - ]  pure-ftpd-mysql
...

```
so, here is the new /var/log/messages
```

root@main-server:/etc/init.d# tail -100 /var/log/messages
Sep  2 07:59:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 08:03:57 main-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="370" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] rsyslogd was HUPed, type 'lightweight'.
Sep  3 13:20:50 main-server kernel: [8344781.246256] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.246259] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.426333] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.426336] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.491340] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.491348] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.511473] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.511476] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.676591] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.676595] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.692537] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.692541] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.709312] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.709315] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.723954] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:50 main-server kernel: [8344781.723957] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.606662] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.606665] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.627026] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.627029] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.631684] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.631687] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.646915] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:51 main-server kernel: [8344782.646917] grub-probe: sending ioctl 1261 to a partition!
Sep  3 13:20:54 main-server kernel: [8344786.010547] __ratelimit: 24 callbacks suppressed
Sep  3 13:20:56 main-server kernel: [8344787.028530] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Sep  3 13:20:56 main-server kernel: [8344787.029428] SGI XFS Quota Management subsystem
Sep  3 13:20:56 main-server kernel: [8344787.068418] JFS: nTxBlock = 7993, nTxLock = 63949
Sep  3 13:20:56 main-server kernel: [8344787.229269] NTFS driver 2.1.29 [Flags: R/O MODULE].
Sep  3 13:20:56 main-server kernel: [8344787.399200] QNX4 filesystem 0.2.3 registered.
Sep  3 13:20:56 main-server kernel: [8344787.620222] Btrfs loaded
Sep  3 13:20:56 main-server os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Sep  3 13:20:56 main-server 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Sep  3 13:20:56 main-server os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Sep  3 13:20:56 main-server os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Sep  3 13:20:56 main-server 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Sep  3 13:20:56 main-server os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests

```
JB

---

### Post by JBtje on 2012-09-03
well, since the internal system logger does not seem to be working correctly, i installed ubuntu 12.04 on a new server.
There, i faced the same problem: Pure-FTPD didn't want to start....
 
luckely, this time i did remember that i had to do one step... I set pure-FTPD to run its sessions over TLS, but did not provide the certificate!
```
echo 1 > /etc/pure-ftpd/conf/TLS
```
 
Undoing this (echoing 0), fixed the problem: pure-FTPD now starts on both my newly configured server, as the "old" one.
 
Thank you for your help and time!
JB

---

