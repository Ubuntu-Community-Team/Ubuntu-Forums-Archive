---
title: "Server crashing: mpm_prefork:error and coredumps"
date: 2016-04-05
forum: Ubuntu Cloud and Juju
---

### Post by Walid_Doch on 2016-04-05
I have a WP website hosted on a LAMP server on an Amazon AWS Ubuntu Server and the website keeps crashing, I think it happens when having a lot of traffic. 


This is the error I get as an output: 


    `
    ```
[Mon Apr 04 00:13:56.619162 2016] [:error] [pid 8216] [client 185.130.5.165:53666] PHP Warning:  fread(): SSL: Connection reset by peer in /var/www/html/wp-includes/class-wp-http-streams.php on line 269
    [Mon Apr 04 00:31:14.065055 2016] [mpm_prefork:error] [pid 29211] AH00161: server reached MaxRequestWorkers setting, consider raising the MaxRequestWorkers setting
    [Mon Apr 04 04:33:04.783598 2016] [core:notice] [pid 29211] AH00051: child pid 29513 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783674 2016] [core:notice] [pid 29211] AH00051: child pid 29663 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783721 2016] [core:notice] [pid 29211] AH00051: child pid 29631 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783768 2016] [core:notice] [pid 29211] AH00051: child pid 31945 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783829 2016] [core:notice] [pid 29211] AH00051: child pid 29387 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783907 2016] [core:notice] [pid 29211] AH00051: child pid 6490 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.783968 2016] [core:notice] [pid 29211] AH00051: child pid 31917 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784022 2016] [core:notice] [pid 29211] AH00051: child pid 6473 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784071 2016] [core:notice] [pid 29211] AH00051: child pid 8976 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784108 2016] [core:notice] [pid 29211] AH00051: child pid 32040 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784145 2016] [core:notice] [pid 29211] AH00051: child pid 32046 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784181 2016] [core:notice] [pid 29211] AH00051: child pid 32050 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784234 2016] [core:notice] [pid 29211] AH00051: child pid 31437 exit signal Segmentation fault (11), possible coredump in /etc/apache2
    [Mon Apr 04 04:33:04.784285 2016] [core:notice] [pid 29211] AH00051: child pid 8796 exit signal Segmentation fault (11), possible coredump in /etc/apache2

```    `


I made the traffic calculation, just to make sure this is not a cause of insufficient RAM. I have 8GB RAM and for my traffic I only need less than 1 GB. I have around 540 pages opening a day, I have around 10 pages and each page is a 30KB load. (540*10*30)/1,000,000 < 1GB. 


    ```
<IfModule mpm_prefork_module>
            StartServers              5
            MinSpareServers           5
            MaxSpareServers          10
            MaxRequestWorkers        185
            ServerLimit              185
            MaxConnectionsPerChild   1000
    </IfModule>

```





What can this error be?
Is it from the server? what should I change on my server to solve this?


- I am using an SSL connection - I connect to the server using a .pkk file and not a password. 




