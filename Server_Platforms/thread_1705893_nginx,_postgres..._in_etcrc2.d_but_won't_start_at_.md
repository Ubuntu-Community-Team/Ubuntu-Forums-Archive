---
title: "nginx, postgres... in /etc/rc2.d but won't start at boot"
date: 2011-03-12
forum: Server Platforms
---

### Post by cerberos1 on 2011-03-12
Nothing (nginx, apache2, postgresql-8.4, mysql, php5-fpm, rabbitmq-server) in /etc/rc2.d starts at boot although I can start things manually without any error messages (both using service nginx start and /etc/init.d/nginx start). I'm using ubuntu server 10.04, spent hours looking into this and am getting very frustrated.

I've removed everything apart from nginx for debugging purposes, I've removed and readded the items several times with
```
update-rc.d -f nginx remove; update-rc.d nginx defaults
```Here's some pertinent output
```
root@neo[/etc/rc2.d]$ runlevel
N 2
root@neo[/etc/rc2.d]$ ls -la
total 12
drwxr-xr-x  2 root root 4096 2011-03-13 01:17 ./
drwxr-xr-x 81 root root 4096 2011-03-13 01:17 ../
-rw-r--r--  1 root root  677 2010-03-30 07:17 README
lrwxrwxrwx  1 root root   18 2010-11-14 15:27 S10sysklogd -> ../init.d/sysklogd*
lrwxrwxrwx  1 root root   19 2011-03-13 01:17 S10vzquota -> /etc/init.d/vzquota*
lrwxrwxrwx  1 root root   15 2010-11-14 15:27 S11klogd -> ../init.d/klogd*
lrwxrwxrwx  1 root root   15 2011-03-12 17:28 S20nginx -> ../init.d/nginx*
lrwxrwxrwx  1 root root   15 2010-08-31 14:52 S50rsync -> ../init.d/rsync*
lrwxrwxrwx  1 root root   18 2010-08-31 05:29 S99rc.local -> ../init.d/rc.local*
root@neo[/etc/rc2.d]$ ls -la ../init.d
total 216
drwxr-xr-x  2 root root  4096 2011-03-12 19:12 ./
drwxr-xr-x 81 root root  4096 2011-03-13 01:17 ../
-rwxr-xr-x  1 root root  6157 2010-04-13 20:20 apache2*
-rwxr-xr-x  1 root root  2341 2009-09-07 18:58 bootlogd*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 console-setup -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-10-02 02:38 cron -> /lib/init/upstart-job*
-rw-r--r--  1 root root    24 2010-05-04 16:23 .depend.boot
-rw-r--r--  1 root root    24 2010-05-04 16:23 .depend.start
-rw-r--r--  1 root root    10 2010-05-04 16:23 .depend.stop
-rwxr-xr-x  1 root root  1329 2009-09-07 18:58 halt*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 hostname -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2011-03-12 16:38 hwclock -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2011-03-12 16:38 hwclock-save -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  2189 2008-06-01 15:12 ipkungfu*
-rwxr-xr-x  1 root root  1293 2009-09-07 18:58 killprocs*
-rwxr-xr-x  1 root root  1816 2009-09-22 21:36 klogd*
-rw-r--r--  1 root root     0 2010-05-04 16:23 .legacy-bootordering
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 module-init-tools -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-12-11 16:05 mysql -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  2256 2009-12-03 16:04 networking*
lrwxrwxrwx  1 root root    21 2011-03-12 16:39 network-interface -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2011-03-12 16:39 network-interface-security -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  2006 2010-02-15 07:16 nginx*
-rwxr-xr-x  1 root root   882 2009-09-07 18:58 ondemand*
-rwxr-xr-x  1 root root  2168 2010-10-01 08:59 php5-fpm*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 plymouth -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 plymouth-log -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 plymouth-splash -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 plymouth-stop -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  4695 2010-02-19 10:24 postfix*
-rwxr-xr-x  1 root root  1027 2010-04-09 06:33 postgresql-8.4*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 procps -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  3093 2010-01-18 08:35 quota*
-rwxr-xr-x  1 root root  1823 2010-01-18 08:35 quotarpc*
-rwxr-xr-x  1 root root  2827 2010-03-31 15:57 rabbitmq-server*
-rwxr-xr-x  1 root root  8863 2009-09-07 18:58 rc*
-rwxr-xr-x  1 root root   801 2009-09-07 18:58 rc.local*
-rwxr-xr-x  1 root root   117 2009-09-07 18:58 rcS*
-rw-r--r--  1 root root  1510 2009-09-07 18:58 README
-rwxr-xr-x  1 root root   639 2009-09-07 18:58 reboot*
-rwxr-xr-x  1 root root  4400 2010-03-30 15:14 rsync*
-rwxr-xr-x  1 root root  1055 2009-11-10 18:54 screen-cleanup*
-rwxr-xr-x  1 root root 33391 2010-02-15 09:40 sendmail*
-rwxr-xr-x  1 root root  3200 2010-03-30 00:20 sendsigs*
-rwxr-xr-x  1 root root   590 2009-09-07 18:58 single*
-rw-r--r--  1 root root  4271 2009-09-07 18:58 skeleton
-rwxr-xr-x  1 root root  3899 2010-03-08 16:11 ssh*
-rwxr-xr-x  1 root root   519 2009-09-07 18:58 stop-bootlogd*
-rwxr-xr-x  1 root root  1095 2009-09-07 18:58 stop-bootlogd-single*
-rwxr-xr-x  1 root root  3582 2009-09-22 21:36 sysklogd*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 udev -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 udev-finish -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 udevmonitor -> /lib/init/upstart-job*
lrwxrwxrwx  1 root root    21 2010-08-31 05:29 udevtrigger -> /lib/init/upstart-job*
-rwxr-xr-x  1 root root  2787 2009-11-05 13:03 umountfs*
-rwxr-xr-x  1 root root  2075 2009-10-14 04:16 umountnfs.sh*
-rwxr-xr-x  1 root root  1683 2009-10-14 04:20 umountroot*
-rwxr-xr-x  1 root root  1997 2009-09-07 18:58 urandom*
-rwxr-xr-x  1 root root   336 2011-03-13 01:17 vzquota*

```

---

