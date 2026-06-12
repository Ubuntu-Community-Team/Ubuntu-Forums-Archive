---
title: "Automatic Deploy using preseed"
date: 2013-08-10
forum: Server Platforms
---

### Post by Trent_Vendy on 2013-08-10
I have a reasonable understanding of Ubuntu Server but I'm at a loss here.
I am trying to setup an auto-install server using preseed. The idea being: I want 2 types of nodes, Web and Database, when a new node is network booted, it asks which category the new node will be applied to (web or database), then provisions that node appropriately. I am using tftpd-hpa and dhcpd3, it loads the customized install screen, but no matter what I select, my preseed file never gets loaded and you have to manually input at each screen, and once you finish the install, the extra packages I told it to install aren't there. 

Any ideas?

---

### Post by awells527 on 2013-08-13
It sounds like the preseed file is not being downloaded.  Can you check the Apache logs on your preseed server and see if the file is even requested by the clients?

I run something like this to verify:

```
[root@server ~]$ cat /var/log/apache2/access.log | grep preseed.php
192.168.15.138 - - [05/Aug/2013:10:18:45 -0500] "GET /ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2743 "-" "Wget"
192.168.15.111 - - [05/Aug/2013:10:20:47 -0500] "GET /ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2743 "-" "Wget"
192.168.15.111 - - [05/Aug/2013:13:09:42 -0500] "GET /ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2743 "-" "Wget"
192.168.15.84 - - [05/Aug/2013:14:54:51 -0500] "GET /ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2775 "-" "Wget"
192.168.15.84 - - [05/Aug/2013:17:26:20 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.65 - - [05/Aug/2013:19:12:26 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.84 - - [05/Aug/2013:19:49:35 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.84 - - [05/Aug/2013:20:20:42 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.65 - - [06/Aug/2013:06:19:26 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.144 - - [07/Aug/2013:10:52:18 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.144 - - [07/Aug/2013:15:00:42 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.149 - - [07/Aug/2013:15:01:08 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.148 - - [07/Aug/2013:15:01:54 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.144 - - [10/Aug/2013:08:13:42 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.83 - - [10/Aug/2013:08:25:32 -0500] "GET /deploy/ps/preseed.php?server=1&autopart=1 HTTP/1.1" 200 2937 "-" "Wget"
192.168.15.81 - - [13/Aug/2013:10:25:19 -0500] "GET /deploy/ps/preseed.php?xfce=1&autopart=1 HTTP/1.1" 200 3021 "-" "Wget"
192.168.15.81 - - [13/Aug/2013:11:42:28 -0500] "GET /deploy/ps/preseed.php?xfce=1&autopart=1 HTTP/1.1" 200 3021 "-" "Wget"
192.168.15.81 - - [13/Aug/2013:12:34:10 -0500] "GET /deploy/ps/preseed.php?xfce=1&autopart=1 HTTP/1.1" 200 3026 "-" "Wget"
```

Check for possible 404 errors or even 500 errors in case the web server isn't correctly configured.

---