auth.log: 


    ```
Apr  4 07:09:01 ip-194-64-78-111 CRON[12093]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 07:09:01 ip-194-64-78-111 CRON[12093]: pam_unix(cron:session): session closed for user root
    Apr  4 07:13:24 ip-194-64-78-111 sshd[12122]: Received disconnect from 183.3.202.112: 11:  [preauth]
    Apr  4 07:17:01 ip-194-64-78-111 CRON[12160]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 07:17:01 ip-194-64-78-111 CRON[12160]: pam_unix(cron:session): session closed for user root
    Apr  4 07:30:01 ip-194-64-78-111 sshd[12243]: Received disconnect from 121.158.47.250: 11: Bye Bye [preauth]
    Apr  4 07:30:02 ip-194-64-78-111 sshd[12245]: Received disconnect from 121.158.47.250: 11: Bye Bye [preauth]
    Apr  4 07:30:04 ip-194-64-78-111 sshd[12247]: Received disconnect from 121.158.47.250: 11: Bye Bye [preauth]
    Apr  4 07:30:06 ip-194-64-78-111 sshd[12249]: Received disconnect from 121.158.47.250: 11: Bye Bye [preauth]
    Apr  4 07:30:08 ip-194-64-78-111 sshd[12251]: Received disconnect from 121.158.47.250: 11: Bye Bye [preauth]
    Apr  4 07:39:01 ip-194-64-78-111 CRON[12412]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 07:39:01 ip-194-64-78-111 CRON[12412]: pam_unix(cron:session): session closed for user root
    Apr  4 08:16:49 ip-194-64-78-111 sshd[12880]: fatal: Read from socket failed: Connection reset by peer [preauth]
    Apr  4 08:17:01 ip-194-64-78-111 CRON[12891]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 08:17:01 ip-194-64-78-111 CRON[12891]: pam_unix(cron:session): session closed for user root
    Apr  4 08:38:05 ip-194-64-78-111 sshd[13234]: fatal: Read from socket failed: Connection reset by peer [preauth]
    Apr  4 08:39:01 ip-194-64-78-111 CRON[13241]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 08:39:02 ip-194-64-78-111 CRON[13241]: pam_unix(cron:session): session closed for user root
    Apr  4 08:55:46 ip-194-64-78-111 sshd[13571]: fatal: Read from socket failed: Connection reset by peer [preauth]
    Apr  4 08:56:01 ip-194-64-78-111 sshd[13576]: Accepted publickey for ubuntu from 66.66.66.66 port 53868 ssh2: RSA 35:09:e1:ed:ef:2a:11:db:73:a3:d9:a9:78:96:97:47
    Apr  4 08:56:01 ip-194-64-78-111 sshd[13576]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
    Apr  4 08:56:08 ip-194-64-78-111 sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/bin/su
    Apr  4 08:56:08 ip-194-64-78-111 sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
    Apr  4 08:56:08 ip-194-64-78-111 su[13686]: Successful su for root by root
    Apr  4 08:56:08 ip-194-64-78-111 su[13686]: + /dev/pts/0 root:root
    Apr  4 08:56:08 ip-194-64-78-111 su[13686]: pam_unix(su:session): session opened for user root by ubuntu(uid=0)
    Apr  4 08:59:36 ip-194-64-78-111 sshd[13766]: fatal: Read from socket failed: Connection reset by peer [preauth]
    Apr  4 09:00:28 ip-194-64-78-111 sshd[13776]: Received disconnect from 183.3.202.112: 11:  [preauth]
    Apr  4 09:00:49 ip-194-64-78-111 sshd[13781]: fatal: Read from socket failed: Connection reset by peer [preauth]
    Apr  4 10:17:01 ip-194-64-78-111 CRON[14730]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 10:17:01 ip-194-64-78-111 CRON[14730]: pam_unix(cron:session): session closed for user root
    Apr  4 10:20:31 ip-194-64-78-111 sshd[14789]: Accepted publickey for ubuntu from 66.66.66.66 port 54837 ssh2: RSA 35:09:e1:ed:ef:2a:11:db:73:a3:d9:a9:78:96:97:47
    Apr  4 10:20:31 ip-194-64-78-111 sshd[14789]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
    Apr  4 10:28:39 ip-194-64-78-111 sshd[14955]: Accepted publickey for ubuntu from 66.66.66.66 port 54924 ssh2: RSA 35:09:e1:ed:ef:2a:11:db:73:a3:d9:a9:78:96:97:47
    Apr  4 10:28:39 ip-194-64-78-111 sshd[14955]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
    Apr  4 10:34:26 ip-194-64-78-111 sshd[15120]: Accepted publickey for ubuntu from 66.66.66.66 port 54938 ssh2: RSA 35:09:e1:ed:ef:2a:11:db:73:a3:d9:a9:78:96:97:47
    Apr  4 10:34:26 ip-194-64-78-111 sshd[15120]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
    Apr  4 10:38:03 ip-194-64-78-111 sudo:   ubuntu : TTY=pts/1 ; PWD=/var/www/html/wp-content/themes/twentyfifteen-child ; USER=root ; COMMAND=/bin/chmod 744 functions.php
    Apr  4 10:38:03 ip-194-64-78-111 sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
    Apr  4 10:38:03 ip-194-64-78-111 sudo: pam_unix(sudo:session): session closed for user root
    Apr  4 10:39:01 ip-194-64-78-111 CRON[15273]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 10:39:01 ip-194-64-78-111 CRON[15273]: pam_unix(cron:session): session closed for user root
    Apr  4 10:39:21 ip-194-64-78-111 sudo:   ubuntu : TTY=pts/1 ; PWD=/var/www/html/wp-content/themes/twentyfifteen-child ; USER=root ; COMMAND=/bin/chmod 777 functions.php
    Apr  4 10:39:21 ip-194-64-78-111 sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
    Apr  4 10:39:21 ip-194-64-78-111 sudo: pam_unix(sudo:session): session closed for user root
    Apr  4 10:52:37 ip-194-64-78-111 sshd[14955]: pam_unix(sshd:session): session closed for user ubuntu
    Apr  4 10:52:42 ip-194-64-78-111 sshd[15557]: Accepted publickey for ubuntu from 66.66.66.66 port 55205 ssh2: RSA 35:09:e1:ed:ef:2a:11:db:73:a3:d9:a9:78:96:97:47
    Apr  4 10:52:42 ip-194-64-78-111 sshd[15557]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
    Apr  4 10:52:45 ip-194-64-78-111 sshd[15120]: pam_unix(sshd:session): session closed for user ubuntu
    Apr  4 10:55:07 ip-194-64-78-111 sshd[15687]: Received disconnect from 183.3.202.112: 11:  [preauth]
    Apr  4 11:39:01 ip-194-64-78-111 CRON[16691]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 11:39:01 ip-194-64-78-111 CRON[16691]: pam_unix(cron:session): session closed for user root
    Apr  4 11:42:13 ip-194-64-78-111 sshd[14789]: pam_unix(sshd:session): session closed for user ubuntu
    Apr  4 11:42:27 ip-194-64-78-111 sshd[16750]: Connection closed by 66.66.66.66 [preauth]
    Apr  4 12:09:01 ip-194-64-78-111 CRON[17365]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 12:09:01 ip-194-64-78-111 CRON[17365]: pam_unix(cron:session): session closed for user root
    Apr  4 12:09:31 ip-194-64-78-111 sshd[17395]: Received disconnect from 183.3.202.112: 11:  [preauth]
    Apr  4 12:17:01 ip-194-64-78-111 CRON[17517]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 12:17:01 ip-194-64-78-111 CRON[17517]: pam_unix(cron:session): session closed for user root
    Apr  4 12:59:15 ip-194-64-78-111 sshd[18471]: Received disconnect from 91.197.232.30: 11: Bye [preauth]
    Apr  4 13:09:01 ip-194-64-78-111 CRON[18587]: pam_unix(cron:session): session opened for user root by (uid=0)
    Apr  4 13:09:01 ip-194-64-78-111 CRON[18587]: pam_unix(cron:session): session closed for user root


```


