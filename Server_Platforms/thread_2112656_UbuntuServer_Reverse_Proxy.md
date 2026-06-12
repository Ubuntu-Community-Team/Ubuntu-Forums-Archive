---
title: "UbuntuServer Reverse Proxy"
date: 2013-02-05
forum: Server Platforms
---

### Post by TooNick on 2013-02-05
Hi, I'm running an Ubuntu 12.04 Server and I'm trying to settup a reverse proxy. What I'm trying to reach is this:
name.dyndns-ip.com --> localhost:4040
synology.name.dyndns-ip.com --> otherinternalip:5000
I tried to do this by editing /etc/apache2/sites-enabled/proxiedhosts
like this:
> 
<VirtualHost *:80>
ServerName name.dyndns-ip.com
ProxyPass / [http://localhost:4040/](http://localhost:4040/)
ProxyPassReverse / [http://localhost:4040/](http://localhost:4040/)

<VirtualHost *:80>
ServerName synology.name.dyndns-ip.com
ProxyPass / [http://otherinternalip:5000/]("http://192.168.178.43:5000/")
ProxyPassReverse / [http://otherinternalip:5000/]("http://192.168.178.43:5000/")
</VirtualHost>When I navigate to name.dyndns-ip.com, I get the same view I woudl get as if I went to localhost:4040 like it's supposed to. However when I navigate to synology.name.dyndns-ip.com, I get the error server not found. How to I correctly add another internal host to the reverse proxy.

BTW I followed this tutorial: [http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

---

