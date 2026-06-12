---
title: "Apache2 Secure Server"
date: 2007-05-21
forum: Server Platforms
---

### Post by revelation1114 on 2007-05-21
Hey, I'm trying to set up an Apache2 secure server with SSL. I keep getting this error when I try to start Apache2:
```
(98)Address already in use: make_sock: could not bind to address <my_ip>:80
no listening sockets available, shutting down
Unable to open logs

```

netstat -lnp | grep 80 gives nothing, so I don't think there's anything using port 80.

Now, I've set my ports.conf to Listen <my ip address>:80, my VirtualHost *:80 to VirtualHost <my ip address>:80 and my mod-ssl.conf to Listen <my ip address>:80. This error **only** comes up when I have mod_ssl enabled. I can't figure out why it's unable to bind to port 80, and Apache won't be more verbose in logs.

Any help given would be greatly appreciated.

---

### Post by mbradlcu on 2007-05-22
here's my ports config for apache that has ssl working:

> root@lnx-file1:/etc/apache2# cat ports.conf 
Listen 80
Listen 443


I think you need apache to listen on 443,
hope this helps

---

### Post by Wim Sturkenboom on 2007-05-22
Not familiar with the Ubuntu server setup, but there might be a chance that somewhere in one of the apache configs is a another *LISTEN 80*.

---

### Post by linuxstbdotcom on 2007-06-04
Simple edit you mod_ssl.conf file in etc/apache2/conf.d and comment out the two listen ports. Now why port 80 is there at two places i don't know ;)

---

