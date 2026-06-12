---
title: "Evolution - Mail client on LAN fails to login"
date: 2009-05-14
forum: Server Platforms
---

### Post by satimis on 2009-05-14
Hi folks,


Ubuntu 8.04


Unable to login

/# tail /var/log/mail.log```

May 14 07:58:45 vz2 imapd: Connection, ip=[::ffff:192.168.0.100]
May 14 07:58:48 vz2 last message repeated 2 times
May 14 07:59:05 vz2 postfix/smtpd[7981]: connect from unknown[192.168.0.100]
May 14 07:59:05 vz2 postfix/smtpd[7981]: disconnect from unknown[192.168.0.100]
May 14 07:59:06 vz2 postfix/smtpd[7981]: connect from unknown[192.168.0.100]
May 14 07:59:06 vz2 postfix/smtpd[7981]: disconnect from unknown[192.168.0.100]
May 14 07:59:16 vz2 imapd: Connection, ip=[::ffff:192.168.0.100]
May 14 07:59:27 vz2 imapd: LOGIN FAILED, user=satimis, ip=[::ffff:192.168.0.100]
May 14 07:59:39 vz2 imapd: LOGIN FAILED, user=satimis, ip=[::ffff:192.168.0.100]
May 14 07:59:50 vz2 imapd: LOGOUT, ip=[::ffff:192.168.0.100], rcvd=100, sent=524

```

Please advise where to check and how to fix the problem.  TIA


B.R.
satimis

---

### Post by a9k3d on 2009-05-14
It would help to know which IMAP server you are using.
I suspect that the "auth" (dovecot-auth, courierauth) part of your installation is not running.
I'd restart the IMAP server and the "auth". Then **ls -ltr /var/log** which will show all the log files that just changed at the bottom of the list. You may find clues in mail.info, auth.log, and daemon.log or others that changed.

---

### Post by satimis on 2009-05-14
> **a9k3d said:**
> It would help to know which IMAP server you are using.
I suspect that the "auth" (dovecot-auth, courierauth) part of your installation is not running.
I'd restart the IMAP server and the "auth". Then **ls -ltr /var/log** which will show all the log files that just changed at the bottom of the list. You may find clues in mail.info, auth.log, and daemon.log or others that changed.

Hi a9k3d,


OpenVZ virtual machine
Host - Ubuntu 8.04
Guest (VE) - Mail server on Ubuntu 8.04


Thanks for your advice.

I was following following document building this mail server running virtual domain
[http://flurdy.com/docs/postfix/edition7.html](http://flurdy.com/docs/postfix/edition7.html)


The server can send and receive mails.  But remote mail client can't login to download mails.


After starting the guest (Mail server)

root@vz2:/# ls -ltr /var/log```

