---
title: "Apache proxy 404 to other server"
date: 2013-02-09
forum: Server Platforms
---

### Post by copyrights on 2013-02-09
Hallo,

I have a new web server that should replace step by step the old one (very old hard, started to get faulty).

By now the only thing the new server does is to proxy the traffic to the old one.

```
ProxyRequests Off

<Proxy *>
  Order Allow,Deny
  Allow from all
</Proxy>
ProxyVia On
ProxyPreserveHost On

ProxyPass / http://oldserver:portforproxy/
ProxyPassReverse / http://oldserver:portforproxy/
```

I tried to add some stuff on the new server, but as the proxy is to / it gets proxy to the old server.

```
Alias /newserver/ "/var/www/"
<Directory "/var/www/">

                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
</Directory>
```

Knows some one a way to first lookup on the local (new) server and if not found the old server afterwards?

---

### Post by hawkmage on 2013-02-09
It is not really simple especially of the content of the sites it complex.  What I am going to suggest is based on the idea that the portions of the site that are related are under a single subdirectory of the site hierarchy.  

I would sugest that move all of the content (not directories) from the old server to the new.  Then for the directories that are still on the old server proxy them individually.  As you move over the content to the new server you can remove the proxy statements for the directories that you moved over.

---

### Post by copyrights on 2013-02-11
I know, but it would be much easier the other way round. But thank you.

---

### Post by volkswagner on 2013-02-11
I have not tried this but generally Apache2 looks for servername match.  If no match is found it will load the first alpha-numeric vhost file.

You could try putting your proxy catch-all in /etc/apache2/sites-available/default.
You will notice the above is linked to /etc/apache2/sites-enabled/000-default, thus allowing it to come up first when there is no name match.

I do feel you would be better off having the new server as the proxy as indicated above.  It just make more logic sense in my opinion.  I is better to direct to the known hosts, and fall back on the unknown vs. the other way around.

Good luck.

---