GBD output: 


    ```
(gdb) gdb apache2 -core /tmp/apache-coredumps/core
    [1]+  Stopped                 gdb /usr/sbin/apache2
    root@ip-666-66-66-66:/# db apache2 -core /tmp/apache-coredumps/core
    db: command not found
    root@ip-666-66-66-66:/# gdb apache2 -core /tmp/apache-coredumps/core
    GNU gdb (Ubuntu 7.7.1-0ubuntu5~14.04.2) 7.7.1
    Copyright (C) 2014 Free Software Foundation, Inc.
    License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
    and "show warranty" for details.
    This GDB was configured as "x86_64-linux-gnu".
    Type "show configuration" for configuration details.
    For bug reporting instructions, please see:
    <http://www.gnu.org/software/gdb/bugs/>.
    Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.
    For help, type "help".
    Type "apropos word" to search for commands related to "word"...
    Reading symbols from apache2...Reading symbols from /usr/lib/debug//usr/sbin/apache2...done.
    done.
    [New LWP 6194]
    [Thread debugging using libthread_db enabled]
    Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
    
    warning: the debug information found in "/usr/lib/debug//usr/lib/php5/20121212/mysql.so" does not match "/usr/lib/php5/20121212/mysql.so" (CRC mismatch).
    
    
    warning: the debug information found in "/usr/lib/debug/usr/lib/php5/20121212/mysql.so" does not match "/usr/lib/php5/20121212/mysql.so" (CRC mismatch).
    
    
    warning: the debug information found in "/usr/lib/debug//usr/lib/php5/20121212/mysqli.so" does not match "/usr/lib/php5/20121212/mysqli.so" (CRC mismatch).
    
    
    warning: the debug information found in "/usr/lib/debug/usr/lib/php5/20121212/mysqli.so" does not match "/usr/lib/php5/20121212/mysqli.so" (CRC mismatch).
    
    
    warning: the debug information found in "/usr/lib/debug//usr/lib/php5/20121212/pdo_mysql.so" does not match "/usr/lib/php5/20121212/pdo_mysql.so" (CRC mismatch).
    
    
    warning: the debug information found in "/usr/lib/debug/usr/lib/php5/20121212/pdo_mysql.so" does not match "/usr/lib/php5/20121212/pdo_mysql.so" (CRC mismatch).
    
    Core was generated by `/usr/sbin/apache2 -k start'.
    Program terminated with signal SIGSEGV, Segmentation fault.
    #0  _zend_mm_free_int (heap=0x7f4b910ecfb0, p=0x7f4b910f0e70) at /build/php5-pO28mL/php5-5.5.9+dfsg/Zend/zend_alloc.c:2104
    2104    /build/php5-pO28mL/php5-5.5.9+dfsg/Zend/zend_alloc.c: No such file or directory.
```

---

### Post by Michael_McKenney on 2016-04-05
As with most hosted servers, you need resources that cost a premium.  You need to scale up your CPU cores, RAM, network bandwidth.  The error is server reached MaxRequestWorkers setting, consider raising the MaxRequestWorkers setting.   I would check your CPU, RAM and network resources to see which is maxed out.  Increase your MaxRequestWorkers by 25%-50% and reboot.  Monitor resources and purchase more of them.

---

### Post by Walid_Doch on 2016-04-06
> **Michael_McKenney said:**
> As with most hosted servers, you need resources that cost a premium.  You need to scale up your CPU cores, RAM, network bandwidth.  The error is server reached MaxRequestWorkers setting, consider raising the MaxRequestWorkers setting.   I would check your CPU, RAM and network resources to see which is maxed out.  Increase your MaxRequestWorkers by 25%-50% and reboot.  Monitor resources and purchase more of them.



I used htop to monitor processes:
I opened tons of tabs and I didn't see the bars passing the 50% (CPU and Memory).

On the other hand, I got inside the Amazon AWS instance management dashboard, and I found this graph: 
[IMG]http://i64.tinypic.com/15flstx.png[/IMG]


How can I find out what's causing this strange bumps, might this be it?

---

### Post by Michael_McKenney on 2016-04-08
CPU spikes are still OK.  You could try adding threads to the server for data processing.  Check your ram limits next.

---

