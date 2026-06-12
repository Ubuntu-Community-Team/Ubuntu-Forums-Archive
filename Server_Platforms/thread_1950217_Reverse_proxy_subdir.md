---
title: "Reverse proxy subdir"
date: 2012-03-31
forum: Server Platforms
---

### Post by christfort on 2012-03-31
I have problems with reverse proxy. When I enter:

ProxyPass / [http://mysite.dk:8080/](http://mysite.dk:8080/)
ReverseProxy / [http://mysite.dk:8080/](http://mysite.dk:8080/)

everything works. However when I wish to redirect a subdir and enter:

ProxyPass /test [http://mysite.dk:8080](http://mysite.dk:8080)
ReverseProxy /test [http://mysite.dk:8080](http://mysite.dk:8080)

I get an error:

The requested URL /redirect.html was not found on this server.

I use ubuntu server 10.04 lts.

I have enabled mod proxy and proxy_html

What am I doing wrong?

---

### Post by dharmavir on 2012-04-03
> **christfort said:**
> I have problems with reverse proxy. When I enter:

ProxyPass / [http://mysite.dk:8080/](http://mysite.dk:8080/)
ReverseProxy / [http://mysite.dk:8080/](http://mysite.dk:8080/)

everything works. However when I wish to redirect a subdir and enter:

ProxyPass /test [http://mysite.dk:8080](http://mysite.dk:8080)
ReverseProxy /test [http://mysite.dk:8080](http://mysite.dk:8080)

I get an error:

The requested URL /redirect.html was not found on this server.

I use ubuntu server 10.04 lts.

I have enabled mod proxy and proxy_html

What am I doing wrong?

Please mention proper details about what proxy you're trying to use? People here at forum will only be able to help you if you provide enough details.
If you're using apache mod_proxy.so I would recommend you something more specialized for the job like "haproxy" which is quite easy to setup and it is enterprise ready.

---

### Post by SeijiSensei on 2012-04-03
It's pretty obvious he's using apache's mod_proxy, and he doesn't need anything more "specialized" than that.

You don't happen to have any Rewrite rules specified for this virtual host, do you?  I don't understand where the /redirect.html is coming from.  What happens if you specify the target home page in the ProxyPass directive?

```
ProxyPass /test  http://www.example.com/index.html
```

---

