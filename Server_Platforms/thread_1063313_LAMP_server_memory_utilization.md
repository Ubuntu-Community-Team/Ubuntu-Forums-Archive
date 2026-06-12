---
title: "LAMP server memory utilization"
date: 2009-02-07
forum: Server Platforms
---

### Post by Keirnan on 2009-02-07
I am relatively new to LAMP servers.  My problem is that my server will continue to consume memory, and never seems to release it.  If I leave it alone for several days, it will have consumed all the physical RAM and all the swap.  It does this very slowly.  I can't seem to figure out where the memory goes.  I don't see any big consumers, but I notice that the amount of used memory never goes down, only up.  If I restart apache (apache2ctl restart), it will only free up a small amount of memory.  Likewise for MySQL.  The only thing that restarts the memory counter is if I reboot the box.

This is a website running on a dedicated Ubuntu 8.1 server.  3.0Ghz P4, 1GB RAM, hardware mirrored 500GB hard drives.  

It is running ISPCP, a VHCS fork ([www.isp-control.net](www.isp-control.net)) and everything that comes with it:
-Bind 9
-MySQL 5
-PHP 5
-ProFTPD
-Postfix
-Courier

As well as Fail2Ban.

Everything has its default config, except for MySQL, where I changed the key_buffer_pool to 48MB and increased table cache size to 128.  Everything else in the MySQL config is unchanged.  I have not changed any PHP, mail, or Apache settings.

The server is running 5 virtual hosts.  4 of those virtual hosts are basically unused.  The remaining one gets approximately 4000 page views per day.  There are never more than 25 concurrent sessions.

CPU utilization is extremely low, typically 95+% idle.

Here is top, sorted by memory:

top - 15:53:19 up 10:50,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 101 total,   1 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.2%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1018156k total,   748576k used,   269580k free,    81292k buffers
Swap:  3036276k total,        0k used,  3036276k free,   444640k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4469 mysql     20   0  161m  39m 5332 S    0  4.0   3:27.42 mysqld
26057 vu2002    20   0 29804  15m 3264 S    0  1.6   0:54.48 php5-cgi
26055 vu2002    20   0 29832  15m 3264 S    0  1.6   0:23.51 php5-cgi
26058 vu2002    20   0 27784  13m 3264 S    0  1.4   0:23.53 php5-cgi
 5144 vu2001    20   0 25584  11m 3280 S    0  1.2   0:02.79 php5-cgi
26059 vu2002    20   0 25188  11m 3264 S    0  1.1   0:26.48 php5-cgi
 4778 www-data  20   0  234m  10m 1644 S    0  1.1   0:04.78 apache2
 5143 vu2001    20   0 24844  10m 3252 S    0  1.1   0:03.33 php5-cgi
 4775 www-data  20   0  233m  10m 1640 S    0  1.0   0:04.85 apache2
 4763 root      20   0 13480 9868 2040 S    0  1.0   0:03.45 ispcp-apache-lo
 4762 root      20   0 13340 9800 2040 S    0  1.0   0:00.42 ispcp-apache-lo
 4348 bind      20   0 44620 8836 2032 S    0  0.9   0:00.79 named
31403 www-data  20   0  232m 8420 1648 S    0  0.8   0:01.77 apache2
 4533 postgrey  20   0 11136 8260 2680 S    0  0.8   0:00.18 postgrey

Here is free:

             total       used       free     shared    buffers     cached
Mem:       1018156     748408     269748          0      81340     444660
-/+ buffers/cache:     222408     795748
Swap:      3036276          0    3036276


I was thinking it was just a lot of apache php5-cgi or apache processes, but they don't seem to be using that much.  MySQL is the #1 consumer, at 4% of the memory, but it doesn't seem to get much higher than that.  Even when I am using tons of swap, no single process uses more than MySQL.

Here is ps aux at almost 11 hours of up time.  In another 24 hours or so, it will be swapping:


USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2844  1692 ?        Ss   05:03   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   05:03   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   05:03   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   05:03   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   05:03   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   05:03   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   05:03   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   05:03   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   05:03   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   05:03   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   05:03   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   05:03   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   05:03   0:00 [kacpi_notify]
root       123  0.0  0.0      0     0 ?        S<   05:03   0:00 [kseriod]
root       163  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root       164  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root       165  0.0  0.0      0     0 ?        S<   05:03   0:00 [kswapd0]
root       207  0.0  0.0      0     0 ?        S<   05:03   0:00 [aio/0]
root       208  0.0  0.0      0     0 ?        S<   05:03   0:00 [aio/1]
root      1275  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksuspend_usbd]
root      1282  0.0  0.0      0     0 ?        S<   05:03   0:00 [khubd]
root      1434  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_0]
root      1468  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata/0]
root      1469  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata/1]
root      1471  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata_aux]
root      2322  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_1]
root      2324  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_2]
root      2381  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_3]
root      2382  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_4]
root      2483  0.0  0.0      0     0 ?        S<   05:03   0:00 [kjournald]
root      2640  0.0  0.0   2224   672 ?        S<s  05:03   0:00 /sbin/udevd --daemon
root      2967  0.0  0.0      0     0 ?        S<   05:03   0:00 [kpsmoused]
root      4255  0.0  0.0   1716   512 tty4     Ss+  05:03   0:00 /sbin/getty 38400 tty4
root      4256  0.0  0.0   1716   516 tty5     Ss+  05:03   0:00 /sbin/getty 38400 tty5
root      4258  0.0  0.0   1716   516 tty2     Ss+  05:03   0:00 /sbin/getty 38400 tty2
root      4260  0.0  0.0   1716   512 tty3     Ss+  05:03   0:00 /sbin/getty 38400 tty3
root      4262  0.0  0.0   1716   512 tty6     Ss+  05:03   0:00 /sbin/getty 38400 tty6
syslog    4304  0.0  0.0   1936   684 ?        Ss   05:03   0:00 /sbin/syslogd -u syslog
root      4323  0.0  0.0   1872   544 ?        S    05:03   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4325  0.0  0.1   3152  2008 ?        Ss   05:03   0:00 /sbin/klogd -P /var/run/klogd/kmsg
bind      4348  0.0  0.8  44620  8836 ?        Ssl  05:03   0:00 /usr/sbin/named -u bind
root      4371  0.0  0.0   5316  1012 ?        Ss   05:03   0:00 /usr/sbin/sshd
root      4427  0.0  0.0   1772   520 ?        S    05:03   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4469  0.5  4.0 164892 40840 ?        Sl   05:03   3:28 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql -
root      4470  0.0  0.0   1700   556 ?        S    05:03   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
polw      4529  0.0  0.5   8140  5948 ?        Ss   05:03   0:00 policyd-weight (master)
polw      4530  0.0  0.5   8272  5584 ?        Ss   05:03   0:00 policyd-weight (cache)
postgrey  4533  0.0  0.8  11136  8260 ?        Ss   05:03   0:00 /usr/sbin/postgrey --pidfile=/var/run/postgrey.pid --daemo
root      4557  0.0  0.0   1904   452 ?        S    05:03   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/p
root      4558  0.0  0.0   2112   672 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4573  0.0  0.0   1904   364 ?        S    05:03   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd.pid -s
root      4574  0.0  0.0   2008   600 ?        S    05:03   0:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20
root      4587  0.0  0.0   1904   452 ?        S    05:03   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/pop3d.pid -s
root      4588  0.0  0.0   2008   612 ?        S    05:03   0:00 /usr/sbin/couriertcpd -maxprocs=40 -maxperip=4 -nodnslooku
root      4591  0.0  0.1   2912  1284 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4592  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4593  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4594  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4595  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courier/courier-authlib/authdaemond
root      4660  0.0  0.1   5396  1784 ?        Ss   05:03   0:00 /usr/lib/postfix/master
postfix   4664  0.0  0.1   5444  1832 ?        S    05:03   0:00 qmgr -l -t fifo -u
nobody    4708  0.0  0.1   5992  1920 ?        Ss   05:03   0:00 proftpd: (accepting connections)
daemon    4722  0.0  0.0   1984   424 ?        Ss   05:03   0:00 /usr/sbin/atd
root      4733  0.0  0.0   2104   888 ?        Ss   05:03   0:00 /usr/sbin/cron
root      4759  0.0  0.3  11476  3340 ?        Ss   05:03   0:01 /usr/sbin/apache2 -k start
root      4760  0.0  0.0   1772   488 ?        S    05:03   0:00 /bin/sh -c /var/www/ispcp/engine/ispcp-apache-logger -e
root      4761  0.0  0.0   1772   484 ?        S    05:03   0:00 /bin/sh -c /var/www/ispcp/engine/ispcp-apache-logger
root      4762  0.0  0.9  13340  9800 ?        S    05:03   0:00 /usr/bin/perl /var/www/ispcp/engine/ispcp-apache-logger -e
root      4763  0.0  0.9  13480  9868 ?        S    05:03   0:03 /usr/bin/perl /var/www/ispcp/engine/ispcp-apache-logger
www-data  4765  0.0  0.2  10928  2148 ?        S    05:03   0:00 /usr/sbin/apache2 -k start
www-data  4772  0.0  0.2  11248  2240 ?        S    05:03   0:00 /usr/sbin/apache2 -k start
www-data  4775  0.0  1.0 239028 10272 ?        Sl   05:03   0:04 /usr/sbin/apache2 -k start
www-data  4778  0.0  1.0 240052 11036 ?        Sl   05:03   0:04 /usr/sbin/apache2 -k start
root      4837  0.0  0.4  40228  4616 ?        Sl   05:03   0:12 /usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fa
root      4860  0.0  0.0   1700   448 ?        S    05:03   0:00 /var/www/ispcp/daemon/ispcp_daemon -p /var/run/ispcp_daemo
root      4933  0.0  0.0   1716   512 tty1     Ss+  05:03   0:00 /sbin/getty 38400 tty1
polw      4978  0.0  0.6   8400  6264 ?        S    05:09   0:00 policyd-weight (child)
vu2001    5142  0.0  0.5  19240  5484 ?        Ss   05:39   0:00 /usr/bin/php5-cgi
vu2001    5143  0.0  1.0  24844 11028 ?        S    05:39   0:03 /usr/bin/php5-cgi
vu2001    5144  0.0  1.1  25584 11820 ?        S    05:39   0:02 /usr/bin/php5-cgi
postfix  25912  0.0  0.1   5404  1672 ?        S    14:36   0:00 pickup -l -t fifo -u -c
vu2002   26054  0.0  0.5  19240  5488 ?        Ss   15:00   0:00 /usr/bin/php5-cgi
vu2002   26055  0.7  1.5  29832 15964 ?        S    15:00   0:24 /usr/bin/php5-cgi
vu2002   26056  0.0  0.5  19240  5488 ?        Ss   15:00   0:00 /usr/bin/php5-cgi
vu2002   26057  1.6  1.5  29804 15992 ?        S    15:00   0:55 /usr/bin/php5-cgi
vu2002   26058  0.7  1.3  27784 13872 ?        S    15:00   0:24 /usr/bin/php5-cgi
vu2002   26059  0.8  1.1  25444 11664 ?        S    15:00   0:27 /usr/bin/php5-cgi
root     26241  0.0  0.2   8056  2520 ?        Ss   15:42   0:00 sshd: pragupia6060 [priv]
1000     26243  0.0  0.1   8056  1552 ?        S    15:42   0:00 sshd: pragupia6060@pts/0
1000     26244  0.0  0.2   5560  2980 pts/0    Ss   15:42   0:00 -bash
postfix  26266  0.0  0.3   6612  3188 ?        S    15:46   0:00 smtpd -n smtp -t inet -u -c -o stress
postfix  26267  0.0  0.1   5408  1732 ?        S    15:46   0:00 anvil -l -t unix -u -c
1000     26294  0.0  0.0   2644  1008 pts/0    R+   15:57   0:00 ps aux
polw     31044  0.0  0.6   8404  6300 ?        S    09:38   0:00 policyd-weight (child)
www-data 31403  0.0  0.8 237696  8420 ?        Sl   10:51   0:01 /usr/sbin/apache2 -k start

