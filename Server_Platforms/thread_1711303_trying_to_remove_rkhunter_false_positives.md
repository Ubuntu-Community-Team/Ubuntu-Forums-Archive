---
title: "trying to remove rkhunter false positives"
date: 2011-03-21
forum: Server Platforms
---

### Post by pdc124 on 2011-03-21
these are the warnings im getting ( and have been getting )
> [06:31:18] Warning: The following processes are using deleted files:
[06:31:18]          Process: /usr/sbin/smbd    PID: 923    File: /var/log/samba/log.smbd.1
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 23537    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 23754    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 23757    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 24980    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 24981    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 24982    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 24983    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 24984    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/sbin/cron    PID: 25747    File: /tmp/tmpfkDkHGH
[06:31:18]          Process: /bin/dash    PID: 25749    File: /tmp/tmpfkDkHGH
[06:31:18]          Process: /bin/run-parts    PID: 25750    File: /tmp/tmpfkDkHGH
[06:31:18]          Process: /bin/dash    PID: 25883    File: /tmp/tmpfkDkHGH
[06:31:18]          Process: /bin/dash    PID: 25885    File: /tmp/tmpfkDkHGH
[06:31:18]          Process: /usr/sbin/mysqld    PID: 29507    File: /tmp/ibn08YlS
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 29675    File: /var/run/apache2/ssl_mutex
[06:31:18]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 31854    File: /var/run/apache2/ssl_mutex
[06:31:19]          Process: /usr/lib/apache2/mpm-prefork/apache2    PID: 31856    File: /var/run/apache2/ssl_mutex
[06:31:19]          Process: rkhunter    PID: 32191    File: /tmp/tmpfkDkHGH
[06:31:19]          Process: grep    PID: 32193    File: /tmp/tmpfkDkHGH
[06:31:19] Info: Starting test name 'running_procs'


[06:32:54] Info: Starting test name 'apps'
[06:32:56]   Checking version of Exim MTA                    [ OK ]
[06:32:56] Info: Application 'exim' version '4.72' found.
[06:32:56]   Checking version of GnuPG                       [ Warning ]
[06:32:56] Warning: Application 'gpg', version '1.4.10', is out of date, and possibly a security risk.
[06:32:56] Info: Application 'httpd' not found.
[06:32:56] Info: Application 'named' not found.
[06:32:56]   Checking version of OpenSSL                     [ OK ]
[06:32:56] Info: Found application 'openssl': it is whitelisted.
[06:32:56]   Checking version of PHP                         [ OK ]
[06:32:56] Info: Application 'php' version '5.3.3' found.
[06:32:56] Info: Application 'procmail' not found.
[06:32:56] Info: Application 'proftpd' not found.
[06:32:56]   Checking version of OpenSSH                     [ Warning ]
[06:32:56] Warning: Application 'sshd', version '5.5p1', is out of date, and possibly a security risk.
[06:32:56] Info: Applications checked: 5 out of 9
[06:32:56]
[06:32:56] System checks summary


in the conf file ive added 

> APP_WHITELIST="GnuPG  openssl  openSSH"
 but that doesnt stop the error messages

i can stop it looking for deleted files , but is that the best way , and how do i stop the warning about ssh  ?

---

