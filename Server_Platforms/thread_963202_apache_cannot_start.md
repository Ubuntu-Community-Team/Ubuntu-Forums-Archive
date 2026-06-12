---
title: "apache cannot start"
date: 2008-10-30
forum: Server Platforms
---

### Post by blackcloud on 2008-10-30
after installing ffmpeg and adding extension=ffmpeg.so i try to restart my apache but my apache not work this my log :

[Thu Oct 30 08:45:11 2008] [alert] FastCGI: read() from pipe failed (0)
[Thu Oct 30 08:45:11 2008] [alert] FastCGI: the PM is shutting down, Apache seems to have disappeared - bye
[Thu Oct 30 08:47:55 2008] [notice] FastCGI: process manager initialized (pid 8387)
/usr/sbin/apache2: symbol lookup error: /usr/lib/php5/20060613+lfs/ffmpeg.so: undefined symbol: avcodec_build
[Thu Oct 30 08:47:55 2008] [alert] FastCGI: read() from pipe failed (0)
[Thu Oct 30 08:47:55 2008] [alert] FastCGI: the PM is shutting down, Apache seems to have disappeared - bye
[Thu Oct 30 08:50:22 2008] [notice] FastCGI: process manager initialized (pid 8415)
[Thu Oct 30 08:50:22 2008] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Thu Oct 30 08:50:22 2008] [notice] Apache/2.2.4 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.2.3-1ubuntu6.4 configured -- resuming normal operations 

how i can solve my problem help me plss.

---