Obviously, once it starts swapping things get very slow.  Any ideas?

---

### Post by gombadi on 2009-02-07
> 
Here is ps aux at almost 11 hours of up time. In another 24 hours or so, it will be swapping


Post the same results (top, free, ps) every 4 to 6 hours so we can see trends instead of a one off snapshot.

Also when you post the results can you wrap them in a code tag - press the # button on the text entry tool bar. It makes the output a lot easier to read.

You may also want to include the output of - 
```

vmstat -s
vmstat 2 10

```

You may also want to keep an eye on the output of slabtop to see if it shows anything interesting.

---

### Post by Keirnan on 2009-02-07
Thanks so much for the reply.

Here is the output of vmstat -s:
```

      1018156 K total memory
       854916 K used memory
       383396 K active memory
       428436 K inactive memory
       163240 K free memory
        87856 K buffer memory
       451784 K swap cache
      3036276 K total swap
            0 K used swap
      3036276 K free swap
       219036 non-nice user cpu ticks
           17 nice user cpu ticks
        44155 system cpu ticks
      9243817 idle cpu ticks
         5510 IO-wait cpu ticks
          537 IRQ cpu ticks
         1753 softirq cpu ticks
            0 stolen cpu ticks
       455927 pages paged in
       950492 pages paged out
            0 pages swapped in
            0 pages swapped out
     12198813 interrupts
      6801841 CPU context switches
   1234011795 boot time
       124200 forks

```

