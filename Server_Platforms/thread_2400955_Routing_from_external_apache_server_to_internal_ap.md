---
title: "Routing from external apache server to internal apache server based on url path?"
date: 2018-09-12
forum: Server Platforms
---

### Post by SagaciousKJB on 2018-09-12
I have a server running apache and some cctv software called zoneminder. When I access my.subdomain.com/zm/ I  can remotely view my cameras. I have this on a small server running 24/7

Well I also have some dvr software running on another local machine, and it also has an apache interface that I want to connect to by reaching my.subdomain.com/mythweb/, but I don't want to leave it running all the time.

My router is very basic and cannot handle fancy routing, and I am not sure what is the best way to make the first local machine running zoneminder to proxy the second local machine running mythweb, and based entirely on the url path.

So I  want...

my.subdomain.com/zm/ to go to 192.168.1.2:80

and

my.subdomain.com/mythweb/ to go to 192.168.1.3:80

But whatever needs to be done to achieve this must be done on the 192.168.1.2 server.

---

### Post by SeijiSensei on 2018-09-12
Read about proxies, particularly "reverse proxies," on Apache:  [https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html)

---

