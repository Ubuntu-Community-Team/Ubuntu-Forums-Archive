---
title: "Internal Server Error."
date: 2007-04-29
forum: Server Platforms
---

### Post by thebear8me on 2007-04-29
I have set up Ubuntu server and had the web server running fine.  I updated my web page on my macbook and conneted via SSH and tranfered the files.  Now for some reason I am getting an internal error when trying to view the web pages.  I tried transfering the files as binary and ascii without any success.  Here is what my apache error log shows.

```
[Sun Apr 29 21:53:29 2007] [crit] [client 192.168.15.117] configuration error:  couldn't perform authentication. AuthType not set!: /
[Sun Apr 29 21:53:31 2007] [crit] [client 192.168.15.117] configuration error:  couldn't perform authentication. AuthType not set!: /
[Sun Apr 29 21:53:32 2007] [crit] [client 192.168.15.117] configuration error:  couldn't perform authentication. AuthType not set!: /
[Sun Apr 29 21:54:02 2007] [notice] SIGHUP received.  Attempting to restart
[Sun Apr 29 21:54:02 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
[Sun Apr 29 21:54:04 2007] [crit] [client 192.168.15.117] configuration error:  couldn't perform authentication. AuthType not set!: /
[Sun Apr 29 21:54:05 2007] [crit] [client 192.168.15.117] configuration error:  couldn't perform authentication. AuthType not set!: /
[Sun Apr 29 22:10:27 2007] [notice] caught SIGTERM, shutting down
[Sun Apr 29 22:12:18 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
[Sun Apr 29 22:16:12 2007] [crit] [client 192.168.15.104] configuration error:  couldn't perform authentication. AuthType not set!: /
```

Any help would be very much appreciated.

This is my first go at the Ubuntu server.

Thanks

---

### Post by thebear8me on 2007-04-30
Any ideas?:confused: 


Thanks

---