Am I reading this right in that 428MB of my memory is "used" but inactive?  Is that normal?

---

### Post by Keirnan on 2009-02-07
Thanks for the reply.

Posting the results every few hours is a good idea.  Here is top, over 2 hours after my last post.  Notice I used about 100MB of memory in the last 2 hours.  From this, it appears to be getting used up by a single php5-cgi process.  I suppose this isn't crazy, since my memory limit in php.ini is 128MB.  I am guessing the problem, then, is that I don't think this process will go away.

```

top - 18:19:28 up 13:16,  1 user,  load average: 0.00, 0.02, 0.00
Tasks: 100 total,   3 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1018156k total,   851868k used,   166288k free,    88116k buffers
Swap:  3036276k total,        0k used,  3036276k free,   451840k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
26058 vu2002    20   0  129m  83m 3268 S    0  8.4   0:56.54 php5-cgi
 4469 mysql     20   0  161m  41m 5332 S    0  4.1   3:53.50 mysqld
26057 vu2002    20   0 30132  16m 3312 R    1  1.6   2:05.74 php5-cgi
 5144 vu2001    20   0 25584  11m 3308 S    0  1.2   0:03.37 php5-cgi
26574 vu2002    20   0 25504  11m 3264 S    0  1.2   0:21.35 php5-cgi
26059 vu2002    20   0 25456  11m 3268 S    0  1.1   1:10.12 php5-cgi
26573 vu2002    20   0 25468  11m 3240 S    0  1.1   0:23.85 php5-cgi
26397 vu2002    20   0 25296  11m 3264 S    0  1.1   1:08.82 php5-cgi
26396 vu2002    20   0 25292  11m 3272 S    0  1.1   0:37.31 php5-cgi
 4778 www-data  20   0  234m  10m 1644 S    0  1.1   0:05.20 apache2
 5143 vu2001    20   0 24844  10m 3252 S    0  1.1   0:04.18 php5-cgi
 4775 www-data  20   0  233m  10m 1640 S    0  1.0   0:05.31 apache2
 4763 root      20   0 13480 9868 2040 S    0  1.0   0:03.85 ispcp-apache-lo
 4762 root      20   0 13340 9800 2040 S    0  1.0   0:00.42 ispcp-apache-lo
 4348 bind      20   0 44620 8836 2032 S    0  0.9   0:00.80 named
31403 www-data  20   0  232m 8528 1648 S    0  0.8   0:02.31 apache2
 4533 postgrey  20   0 11136 8260 2680 S    0  0.8   0:00.20 postgrey
31044 polw      20   0  8404 6300 1456 S    0  0.6   0:00.42 policyd-weight
 4978 polw      20   0  8400 6264 1424 S    0  0.6   0:00.85 policyd-weight
 4529 polw      20   0  8140 5948 1244 S    0  0.6   0:00.14 policyd-weight
 4530 polw      20   0  8272 5596  876 S    0  0.5   0:00.13 policyd-weight
26056 vu2002    20   0 19240 5488 3700 S    0  0.5   0:00.03 php5-cgi
26395 vu2002    20   0 19240 5488 3700 S    0  0.5   0:00.02 php5-cgi
26572 vu2002    20   0 19240 5488 3700 S    0  0.5   0:00.04 php5-cgi
 5142 vu2001    20   0 19240 5484 3700 S    0  0.5   0:00.02 php5-cgi
 4837 root      20   0 40228 4616 1848 S    0  0.5   0:14.25 fail2ban-server
 4759 root      20   0 11476 3340 1744 S    0  0.3   0:01.45 apache2
27287 pragupia  20   0  5560 2940 1416 S    0  0.3   0:00.10 bash
27284 root      20   0  8056 2524 2068 S    0  0.2   0:00.01 sshd
 4772 www-data  20   0 11248 2240  624 S    0  0.2   0:00.45 apache2
 4765 www-data  20   0 10928 2148  556 S    0  0.2   0:00.00 apache2
 4325 klog      20   0  3152 2008  424 S    0  0.2   0:00.11 klogd
 4708 nobody    20   0  5992 1920  568 S    0  0.2   0:00.38 proftpd
 4664 postfix   20   0  5444 1832 1488 S    0  0.2   0:00.08 qmgr
 4660 root      20   0  5396 1784 1452 S    0  0.2   0:00.27 master
26890 postfix   20   0  5404 1740 1412 S    0  0.2   0:00.00 pickup
27027 postfix   20   0  5408 1732 1412 S    0  0.2   0:00.00 anvil

```

