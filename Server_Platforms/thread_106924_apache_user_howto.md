---
title: "apache user howto?"
date: 2005-12-21
forum: Server Platforms
---

### Post by rcotten on 2005-12-21
Trying to find some info on howto setup users so they have their own webspace and cgi-bin directories with ftp access to only those directories.

ex.

/home/rcotten/www
/home/rcotten/www/cgi-bin

Then when user rcotten ftps in they are put in /home/rcotten/www by default.

Appreciate if someone can point me to some help files.

Thanks,

---

### Post by amohanty on 2005-12-22
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

The ftp thing depends on the ftp server you are using. If you post what you intend to use as a ftp server it would be useful in guiding you to the right resource.

HTH
AM

---

### Post by rcotten on 2005-12-22
That helped. The file you need to edit is /etc/apache2/apache2.conf
The tutorial doesn't seem to tell you that anywhere.

:)

---

### Post by amohanty on 2005-12-22
I think the reason it doesnt say is becuase you can do all of it in httpd.conf or apache2.conf, and both will work.

---

