---
title: "ssl to apache 2"
date: 2012-01-26
forum: Server Platforms
---

### Post by BrandonDaAwesome on 2012-01-26
how do you add ssl to apache 2?

---

### Post by cariboo on 2012-01-27
A bump for the move.

---

### Post by ruffEdgz on 2012-01-27
When you install apache2 onto your system, you will need to navigate to /etc/apache2/?

From there, you will find two important directories called 'mods-available' and 'mods-enabled'. The idea behind these is to symlink files from the 'mods-available' to the 'mods-enabled'. So for SSL to work you will need to complete the following command:
```

ln -s /etc/apache2/mods-available/ssl.* /etc/apache2/mods-enabled/

```
Once that is done, you have complete a majority of the work for getting SSL to work on apache2. 

Here is some links to explain more about mod_ssl on apache:
---
[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html)
[http://httpd.apache.org/docs/2.1/ssl/ssl_howto.html](http://httpd.apache.org/docs/2.1/ssl/ssl_howto.html)
[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html)
[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatefile](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatefile)
[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatechainfile](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatechainfile)
[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatekeyfile](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcertificatekeyfile)
[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcacertificatefile](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslcacertificatefile)

Cheers!

---

