---
title: "PHP Not Following session.save_path"
date: 2011-01-03
forum: Server Platforms
---

### Post by bsntech on 2011-01-03
I have two version of PHP installed on my Ubuntu Lucid 10.04 server - the default PHP 5.3.2 that comes with the distribution - and I then compiled PHP 5.2.14 to the /opt/php5.2.14 directory and it runs in Apache via FastCGI mode.

The PHP 5.3.2 is working without any problem and it places all session files in the /home/session-data folder - which is set in the PHP.INI file.

The PHP 5.2.14 also has the same directive set and it shows via a phpinfo() that it is set correctly:

session.save_path=/home/session-data

I have ensured that all session variables/settings are the same between PHP 5.3.2 and PHP 5.2.14 - but the PHP 5.2.14 does not pay attention to the save path and is still placing the session files in the /tmp folder.

Checking the session files in the /tmp folder, they are owned by www-data with 600 chmod permission settings (read/write for user, no access for group/others).

The permissions on the /home/session data folder is 770 with www-data owning the folder.

Any idea why PHP 5.2.14 would not be paying attention to the session.save_path directive and still saving the session files in the /tmp folder?

Thank you!

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

### Post by bsntech on 2011-01-04
Issue resolved.  Very strange problem needless to say.

The sites that used the FastCGI PHP 5.2.14 was following the session-data and log_file orders.  These VirtualHosts just had one line in the VirtualHosts config:

> Include /etc/apache2/php5-2-14.conf

This line pointed to a file with this contents:

> ScriptAlias /cgi-bin-php/ "/opt/php5.2.14/bin/"
SetEnv PHP_INI_SCAN_DIR "/opt/php5.2.14/"
AddHandler php-script .php
Action php-script /cgi-bin-php/php-cgi
<FilesMatch "\.php">
    SetHandler php-script
</FilesMatch>


That tells Apache to use the PHP 5.2.14 installation for parsing the PHP files.

Well, that is fine and dandy for VirtualHosts that fully rely on PHP 5.2.14.  In my case, I had a directory of a webhost that I wanted run using PHP 5.2.14 - NOT the whole VirtualHost.  So I added this contents to the VirtualHosts:

> ScriptAlias /cgi-bin-php/ "/opt/php5.2.14/bin/"
        <Directory /home/<location>>
                SetEnv PHP_INI_SCAN_DIR "/opt/php5.2.14/"
                AddHandler php-script .php
                Action php-script /cgi-bin-php/php-cgi
                <FilesMatch "\.php">
                    SetHandler php-script
                </FilesMatch>
        </Directory>

Apparently the SetEnv setting does not work where it is placed at.  Apache didn't throw any errors, but it wasn't working.

When I ran a phpinfo(); from one of the VirtualHosts that pointed to just the file (the first two sets of code), the session directory and log file directives were correct.

I then ran a phpinfo(); from the specific directory where I wanted PHP 5.2.14 to run but to still have the VirtualHost use PHP 5.3.2 for all other directories.  When doing this, none of those directives were set and it wasn't even picking up a php.ini file to parse!  It said that the configuration file path was /opt/php5.2.14/lib - but I didn't have a php.ini file there.

So the fix was to copy the php.ini file from the /opt/php5.2.14 to opt/php5.2.14/lib.  After doing so, I then re-ran the phpinfo(); in the specific directory and issue fixed!

I opted to make a copy of the file instead of just moving the file because for the specific directory, I needed to allow all php functions.  For the other VirtualHosts, I have a suhosin blacklist setup that blocks certain functions.

If anyone is interested in how to two versions of PHP on their system:
[Install Two Versions of PHP on Ubuntu]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/1681-install-two-versions-of-php-on-ubuntu-lucid-1004-php-53-and-php-52.html")
[Install the Suhosin Extension for FastCGI PHP]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/1722-howto-install-the-suhosin-extension-for-a-fastcgi-based-php-install.html")

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