total 4836
-rw-rw-r-- 1 root        utmp         0 May 13  2008 btmp.1
drwxr-xr-x 2 root        root      4096 May 13  2008 fsck
-rw-r----- 1 root        adm         31 May 13  2008 boot
-rw-r----- 1 syslog      adm          0 May 13  2008 lpr.log
drwxr-sr-x 2 news        kmem      4096 May 13  2008 news
-rw-r----- 1 syslog      adm          0 May 13  2008 kern.log
-rw-r--r-- 1 root        root         0 May 13  2008 bootstrap.log
-rw-r----- 1 mysql       adm          0 Apr 23 03:45 mysql.err
-rw-r----- 1 syslog      adm        251 Apr 23 04:58 debug.0
drwxr-s--- 2 Debian-exim adm       4096 Apr 25 06:25 exim4
-rw-r----- 1 syslog      adm       3371 Apr 26 05:39 daemon.log.1.gz
-rw-r----- 1 syslog      adm        334 Apr 26 06:45 mail.warn.1.gz
-rw-r----- 1 syslog      adm       7690 Apr 26 06:45 mail.log.1.gz
-rw-r----- 1 syslog      adm       7691 Apr 26 06:45 mail.info.1.gz
-rw-r----- 1 syslog      adm        333 Apr 26 06:45 mail.err.1.gz
-rw-r----- 1 syslog      adm        731 Apr 26 06:45 messages.1.gz
-rw-r----- 1 syslog      adm          0 Apr 26 06:47 debug
-rw-r----- 1 syslog      adm       5430 Apr 26 06:47 auth.log.1.gz
-rw-r----- 1 syslog      adm      11694 Apr 30 06:25 syslog.6.gz
-rw-r----- 1 mysql       adm         20 Apr 30 06:29 mysql.log.7.gz
-rw-r--r-- 1 root        root      2354 May  1 15:11 aptitude.1.gz
-rw-r----- 1 root        adm     151123 May  1 15:11 dpkg.log.1
-rw-rw-r-- 1 root        utmp   1868928 May  2 06:22 wtmp.1
-rw-r----- 1 syslog      adm      11591 May  2 06:40 syslog.5.gz
-rw-r--r-- 1 root        root      5468 May  2 06:40 shorewall-init.log.3.gz
-rw-r----- 1 mysql       adm         20 May  2 06:54 mysql.log.6.gz
-rw-rw-r-- 1 root        utmp         0 May  2 06:54 btmp
drwxr-xr-x 2 root        root      4096 May  2 06:54 apt
-rw-r----- 1 syslog      adm       2797 May  3 00:03 user.log.0
-rw-r----- 1 root        adm       6328 May  3 05:49 shorewall-init.log.2.gz
-rw-r----- 1 syslog      adm      51222 May  3 05:49 daemon.log.0
-rw-r----- 1 syslog      adm       4929 May  3 05:49 mail.err.0
-rw-r----- 1 syslog      adm       6133 May  3 05:49 mail.warn.0
-rw-r----- 1 syslog      adm     237781 May  3 05:50 mail.log.0
-rw-r----- 1 syslog      adm     237781 May  3 05:50 mail.info.0
-rw-r----- 1 syslog      adm       6505 May  3 06:25 syslog.4.gz
-rw-r----- 1 mysql       adm         20 May  3 06:27 mysql.log.5.gz
-rw-r----- 1 syslog      adm      11033 May  3 06:27 messages.0
-rw-r----- 1 syslog      adm     193502 May  3 06:47 auth.log.0
-rw-r----- 1 syslog      adm       5917 May  4 06:25 syslog.3.gz
-rw-r----- 1 mysql       adm         20 May  4 06:34 mysql.log.4.gz
-rw-r----- 1 syslog      adm      11381 May  7 06:39 syslog.2.gz
-rw-r----- 1 mysql       adm         20 May  7 06:50 mysql.log.3.gz
-rw-r----- 1 root        adm      14845 May  7 23:48 shorewall-init.log.1.gz
-rw-r----- 1 syslog      adm       6184 May  8 06:25 syslog.1.gz
-rw-r----- 1 mysql       adm         20 May  8 06:32 mysql.log.2.gz
-rw-r--r-- 1 root        root      4321 May  8 22:31 aptitude
-rw-rw-r-- 1 root        utmp   1461460 May  8 22:31 lastlog
-rw-r--r-- 1 root        root    120120 May  8 22:31 faillog
-rw-r----- 1 root        adm       5431 May  8 22:31 dpkg.log
drwxr-xr-x 2 clamav      clamav    4096 May 11 06:37 clamav
drwxr-x--- 2 root        adm       4096 May 11 06:37 apache2
-rw-r----- 1 mysql       adm         20 May 11 06:37 mysql.log.1.gz
-rw-r----- 1 root        adm         28 May 13 08:27 dmesg.4.gz
-rw-r----- 1 root        adm         28 May 13 13:19 dmesg.3.gz
-rw-r----- 1 root        adm         28 May 13 23:20 dmesg.2.gz
-rw-r----- 1 syslog      adm       4267 May 13 23:21 mail.err
-rw-r----- 1 root        adm         28 May 14 04:02 dmesg.1.gz
-rw-r----- 1 root        adm          0 May 14 06:08 dmesg.0
-rw-r----- 1 syslog      adm     332219 May 14 06:25 syslog.0
-rw-r----- 1 mysql       adm          0 May 14 06:35 mysql.log
drwxr-s--- 2 mysql       adm       4096 May 14 06:35 mysql
-rw-r----- 1 syslog      adm      26402 May 14 16:05 mail.warn
-rw-r----- 1 syslog      adm       4028 May 14 16:05 user.log
-rw-r----- 1 root        adm      44373 May 15 01:00 shorewall-init.log
-rw-r----- 1 root        adm          0 May 15 01:00 dmesg
-rw-rw-r-- 1 root        utmp     74880 May 15 01:00 wtmp
-rw-r----- 1 syslog      adm      74486 May 15 01:00 daemon.log
-rw-r----- 1 syslog      adm     450041 May 15 01:00 mail.log
-rw-r----- 1 syslog      adm     446896 May 15 01:00 mail.info
-rw-r----- 1 syslog      adm      28978 May 15 02:17 syslog
-rw-r----- 1 syslog      adm     288645 May 15 02:17 auth.log
-rw-r----- 1 syslog      adm      17136 May 15 02:20 messages

```


root@vz2:/# /etc/init.d/postfix restart```

 * Stopping Postfix Mail Transport Agent postfix 	  [ OK ] 
 * Starting Postfix Mail Transport Agent postfix          [ OK ] 

