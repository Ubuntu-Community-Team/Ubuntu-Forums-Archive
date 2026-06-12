---
title: "Why is root running apache?"
date: 2014-02-13
forum: Server Platforms
---

### Post by monkeybrain20122 on 2014-02-13
I found this with the ps command(Other entries removed)

```
$ ps -U root
  PID TTY          TIME CMD
    
 1262 ?        00:00:00 apache2
 
```

 
```
$ ps -u www-data
  PID TTY          TIME CMD
 1543 ?        00:00:01 apache2
 1544 ?        00:00:01 apache2
 1545 ?        00:00:01 apache2
 1546 ?        00:00:01 apache2
 1547 ?        00:00:01 apache2
 3593 ?        00:00:01 apache2
```

Shouldn't apache2 be run by www-data? I haven't modified any configuration.

Also 

```
~$ ls -l /var/www
total 12
-rw-r--r-- 1 root root  177 Jan 20 03:41 index.html
-rw-r--r-- 1 root root   20 Jan 20 04:50 info.php
drwxr-xr-x 3 root root 4096 Jan 28 00:28 R

```

Shouldn't the webroot be owned by www-data instead of root? Again I haven't changed any configuration.

---

### Post by slickymaster on 2014-02-13
By default, on Ubuntu, Apache runs as www-data but it must start as root in order to bind to port 80 (and 443 if SSLing). But it doesn't actually listen to it, the www-data process is the one that listens to port 80 and interacts with users.

---

### Post by sandyd on 2014-02-13
moved to server platforms

---

### Post by SeijiSensei on 2014-02-16
All server processes that use listeners with restricted permissions have to start first as root.  Usually they leave a "stub" behind with root privileges and spawn children as the restricted owner.  Here's the output for Apache on my CentOS 6.4 server:

```

root     18204  0.0  0.9 267052  9708 ?        Ss   Feb14   0:22 /usr/sbin/httpd
apache   25068  0.0  2.8 286796 28872 ?        S    10:14   0:00 /usr/sbin/httpd
apache   25089  0.0  2.6 284688 26776 ?        S    10:15   0:00 /usr/sbin/httpd
apache   25093  0.0  1.0 269600 10764 ?        S    10:15   0:00 /usr/sbin/httpd
apache   25132  0.0  0.6 267184  7000 ?        S    10:16   0:00 /usr/sbin/httpd
apache   25167  0.0  0.7 267184  7116 ?        S    10:18   0:00 /usr/sbin/httpd
apache   25168  0.0  0.6 267184  7000 ?        S    10:18   0:00 /usr/sbin/httpd
apache   25232  0.0  1.2 271280 12380 ?        S    10:20   0:00 /usr/sbin/httpd
apache   25233  0.0  0.6 267184  7000 ?        S    10:20   0:00 /usr/sbin/httpd
apache   25240  0.0  0.6 267184  6960 ?        S    10:21   0:00 /usr/sbin/httpd
apache   25283  0.0  0.6 267184  6960 ?        S    10:22   0:00 /usr/sbin/httpd

```
The "apache" user in RedHat/CentOS is the equivalent of www-user in Debian/Ubuntu.

---

