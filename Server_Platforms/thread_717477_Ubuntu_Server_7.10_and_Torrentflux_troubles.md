---
title: "Ubuntu Server 7.10 and Torrentflux troubles"
date: 2008-03-07
forum: Server Platforms
---

### Post by papodaca on 2008-03-07
I've looked at all the threads on torrentflux, I have installed the LAMP server from the cd.  Updated everything, then installed torrentflux from the repository.  It seems to be working but when it comes to using torrent they fail right away.  All of the settings are green in the admin settings page.  And i have made sure that all of the permissions are torrent for the critical files and am an end as to what is happening.  If any one has any idea it would be very helpful or i may have to look at the new Transsmission web ui.....

---

### Post by cox377 on 2008-03-07
have you checked the logs?

CoXen

---

### Post by papodaca on 2008-03-07
don't think there is anything useful nor anything referring to torrentflux but here is the /var/log/apache2/error.log:
> [Thu Mar 06 10:09:52 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 configured -- resuming normal operations
[Thu Mar 06 10:38:54 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 10:40:09 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Thu Mar 06 10:40:10 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 06 10:40:10 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Thu Mar 06 10:41:16 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 18:42:25 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Thu Mar 06 20:31:23 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 20:32:33 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Thu Mar 06 20:36:40 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 20:37:49 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Thu Mar 06 22:22:43 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 22:45:45 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 06 22:47:41 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 06 22:47:41 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 06 23:45:38 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 06 23:47:25 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Fri Mar 07 00:20:53 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Mar 07 00:21:03 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Fri Mar 07 00:46:58 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Mar 07 00:47:01 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

---

