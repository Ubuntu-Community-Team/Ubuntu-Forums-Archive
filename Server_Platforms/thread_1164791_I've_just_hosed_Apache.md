---
title: "I've just hosed Apache"
date: 2009-05-20
forum: Server Platforms
---

### Post by aaronLund on 2009-05-20
.....and can't seem to get it going.

When I run:

```
sudo /etc/init.d/apache2 restart
```

I get:

```
 * Restarting web server apache2                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 19 21:50:39 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 19 21:50:39 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

                                                                         [fail]
```

I don't see it running when I grep for it either.  (only see my grep)

This was working a while back......say, a couple of months ago.  It's been a while since I've worked locally though.

Anyway...I'm sure I'm doing something stupid.  Thanks for any advice.

---

### Post by bapoumba on 2009-05-21
Moved to Servers.

---

### Post by mbeach on 2009-05-21
take a look at:
[http://ubuntuforums.org/showthread.php?t=1164382](http://ubuntuforums.org/showthread.php?t=1164382)

specifically take a read of:
/usr/share/doc/apache2/NEWS.Debian.gz

---