```


root@vz2:/# /etc/init.d/courier-imap-ssl restart```

 * Stopping Courier IMAP-SSL server...                    [ OK ] 
 * Starting Courier IMAP-SSL server...                    [ OK ] 

```


root@vz2:/# /etc/init.d/courier-imap restart ```
   
 * Stopping Courier IMAP server...                        [ OK ] 
 * Starting Courier IMAP server...                        [ OK ] 

```


root@vz2:/# /etc/init.d/courier-authdaemon restart```

 * Stopping Courier authentication services authdaemond         [ OK ] 
 * Starting Courier authentication services authdaemond         [ OK ] 

```


root@vz2:/# /etc/init.d/mysql restart        ```
     
 * Stopping MySQL database server mysqld                  [ OK ] 
 * Starting MySQL database server mysqld                  [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```


root@vz2:/# /etc/init.d/amavis restart```

Stopping amavisd: amavisd-new.
Starting amavisd: amavisd-new.

```


root@vz2:/# /etc/init.d/spamassassin restart```

Restarting SpamAssassin Mail Filter Daemon: spamd.

```


root@vz2:/# /etc/init.d/clamav-daemon restart```

 * Stopping ClamAV daemon clamd  	                  [ OK ] 
 * Starting ClamAV daemon clamd                                
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
                                                          [ OK ]

```


root@vz2:/# /etc/init.d/clamav-freshclam restart```

 * Stopping ClamAV virus database updater freshclam              [ OK ] 
 * Starting ClamAV virus database updater freshclam              [ OK ]

```


root@vz2:/# ls -ltr /var/log/```

total 4856
-rw-rw-r-- 1 root        utmp         0 May 13  2008 btmp.1
drwxr-xr-x 2 root        root      4096 May 13  2008 fsck
-rw-r----- 1 root        adm         31 May 13  2008 boot
-rw-r----- 1 syslog      adm          0 May 13  2008 lpr.log
drwxr-sr-x 2 news        kmem      4096 May 13  2008 news
-rw-r----- 1 syslog      adm          0 May 13  2008 kern.log
-rw-r--r-- 1 root        root         0 May 13  2008 bootstrap.log
-rw-r----- 1 mysql       adm          0 Apr 23 03:45 mysql.err
-rw-r----- 1 syslog      adm        251 Apr 23 04:58 debug.0
drwxr-s--- 2 Debian-exim adm       4096 Apr 25 06:25 exim4
-rw-r----- 1 syslog      adm       3371 Apr 26 05:39 daemon.log.1.gz
-rw-r----- 1 syslog      adm        334 Apr 26 06:45 mail.warn.1.gz
-rw-r----- 1 syslog      adm       7690 Apr 26 06:45 mail.log.1.gz
-rw-r----- 1 syslog      adm       7691 Apr 26 06:45 mail.info.1.gz
-rw-r----- 1 syslog      adm        333 Apr 26 06:45 mail.err.1.gz
-rw-r----- 1 syslog      adm        731 Apr 26 06:45 messages.1.gz
-rw-r----- 1 syslog      adm          0 Apr 26 06:47 debug
-rw-r----- 1 syslog      adm       5430 Apr 26 06:47 auth.log.1.gz
-rw-r----- 1 syslog      adm      11694 Apr 30 06:25 syslog.6.gz
-rw-r----- 1 mysql       adm         20 Apr 30 06:29 mysql.log.7.gz
-rw-r--r-- 1 root        root      2354 May  1 15:11 aptitude.1.gz
-rw-r----- 1 root        adm     151123 May  1 15:11 dpkg.log.1
-rw-rw-r-- 1 root        utmp   1868928 May  2 06:22 wtmp.1
-rw-r----- 1 syslog      adm      11591 May  2 06:40 syslog.5.gz
-rw-r--r-- 1 root        root      5468 May  2 06:40 shorewall-init.log.3.gz
-rw-r----- 1 mysql       adm         20 May  2 06:54 mysql.log.6.gz
-rw-rw-r-- 1 root        utmp         0 May  2 06:54 btmp
drwxr-xr-x 2 root        root      4096 May  2 06:54 apt
-rw-r----- 1 syslog      adm       2797 May  3 00:03 user.log.0
-rw-r----- 1 root        adm       6328 May  3 05:49 shorewall-init.log.2.gz
-rw-r----- 1 syslog      adm      51222 May  3 05:49 daemon.log.0
-rw-r----- 1 syslog      adm       4929 May  3 05:49 mail.err.0
-rw-r----- 1 syslog      adm       6133 May  3 05:49 mail.warn.0
-rw-r----- 1 syslog      adm     237781 May  3 05:50 mail.log.0
-rw-r----- 1 syslog      adm     237781 May  3 05:50 mail.info.0
-rw-r----- 1 syslog      adm       6505 May  3 06:25 syslog.4.gz
-rw-r----- 1 mysql       adm         20 May  3 06:27 mysql.log.5.gz
-rw-r----- 1 syslog      adm      11033 May  3 06:27 messages.0
-rw-r----- 1 syslog      adm     193502 May  3 06:47 auth.log.0
-rw-r----- 1 syslog      adm       5917 May  4 06:25 syslog.3.gz
-rw-r----- 1 mysql       adm         20 May  4 06:34 mysql.log.4.gz
-rw-r----- 1 syslog      adm      11381 May  7 06:39 syslog.2.gz
-rw-r----- 1 mysql       adm         20 May  7 06:50 mysql.log.3.gz
-rw-r----- 1 root        adm      14845 May  7 23:48 shorewall-init.log.1.gz
-rw-r----- 1 syslog      adm       6184 May  8 06:25 syslog.1.gz
-rw-r----- 1 mysql       adm         20 May  8 06:32 mysql.log.2.gz
-rw-r--r-- 1 root        root      4321 May  8 22:31 aptitude
-rw-rw-r-- 1 root        utmp   1461460 May  8 22:31 lastlog
-rw-r--r-- 1 root        root    120120 May  8 22:31 faillog
-rw-r----- 1 root        adm       5431 May  8 22:31 dpkg.log
drwxr-xr-x 2 clamav      clamav    4096 May 11 06:37 clamav
drwxr-x--- 2 root        adm       4096 May 11 06:37 apache2
-rw-r----- 1 mysql       adm         20 May 11 06:37 mysql.log.1.gz
-rw-r----- 1 root        adm         28 May 13 08:27 dmesg.4.gz
-rw-r----- 1 root        adm         28 May 13 13:19 dmesg.3.gz
-rw-r----- 1 root        adm         28 May 13 23:20 dmesg.2.gz
-rw-r----- 1 syslog      adm       4267 May 13 23:21 mail.err
-rw-r----- 1 root        adm         28 May 14 04:02 dmesg.1.gz
-rw-r----- 1 root        adm          0 May 14 06:08 dmesg.0
-rw-r----- 1 syslog      adm     332219 May 14 06:25 syslog.0
-rw-r----- 1 mysql       adm          0 May 14 06:35 mysql.log
drwxr-s--- 2 mysql       adm       4096 May 14 06:35 mysql
-rw-r----- 1 syslog      adm      26402 May 14 16:05 mail.warn
-rw-r----- 1 syslog      adm       4028 May 14 16:05 user.log
-rw-r----- 1 root        adm      44373 May 15 01:00 shorewall-init.log
-rw-r----- 1 root        adm          0 May 15 01:00 dmesg
-rw-rw-r-- 1 root        utmp     74880 May 15 01:00 wtmp
-rw-r----- 1 syslog      adm      75955 May 15 02:28 daemon.log
-rw-r----- 1 syslog      adm     290549 May 15 02:39 auth.log
-rw-r----- 1 syslog      adm      17167 May 15 02:40 messages
-rw-r----- 1 syslog      adm      38357 May 15 02:48 syslog
-rw-r----- 1 syslog      adm     457745 May 15 02:48 mail.log
-rw-r----- 1 syslog      adm     454600 May 15 02:48 mail.info

```


On host started Evolution to download mails on the mail server without success.


root@vz2:/# tail /var/log/mail.info```

May 15 02:29:05 vz2 spamd[3198]: spamd: server pid: 3198 
May 15 02:29:06 vz2 spamd[3198]: spamd: server successfully spawned child process, pid 3199 
May 15 02:29:06 vz2 spamd[3198]: spamd: server successfully spawned child process, pid 3200 
May 15 02:29:06 vz2 spamd[3198]: prefork: child states: II 
May 15 02:48:59 vz2 authdaemond: stopping authdaemond children
May 15 02:48:59 vz2 authdaemond: modules="authmysql", daemons=5
May 15 02:48:59 vz2 authdaemond: Installing libauthmysql
May 15 02:48:59 vz2 authdaemond: Installation complete: authmysql
May 15 02:56:45 vz2 imapd: LOGIN FAILED, user=satimis@satimis.com, ip=[::ffff:192.168.0.100]
May 15 02:57:02 vz2 imapd: LOGIN FAILED, user=satimis@satimis.com, ip=[::ffff:192.168.0.100]

```


Please help.  TIA


Remark: Shorewall has been stopped during testing.


B.R.
satimis

---