---

### Post by Keirnan on 2009-02-07
Here is ps aux, again roughly 2 hours after the previous run:

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2844  1692 ?        Ss   05:03   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   05:03   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   05:03   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   05:03   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   05:03   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   05:03   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   05:03   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   05:03   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   05:03   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   05:03   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   05:03   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   05:03   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   05:03   0:00 [kacpi_notify]
root       123  0.0  0.0      0     0 ?        S<   05:03   0:00 [kseriod]
root       163  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root       164  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root       165  0.0  0.0      0     0 ?        S<   05:03   0:00 [kswapd0]
root       207  0.0  0.0      0     0 ?        S<   05:03   0:00 [aio/0]
root       208  0.0  0.0      0     0 ?        S<   05:03   0:00 [aio/1]
root      1275  0.0  0.0      0     0 ?        S<   05:03   0:00 [ksuspend_usbd]
root      1282  0.0  0.0      0     0 ?        S<   05:03   0:00 [khubd]
root      1434  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_0]
root      1468  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata/0]
root      1469  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata/1]
root      1471  0.0  0.0      0     0 ?        S<   05:03   0:00 [ata_aux]
root      2322  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_1]
root      2324  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_2]
root      2381  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_3]
root      2382  0.0  0.0      0     0 ?        S<   05:03   0:00 [scsi_eh_4]
root      2483  0.0  0.0      0     0 ?        S<   05:03   0:01 [kjournald]
root      2640  0.0  0.0   2224   672 ?        S<s  05:03   0:00 /sbin/udevd --d
root      2967  0.0  0.0      0     0 ?        S<   05:03   0:00 [kpsmoused]
root      4255  0.0  0.0   1716   512 tty4     Ss+  05:03   0:00 /sbin/getty 384
root      4256  0.0  0.0   1716   516 tty5     Ss+  05:03   0:00 /sbin/getty 384
root      4258  0.0  0.0   1716   516 tty2     Ss+  05:03   0:00 /sbin/getty 384
root      4260  0.0  0.0   1716   512 tty3     Ss+  05:03   0:00 /sbin/getty 384
root      4262  0.0  0.0   1716   512 tty6     Ss+  05:03   0:00 /sbin/getty 384
syslog    4304  0.0  0.0   1936   684 ?        Ss   05:03   0:00 /sbin/syslogd -
root      4323  0.0  0.0   1872   544 ?        S    05:03   0:00 /bin/dd bs 1 if
klog      4325  0.0  0.1   3152  2008 ?        Ss   05:03   0:00 /sbin/klogd -P
bind      4348  0.0  0.8  44620  8836 ?        Ssl  05:03   0:00 /usr/sbin/named
root      4371  0.0  0.0   5316  1012 ?        Ss   05:03   0:00 /usr/sbin/sshd
root      4427  0.0  0.0   1772   520 ?        S    05:03   0:00 /bin/sh /usr/bi
mysql     4469  0.4  4.1 164948 42216 ?        Sl   05:03   3:53 /usr/sbin/mysql
root      4470  0.0  0.0   1700   556 ?        S    05:03   0:00 logger -p daemo
polw      4529  0.0  0.5   8140  5948 ?        Ss   05:03   0:00 policyd-weight
polw      4530  0.0  0.5   8272  5596 ?        Ss   05:03   0:00 policyd-weight
postgrey  4533  0.0  0.8  11136  8260 ?        Ss   05:03   0:00 /usr/sbin/postg
root      4557  0.0  0.0   1904   452 ?        S    05:03   0:00 /usr/sbin/couri
root      4558  0.0  0.0   2112   672 ?        S    05:03   0:00 /usr/lib/courie
root      4573  0.0  0.0   1904   364 ?        S    05:03   0:00 /usr/sbin/couri
root      4574  0.0  0.0   2008   600 ?        S    05:03   0:00 /usr/sbin/couri
root      4587  0.0  0.0   1904   452 ?        S    05:03   0:00 /usr/sbin/couri
root      4588  0.0  0.0   2008   612 ?        S    05:03   0:00 /usr/sbin/couri
root      4591  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courie
root      4592  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courie
root      4593  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courie
root      4594  0.0  0.0   2116   588 ?        S    05:03   0:00 /usr/lib/courie
root      4595  0.0  0.1   2912  1284 ?        S    05:03   0:00 /usr/lib/courie
root      4660  0.0  0.1   5396  1784 ?        Ss   05:03   0:00 /usr/lib/postfi
postfix   4664  0.0  0.1   5444  1832 ?        S    05:03   0:00 qmgr -l -t fifo
nobody    4708  0.0  0.1   5992  1920 ?        Ss   05:03   0:00 proftpd: (accep
daemon    4722  0.0  0.0   1984   424 ?        Ss   05:03   0:00 /usr/sbin/atd
root      4733  0.0  0.0   2104   888 ?        Ss   05:03   0:00 /usr/sbin/cron
root      4759  0.0  0.3  11476  3340 ?        Ss   05:03   0:01 /usr/sbin/apach
root      4760  0.0  0.0   1772   488 ?        S    05:03   0:00 /bin/sh -c /var
root      4761  0.0  0.0   1772   484 ?        S    05:03   0:00 /bin/sh -c /var
root      4762  0.0  0.9  13340  9800 ?        S    05:03   0:00 /usr/bin/perl /
root      4763  0.0  0.9  13480  9868 ?        S    05:03   0:03 /usr/bin/perl /
www-data  4765  0.0  0.2  10928  2148 ?        S    05:03   0:00 /usr/sbin/apach
www-data  4772  0.0  0.2  11248  2240 ?        S    05:03   0:00 /usr/sbin/apach
www-data  4775  0.0  1.0 239028 10288 ?        Sl   05:03   0:05 /usr/sbin/apach
www-data  4778  0.0  1.0 240052 11068 ?        Sl   05:03   0:05 /usr/sbin/apach
root      4837  0.0  0.4  40228  4616 ?        Sl   05:03   0:14 /usr/bin/python
root      4860  0.0  0.0   1700   448 ?        S    05:03   0:00 /var/www/ispcp/
root      4933  0.0  0.0   1716   512 tty1     Ss+  05:03   0:00 /sbin/getty 384
polw      4978  0.0  0.6   8400  6268 ?        S    05:09   0:00 policyd-weight
vu2001    5142  0.0  0.5  19240  5484 ?        Ss   05:39   0:00 /usr/bin/php5-c
vu2001    5143  0.0  1.0  24844 11028 ?        S    05:39   0:04 /usr/bin/php5-c
vu2001    5144  0.0  1.1  25584 11848 ?        S    05:39   0:03 /usr/bin/php5-c
vu2002   26056  0.0  0.5  19240  5488 ?        Ss   15:00   0:00 /usr/bin/php5-c
vu2002   26057  1.0  1.6  30132 16400 ?        S    15:00   2:07 /usr/bin/php5-c
vu2002   26058  0.4  8.4 132328 85908 ?        S    15:00   0:56 /usr/bin/php5-c
vu2002   26059  0.5  1.1  25200 11428 ?        S    15:00   1:11 /usr/bin/php5-c
vu2002   26395  0.0  0.5  19240  5488 ?        Ss   16:01   0:00 /usr/bin/php5-c
vu2002   26396  0.4  1.1  25292 11512 ?        S    16:01   0:37 /usr/bin/php5-c
vu2002   26397  0.8  1.1  25040 11260 ?        S    16:01   1:09 /usr/bin/php5-c
vu2002   26572  0.0  0.5  19240  5488 ?        Ss   16:39   0:00 /usr/bin/php5-c
vu2002   26573  0.3  1.1  25212 11408 ?        S    16:39   0:24 /usr/bin/php5-c
vu2002   26574  0.3  1.1  25760 11980 ?        S    16:39   0:22 /usr/bin/php5-c
postfix  26890  0.0  0.1   5404  1740 ?        S    17:55   0:00 pickup -l -t fi
postfix  27027  0.0  0.1   5408  1744 ?        S    18:02   0:00 anvil -l -t uni
root     27284  0.0  0.2   8056  2524 ?        Ss   18:15   0:00 sshd: pragupia6
1000     27286  0.0  0.1   8056  1556 ?        S    18:16   0:00 sshd: pragupia6
1000     27287  0.0  0.2   5560  2944 pts/0    Ss   18:16   0:00 -bash
postfix  27311  0.0  0.3   6612  3172 ?        S    18:20   0:00 smtpd -n smtp -
postfix  27314  0.0  0.3   6612  3196 ?        S    18:20   0:00 smtpd -n smtp -
postfix  27315  0.0  0.3   6612  3196 ?        S    18:21   0:00 smtpd -n smtp -
postfix  27321  0.0  0.3   6612  3176 ?        S    18:22   0:00 smtpd -n smtp -
postfix  27327  0.0  0.2   5880  2576 ?        S    18:23   0:00 trivial-rewrite
1000     27328  0.0  0.0   2644  1008 pts/0    R+   18:23   0:00 ps aux
polw     31044  0.0  0.6   8404  6300 ?        S    09:38   0:00 policyd-weight
www-data 31403  0.0  0.8 237696  8532 ?        Sl   10:51   0:02 /usr/sbin/apach

```

---

### Post by Keirnan on 2009-02-07
I had never heard of slabtop, but here is the output from it:

```

 Active / Total Objects (% used)    : 131118 / 132347 (99.1%)
 Active / Total Slabs (% used)      : 5472 / 5472 (100.0%)
 Active / Total Caches (% used)     : 48 / 53 (90.6%)
 Active / Total Size (% used)       : 22616.35K / 22835.91K (99.0%)
 Minimum / Average / Maximum Object : 0.01K / 0.17K / 8.00K

  OBJS ACTIVE  USE OBJ SIZE  SLABS OBJ/SLAB CACHE SIZE NAME
 37157  36939  99%    0.05K    509       73      2036K buffer_head
 27900  27885  99%    0.13K    930       30      3720K dentry
 12872  12871  99%    0.48K   1609        8      6436K ext3_inode_cache
 10200  10199  99%    0.05K    120       85       480K sysfs_dir_cache
  6084   6083  99%    0.29K    468       13      1872K radix_tree_node
  5120   5103  99%    0.01K     10      512        40K kmalloc-8
  4416   4415  99%    0.09K     96       46       384K vm_area_struct
  4096   4011  97%    0.06K     64       64       256K kmalloc-64
  2889   2889 100%    0.43K    321        9      1284K shmem_inode_cache
  2856   2853  99%    0.33K    238       12       952K inode_cache
  2816   2599  92%    0.02K     11      256        44K kmalloc-16
  2442   2436  99%    0.34K    222       11       888K proc_inode_cache
  2142   1945  90%    0.19K    102       21       408K kmalloc-192
  1536   1524  99%    0.03K     12      128        48K kmalloc-32
  1536   1388  90%    0.02K      6      256        24K anon_vma
  1428   1417  99%    0.04K     14      102        56K pid_namespace
  1216   1209  99%    0.50K    152        8       608K kmalloc-512
   850    850 100%    0.02K      5      170        20K Acpi-Namespace
   832    713  85%    0.12K     26       32       104K kmalloc-128
   512    512 100%    0.02K      2      256         8K revoke_record
   464    445  95%    0.25K     29       16       116K kmalloc-256
   378    366  96%    0.09K      9       42        36K kmalloc-96
   352    327  92%    2.00K     88        4       704K kmalloc-2048
   340    340 100%    0.02K      2      170         8K journal_handle
   240    228  95%    0.38K     24       10        96K sock_inode_cache
   225    207  92%    1.44K     45        5       360K task_struct
   220    220 100%    8.00K    220        1      1760K pmd
   196    196 100%    0.14K      7       28        28K idr_layer_cache
   188    185  98%    1.00K     47        4       188K kmalloc-1024
   146    146 100%    0.05K      2       73         8K uid_cache
   140     95  67%    0.38K     14       10        56K files_cache
   114    108  94%    1.31K     19        6       152K sighand_cache
    90     79  87%    0.44K     10        9        40K mm_struct
    78     78 100%    0.10K      2       39         8K file_lock_cache
    56     56 100%    0.14K      2       28         8K sigqueue
    42     38  90%    1.25K      7        6        56K TCP

```

---

### Post by gombadi on 2009-02-07
The first hit for "vmstat -s inactive memory" on the Linux help system ([http://www.google.com](http://www.google.com)) said -

> 
vmstat -m only shows malloced memory.  The inactive memory are pages
that have been faulted into memory by the vm system and therefore
don't show up as malloced memory.  The text and data for your
processes don't show up in vmstat -m either.  Inactive memory just
means that 'You asked for it once, and on the off chance you'll ask
for it again, I'll keep it around rather than have this page of memory
go to waste.'  But the inactive pool is the first one to have pages
taken from it when other uses of the memory come up.



---

### Post by Keirnan on 2009-02-07
> **gombadi said:**
> The first hit for "vmstat -s inactive memory" on the Linux help system ([http://www.google.com](http://www.google.com)) said -

Thanks for the reply.

Sorry, but is that intended to address the threads topic directly, or are you just referring to my post above asking if this was normal?  That is, are you suggesting that the behavior I am experiencing (slowly eating all physical memory, then swapping) is expected?

Thanks!

---

### Post by gombadi on 2009-02-07
The "was it normal" - I was showing what inactive memory was and that it is not that important.

The words normal and expected are very hard to define when it gomes to memory usage.

Every system is different and will use memory differently so answering "is it normal" is impossible without a long term anaylsis of the server and its daily usage patterns.

I would rate the php5-cgi memory usage as interesting but again it needs to be looked at over a longer time period. As you say will memory usage keep expanding, will it start more php5-cgi processes that will also use memory or will processes be killed off in quiet periods. These are all things that will be answered over time.

Keep posting the results every 4~6 hours and we will see what the results show.

---

### Post by hyper_ch on 2009-02-08
(1) when posting any output enclose it in [noparse]```

```[/noparse] brackets

(2) unused ram = wasted ram. run
```

free -m

```
That shows you how much is cache and how much is actually in use.

---

### Post by jimv on 2009-02-08
Everyone's having you run all these great memory commands, but no one has addressed your problem.  It looks like one of your PHP scripts is causing a memory leak...which can be difficult to troubleshoot.  Might want to Google for methods of checking your scripts for leaks.

---

### Post by Keirnan on 2009-02-08
Thanks for the help everyone.  I am waiting for it to start swapping, and then I will post updated statistics.

---

