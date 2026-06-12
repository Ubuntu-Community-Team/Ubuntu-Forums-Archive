---
title: "Enabling Apache and PHP with mod_userdir"
date: 2010-11-07
forum: Server Platforms
---

### Post by tornadof3 on 2010-11-07
Hello

I have a frustrating problem - Apache will serve PHP pages correctly from /var/www but any PHP files in /home/username/public_html are not correctly processed and instead are sent to the browser as a download attempt (i.e. they are not passed to the PHP interpreter).

I have googled and followed the instructions about commenting out the lines in /etc/apache2/mods_enabled/php5.conf, which at present looks like this:

```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
	SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    #<IfModule mod_userdir.c>
      #  <Directory /home/*/public_html>
     #       php_admin_value engine On
     #   </Directory>
    #</IfModule>
</IfModule>
```

I have tried it with the hashes removed and the engine value both On and Off to no avail. Any ideas?

---

### Post by Vegan on 2010-11-07
did you enable the mod?

```
sudo a2enable mod_userdir
```

---

### Post by tornadof3 on 2010-11-07
Yep; mod_userdir is enabled and serves static pages without error. And I've restarted apache (and indeed the machine) several times...

---

