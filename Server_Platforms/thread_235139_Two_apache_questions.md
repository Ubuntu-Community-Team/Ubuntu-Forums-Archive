---
title: "Two apache questions"
date: 2006-08-12
forum: Server Platforms
---

### Post by lionsnob on 2006-08-12
Hello all!

I'm trying to set up a web server based on the server guide [here]("https://help.ubuntu.com/ubuntu/serverguide/C/httpd.html").  I have some questions about some of the steps in the guide.

1) After I do the final few steps in the apache setup, I'm no longer able to access my web server using just http:// only [https://.](https://.)  Is this expected behavior?

2) When I do use the [http://,](http://,) I get this message:

Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

Hint: [https://127.0.1.1/](https://127.0.1.1/)

Is there a way to automatically forward the browser to the https:// URL?  Also, is there a way to change the 127.0.1.1 to say something else, such as an internal IP address or domain name?

Thanks!

---

### Post by davham on 2006-08-12
You might want to look at this page. 

[http://plone.org/documentation/tutorial/plone-apache/preface](http://plone.org/documentation/tutorial/plone-apache/preface)

It might have something to do with the ports.conf file. Maybe something like this


```
Listen 80
<IfModule mod_ssl.c>
  Listen 443
</IfModule>
```

---

### Post by lionsnob on 2006-08-12
Cool, I'll have to try that, thanks for the link.  I guess I don't mind always being in https as long as there is some auto redirect from http.  Anyone know of a simple way?

---

