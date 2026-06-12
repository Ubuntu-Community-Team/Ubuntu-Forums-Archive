---
title: "Slow apache, help!"
date: 2007-01-19
forum: Server Platforms
---

### Post by Mirrorball on 2007-01-19
I'm a newbie to server configuration and I'm struggling to maintain a VPS. I've noticed this problem recently: when I click a link in my site, sometimes nothing happens, until the connection times out. What could be causing this problem and what could I do to solve it? Increase the max number of Apache processes, threads per child, or what?

---

### Post by jtc on 2007-01-19
Any idea how well visited your site is? What does the log-files say? In other words, do we have to optimize apache to handle a high load or is there something broken we need to fix?

---

### Post by Mirrorball on 2007-01-19
The site ran fine on a shared server. Obviously it doesn't get visited a lot. There is a vBulletin forum that has about 40 online users at a time, but at least half of them are "Yahoo! Slurps." Yahoo just loves my forum.

Here is some output that may help:
```

top

Tasks:  32 total,   1 running,  31 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  0.2% sy,  0.0% ni, 99.0% id,  0.2% wa,  0.0% hi,  0.0% si
Mem:   8296452k total,  8075008k used,   221444k free,   115148k buffers
Swap: 16779884k total,      708k used, 16779176k free,  3397972k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      16   0  1800  668  564 S    0  0.0   0:00.03 init
10047 root      15   0  1496  576  456 S    0  0.0   0:00.25 syslogd
11356 root      16   0  4772 1084  748 S    0  0.0   0:00.00 sshd
11368 root      16   0  3372  944  724 S    0  0.0   0:00.00 vsftpd
11392 root      16   0  2112  808  648 S    0  0.0   0:00.00 xinetd
11554 root      16   0  2032  756  608 S    0  0.0   0:00.00 cron
15694 root      20   0  2340 1212  984 S    0  0.0   0:00.00 mysqld_safe
15756 mysql     16   0  127m  48m 5236 S    0  0.6   6:45.99 mysqld
15757 root      15   0  1428  524  452 S    0  0.0   0:00.00 logger
29925 root      15   0  4624 1616 1304 S    0  0.0   0:00.35 master
29929 postfix   15   0  4676 1732 1376 S    0  0.0   0:00.12 qmgr
 5356 root      16   0  1776  604  460 S    0  0.0   0:01.80 dovecot
 5365 root      16   0  8268 2192 1700 S    0  0.0   0:00.83 dovecot-auth
 5683 postfix   16   0  4692 1996 1648 S    0  0.0   0:00.01 tlsmgr
16331 root      15   0 51884 8860 3048 S    0  0.1   0:00.65 apache2
30561 postfix   16   0  4640 1624 1308 S    0  0.0   0:00.00 pickup
19836 www-data  15   0 55736  18m 9988 S    0  0.2   0:02.57 apache2

ps axuw

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1800   668 ?        Ss   Jan17   0:00 init [2]
root     10047  0.0  0.0   1496   576 ?        Ss   Jan17   0:00 /sbin/syslogd
root     11356  0.0  0.0   4772  1084 ?        Ss   Jan17   0:00 /usr/sbin/sshd
root     11368  0.0  0.0   3372   944 ?        Ss   Jan17   0:00 /usr/sbin/vsftpd
root     11392  0.0  0.0   2112   808 ?        Ss   Jan17   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root     11554  0.0  0.0   2032   756 ?        Ss   Jan17   0:00 /usr/sbin/cron
root     15694  0.0  0.0   2340  1212 ?        S    Jan17   0:00 /bin/sh /usr/bin/mysqld_safe
mysql    15756  0.2  0.5 130628 49572 ?        Sl   Jan17   6:46 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mys
root     15757  0.0  0.0   1428   524 ?        S    Jan17   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     29925  0.0  0.0   4624  1616 ?        Ss   Jan18   0:00 /usr/lib/postfix/master
postfix  29929  0.0  0.0   4676  1732 ?        S    Jan18   0:00 qmgr -l -t fifo -u
root      5356  0.0  0.0   1776   604 ?        Ss   Jan18   0:01 /usr/sbin/dovecot
root      5365  0.0  0.0   8268  2192 ?        S    Jan18   0:00 dovecot-auth
postfix   5683  0.0  0.0   4692  1996 ?        S    Jan18   0:00 tlsmgr -l -t unix -u -c
root     16331  0.0  0.1  51884  8860 ?        Ss   07:32   0:00 /usr/sbin/apache2 -k start -DSSL
postfix  30561  0.0  0.0   4640  1624 ?        S    15:29   0:00 pickup -l -t fifo -u -c
www-data 19836  0.1  0.2  55736 18508 ?        S    15:40   0:02 /usr/sbin/apache2 -k start -DSSL
dovecot  19877  0.0  0.0   3156  1464 ?        S    15:40   0:00 pop3-login
www-data 15644  0.0  0.1  52752 13192 ?        S    15:57   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 17702  0.1  0.1  52764 14152 ?        S    15:59   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 17716  0.1  0.1  53036 13028 ?        S    15:59   0:00 /usr/sbin/apache2 -k start -DSSL
dovecot  24221  0.0  0.0   3156  1464 ?        S    16:00   0:00 pop3-login
www-data 26347  0.3  0.1  53040 13000 ?        S    16:02   0:01 /usr/sbin/apache2 -k start -DSSL
www-data 30054  0.3  0.1  53104 14700 ?        S    16:04   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 30528  0.2  0.1  55212 14208 ?        S    16:04   0:00 /usr/sbin/apache2 -k start -DSSL
dovecot  32379  0.0  0.0   3156  1464 ?        S    16:05   0:00 pop3-login
www-data 32647  0.0  0.1  52936 11776 ?        S    16:05   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 32657  0.3  0.1  52736 12272 ?        S    16:05   0:00 /usr/sbin/apache2 -k start -DSSL
root      1425  0.0  0.0   7560  2388 ?        Ss   16:06   0:00 sshd: root@pts/0
root      1452  0.0  0.0   3824  1784 pts/0    Ss   16:06   0:00 -bash
root      1870  0.0  0.0   2312   956 pts/0    R+   16:07   0:00 ps axuw

```

---

### Post by jtc on 2007-01-19
Are there any error-messages in the serverlog, about when apache stops serving webpages? Perhaps the following line?

> server reached MaxClients setting, consider raising the MaxClients setting 

If that's the case, perhaps you could take a look at this thread.

[http://www.vbulletin.com/forum/showthread.php?t=159978]("http://www.vbulletin.com/forum/showthread.php?t=159978")

If that's not the case, we'll try something else :-)

---

### Post by Mirrorball on 2007-01-19
I found four lines of "server reached MaxClients setting." Maybe this is problem. I'm feeling hopeful. Thanks!

---

### Post by Mirrorball on 2007-01-19
So far, the server has been running perfectly. And I just raised the MaxClients setting from 10 to 20. Thanks again for your suggestion!

---

