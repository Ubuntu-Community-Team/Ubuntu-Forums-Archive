---
title: "apache2 + public_html"
date: 2011-04-04
forum: Server Platforms
---

### Post by zsepi on 2011-04-04
Hello!

I've got a strange problem and not found any solution on web.

System: ubuntu 10.10
server: apache2 v2.2.16

I want to use the users public_html directory to run php scripts, but... in browser I get only downloading window to save.

The apache2 is working in default directory (/var/www/index.php appears normally), but not in public_html.

Tried a lot of solution from web and from this forum also, but still doesn't work correctly.

My /etc/apache2/mods-available/php5.conf is:
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
      <IfModule mod_userdir.c>
          <Directory /home/*/public_html>
              php_admin_value engine Off
          </Directory>
      </IfModule>
  </IfModule>

```

I've set up /etc/apache2/apache2.conf by adding this:
```
 #UserDir is now a module
 UserDir public_html
 UserDir disabled root
 <Directory /home/*/public_html>
   AllowOverride FileInfo AuthConfig Limit
   Options Indexes SymLinksIfOwnerMatch IncludesNoExec
 </Directory>
```

Of course I tried ```
sudo a2enmod userdir
``` at first to set up apache, and restarted the deamon by ```
sudo /etc/init.d/apache2 restart
```.

Does anybody know, what the problem is?

Thanks for answers.

Regards,
z

---

### Post by domu on 2011-04-04
I think that you need to follow the commented instructions in your post inside /etc/apache2/mods-available/php5.conf i.e. comment out (i.e. put hash in front of) these lines:
```
    <IfModule mod_userdir.c>
          <Directory /home/*/public_html>
              php_admin_value engine Off
          </Directory>
    </IfModule>
```

and then restart apache again.

---

### Post by volkswagner on 2011-04-04
Two other things to check
If you had other files int public_html, you may need to clear the cache on the browser you are using.

Verify the permissions inside public_html are readable by www-data.

---

### Post by zsepi on 2011-04-04
[hurray]("http://www.youtube.com/watch?v=DQ1G9m-MjIY")
I commented out theese lines and now...
It works. Thank You!

---

