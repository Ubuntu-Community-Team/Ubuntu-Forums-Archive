---
title: "Apache2 trouble with NameVirtualHost"
date: 2010-01-11
forum: Server Platforms
---

### Post by artheus on 2010-01-11
Hey!

I've got a little trouble with using the NameVirtualHost in Apache2.

What I've done is to just create a new file named **artheus.se** in the **/etc/apache2/sites-available/**.
And in that I've written

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName artheus.se
        ServerAlias *.artheus.se

        DocumentRoot /www/mydomain/

        ErrorLog /var/log/apache2/artheus-se.log
</VirtualHost>
```

And after that I used **sudo a2ensite artheus.se** to enable the site.

All other settings in apache2 are unchanged. Except for that I added the line **ServerName artheus.se**, at the very last, in my apache2.conf file.

And the problem I've encountered is that when I visit my domain "artheus.se" it won't use the document root **/www/artheus/** it'll just use the one specified in the **/etc/apache2/sites-available/default** file. Is there something I've forgotten??

And I've used the **/etc/init.d/apache2 restart** command.

Cheers,
Artheus

---

### Post by artheus on 2010-01-12
And one more thing..

when I in my browser write "www.artheus.se" it seems to work. But when I then write "artheus.se" (no prefix "www") it just returns the "/var/www" which is defined in **/etc/apache2/sites-available/default**

---

