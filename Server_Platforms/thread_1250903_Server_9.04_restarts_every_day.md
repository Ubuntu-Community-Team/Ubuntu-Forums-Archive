---
title: "Server 9.04 restarts every day"
date: 2009-08-27
forum: Server Platforms
---

### Post by timmson on 2009-08-27
Hello!
please help!
i have a big problem. production server on ubuntu server 9.04 restarts every day. 

```

root@spider:/var/log# cat /var/log/messages | egrep "signal"
Aug 26 11:50:59 spider exiting on signal 15
Aug 27 10:20:22 spider exiting on signal 15

```

```

root@spider:/var/log# cat syslog | egrep "TERM|signal"
Aug 27 10:19:13 spider init: tty1 main process (2978) killed by INT signal
Aug 27 10:19:56 spider init: tty1 main process (22054) killed by INT signal
Aug 27 10:20:13 spider init: tty5 main process (2246) killed by TERM signal
Aug 27 10:20:13 spider init: tty2 main process (2249) killed by TERM signal
Aug 27 10:20:13 spider init: tty3 main process (2252) killed by TERM signal
...
Aug 27 10:20:13 spider init: tty1 main process (22155) killed by TERM signal
Aug 27 10:20:13 spider init: tty4 main process (2245) killed by TERM signal
Aug 27 10:20:22 spider exiting on signal 15

```

```

root@spider:/etc/cron.daily# ls -lah /etc/cron.daily
total 57K
drwxr-xr-x   2 root root  352 2009-08-20 13:26 .
drwxr-xr-x 108 root root 5,4K 2009-08-27 10:23 ..
-rwxr-xr-x   1 root root  633 2009-04-01 20:06 apache2
-rwxr-xr-x   1 root root 8,5K 2009-04-17 08:26 apt
-rwxr-xr-x   1 root root  314 2008-09-02 16:50 aptitude
-rwxr-xr-x   1 root root  502 2007-12-12 18:31 bsdmainutils
-rwxr-xr-x   1 root root   89 2008-10-09 11:12 logrotate
-rwxr-xr-x   1 root root  954 2008-07-11 19:03 man-db
-rwxr-xr-x   1 root root  646 2008-06-26 18:19 mlocate
-rw-r--r--   1 root root  102 2008-09-09 23:52 .placeholder
-rwxr-xr-x   1 root root 2,1K 2008-11-17 12:52 popularity-contest
-rwxr-xr-x   1 root root 3,3K 2008-09-09 23:52 standard
-rwxr-xr-x   1 root root 1,3K 2008-08-30 04:41 sysklogd

```

what is the problem???
what daemon can reboot system?

---

