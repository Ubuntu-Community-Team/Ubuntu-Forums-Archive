---
title: "find and start apache"
date: 2015-05-21
forum: Server Platforms
---

### Post by amkashirin on 2015-05-21
Hello,
I have the old Ubuntu server with the apache web-service:
user@server:~$ uname -a
Linux server 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64 GNU/Linux

I know there is the apache service on it but it do not start. How I can find this service and restart it?

---

### Post by allan7 on 2015-05-21
First Try to run: sudo service apache2 status
to know what state it is then 
Run: sudo service apache2 start 
to start it

---

### Post by amkashirin on 2015-05-21
allan7,
thanks, but:
user@server:~$ sudo service apache2 status
[sudo] password for user:
sudo: service: command not found
user@server:~$

---

### Post by allan7 on 2015-05-21
Are u sure u'r on Debian(Ubuntu Distro)?
Please run: cat /proc/version
and see what distro you have

---

### Post by amkashirin on 2015-05-21
user@server:~$ cat /proc/version
Linux version 2.6.24-19-server (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 18:43:06 UTC 2008

---

### Post by allan7 on 2015-05-21
okay, Your ubuntu version is indeed old
Run: /etc/init.d/httpd start

---

### Post by amkashirin on 2015-05-21
user@server:~$ /etc/init.d/httpd start
-bash: /etc/init.d/httpd: No such file or directory

---

### Post by allan7 on 2015-05-21
I'm not sure if the service is named "httpd" or "apache" in old ubuntu version
navigate to /usr/sbin if you can see apache2 in there

---

### Post by allan7 on 2015-05-21
httpd is Redhat version
and
apache is Debian 
so try /etc/init.d/apache or apache2

---

### Post by allan7 on 2015-05-21
httpd is Redhat version
and
apache is Debian 
so try /etc/init.d/apache or apache2

---

### Post by amkashirin on 2015-05-21
I do not see any apache in /etc/init.d:
```
user@server:~$ ls -las /etc/init.d/
total 380
 4 drwxr-xr-x  2 root root  4096 2012-05-29 13:26 .
 4 drwxr-xr-x 85 root root  4096 2015-05-21 14:38 ..
 4 -rwxr-xr-x  1 root root  2653 2008-05-03 00:42 apparmor
 4 -rwxr-xr-x  1 root root   969 2007-02-20 17:05 atd
 4 -rwxr-xr-x  1 root root  3597 2008-04-18 20:02 bootclean
 4 -rwxr-xr-x  1 root root  2121 2008-04-18 20:02 bootlogd
 4 -rwxr-xr-x  1 root root  1768 2008-04-18 20:02 bootmisc.sh
 4 -rwxr-xr-x  1 root root  3454 2008-04-18 20:02 checkfs.sh
12 -rwxr-xr-x  1 root root 10602 2008-04-18 20:02 checkroot.sh
 8 -rwxr-xr-x  1 root root  6355 2007-05-30 16:29 console-screen.sh
 4 -rwxr-xr-x  1 root root  1634 2008-01-28 20:49 console-setup
 4 -rwxr-xr-x  1 root root  1761 2008-04-08 22:12 cron
 8 -rwxr-xr-x  1 root root  4546 2008-05-15 05:43 dbus
 4 -rwxr-xr-x  1 root root  1223 2007-06-22 08:55 dns-clean
 8 -rwxr-xr-x  1 root root  5076 2008-05-15 10:24 dovecot
 8 -rwxr-xr-x  1 root root  7195 2008-04-05 03:11 glibc.sh
 4 -rwxr-xr-x  1 root root  1228 2008-04-18 20:02 halt
 4 -rwxr-xr-x  1 root root   909 2008-04-18 20:02 hostname.sh
 8 -rwxr-xr-x  1 root root  4528 2008-04-29 15:58 hwclockfirst.sh
 8 -rwxr-xr-x  1 root root  4521 2008-04-29 15:58 hwclock.sh
 4 -rwxr-xr-x  1 root root  1376 2008-01-28 20:49 keyboard-setup
 4 -rwxr-xr-x  1 root root   944 2008-04-18 20:02 killprocs
 4 -rwxr-xr-x  1 root root  1729 2007-11-23 12:02 klogd
 4 -rwxr-xr-x  1 root root   748 2006-01-23 21:47 loopback
 4 -rwxr-xr-x  1 root root  1399 2008-02-26 00:20 module-init-tools
 4 -rwxr-xr-x  1 root root   596 2008-04-18 20:02 mountall-bootclean.sh
 4 -rwxr-xr-x  1 root root  2430 2008-04-18 20:02 mountall.sh
 4 -rwxr-xr-x  1 root root  1465 2008-04-18 20:02 mountdevsubfs.sh
 4 -rwxr-xr-x  1 root root  1544 2008-04-18 20:02 mountkernfs.sh
 4 -rwxr-xr-x  1 root root   594 2008-04-18 20:02 mountnfs-bootclean.sh
 4 -rwxr-xr-x  1 root root  1244 2008-04-18 20:02 mountoverflowtmp
 4 -rwxr-xr-x  1 root root  3123 2008-04-18 20:02 mtab.sh
 4 -rwxr-xr-x  1 root root  1772 2007-12-03 23:50 networking
 8 -rwxr-xr-x  1 root root  5942 2008-12-02 22:32 nfs-common
 4 -rwxr-xr-x  1 root root  2377 2007-10-23 21:02 pcmciautils
 4 -rwxr-xr-x  1 root root  1872 2007-12-04 03:21 portmap
 8 -rwxr-xr-x  1 root root  4202 2008-04-18 20:50 postfix
 4 -rwxr-xr-x  1 root root  1396 2008-09-17 16:04 postgresql-8.3
 4 -rwxr-xr-x  1 root root   375 2007-10-05 00:47 pppd-dns
 4 -rwxr-xr-x  1 root root  1261 2008-03-14 02:02 procps
 8 -rwxr-xr-x  1 root root  7891 2008-04-19 09:05 rc
 4 -rwxr-xr-x  1 root root   522 2008-04-18 20:02 rc.local
 4 -rwxr-xr-x  1 root root   117 2008-04-19 09:05 rcS
 4 -rw-r--r--  1 root root  1335 2008-04-19 09:05 README
 4 -rwxr-xr-x  1 root root   692 2008-04-18 20:02 reboot
 4 -rwxr-xr-x  1 root root  1000 2008-04-18 20:02 rmnologin
 8 -rwxr-xr-x  1 root root  4945 2008-04-11 04:11 rsync
 4 -rwxr-xr-x  1 root root  2663 2008-06-30 19:54 samba
 4 -rwxr-xr-x  1 root root  1199 2008-04-18 20:02 sendsigs
 4 -rwxr-xr-x  1 root root   585 2008-04-18 20:02 single
 8 -rwxr-xr-x  1 root root  4215 2008-04-18 20:02 skeleton
60 -rwxr-xr-x  1 root root 56080 2012-05-29 13:26 snmpd
 4 -rwxr-xr-x  1 root root  3839 2008-05-14 18:39 ssh
 4 -rwxr-xr-x  1 root root   510 2008-04-18 20:02 stop-bootlogd
 4 -rwxr-xr-x  1 root root   647 2008-04-18 20:02 stop-bootlogd-single
 4 -rwxr-xr-x  1 root root  3343 2007-11-23 12:02 sysklogd
 4 -rwxr-xr-x  1 root root  2488 2008-04-11 16:22 udev
 4 -rwxr-xr-x  1 root root   706 2008-04-11 16:22 udev-finish
 8 -rwxr-xr-x  1 root root  7053 2008-07-25 11:23 ufw
 4 -rwxr-xr-x  1 root root  4030 2008-04-18 20:02 umountfs
 4 -rwxr-xr-x  1 root root  1833 2008-04-18 20:02 umountnfs.sh
 4 -rwxr-xr-x  1 root root  1863 2008-04-18 20:02 umountroot
 4 -rwxr-xr-x  1 root root  1815 2008-04-18 20:02 urandom
 4 -rwxr-xr-x  1 root root  2445 2008-04-18 20:02 waitnfs.sh
 4 -rwxr-xr-x  1 root root  1224 2008-06-30 19:54 winbind
 4 -rwxr-xr-x  1 root root  1626 2008-03-13 03:19 wpa-ifupdown
 4 -rwxr-xr-x  1 root root  1843 2008-05-14 04:10 x11-common
```

---

### Post by allan7 on 2015-05-21
Do you know if it was installed previously?
You want to try to install it?
sudo apt-get update
sudo apt-get install apache2

Reminder: don't experiment on a production environment.

---

### Post by amkashirin on 2015-05-21
I know that apache was installed previosly. This is 100%. May be not standart installing was. How I can find it?

---

### Post by allan7 on 2015-05-21
there are a couple of ways to find out.

1. ps aux | grep apache*
2. which apachectl -- it will locate where the program is
and if not try to run: aptitude 
then press / to do a search. type apache and see if there's letter i in front of the entry then i think it is installed

---

### Post by amkashirin on 2015-05-22
user@server:~$ ps aux | grep apache*
user  10567  0.0  0.0   5164   840 pts/0    S+   08:58   0:00 grep apache*

---

### Post by allan7 on 2015-05-22
I don't think it is installed. 
I would suggest to run the installation and if it's already there the system will just prompt if you have the latest version and you can choose to proceed or not

---

### Post by amkashirin on 2015-05-22
I find it:
wwwuser@srvis9:~/Distr/httpd-2.2.9$ ls -las
total 1500
  4 drwxr-xr-x 12     501 staff     4096 2008-09-17 17:49 .
  4 drwxr-xr-x 10 wwwuser wwwuser   4096 2013-08-15 18:21 ..
 16 -rw-r--r--  1     501 staff    14882 2004-11-21 21:50 ABOUT_APACHE
 20 -rw-r--r--  1     501 staff    18886 2008-02-05 02:00 acinclude.m4
 60 -rw-r--r--  1     501 staff    54614 2008-06-07 07:13 Apache.dsw
192 -rw-r--r--  1     501 staff   189152 2004-11-21 21:50 apachenw.mcp.zip
  4 drwxr-xr-x  5     501 staff     4096 2008-09-17 17:52 build
  4 -rw-r--r--  1     501 staff     2644 2007-08-24 10:00 BuildAll.dsp
  4 -rw-r--r--  1     501 staff     2694 2008-06-07 07:13 BuildBin.dsp
  8 -rwxr-xr-x  1     501 staff     5771 2006-07-12 07:38 buildconf
  8 -rw-r--r--  1 root    root      6216 2008-09-17 17:49 buildmark.o
 88 -rw-r--r--  1     501 staff    85602 2008-06-10 22:49 CHANGES
 12 -rw-r--r--  1     501 staff    10943 2004-11-21 21:50 config.layout
 56 -rw-r--r--  1 root    root     52020 2008-09-17 17:46 config.log
  4 -rwxr-xr-x  1 root    root       207 2008-09-17 17:46 config.nice
 40 -rwxr-xr-x  1 root    root     40738 2008-09-17 17:46 config.status
652 -rwxr-xr-x  1     501 staff   660990 2008-06-10 23:18 configure
 24 -rw-r--r--  1     501 staff    23300 2008-06-09 20:04 configure.in
  0 -rw-r--r--  1     501 staff        0 2008-09-17 17:46 .deps
  4 drwxr-xr-x  9     501 staff     4096 2008-06-10 23:17 docs
  4 -rw-r--r--  1     501 staff      403 2004-11-21 21:50 emacs-style
  8 -rw-r--r--  1     501 staff     7214 2005-01-24 17:51 .gdbinit
  8 -rwxr-xr-x  1 root    root      6710 2008-09-17 17:49 httpd
  8 -rw-r--r--  1     501 staff     4124 2007-01-11 08:44 httpd.dsp
 20 -rw-r--r--  1     501 staff    19127 2008-06-10 23:18 httpd.spec
  4 drwxr-xr-x  2     501 staff     4096 2008-09-17 17:46 include
  8 -rw-r--r--  1     501 staff     4306 2008-02-13 15:54 INSTALL
  4 -rw-r--r--  1     501 staff     2909 2006-12-07 20:49 InstallBin.dsp
  8 -rw-r--r--  1     501 staff     5145 2005-11-29 11:56 LAYOUT
 20 -rw-r--r--  1     501 staff    17039 2007-01-12 13:53 libhttpd.dsp
  4 drwxr-xr-x  2 root    root      4096 2008-09-17 17:49 .libs
 32 -rw-r--r--  1     501 staff    28690 2008-01-19 02:32 LICENSE
 12 -rw-r--r--  1 root    root      8931 2008-09-17 17:46 Makefile
 12 -rw-r--r--  1     501 staff     8696 2008-02-05 02:00 Makefile.in
 36 -rw-r--r--  1     501 staff    33681 2008-06-07 07:13 Makefile.win
  4 drwxr-xr-x 20     501 staff     4096 2008-09-17 16:58 modules
  4 -rw-r--r--  1 root    root      3952 2008-09-17 17:46 modules.c
  4 -rw-r--r--  1 root    root       312 2008-09-17 17:49 modules.lo
 24 -rw-r--r--  1 root    root     22088 2008-09-17 17:49 modules.o
  4 -rw-r--r--  1     501 staff      828 2008-01-11 16:23 NOTICE
 12 -rw-r--r--  1     501 staff    10559 2007-08-06 21:58 NWGNUmakefile
  4 drwxr-xr-x  9     501 staff     4096 2008-09-17 16:58 os
  8 -rw-r--r--  1     501 staff     5954 2007-01-10 08:50 README
  8 -rw-r--r--  1     501 staff     4992 2008-02-18 18:02 README.platforms
 12 -rw-r--r--  1     501 staff    10183 2005-03-14 08:24 ROADMAP
  4 drwxr-xr-x  4     501 staff     4096 2008-09-17 17:48 server
  4 drwxr-xr-x  5     501 staff     4096 2008-09-17 16:58 srclib
  4 drwxr-xr-x  5     501 staff     4096 2008-09-17 17:49 support
  4 drwxr-xr-x  2     501 staff     4096 2008-09-17 16:58 test
  8 -rw-r--r--  1     501 staff     8183 2005-10-17 21:17 VERSIONING


may be it help?

---

### Post by amkashirin on 2015-05-22
I find it!!!!:popcorn:

find / -name httpd
/home/wwwuser/Distr/httpd-2.2.9/.libs/httpd
/home/wwwuser/Distr/httpd-2.2.9/httpd
/usr/local/apache/bin/httpd

cd /usr/local/apache/bin
./httpd -k  start

After that apache started and work.

Thanks for your time!

---

### Post by allan7 on 2015-05-22
Glad to hear you figured it out. It looks to me as it was purposely installed in a specific folder. But anyways... I am not so familiar with an older version.

Have fun with it!!! 

Cheers:guitar:

---

### Post by SeijiSensei on 2015-05-22
Apache is installed to /usr/local only if you built it from source.  If you use the repository versions, as you generally should, it would be stored as /usr/sbin/apache2.

---

