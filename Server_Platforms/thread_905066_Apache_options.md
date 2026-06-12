---
title: "Apache options"
date: 2008-08-29
forum: Server Platforms
---

### Post by Vegan on 2008-08-29
Anyone know how to enable the HTTP compression with Ubuntu server with Apache2 using virtual hosts.

[http://www.microsoft.com/search/Tools/default.aspx](http://www.microsoft.com/search/Tools/default.aspx)

---

### Post by mbeach on 2008-08-30
according to 
[http://en.wikipedia.org/wiki/HTTP_compression](http://en.wikipedia.org/wiki/HTTP_compression)
it would appear you need to enable mod_deflate or mod_gzip

so assuming a 'a2enmod deflate' would do the trick, I came across:
[https://launchpad.net/ubuntu/+source/apache2/+bug/44975](https://launchpad.net/ubuntu/+source/apache2/+bug/44975)
which may give you some insights - its a bit dated, but likely might get you going in the right direction.

what is not clear to me is if you can turn it off/on for particular virtual hosts, or is it a global server thing.  Try it in virtual host file, apache2 will tell you if you can/can't.  Not sure if apache2 -t or apache2 -s will give you that info or not - worth a shot before restarting service.

appears to be a good bit on how to test results at:
[http://www.linuxjournal.com/article/6802](http://www.linuxjournal.com/article/6802)

good luck - never tried this so perhaps combine this post with your own searches.
mb.

---

### Post by windependence on 2008-08-30
More here too:

> **How do I get SSL compression working?**


Although SSL compression negotiation was defined in the specification of SSLv2 and TLS, it took until May 2004 for RFC 3749 to define DEFLATE as a negotiable standard compression method. 

OpenSSL 0.9.8 started to support this by default when compiled with the zlib option. If both the client and the server support compression, it will be used. However, most clients still try to initially connect with an SSLv2 Hello. As SSLv2 did not include an array of prefered compression algorithms in its handshake, compression cannot be negotiated with these clients. If the client disables support for SSLv2, either an SSLv3 or TLS Hello may be sent, depending on which SSL library is used, and compression may be set up. You can verify whether clients make use of SSL compression by logging the %{SSL_COMPRESS_METHOD}x variable. 


[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html)

-Tim

---

### Post by Vegan on 2008-08-30
I now have HTTP compression operational, I added some commands to my httpd.conf too but it did not work as per the Apache docs, which did not suggest using this mod, making me think it was available by default. This will speed up web serving with 3x faster delivery.

sudo a2enmod deflate

HTTP Conditional Get not enabled for the date selected
URL generates an ETag value:"1b614c-333a-4559b671ba740"-gzip
HTTP Compression enabled using gzip

So now the conditional get part.

---

### Post by datajelly on 2008-09-05
I'm not sure if you're still having difficulties getting everything setup, but we have a walkthrough for using compression+SSL offloading with Apache that may be of some help:

[http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html]("http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html")

---

