---
title: "Apache2 Error"
date: 2006-10-18
forum: Server Platforms
---

### Post by mzracer360 on 2006-10-18
I originally installed my Ubuntu server without mySQL and PHP and all that stuff.  Now, I've decided I want it.  I have been following the how-to ([http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service")) and have been successful up until i got to installing the image gallery.  I was able to install everything and gety everything to work up to libjpeg-progs.  After installing that I did ```
sudo /etc/init.d/apache2 restart
```  Thats when I got this:
```
 * Forcing reload of apache 2.0 web server...                            [fail]

``` and I am still getting it.

---

### Post by kidders on 2006-10-18
Hi there,

Do your system logs tell you anything useful? There may be some sort of syntactical problem in your apache config.

---

