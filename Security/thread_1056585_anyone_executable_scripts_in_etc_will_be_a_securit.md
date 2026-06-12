---
title: "anyone executable scripts in /etc will be a security hole?"
date: 2009-01-31
forum: Security
---

### Post by say2sky on 2009-01-31
today I am curious to find what is the file permissions in /etc directory for a new system, it shows a lot of scripts are executable by anyone.

```
ls -Rla /etc/|grep -v ^d |grep -v ^l|grep -v "\-rw\-"|grep -v ^total |grep -v ^/|grep -v ^$ 
-rwxr-xr-x   1 root root       306 2008-11-09 08:49 rc.local
-rwxr-xr-x   1 root root       268 2008-05-03 15:40 rmt
-r--r-----   1 root root       502 2008-11-09 16:14 sudoers
-rwxr-xr-x 1 root root 698 2008-09-03 07:37 85-anacron.sh
-rwxr-xr-x 1 root root 168 2008-09-03 07:37 15-anacron.sh
-rwxr-xr-x 1 root root 698 2008-09-03 07:37 85-anacron.sh
-rwxr-xr-x 1 root root 168 2008-09-03 07:37 15-anacron.sh
-rwxr-xr-x 1 root root 400 2008-11-07 07:53 alsa-utils
-rwxr-xr-x 1 root root 753 2008-09-03 07:37 anacron
-rwxr-xr-x 1 root root 961 2008-10-16 09:50 ppp
-rwxr-xr-x 1 root root 216 2008-11-05 12:19 alsa
-rwxr-xr-x 1 root root 24 2008-10-17 06:10 usplash
-rwxr-xr-x   1 root root  311 2008-09-03 07:37 0anacron
-rwxr-xr-x   1 root root  633 2008-11-05 23:53 apache2
-rwxr-xr-x   1 root root 7679 2008-11-24 20:16 apt
-rwxr-xr-x   1 root root  314 2008-09-02 20:50 aptitude
-rwxr-xr-x   1 root root  502 2008-11-05 05:43 bsdmainutils
-rwxr-xr-x   1 root root 1958 2009-01-15 15:18 chkrootkit
-rwxr-xr-x   1 root root   89 2008-11-07 22:07 logrotate
-rwxr-xr-x   1 root root  954 2008-11-05 20:34 man-db
-rwxr-xr-x   1 root root 1154 2008-08-21 01:04 ntp
-rwxr-xr-x   1 root root  651 2008-10-01 19:41 rkhunter
-rwxr-xr-x   1 root root 3349 2008-09-10 03:46 standard
-rwxr-xr-x   1 root root 1309 2008-08-30 08:40 sysklogd
-rwxr-xr-x   1 root root  313 2008-09-03 07:37 0anacron
-rwxr-xr-x   1 root root  129 2008-09-10 03:46 standard
-rwxr-xr-x   1 root root  312 2008-09-03 07:37 0anacron
-rwxr-xr-x   1 root root  107 2009-01-31 22:44 apt-xapian-index
-rwxr-xr-x   1 root root  528 2008-11-05 20:34 man-db
-rwxr-xr-x   1 root root 1785 2008-10-01 19:41 rkhunter
-rwxr-xr-x   1 root root 1220 2008-08-30 08:40 sysklogd
-rwxr-xr-x 1 root root 1753 2008-11-07 04:03 samba
-rwxr-xr-x   1 root root  8504 2008-10-23 21:40 failsafeDexconf
-rwxr-xr-x   1 root root  5618 2008-06-25 10:05 failsafeDexconf.old
-rwxr-xr-x   1 root root  7830 2008-12-22 16:20 failsafeXinit
-rwxr-xr-x   1 root root  4582 2008-10-23 21:40 failsafeXServer
-rwxr-xr-x   1 root root  4182 2008-11-08 23:52 XKeepsCrashing
-rwxr-xr-x   1 root root  6259 2008-11-08 23:50 Xsession

```

I think this should be reasonable.
but
why these scripts need to be global executable? will these can be a security hole?

---

### Post by cariboo on 2009-02-01
Most of the scripts are startup scripts for the various services that are started at boot time and configuration files. Have a look at this [page]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html") for an overview of the Linux File system.

Jim

---

