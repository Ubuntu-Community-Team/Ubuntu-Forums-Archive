---
title: "Apache proxy to another apache"
date: 2008-11-15
forum: Server Platforms
---

### Post by self-defence on 2008-11-15
Hi,

I've got a bit of a problem that I can't seem to figure out and as much as I search around I can't find what I'm trying to do.
Anyway I've got an Apache server running on a network and this server is visible to the internet. On the same network I've got another web server.
On the main one I've already setup a sub domain (example:[http://sub.domain.com/](http://sub.domain.com/)) but now I'd like to set up apache forward everything on this sub domain to the second server.
I've tried adding something like this to the httpd.conf but I think I'm barking up the wrong tree.
```
ProxyPass / http://lan_ip_second_server
ProxyPassReverse / http://lan_ip_second_server7
<Proxy http://lan_ip_second_server/>
Order Allow,Deny
Allow from all
</Proxy>
``` 

Can this even be done?

Thanks for the help and bye

---

### Post by Philio on 2008-11-15
Try it as a virtual host as follows:

<VirtualHost 1.2.3.4:80>
ServerName sub.domain.com
ProxyPass / [http://1.2.3.5/](http://1.2.3.5/)
ProxyPassReverse / [http://1.2.3.5/](http://1.2.3.5/)
</VirtualHost>

---

### Post by self-defence on 2008-11-16
Philio -> Thanks.... I didn't even think that it was that easy.
I just had add this:
```
ServerName sub.domain.com
ProxyPass / http://1.2.3.4/
ProxyPassReverse / http://1.2.3.4.5/
<Proxy http://1.2.3.4/>
Order Allow,Deny
Allow from all
</Proxy>
```

So thanks again. :)

---

