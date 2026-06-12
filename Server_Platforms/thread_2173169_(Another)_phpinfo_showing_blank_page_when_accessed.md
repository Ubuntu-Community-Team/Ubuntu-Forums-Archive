---
title: "(Another) phpinfo showing blank page when accessed from /var/www/ thread"
date: 2013-09-08
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-09-08
As the thread title suggests, I'm aware that this will not be the first time this has come up, but none of the solutions I've yet turned up have produced results. I'll therefore outline what I've tried as well as various aspects of my setup, to see if anyone can offer any additional suggestions I can try.

[LIST=1]
[*]Firstly, this is a purely home-based LAMP server using 13.04 64-bit, with a Kubuntu desktop on it
[*]The phpinfo file I'm trying contains nothing other than this > <?php phpinfo(); ?>
[*]If placed in the /var/www/ folder, this shows a blank page, but 'View Source' show the above code
[*]The server is happily running phpMyAdmin, Webmin/VirtualMin and Mantis
[*]If placed in the /usr/share/mantis/www/ folder, the phpinfo file runs just fine
[*]This shows /etc/php5/apache2/php.ini as my configuration file, and also shows that it has scanned /etc/php5/apache2/conf.d and has found:
[LIST=1]
[*]/etc/php5/apache2/conf.d/10-pdo.ini,
[*]/etc/php5/apache2/conf.d/20-gd.ini,
[*]/etc/php5/apache2/conf.d/20-mysql.ini,
[*]/etc/php5/apache2/conf.d/20-mysqli.ini,
[*]/etc/php5/apache2/conf.d/20-pdo_mysql.ini,
[*]/etc/php5/apache2/conf.d/mcrypt.ini
[/LIST]

[*]The /etc/php5/apache2/php.ini file has **short_open_tag** turned off
[*]Lastly, I have amended  /etc/apache2/mods-available/php5.conf to read as follows: ```
<FilesMatch ".+\.ph(p[345]?|t|tml)$">
     # SetHandler application/x-httpd-php
< /FilesMatch>
< FilesMatch ".+\.phps$">
     # SetHandler application/x-httpd-php-source
     # Deny access to raw php sources by default
     # To re-enable it's recommended to enable access to the files
     # only in specific virtual host or directory
     Order Deny,Allow
     Deny from all
< /FilesMatch>
 # Deny access to files without filename (e.g. '.php')
< FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
     Order Deny,Allow
     Deny from all
< /FilesMatch>

 # Running PHP scripts in user directories is disabled by default
 #
 # To re-enable PHP in user directories comment the following lines
 # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
 # prevents .htaccess files from disabling it.
 #<IfModule mod_userdir.c>
 #    <Directory /home/*/public_html>
 #        php_admin_value engine Off
 #    </Directory>
 #</IfModule>
```
[*]Though given what phpinfo is telling me, I'm not sure whether this last file is being read, more specifically, the last few lines
[/LIST]

I've run out of ideas now, as PHP clearly works, I'm not seeing any permissions issues for the /var/www/ folder, there are no errors showing up in the logs, it just doesn't work from that particular folder. Can anyone give me any suggestions as to where to look next?

---

### Post by SeijiSensei on 2013-09-10
> ```
<FilesMatch ".+\.ph(p[345]?|t|tml)$">
     # SetHandler application/x-httpd-php
< /FilesMatch>
```


By commenting out the SetHandler line, you've disabled the handler for PHP files, so they won't be parsed.  Remove the hash mark in front of SetHandler and restart the Apache server.

What purpose did you have in disabling the SetHandler directive?

---

### Post by Chris of Arabia on 2013-09-10
If that's what I've done, then it was a complete accident on my part, and entirely unintentional. I only aimed to comment out those last 5 lines. I'll get that sorted tomorrow and report back.

---

### Post by Chris of Arabia on 2013-09-11
OK, all done and it now works as expected. Thanks SeijiSensei :), very much appreciated.

Consider this one solved.

---

