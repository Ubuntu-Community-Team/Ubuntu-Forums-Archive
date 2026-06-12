---
title: "apache2ctl permissions question"
date: 2008-03-01
forum: Server Platforms
---

### Post by rgeddes on 2008-03-01
I'm running apache2 on 7.10, and I update/upgrade at every opportunity.

I tried using the apache2ctl command as follows:

```
$0> sudo apache2ctl status
[sudo] password for rgeddes:
Forbidden

You don't have permission to access /server-status on this server.

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server
at localhost Port 80

```

I would think root would have the permissions to use apache2ctl. 

Is there another layer of permissions, apache maybe, that I  have to tweak to get permission, as root, to run apache2ctl?

Thanks

---

### Post by nickjqw on 2008-03-01
Hi,

You have to enable the apache URL for apache2ctl status to work.  The error is telling you that you don't have access to the url [http://localhost/server-status](http://localhost/server-status) which is where apache2ctl gets its status information.

You need to add this to the appropriate apache configuration file (such as /etc/apache2/sites-available/default):
   <Location /server-status>
        SetHandler server-status
        Order Allow,Deny
        Allow from all
   </Location>

Instead of "Allow from all" you should try "Allow from localhost" or "Allow from 127.0.0.1" so that only the apache2ctl status command can access your stats and not the world at large.

Nick

---

