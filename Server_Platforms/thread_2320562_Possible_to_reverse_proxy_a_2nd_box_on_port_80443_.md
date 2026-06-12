---
title: "Possible to reverse proxy a 2nd box on port 80/443 for non-web related tasks?"
date: 2016-04-15
forum: Server Platforms
---

### Post by Roasted on 2016-04-15
Hello friends. I'm curious about something. I currently have a web server and a NAS. The web server has ports 80 and 443 forwarded through my router. It also runs DDNS, so I have a domain name tied to my LAN. The NAS also acts as an NVR running video surveillance software. At the moment, I'm testing out (and really liking) Bluecherry. Bluecherry is a Linux server based NVR program that has a cross platform (Win/Mac/Lin) client. By default, the client talks over port 7001. 

I know I can set up a reverse proxy to forward users who visit a certain URL to my NAS box, as in, say my domain is mydomain.org and I'm hosting a folder called /share on the NAS. I know how to reverse proxy it so mydomain.org/anythingbesidesSHAREhere stays on the web server, yet mydomain.org/share forwards to the NAS.

But I'm not sure how I can (I can't even see how this is possible) to forward specific traffic (specifically my systems using the Bluecherry client which listen on a certain port, not an Apache sub folder) over to the NAS.

Assuming my domain is simply mydomain.org, is there any possible way I can simulate/create/whatever a path called mydomain.org/bluecherry, and when that gets accessed, my web server basically forwards that 80/443 request to the Bluecherry client requesting access from outside my LAN?

Given the Bluecherry client is not a web application that I can host on Apache, I'm very doubtful. But I figured I'd ask. Thanks for any insight!

---

### Post by imac_89 on 2016-05-05
Yes there is! I used something similar when I had a game server setup. Players could visit map.foo.bar which pointed to my foo.bar, but apache reverse proxied the request to the map engine a game plugin created. (cough, dynmap (minecraft/bukkit), cough).

I will try and dig up a link.... give me a few minutes.

---

### Post by imac_89 on 2016-05-05
I believe this was [the article in question]("http://www.apachetutor.org/admin/reverseproxies").

My take away was this:

```
<VirtualHost *:80>
	ServerAdmin webmaster@foo.bar
        ServerName map.foo.bar


	ErrorLog ${APACHE_LOG_DIR}/map.foo.bar.error.log


	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel info


	CustomLog ${APACHE_LOG_DIR}/map.foo.bar.access.log combined


        ProxyRequests Off
        ProxyPreserveHost Off


        <Location />
            ProxyPass http://192.168.X.X:[port]/
            ProxyPassReverse http://192.168.X.X:[port]/
            Require all granted
        </Location>


        ProxyErrorOverride On
        ErrorDocument 404 /


</VirtualHost>


```

---

