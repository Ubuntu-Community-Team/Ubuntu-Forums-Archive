---
title: "Apache Periodically Locks Up"
date: 2009-09-09
forum: Server Platforms
---

### Post by Palcrypt on 2009-09-09
I've noticed over the last year or so that Apache (2.2.4) periodically locks up and I have to restart it. I've been having trouble tracking down the problem. A look through the apache error log reveals a number of sections like the following:

[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [notice] Graceful restart requested, doing restart
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 19148 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25447 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 493 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 572 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25543 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25607 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25405 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25443 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 474 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25445 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 26731 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25609 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25403 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 491 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 472 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 30855 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 494 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 496 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 573 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 473 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 574 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 617 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 642 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25574 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25575 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25576 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 25577 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [notice] (10)No child processes: cannot send signal 10 to pid 654 (non-child or already dead)
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [error] VirtualHost 208.52.173.12:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Sep 07 07:35:05 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Sun Sep 07 07:35:05 2008] [error] [client 127.0.0.1] File does not exist: /htdocs



Then there is also this at one point:

[Mon Sep 07 18:55:45 2009] [notice] (10)No child processes: cannot send signal 10 to pid 1314 (non-child or already dead)
[Mon Sep 07 18:55:45 2009] [notice] caught SIGWINCH, shutting down gracefully
[Mon Sep 07 18:55:47 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations


I'm not sure if any of that is indicative of my problem, but it is a real nuisance. A couple times a month or so I'll just notice that my sites aren't coming up, and when I restart apache everything is fine. Any help would be greatly appreciated.

p.s. I'm on Ubuntu 7.10 server.

---

