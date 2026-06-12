---
title: "apache2 and ProxyPass problem (2 servers 1 ip-address)"
date: 2007-07-15
forum: Server Platforms
---

### Post by Krijk on 2007-07-15
I have a problem with setting up an Apache2 webserver to proxy to another webserver. I've searched on this forum and googled, but nothing works yet.

Whenever I try to contact second.my.lan it shows my first virtualhost first.my.lan . When I contact 2nd.my.lan it shows the correct website. 

Can anybody help me with this configuration or tell me how to log more extensively.  My current logfiles don't show any clues.


**Server 1**

mod_proxy is enabled
mod_proxy_http is enabled



```
<VirtualHost 10.0.0.50:80>
<Proxy *>
Order deny,allow
Allow from 10.0.0.0/24
</Proxy>

ProxyPreserveHost On
ProxyPass / http://192.168.10.2
ProxyPassReverse / http://192.168.10.2/
ServerName second.my.lan
</VirtualHost>

```



**proxy.conf**


	```
ProxyRequests On

	<Proxy *>
		Order deny,allow
		Allow from 10.0.0.0/24
		#Allow from .your_domain.com
	</Proxy>
```

**Server 2**

When contacting 2nd.my.lan the site can be viewed.

```
<VirtualHost 192.168.10.2>
DocumentRoot "/var/www/htdocs/second"
ServerName 2nd.my.lan
</VirtualHost>
```

---

### Post by Krijk on 2007-07-16
up

---

### Post by Krijk on 2007-07-17
Ok, after some fiddling it's working sort off.

I modified the virtualhost file of first.my.lan. Now I can reach the 2nd webserver by using url [http://first.my.lan/second](http://first.my.lan/second)

```
ServerName first.my.lan

ProxyRequests Off
ProxyPreserveHost On
ProxyPass /second http://2nd.my.lan
ProxyPassReverse /second http://2nd.my.lan

```

It's not what I really wanted, but it works and that was my primary concern

**But other issues started**
I also used another server on the same subnet to avoid going through the firewall. Because I'm lazy I used an existing website which runs a wiki with php.

The wiki isn't displayed properly. Basically the formatting of the homepage is wrong. Also when I'm entering some content it rewrites the url wrong. It goes back to the main website [http://first.my.lan](http://first.my.lan) and tries to get the content there, which off course gives 404's.

Probably I'm still misconfiguring, but if it isn't ProxyPass won't do and I'll have search for other solutions such as squid or running on different ports so the firewall can redirect.

Does anybody know a possible solution to solve the content issue? :confused:

---

### Post by crashemup on 2007-11-06
you can enable proxy_connect. sudo a2enmod proxy_connect and restart apache2. Then you can change your /second to just / in your proxypass argument

---

