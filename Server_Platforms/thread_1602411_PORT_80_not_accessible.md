---
title: "PORT 80 not accessible"
date: 2010-10-21
forum: Server Platforms
---

### Post by mofire on 2010-10-21
Hey all,

I have a Ubuntu server,that was fully configured in one location and was functioning okay. But once I moved to another location where the network configuration has to be changed by assigning it another public IP and network  settings I encountered a problem. the problem is that all other ports are working okay e.g. FTP,webmin etc. but port 80 is not working. could any one have an idea what could the problem, I will really appreciate. Thanks.

---

### Post by Iowan on 2010-10-21
I'll need to look up specifics, but there's an Apache config file that probably sets IP/port. It's possible the port is open... just for the wrong address...

Moved to Server platforms.

---

### Post by James78 on 2010-10-21
Check your VirtualHost configuration. Inside /etc/apache2/sites-enabled

On my server, it shows <VirtualHost 192.168.1.120:80>, but yours, for the IP, might show a public WAN IP.

P.S. Also check NameVirtualHost, as that should mirror the IP also.

---

