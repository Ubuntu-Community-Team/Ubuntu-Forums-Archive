---
title: "To many processes?"
date: 2010-02-22
forum: Server Platforms
---

### Post by Spikerok on 2010-02-22
Is it normal to have 100+ processes when some processes actually identical?

[PHP]USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.3  0.1   3056  1900 ?        Ss   21:04   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   21:04   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   21:04   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   21:04   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:04   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   21:04   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   21:04   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   21:04   0:00 [kintegrityd/0]
root        48  0.0  0.0      0     0 ?        S<   21:04   0:00 [kblockd/0]
root        50  0.0  0.0      0     0 ?        S<   21:04   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   21:04   0:00 [kacpi_notify]
root       139  0.0  0.0      0     0 ?        S<   21:04   0:00 [cqueue]
root       143  0.0  0.0      0     0 ?        S<   21:04   0:00 [kseriod]
root       182  0.0  0.0      0     0 ?        S    21:04   0:00 [pdflush]
root       183  0.0  0.0      0     0 ?        S    21:04   0:00 [pdflush]
root       184  0.0  0.0      0     0 ?        S<   21:04   0:00 [kswapd0]
root       226  0.0  0.0      0     0 ?        S<   21:04   0:00 [aio/0]
root      1214  0.0  0.0      0     0 ?        S<   21:04   0:00 [ksuspend_usbd]
root      1215  0.0  0.0      0     0 ?        S<   21:04   0:00 [khubd]
root      1240  0.0  0.0      0     0 ?        S<   21:04   0:00 [ata/0]
root      1241  0.0  0.0      0     0 ?        S<   21:04   0:00 [ata_aux]
root      1969  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_0]
root      1970  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_1]
root      1992  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_2]
root      1993  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_3]
root      2006  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_4]
root      2007  0.0  0.0      0     0 ?        S<   21:04   0:00 [scsi_eh_5]
root      2131  0.0  0.0      0     0 ?        S<   21:04   0:00 [kjournald]
root      2279  0.0  0.0   2304   720 ?        S<s  21:04   0:00 /sbin/udevd --daemon
root      2550  0.0  0.0      0     0 ?        S<   21:04   0:00 [kpsmoused]
root      3755  0.0  0.0   2248   408 ?        Ss   21:04   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
ntp       3936  0.0  0.1   4264  1316 ?        Ss   21:04   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 106:115 -g
root      4054  0.0  0.0   1780   528 tty4     Ss+  21:04   0:00 /sbin/getty 38400 tty4
root      4055  0.0  0.0   1780   524 tty5     Ss+  21:04   0:00 /sbin/getty 38400 tty5
root      4063  0.0  0.0   1780   524 tty2     Ss+  21:04   0:00 /sbin/getty 38400 tty2
root      4066  0.0  0.0   1780   524 tty3     Ss+  21:04   0:00 /sbin/getty 38400 tty3
root      4068  0.0  0.0   1780   528 tty6     Ss+  21:04   0:00 /sbin/getty 38400 tty6
syslog    4103  0.0  0.0   2012   676 ?        Ss   21:04   0:00 /sbin/syslogd -u syslog
root      4121  0.0  0.0   1940   540 ?        S    21:04   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4123  0.0  0.2   3476  2224 ?        Ss   21:04   0:00 /sbin/klogd -P /var/run/klogd/kmsg
104       4141  0.0  0.0   2640   788 ?        Ss   21:04   0:00 /bin/dbus-daemon --system
root      4160  0.0  0.1   5400  1060 ?        Ss   21:04   0:00 /usr/sbin/sshd
amavis    4186  0.2  5.0  58648 48712 ?        Ss   21:04   0:00 amavisd (master)
root      4219  0.0  0.1   2860  1324 ?        S    21:04   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4261  0.1  1.8 128688 18248 ?        Sl   21:04   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4263  0.0  0.0   1764   552 ?        S    21:04   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
amavis    4280  0.0  4.9  59560 47928 ?        S    21:04   0:00 amavisd (virgin child)
amavis    4282  0.0  4.9  59560 47904 ?        S    21:04   0:00 amavisd (virgin child)
root      4326  0.3  2.8  30220 27536 ?        Ss   21:04   0:00 /usr/sbin/spamd --create-prefs --max-children 5 --helper-home-dir -d --pidfile=/var/run/spamd.pid
root      4613  0.0  2.6  30220 25680 ?        S    21:04   0:00 spamd child
root      4617  0.0  2.6  30220 25680 ?        S    21:04   0:00 spamd child
clamav    4753  0.0  8.6  87168 84204 ?        Ss   21:04   0:00 /usr/sbin/clamd
clamav    4897  0.0  0.0   3172   760 ?        Ss   21:04   0:00 /usr/bin/freshclam -d --quiet
root      4934  0.0  0.0   1968   456 ?        S    21:04   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/courier/courier-authlib/authdaemond
root      4935  0.0  0.1   4500  1084 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4942  0.0  0.0   4500   368 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4944  0.0  0.0   4500   368 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4946  0.0  0.0   4500   368 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4948  0.0  0.0   4500   368 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4950  0.0  0.0   4500   368 ?        S    21:04   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4957  0.0  0.0   1968   460 ?        S    21:04   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd.pid -start -name=imapd /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root      4958  0.0  0.0   2076   620 ?        S    21:04   0:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root      4979  0.0  0.0   1968   368 ?        S    21:04   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd-ssl.pid -start -name=imapd-ssl /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root      4980  0.0  0.0   2076   596 ?        S    21:04   0:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root      4995  0.0  0.0   1968   460 ?        S    21:04   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/pop3d.pid -start -name=pop3d /usr/sbin/couriertcpd -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup -address=0 110 /usr/lib/courier/courier/courierpop3login /usr/lib/courier/courier/courierpop3d Maildir
root      4996  0.0  0.0   2076   616 ?        S    21:04   0:00 /usr/sbin/couriertcpd -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup -address=0 110 /usr/lib/courier/courier/courierpop3login /usr/lib/courier/courier/courierpop3d Maildir
root      5017  0.0  0.0   1968   372 ?        S    21:04   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/pop3d-ssl.pid -start -name=pop3d-ssl /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup 995 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/courierpop3login /usr/lib/courier/courier/courierpop3d Maildir
root      5018  0.0  0.0   2076   596 ?        S    21:04   0:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup 995 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/courierpop3login /usr/lib/courier/courier/courierpop3d Maildir
nobody    5023  0.0  0.1   4924  1352 ?        Ss   21:04   0:00 /usr/local/sbin/mydns -b
nobody    5024  0.0  0.1   5088  1500 ?        S    21:04   0:00 /usr/local/sbin/mydns -b
root      5096  0.0  0.1   5748  1760 ?        Ss   21:04   0:00 /usr/lib/postfix/master
postfix   5107  0.0  0.1   5760  1652 ?        S    21:04   0:00 pickup -l -t fifo -u -c
postfix   5108  0.0  0.2   8124  2092 ?        S    21:04   0:00 qmgr -l -t fifo -u
root      5110  0.0  0.0   6264   800 ?        Ss   21:04   0:00 pure-ftpd (SERVER)                                          
root      5138  0.0  0.0   8368   868 ?        Ss   21:04   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5139  0.0  0.0   8368   504 ?        S    21:04   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5140  0.0  0.0   8368   424 ?        S    21:04   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5141  0.0  0.0   8368   424 ?        S    21:04   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
root      5142  0.0  0.0   8368   424 ?        S    21:04   0:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5
daemon    5174  0.0  0.0   2068   460 ?        Ss   21:04   0:00 /usr/sbin/atd
root      5199  0.0  0.1   3412  1028 ?        Ss   21:04   0:00 /usr/sbin/cron
root      5219  0.0  1.0  40452  9892 ?        Ss   21:04   0:00 /usr/sbin/apache2 -k start
root      5220  0.0  0.2   4408  2800 ?        S    21:04   0:00 vlogger (access log)
www-data  5223  0.0  0.3  21412  2908 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
www-data  5234  0.0  0.5  40452  4916 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
www-data  5235  0.0  0.5  40936  5684 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
www-data  5236  0.0  0.5  40952  5728 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
www-data  5237  0.0  0.5  40452  5376 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
www-data  5238  0.0  0.5  40452  5348 ?        S    21:04   0:00 /usr/sbin/apache2 -k start
root      5240  0.2  0.4  23648  4224 ?        Sl   21:04   0:00 /usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock
root      5256  0.0  0.0   1780   524 tty1     Ss+  21:04   0:00 /sbin/getty 38400 tty1
postfix   5359  0.0  0.2   6128  2496 ?        S    21:05   0:00 tlsmgr -l -t unix -u -c
www-data  5362  0.0  0.4  40452  4756 ?        S    21:05   0:00 /usr/sbin/apache2 -k start
root      5659  0.0  0.2   8448  2900 ?        Ss   21:09   0:00 sshd: vladislav [priv]
1000      5726  0.0  0.1   8448  1552 ?        S    21:09   0:00 sshd: vladislav@pts/0
1000      5727  0.4  0.3   5736  3092 pts/0    Ss   21:09   0:00 -bash
root      5744  0.0  0.1   4064  1508 pts/0    S    21:09   0:00 su
root      5748  0.1  0.1   4248  1804 pts/0    R    21:09   0:00 bash
root      5821  0.0  0.1   2744  1008 pts/0    R+   21:09   0:00 ps aux
root      5822  0.0  0.0   4248   732 pts/0    D+   21:09   0:00 bash[/PHP]

"/usr/sbin/apache2 -k start" - is repeated 6 times...
and some other odd cases, what can i do about it and how.

---

### Post by cdenley on 2010-02-22
That looks normal to me. Servers often have multiple processes so that it can respond to multiple simultaneous requests more quickly.
```

grep -B 2 -A 8 Servers /etc/apache2/apache2.conf

```

---

### Post by Vegan on 2010-02-22
When my server load is up I have seen 12 copies of Apache running, no problem as I have lots of RAM on the Linux box.

---

### Post by James78 on 2010-12-02
My server has 154 processes running right now, and I know for a fact everything is good and great. Either way, as already said, should be completely normal. :p

---

