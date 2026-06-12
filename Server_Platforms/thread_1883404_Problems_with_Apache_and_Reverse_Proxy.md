---
title: "Problems with Apache and Reverse Proxy"
date: 2011-11-19
forum: Server Platforms
---

### Post by trikolon on 2011-11-19
Hi,
i am running a ubuntu server 11.10 as a virtual machine with subsonic on it. I want to connect to the subsonic server from extern, so I configured a apache with reverse proxy to direct the subsonic server (<ip>:4043/music/) to <ip>/music/. This was working for month (on 11.04 and after upgrading to 11.10 too) but for some days now I cant connect to it with teh following error:

Proxy Error
The proxy server could not handle the request GET /music/index.view.

Reason: Error during SSL Handshake with remote server

Apache/2.2.20 (Ubuntu) Server at ______.dyndns.org Port 443

Here is my reverse proxy conf:
        SSLProxyEngine On
        ProxyPass /music/ [https://192.168.2.3:4043/music/](https://192.168.2.3:4043/music/)
        ProxyPassReverse /music/ [https://192.168.2.3:4043/music/](https://192.168.2.3:4043/music/)

Any ideas how i can make this work again?

Ben

---

### Post by volkswagner on 2011-11-19
I see the error states port 443, but your reverse proxy points to port 4043.

Is apache listening on 4043?

What's in ports.conf?

---

### Post by trikolon on 2011-11-19
Hi,
Subsonic rund on Port 4043 (ssl) with its buildin jetty server. I "Redirect" this to the Apache on Port 443 (ssl). But i get this error since 4 days.
Ben

---

