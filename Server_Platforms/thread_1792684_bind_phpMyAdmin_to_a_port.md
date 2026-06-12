---
title: "bind phpMyAdmin to a port"
date: 2011-06-28
forum: Server Platforms
---

### Post by tubaguy50035 on 2011-06-28
Is there a way to bind phpmyadmin to a particular port so that the url is domain.com/phpmyadmin:#### ?

I've found examples to bind it to an ip, but that's not what I wish to do.

---

### Post by Bachstelze on 2011-06-28
You do not bind phpMyAdmin to anything, since it's not an application that listens on a specific port. You must first bind Apache to that port, then create a virtual host for that port and make it serve phpMyAdmin.

In /etc/apache2/ports.conf, add

```
NameVirtualHost 8080
Listen 8080
```

Then modify your phpMyAdmin virtual host to tell Apache to serve it on port 8080, not 80.

---

### Post by tubaguy50035 on 2011-06-28
I realize that it isn't an application.  I meant to ask how do I bind the phpMyAdmin virtual host to a specific port?  I have other virtual hosts that I need to serve out of port 80 as well.

---

### Post by Bachstelze on 2011-06-28
You do that in the VirtualHost directive that declares a virtual host:

```
<VirtualHost *:8080>
...
</VirtualHost>
```

---

