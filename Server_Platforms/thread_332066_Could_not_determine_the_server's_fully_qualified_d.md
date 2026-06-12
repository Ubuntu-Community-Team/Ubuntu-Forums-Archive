---
title: "Could not determine the server's fully qualified domain name"
date: 2007-01-05
forum: Server Platforms
---

### Post by aceron on 2007-01-05
I keep getting this error message when ever i try to start, stop or restart apache2 
> Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
I think this is stopping me from making my webserver public as well.  Do I need to change something in apache for a dynamic host?
Any help would be great and let me know if you need to see any files.

---

### Post by malakhi on 2007-01-05
Please paste the output of ```
hostname
``` and ```
hostname --fqdn
```

Also, make sure Apache is configured with the hostname you are trying to access it with. In other words, if you are trying to reach it with [http://example.com](http://example.com), make sure that is what is listed in apache2.conf

---

### Post by chrisfay on 2007-01-05
> I think this is stopping me from making my webserver public as well.

The error is innocuous in this regard.

---

### Post by maggotbrain on 2007-01-06
> **chrisfay said:**
> The error is innocuous in this regard.

Chrisfay is correct, here.

However, you can clear up this error message by adding the following line to your apache.conf file:

**ServerName** *your.servername.here*

This can be either just the hostname or a fully qualified domain name.

---

