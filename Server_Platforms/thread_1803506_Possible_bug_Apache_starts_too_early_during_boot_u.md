---
title: "Possible bug: Apache starts too early during boot up?"
date: 2011-07-13
forum: Server Platforms
---

### Post by bubblehead74 on 2011-07-13
I made a DEB package that installs my web app into /usr/share/i-librarian/www. The installer registers this location in alias.conf as follows:
```

Alias /librarian /usr/share/i-librarian/www
<Directory /usr/share/i-librarian/www>
 AllowOverride None
 Order deny,allow
 Deny from all
 Allow from 127.0.0.1
 <IfModule mod_php5.c>
  php_value upload_max_filesize 200M
  php_value post_max_size 800M
  php_value max_input_time 120
 </IfModule>
</Directory>
<Directory /usr/share/i-librarian/www/library>
 IndexIgnore *
 AddType text/plain .html .htm .shtml
 <IfModule mod_php5.c>
  php_admin_flag engine off
 </IfModule>
 <FilesMatch "\.sq3$">
  Order allow,deny
 </FilesMatch>
</Directory> 

```
The app should be located at [http://localhost/librarian](http://localhost/librarian). Everything works as it should. However, if I start the computer and go to the above URL, I get 403 error. If I go to [http://127.0.0.1/librarian](http://127.0.0.1/librarian), I don't get the error. If I restart Apache, both URLs work. This makes me think that Apache does not understand what is localhost when computer boots up? Is this a bug, and if so where should I file it?

---

### Post by bubblehead74 on 2011-07-13
OK, I found the related bug report, which has not been addressed for two years!!! How is that even possible?

[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/370542](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/370542)

---

