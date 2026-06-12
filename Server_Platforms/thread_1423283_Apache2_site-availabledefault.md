---
title: "Apache2 site-available/default"
date: 2010-03-06
forum: Server Platforms
---

### Post by ChurroLoco on 2010-03-06
I am very new to using apache and could use some help.  I just installed WordPress on my system and put the WordPress folder into **/usr/share/wordpress**.
Also I made a symlink to that called **/var/www/wordpress**.

Problem occurs when I upload files.  They goto **/var/www/wp-uploads**, and I don't have access to browse to them.

I think I can fix this by editing **apache2/sites-available/default**, but I honestly don't understand what all of it means.  I did experiment and edit it a bit, but only got... well bad results.  Can someone tell me what my current file even means, and maybe how to fix it.  

Here it is.
**/etc/apache2/sites-available/default**
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /usr/share/wordpress>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        <Directory /var/www/wp-uploads>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by stlsaint on 2010-03-06
That file is used when setting up virutal hosting thru apache. How are you uploading files into system and they go into different directory? What are you using for uploading. If there is a folder you dont have access to then either enter them as root or take ownership of them using chown command. 
Example: 
```
chown -R <username> /path/to/folder
```

But im not following how your uploading to a folder that you dont have access to.

---

### Post by ChurroLoco on 2010-03-06
The files are uploaded via the WordPress uploader in the browser.  I'm not sure how they do it.  At first I thought my files (pictures) were'nt being uploaded because I couldn't see them but after search the directory I found that they were uploaded.  

The problem is that they are above apache's root directory listed in that file.  I tried setting apaches root directory up one to**/var/www** and I can access the photos that way but then WordPress doesn't work properly since it isn't at [www.mypage.com](www.mypage.com) instead it is [www.mypage.com/wordpress/](www.mypage.com/wordpress/).

BTW Thanks for the interest.

---

### Post by stlsaint on 2010-03-06
Well them remove the files out of the wordpress dir and place them in the root level of the /var/www/ dir.

---

