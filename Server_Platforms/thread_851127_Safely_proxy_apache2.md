---
title: "Safely proxy apache2"
date: 2008-07-06
forum: Server Platforms
---

### Post by stringkarma on 2008-07-06
Hello, I am trying to deploy dimdim webmeeting on my server. It requires lighttpd server. I already run apache2 and would like to keep it. I found some advice online to allow lighttpd on port 81 and the have apache2 proxy requests to it. I added the following to the default site: 

```
ProxyRequests Off
ProxyPreserveHost On
ProxyPass /dimdim/ http://localhost:81/dimdim/
ProxyPassReverse /dimdim/ http://localhost:81/dimdim/
```

and this seemed to almost work as now when I visited [http://server.com/dimdim/](http://server.com/dimdim/) I got error 403 (forbidden) instead of 404 (not found).

After a little more looking I think that I need to change a line in the mod proxy.conf from

```
Deny from all
```
to 
```
Allow from all
```

when I do this all seems to work. But now I wonder how safe this is. Can I restrict this to only proxy the requests that I want? I have a list of ports that it needs.

---

### Post by stringkarma on 2008-07-08
Politely Bump

---

