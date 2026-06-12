---
title: "Dapper Apache2 Reload Errors"
date: 2006-05-31
forum: Server Platforms
---

### Post by goneskiing on 2006-05-31
Any ideas what is wrong with the config files?

$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName


$ /etc/init.d/apache2 reload  * Reloading apache 2.0 configuration... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by Clochard on 2006-06-04
The first thing I would suggest is to restart Apache using its tool - apache2ctl.  Simply type

```
apache2ctl restart
```

to restart apache gracefully.

The second time you tried to restart without the sudo, so a normal user won't be able to do that - so I think that's why it failed.

The first time though, I assume you're concerned about the domain name warning?  I believe the fix is to add your hostname and domain (FQDN = fully qualified domain name) to /etc/hosts, and to include localhost and localhost.localdomain if you don't have a domain.

Try that and restart apache - should stop the FQDN complaint.

---

### Post by goneskiing on 2006-06-05
*The first time though, I assume you're concerned about the domain name warning? I believe the fix is to add your hostname and domain (FQDN = fully qualified domain name) to /etc/hosts, and to include localhost and localhost.localdomain if you don't have a domain.*

Thks for info.  I don't quite understand this - I have to add localhost to the /etc/hosts file ?  Never had to do this before.  Is this something new or broken in Dapper ?

---

### Post by Randomskk on 2006-06-06
To fix the first warning an easier way, add ServerName to your default virtual host (/etc/apache2/sites-enabled/default-000 I think), like this:
ServerName [www.example.com](www.example.com)

---

