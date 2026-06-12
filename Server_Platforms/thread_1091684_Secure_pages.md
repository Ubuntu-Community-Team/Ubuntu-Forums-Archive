---
title: "Secure pages"
date: 2009-03-09
forum: Server Platforms
---

### Post by quikone8 on 2009-03-09
I have been using Apache2 for some time.  I am now trying to get secure pages or ssl running.  I found I needed to change one line in my securepages.module line file and now I get this error when trying to restart apache;

Failed to start apache :

 * Starting web server apache2
Syntax error on line 307 of /etc/apache2/apache2.conf:
SSLCertificateFile: file '/var/www/sites/tolstores.com/ssl/certs' does not exist or is empty
   ...fail!
 Anyone know what to do?

Ron

---

### Post by hyper_ch on 2009-03-09
you need a ssl certificate

---

### Post by quikone8 on 2009-03-10
> **hyper_ch said:**
> you need a ssl certificate

Is there a really good tutorial to get this done, anyone?

---

### Post by hyper_ch on 2009-03-10
there are many. I'd start off with google or at [http://www.howtoforge.com](http://www.howtoforge.com)

---

