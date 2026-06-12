---
title: "New LAMP Install Apache Errors"
date: 2009-12-15
forum: Server Platforms
---

### Post by indytim on 2009-12-15
I just finished installing a LAMP in Gnome via tasksel.  The version installed is:
Apache 2.2.11-2Ubuntu2.5
PHP 5.2.6
MySQL 5.1.3

I'm getting errors at:

> 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


Been so long since I had to get into nats details on configuring a LAMP in a desktop environment.  Would appreciate pointers to what config file needs to be changed to kick the Apache server off successfully.

Thanks,

IndyTim

---

### Post by car1 on 2009-12-15
You can just add a line to the /etc/hosts file that points your server's hostname to 127.0.0.1:

"127.0.0.1    server_hostname"

---

### Post by indytim on 2009-12-15
Thanks for the reply Car1.  Unfortunately, it's already defined there.

> 
127.0.0.1	localhost


IndyTim

---

### Post by HighCommander540 on 2009-12-15
> **indytim said:**
> I just finished installing a LAMP in Gnome via tasksel.  The version installed is:
Apache 2.2.11-2Ubuntu2.5
PHP 5.2.6
MySQL 5.1.3

I'm getting errors at:



Been so long since I had to get into nats details on configuring a LAMP in a desktop environment.  Would appreciate pointers to what config file needs to be changed to kick the Apache server off successfully.

Thanks,

IndyTim

Well it looks like it just configured wrong. If it is really reading. 127.0.1.1. That is not localhost.

---

### Post by indytim on 2009-12-15
Thanks,

Which Apache config file do I need to modify?

IndyTim

---

### Post by car1 on 2009-12-15
You'll also need to setup the ServerName directive in the apache config file, this is generally named httpd.conf, but if you install from the repository it's apache2.conf and found in /etc/apache2. Set  ServerName to the hostname of your server.

---

### Post by indytim on 2009-12-15
Resolved.  Just needed a few restarts.

---

