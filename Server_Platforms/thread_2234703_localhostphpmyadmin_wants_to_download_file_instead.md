---
title: "localhost/phpmyadmin wants to download file instead or processing it."
date: 2014-07-16
forum: Server Platforms
---

### Post by malacusp on 2014-07-16
I've just upgraded my 13.10 to 14.04LTS and all went smoothly apart from a SpamAssassin problem which I have managed to fix and this problem with phpMyAdmin.
I used to connect to phpMyAdmin using [http://localhost/phpmyadmin](http://localhost/phpmyadmin) in the local server browser.
I can connect to all my php files correctly and all seems okay with my website Joomla php files all get processed as they should but not phpMyAdmin folder.
If I try to connect to localhost/phpmyadmin I get a download dialog from the same browser.
I have searched like mad for this but all the results are on about PHP not being installed or the Apache PHP module not being installed or configured or links to phpmyadmin folder.

I'm assuming it's some configuration issue with the upgrade changes needed to config files in Apache 2.4.7 as this worked perfectly before the upgrade.

The link phpmyadmin.conf file is there in /etc/apache2/conf.enabled and is pointing to /etc/phpmyadmin/apache.conf. All the other files in conf.enabled are being used.
The file itself is being served in that I can connect to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it just doesn't process it with PHP.
If I comment out the [AddType application/x-httpd-php .php] in /etc/phpmyadmin/apache.conf then the phpMyAdmin .php files are served but just as plain text.

I have been scratching my head for days on this so it is probably something really simple to fix(I hope) and really stupid that I haven't thought of it(I'm afraid). :-)

Any help greatly appreciated.

---

### Post by corny2 on 2014-10-18
I had to allow suphp to run files on /usr/share/phpmyadmin by adding to /etc/apache2/mods-available/php5.conf

<Directory /usr/share/phpmyadmin/>
       <IfModule mod_php5.c>
             <FilesMatch "\.ph(p3?|tml)$">
                    SetHandler application/x-httpd-php
             </FilesMatch>
             <FilesMatch "\.phps$">
                    SetHandler application/x-httpd-php-source
             </FilesMatch>
       </IfModule>
</Directory>

and then
# service apache2 restart

---

