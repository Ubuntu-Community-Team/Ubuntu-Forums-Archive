---
title: "server memory conservation"
date: 2010-02-21
forum: Server Platforms
---

### Post by tmilam on 2010-02-21
I have a total of 512MB memory available in my VPS (virtual private server). I'm trying to lower overall memory usage...so far I've changed my LAMP stack to use lighttpd instead of apache.The switch lowered my memory consumption by 4MB. I was hoping for a more dramatic result! The VPS can burst to 2gb of ram, but consistently I only have 512MB available.

```
ehnde@ftp:~$ cat /proc/meminfo | grep "Mem"
MemTotal:      2097152 kB
MemFree:       1796380 kB

```

Question 1: I'd rather not ditch mysql, but does anyone have tips for reducing the memory consumption of mysql?

Question 2: I installed and frequently use rkhunter, but a dependency of rkhunter is exim. I don't want exim running and have no intention of running a mailserver. It's currently set to local delivery only. Is there a way around having exim? Possibly an alternative to rkhunter?

Question 3: Do you have any tips for further reducing memory consumption in a server?

Here are my currently running processes. If you see anything that could be shut off, please advise.

```
ehnde@ftp:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  10448   784 ?        Ss   Feb14   0:07 init [2]      
root      1337  0.0  0.0  35480  1280 pts/0    S    08:21   0:00 su -
root      1338  0.0  0.0  17736  1944 pts/0    S+   08:21   0:00 -su
root      1517  0.0  0.0   9056  1324 pts/0    S    09:32   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1557  0.0  1.0 160996 22124 pts/0    Sl   09:32   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld
root      1558  0.0  0.0   3916   624 pts/0    S    09:32   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
ehnde     3898  0.0  0.0  24364  1884 ?        Ss   Feb15   0:01 SCREEN
ehnde     3899  0.0  0.1  18212  2112 pts/1    Ss   Feb15   0:00 /bin/bash
ehnde     3947  0.0  0.3  48452  7252 pts/1    S+   Feb15   0:57 irssi
root      5713  0.0  0.0  18704   980 ?        Ss   Feb14   0:01 /usr/sbin/cron
root      5794  0.0  0.1  68080  3060 ?        Ss   10:23   0:00 sshd: ehnde [priv]
ehnde     5799  0.0  0.0  68080  1724 ?        S    10:23   0:00 sshd: ehnde@notty
ehnde     5800  0.0  0.0  42168  1832 ?        Ss   10:23   0:00 /usr/lib/openssh/sftp-server
root     11352  0.0  0.0  19436   908 ?        Ss   Feb20   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6
root     12087  0.0  0.1  68080  3088 ?        Ss   07:29   0:00 sshd: ehnde [priv]
ehnde    12100  0.0  0.1  69072  2712 ?        S    07:29   0:01 sshd: ehnde@pts/0
ehnde    12101  0.0  0.1  18220  2176 pts/0    Ss   07:29   0:00 -bash
root     12268  0.0  0.1  68080  3092 ?        Ss   08:26   0:00 sshd: ehnde [priv]
ehnde    12270  0.0  0.0  68232  1784 ?        S    08:26   0:00 sshd: ehnde@pts/2
ehnde    12271  0.0  0.1  18220  2176 pts/2    Ss   08:26   0:00 -bash
112      15371  0.0  0.0  41824  1040 ?        Ss   10:18   0:00 /usr/sbin/exim4 -bd -q30m
www-data 16017  0.0  0.1  57056  2368 ?        S    09:54   0:00 /usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf
www-data 16019  0.0  0.3  93768  6848 ?        Ss   09:54   0:00 /usr/bin/php-cgi
www-data 16029  0.0  0.1  93768  3080 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16030  0.0  0.1  93768  3140 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16031  0.0  0.1  93768  3080 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16032  0.0  0.1  93768  3080 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16036  0.0  0.3 159300  6856 ?        Ss   09:54   0:00 /usr/bin/php-cgi
www-data 16039  0.0  0.1 159300  3148 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16040  0.0  0.1 159300  3088 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16041  0.0  0.1 159300  3088 ?        S    09:54   0:00 /usr/bin/php-cgi
www-data 16042  0.0  0.1 159300  3088 ?        S    09:54   0:00 /usr/bin/php-cgi
root     24470  0.0  0.3  89980  6328 ?        Sl   09:57   0:01 /usr/bin/python2.5 /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock
root     25890  0.0  0.0  48936  1232 ?        Ss   Feb20   0:00 /usr/sbin/sshd
ehnde    26420  0.0  0.0  14884  1056 pts/2    R+   10:50   0:00 ps aux
syslog   31968  0.0  0.0  12368   736 ?        Ss   Feb14   0:02 /sbin/syslogd -u syslog

```

---

### Post by lloyd_b on 2010-02-22
Before you start worrying too much, could you post the output of the "free" command?  I believe the numbers you're looking at include buffers/cache, and by default Linux will try to use *all* free memory for this purpose, freeing it up when it's needed for applications.

Lloyd B.

---

### Post by tmilam on 2010-02-22
> **lloyd_b said:**
> Before you start worrying too much, could you post the output of the "free" command?  I believe the numbers you're looking at include buffers/cache, and by default Linux will try to use *all* free memory for this purpose, freeing it up when it's needed for applications.

Lloyd B.

```
             total       used       free     shared    buffers     cached
Mem:          2048        272       1775          0          0          0
-/+ buffers/cache:        272       1775
Swap:            0          0          0

```

I've been reading [http://nanotux.com/blog/the-ultimate-server](http://nanotux.com/blog/the-ultimate-server) which I found stickied here in the forums. Highly recommended for anyone trying to set up a LLMP on ubuntu, but I'm still trying to find ways to squeak out more memory. 

On the link I posted one very useful tip is replacing your mailserver with google apps (think gmail), and swapping out exim4 or postfix - whichever you may be using - for a lighter mailserver called msmtp. I'll post back later how this changes my memory consumption.

Again, if you have further recommendations please advise!

---

