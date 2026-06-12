---
title: "Webserver ... IP"
date: 2010-12-23
forum: Server Platforms
---

### Post by timZZ on 2010-12-23
Hi,

If I am using Ubuntu 64 bit Server platform running Apache with Virtual hosts and I am looking to research what IP's accessed the machine via port 80 (Website) between a set period of time ...

How would I do this?

---

### Post by arrrghhh on 2010-12-23
[http://httpd.apache.org/docs/2.2/logs.html](http://httpd.apache.org/docs/2.2/logs.html)

See the section on 'Access Logs'

---

### Post by timZZ on 2010-12-23
Yes I thought this might be is ... I can see within the configuration this is not enabled.

#
# The location and format of the access logfile (Common Logfile Format).
# If you do not define any access logfiles within a <VirtualHost>
# container, they will be logged here.  Contrariwise, if you *do*
# define per-<VirtualHost> access logfiles, transactions will be
# logged therein and *not* in this file.
#
#CustomLog logs/access_log common

I will take a look into this.

---

### Post by Calimo on 2010-12-26
Most likely it was defined somewhere else. Have a look in /var/log/apache2. You'll have an "access.log" file with what you want.

---

### Post by timZZ on 2010-12-26
My logs are within /var/log/httpd

---

### Post by timZZ on 2010-12-26
To expand in more detail

within `httpd` I have a log call `access_log` but it does not show the detail I am looking for ..

I can see IP and access.

I am only seeing webmail which I know is not true from Google Analytics and we just went through Christmas and we are a web only company.

---

### Post by 1v82TIn1 on 2010-12-26
I'm not sure if this is what you are looking for but it is worth a try.
There is a GUI application that you can view service and system logs in called "KSystemLog".
When in the application, you can find it in Services > Apache > Access log.

To install it just go to terminal and type:

sudo apt-get install ksystemlog

---

### Post by timZZ on 2010-12-26
I am not running Gnome etc.

I have command line only.

---

### Post by 1v82TIn1 on 2010-12-26
Can you please post output of:

ls /var/log/httpd

---

### Post by timZZ on 2010-12-26
[root@server170 httpd]# ls -l
total 168
-rw-r--r-- 1 root root     0 Dec 26 03:04 access_log
-rw-r--r-- 1 root root   235 Dec 26 03:04 access_log.1.gz
-rw-r--r-- 1 root root   259 Dec 25 03:04 access_log.2.gz
-rw-r--r-- 1 root root  2674 Dec 24 03:04 access_log.3.gz
-rw-r--r-- 1 root root  3054 Dec 23 03:04 access_log.4.gz
-rw-r--r-- 1 root root  3358 Dec 22 03:05 access_log.5.gz
-rw-r--r-- 1 root root  3323 Dec 21 03:04 access_log.6.gz
-rw-r--r-- 1 root root   869 Dec 20 03:04 access_log.7.gz
-rw-r----- 1 root root 22350 Dec 26 06:48 audit_log
-rw-r----- 1 root root  8504 Dec 26 03:04 audit_log.1.gz
-rw-r----- 1 root root  2396 Dec 25 03:04 audit_log.2.gz
-rw-r----- 1 root root  4028 Dec 24 03:04 audit_log.3.gz
-rw-r----- 1 root root  2134 Dec 23 03:04 audit_log.4.gz
-rw-r----- 1 root root  6193 Dec 22 03:05 audit_log.5.gz
-rw-r----- 1 root root  8008 Dec 21 03:04 audit_log.6.gz
-rw-r----- 1 root root  3390 Dec 20 03:04 audit_log.7.gz
-rw-r--r-- 1 root root  1519 Dec 26 03:04 error_log
-rw-r--r-- 1 root root   504 Dec 26 03:04 error_log.1.gz
-rw-r--r-- 1 root root   499 Dec 25 03:04 error_log.2.gz
-rw-r--r-- 1 root root   504 Dec 24 03:04 error_log.3.gz
-rw-r--r-- 1 root root   498 Dec 23 03:04 error_log.4.gz
-rw-r--r-- 1 root root   504 Dec 22 03:05 error_log.5.gz
-rw-r--r-- 1 root root   497 Dec 21 03:04 error_log.6.gz
-rw-r--r-- 1 root root   534 Dec 20 03:04 error_log.7.gz
-rw-r----- 1 root root     0 Jan 20  2010 modsec_debug_log
-rw-r--r-- 1 root root     0 Jan 19  2010 ssl_access_log
-rw-r--r-- 1 root root   237 Dec 26 03:04 ssl_error_log

I have rotating logs

---

### Post by 1v82TIn1 on 2010-12-26
It seems that you have a log for each day in a compressed format. You could try unzipping them and viewing them.
e.g.

cd <directory of apache logs>
gunzip access_log.1.gz


And if you want to compress them again:

cd <directory of apache logs>
gzip access_log.1.gz


Otherwise, if that doesn't work, you could always just sftp from another Ubuntu machine with a GUI on the same network.

---

### Post by SeijiSensei on 2010-12-28
> **timZZ said:**
> I am only seeing webmail which I know is not true from Google Analytics and we just went through Christmas and we are a web only company.

Are you hosting virtual domains?  Are there custom logs defined in the <VirtualHost> containers for those domains?

---

