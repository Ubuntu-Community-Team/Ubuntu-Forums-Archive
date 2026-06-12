---
title: "Running Apache and Etherpad Lite on Port 80?"
date: 2011-08-24
forum: Server Platforms
---

### Post by Fallacy on 2011-08-24
I'm running both Apache on my site and Etherpad Lite, both on different domains. However, running them both on port 80 causes a conflict. I tried to use a reverse proxy in Apache ([this]("http://pastie.org/2424345") is the configuration -- I'm not sure if I did it right), but it doesn't seem to do anything. Help?

---

### Post by internalkernel on 2011-09-08
You wont be able to run both apache and etherpad on the same port - only one will survive. 

Why do want etherpad on port 80? 

I have my etherpad embedded as an iframe, like such: 

[https://github.com/Pita/etherpad-lite/wiki/Embed-Parameters](https://github.com/Pita/etherpad-lite/wiki/Embed-Parameters)

---

### Post by kevincop on 2011-10-04
```
# Sample configuration for proxying an installation of EtherPad for Apache 2 
# The configuration should forward the domain requests to the EtherPad server running on port 9000 on localhost 
# See these instructions to setup EtherPad on your server: http://pauleira.com/13/installing-etherpad/ 

ServerName www.domain.tld 
ServerAlias domain.tld 
ServerAdmin admin@domain.tld 

ProxyRequests Off 
ProxyPass / http://localhost:9000/ 
ProxyPassReverse / http://localhost:9000/ 
ProxyPreserveHost on 

Options FollowSymLinks MultiViews 
AllowOverride All 
Order allow,deny 
Allow from all 

ServerSignature Off
```

Source: [http://blog.ulfklose.de/proxying-etherpad-with-apache](http://blog.ulfklose.de/proxying-etherpad-with-apache)

---

