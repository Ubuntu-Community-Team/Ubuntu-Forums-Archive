---
title: "Debian apache2 reverse proxy drupal mysql connection error"
date: 2010-04-14
forum: Server Platforms
---

### Post by tapas_mishra on 2010-04-14
I installed apache2 and mysql database on a Debian system.
 It is using reverse proxy on apache to redirect requests to apache2 running on any machine which is on Xen server as a Virtual host.

I tried to install Drupal on it. Every thing went fine till 
I pointed my browser to 

http://IP[/url] of LAN where Drupal was installed/drupal
then I see an installation page of Drupal which welcomes me 
I click install in English
then it can not proceed to connect with database.
```

Database configuration
Your web server does not appear to support any common database types. Check with your hosting provider to see if they offer any databases that Drupal supports.

```

I have created a database and username for Drupal separately.
What should I check to.

There is one more error
```

http://Public IP/some location/

```
Is showing me contents of Document Root
but there is a folder named drupal on it.
When I click on it I get error.
```

Not Found

The requested URL /drupal/ was not found on this server.
Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny8 with Suhosin-Patch proxy_html/3.0.0 Server at

```
What things should I check in for?
I am also getting errors like 
```

Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```
on individual DomU's what should I check in.

and on Dom0 when restarting apache2 I get following error.
```

Reloading web server config: apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 14 15:23:05 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

```
~                                                                                                                                                                     
~

---

