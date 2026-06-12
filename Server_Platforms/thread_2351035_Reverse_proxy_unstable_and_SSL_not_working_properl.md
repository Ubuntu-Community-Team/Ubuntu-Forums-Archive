---
title: "Reverse proxy unstable and SSL not working properly"
date: 2017-01-30
forum: Server Platforms
---

### Post by linux-fever on 2017-01-30
Hello all, 
Running multiple instances of Ubuntu Server 16.04.1 for some wordpress sites, reverse proxy, etc. (1 server per site) 

I have been trying to set up an apache2 reverse proxy that is supposed to be directing traffic to four different websites I am hosting on my own server. 

Right now, it's in bypass mode because it refuses requests on port 80. I set each site to permanent redirect to 443/SSL/etc. but the connection keeps dying on port 80 instead of being forwarded on. 

Also, Websites with Cloudflare SSL certs break/go offline to Cloudflare when I put the SSL cert on the reverse proxy, if I put the cert on the server, it partially works, but it isn't full SSL, just mixed-mode. 

Any tips on redirecting port 80 to SSL and getting SSL-full working with Cloudflare certs?

My Rproxy config looks like this:

<VirtualHost *:80> 
Servername myexample.com
RedirectPermanent / [https://myexample.com/](https://myexample.com/)
</VirtualHost>

<VirtualHost *:80> 
Servername nextcloud.myexample.com
RedirectPermanent / [https://nextcloud.myexample.com/](https://nextcloud.myexample.com/)
</VirtualHost>

<VirtualHost *:80> 
Servername blog.myexample.com
RedirectPermanent / [https://blog.myexample.com/](https://blog.myexample.com/)
</VirtualHost>

<VirtualHost *:80> 
Servername plex.myexample.com
RedirectPermanent / [https://plex.myexample.com/](https://plex.myexample.com/)
ProxyPass / [https://10.0.0.7:34343/](https://10.0.0.7:34343/)
ProxyPassReverse / [https://10.0.0.7:34343/](https://10.0.0.7:34343/)
Rewrite magic to not need to put port 34343 in the url
</VirtualHost>

<VirtualHost *:443> 
SSLEngine On
ServerName myexample.com
ProxyPreserveHost On 
ProxyPass / [https://10.0.0.5:443/](https://10.0.0.5:443/)
ProxyPassReverse / [https://10.0.0.5:443/](https://10.0.0.5:443/)
SSLCertFile /path/to/file
SSLCertkeyfile /path/to/file
</VirtualHost>


<VirtualHost *:8443> 
SSLEngine On
ServerName nextcloud.myexample.com
ProxyPreserveHost On 
ProxyPass [https://10.0.0.7:443/](https://10.0.0.7:443/)
ProxyPassReverse [https://10.0.0.7:443/](https://10.0.0.7:443/)
SSLCertFile /path/to/file
SSLCertkeyfile /path/to/file
</VirtualHost>

---

