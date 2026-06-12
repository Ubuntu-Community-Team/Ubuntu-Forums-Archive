---
title: "Cannot load certificate file server.crt: error:0906D06C"
date: 2014-05-29
forum: Server Platforms
---

### Post by smbit on 2014-05-29
Hi, all!
I'm trying to configure OpenVPN on the Ubuntu Server 14.04 using instructions pointed in the *Server Guide*.
Server configuration file was taken from the */usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz *
After running *ser*[I]vice openvpn start

[/I]The following appeared in the [I]/var/log/syslog

[/I]```
Cannot load certificate file server.crt: error:0906D06C:PEM routines:PEM_read_bio:no start line: error:140AD009:SSL routines:SSL_CTX_use_certificate_file:PEM lib 
```

All files included in the same directory as configuration file in* /etc/openvpn*

[I] server.crt
server.key
ca.crt
df2048.pem
[/I]
.. and all entries are setup properly in the *server.conf* file as well.
what can cause the issue. where troubleshooting steps should be started ?!! Please advice.. thank's :confused:

---

### Post by Habitual on 2014-05-29
How was the package installed?

---

### Post by smbit on 2014-05-29
via *apt-get install openvpn easy-rsa *

---

