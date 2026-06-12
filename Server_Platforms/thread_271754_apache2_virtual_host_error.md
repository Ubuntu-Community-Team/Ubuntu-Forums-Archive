---
title: "apache2 virtual host error"
date: 2006-10-05
forum: Server Platforms
---

### Post by GTHvidsten on 2006-10-05
When I start, restart or reload apache2 I get the following warning:
[warn] NameVirtualHost *:0 has no VirtualHosts

What I have done is make a copy of the default file in the sites-available directory, and change the ServerName and DocumentRoot, and finally running 'a2ensite' to activate this new virtual directory.
The '/etc/init.d/apache2 reload' command gives the warning once, while '/etc/init.d/apache2 restart' gives the warning twice.
I previously also had a "Could not determine the server's fully qualified domain name" warning, but I removed that by inserting a ServerName directive into apache2.conf.
How can I get rid of the "has no VirtualHosts" warning(s)?

---

### Post by sonic2000gr on 2006-10-05
Two points:

- Make sure you have a ServerName in the copy of the default site.
- Edit the copy and remove the first line that reads 

```
NameVirtualHost *
```

This already appears in the default site and it is causing you the problem. It is only needed once.

---

### Post by GTHvidsten on 2006-10-05
> **sonic2000gr said:**
> - Edit the copy and remove the first line that reads 

```
NameVirtualHost *
```

This already appears in the default site and it is causing you the problem. It is only needed once.

That was it. Now apache starts and restarts without any warnings.
Thanks for the help! :)

---

