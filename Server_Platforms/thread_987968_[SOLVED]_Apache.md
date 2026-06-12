---
title: "[SOLVED] Apache"
date: 2008-11-20
forum: Server Platforms
---

### Post by theozzlives on 2008-11-20
I'm trying to setup WebDEV on my server and I got it all setup except when I restart Apache it says:

 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]


What would be causing this? my ip is 68.15.116,126

---

### Post by MJN on 2008-11-20
You have two issues:
 
i. You don't have a ServerName directive set in your Apache config i.e. it doesn't know what it (itself) is called. It has to know this for various reasons and so is making an assumption.
 
ii. Are you starting Apache using sudo? (binding processes to ports <1024 requires super-user privileges)
 
Mathew

---

### Post by theozzlives on 2008-11-20
> **MJN said:**
> You have two issues:
 
i. You don't have a ServerName directive set in your Apache config i.e. it doesn't know what it (itself) is called. It has to know this for various reasons and so is making an assumption.
 
ii. Are you starting Apache using sudo? (binding processes to ports <1024 requires super-user privileges)
 
Mathew

thanks, now where do I put the domain in at? This my first server I've hosted myself.

---

### Post by MJN on 2008-11-21
I'm not familiar with WebDEV so don't know where it puts its configuration. However, for a vanilla install of Apache it would be set inside the <Virtualhost>...</Virtualhost> section of /etc/apache2/sites-available/default
 
e.g.
 
```
<Virtualhost *:80>
Servername [www.domain.com]("http://www.domain.com")
.
.
</Virtualhost>
```Mathew

---

### Post by theozzlives on 2008-11-21
I put "ServerName  www.theozzmicrosystems.com" in my httpd.conf and that seemed to work. FrontPage still wont publish using WebDEV. Bummer, all that for naught.

---

