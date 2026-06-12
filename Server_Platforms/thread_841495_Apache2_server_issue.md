---
title: "Apache2 server issue"
date: 2008-06-26
forum: Server Platforms
---

### Post by rtsask on 2008-06-26
Hi , I installed apache2 server but I can't get directory listing for instance when I try [http://192.168.228.70](http://192.168.228.70) I don't get directory listing I just get *It works* How can I fix this please help.

---

### Post by leg on 2008-06-26
Remove the index.html page in /var/www/localhost (or your web viewable directory if not default) and make sure that options +indexes is defined in your sites configuration.

---

### Post by rtsask on 2008-06-26
Or maybe rename of this fiel? right? if is it right? why? why do we have to delete or rename this file?

Thanks

---

### Post by mbeach on 2008-06-26
quick way is likely to edit:
/etc/apache2/sites-available/default
and comment the line:
RedirectMatch ^/$ /apache2-default/
so it looks like
#RedirectMatch ^/$ /apache2-default/

then maybe tell apache to reload the configuration
sudo /etc/init.d/apache2 reload


then take a moment to read over:
[http://httpd.apache.org/docs/2.0/mod/mod_dir.html](http://httpd.apache.org/docs/2.0/mod/mod_dir.html)

---

