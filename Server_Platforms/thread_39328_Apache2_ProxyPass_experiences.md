---
title: "Apache2 ProxyPass experiences"
date: 2005-06-04
forum: Server Platforms
---

### Post by KRavEN on 2005-06-04
I got my virtual hosting working fine.   Then I wanted to trying to use ProxyPass to redirect to an internal server running on another port like webmin and azureus swing web interface.  According to the webmin website you do it like this:

<VirtualHost 10.0.0.200:80>
     ServerName webmin.domain.com
     ProxyPass / [http://localhost:10000](http://localhost:10000)
     ProxyPassReverse / [http://localhost:10000](http://localhost:10000)
</VirtualHost>


I made sure all the proper apache2 proxy_mod modules are installed and loaded and I kept getting this in my server log:

[error] [client 10.0.0.10] client denied by server configuration: proxy:[http://localhost:10000](http://localhost:10000)

beat my head against google for a bit and found nothing (which is why I'm writing this down for others to find)

Then I started looking around in /etc/apache2 and found the file I needed to fixup under /etc/apache2/mods-available     proxy.conf

You gotta go in there and add:

Allow from your.local.network

under the <Proxy *> area

Don't set it to allow all or you'll be an open proxy ie. SpamZombie
(Even says so in the file =] )

Once that's done it all works fine

---

### Post by KRavEN on 2005-06-04
[QUOTE=KRavEN]I got my virtual hosting working fine.   Then I wanted to trying to use ProxyPass to redirect to an internal server running on another port like webmin and azureus swing web interface.  According to the webmin website you do it like this:

<VirtualHost 10.0.0.200:80>
     ServerName webmin.domain.com
     ProxyPass / [http://localhost:10000](http://localhost:10000)
     ProxyPassReverse / [http://localhost:10000](http://localhost:10000)
</VirtualHost>


I made sure all the proper apache2 proxy_mod modules are installed and loaded and I kept getting this in my server log:

[error] [client 10.0.0.10] client denied by server configuration: proxy:[http://localhost:10000](http://localhost:10000)

beat my head against google for a bit and found nothing (which is why I'm writing this down for others to find)

Then I started looking around in /etc/apache2 and found the file I needed to fixup under /etc/apache2/mods-available     proxy.conf

You gotta go in there and add:

Allow from your.local.network

under the <Proxy *> area

Don't set it to allow all or you'll be an open proxy ie. SpamZombie
(Even says so in the file =] )

Once that's done it all works fine[/QUOTE]
 Also found out that if you're gonna proxy from webmin that is running ssl then you need to add the "SSLProxyEngine On" to the virtualhost configuration or you get error 500

---

### Post by Amedee on 2007-09-28
I'm trying to get this to work for webmin in a directory, but it doesn't work.
Any ideas how to do this? I'm using a debian minimal installation, 100% default.

FYI I'm following [http://doxfer.com/Webmin/UnderApache#Webmin_Proxied_Through_Apache](http://doxfer.com/Webmin/UnderApache#Webmin_Proxied_Through_Apache)

---

