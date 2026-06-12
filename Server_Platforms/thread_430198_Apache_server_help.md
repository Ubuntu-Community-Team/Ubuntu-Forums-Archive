---
title: "Apache server help"
date: 2007-05-01
forum: Server Platforms
---

### Post by SuperCow56 on 2007-05-01
I am completely new to this whole server thing, and I don't know anything about it.  When I try and run apache I get this:
```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by kidders on 2007-05-03
Hi there,

> **SuperCow56 said:**
> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerNameThat's not critical, so you can ignore that for the moment.
> **SuperCow56 said:**
>  (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80This however is _not_ good. This may seem like a daft question, but how are you starting Apache, exactly?

It seems not to have sufficient privileges to set up the infrastructure necessary to bind to a network interface. :confused:

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

