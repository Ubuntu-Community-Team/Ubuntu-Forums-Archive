---
title: "Firefox can't open php file from apache2 server on localhost"
date: 2010-03-31
forum: Server Platforms
---

### Post by Makrie on 2010-03-31
Hi.

I've just moved on to 10.04 from 9.10. The program worked fine in 9.10. I *may* have overwritteen a conf file in the upgrade... :redface:

I now get the error as below:

[IMG]http://www.grassmoon.com/ubuntu/php_prob_01.png[/IMG]

My userdir.conf is like this:

[FONT="Courier New"]<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>[/FONT]

and I have the PHP5 module installed. I vaguely recall that I may have had PHP4 installed - would the upgrade have removed it? Is there anywhere I can get it from to try? Anything else to do?

Thanks for your time

Makrie :D

---

### Post by richardjh on 2010-04-06
What do you see when you run php -v from the command line?

Do you have libapache2-mod-php5 installed?

Have you installed everything from the repositories or do you have bits installed manually or from other sources?

Apache is not configured to server php files, which is why you are getting this error. It may be a simple error in a configuration file.

---

### Post by romeroc24 on 2010-04-06
> **Makrie said:**
> Hi.

I've just moved on to 10.04 from 9.10. The program worked fine in 9.10. I *may* have overwritteen a conf file in the upgrade... :redface:

I now get the error as below:

[IMG]http://www.grassmoon.com/ubuntu/php_prob_01.png[/IMG]

My userdir.conf is like this:

[FONT="Courier New"]<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>[/FONT]

and I have the PHP5 module installed. I vaguely recall that I may have had PHP4 installed - would the upgrade have removed it? Is there anywhere I can get it from to try? Anything else to do?

Thanks for your time

Makrie :D

Yes, richardjh you allright!

```

$sudo apt-get install libapache2-mod-php5

```

---

### Post by lisati on 2010-04-06
I had a similar problem with firefox wanting to download PHP files instead of displaying them. I found the answer here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by Makrie on 2010-04-07
Hi all, thanks for helping me with this.

> **richardjh said:**
> What do you see when you run php -v from the command line?

[FONT="Courier New"]marko@mango:~$ php -v
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP 5.3.2-1ubuntu3 with Suhosin-Patch (cli) (built: Mar 29 2010 12:23:29) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies[/FONT]

> Do you have libapache2-mod-php5 installed?

Yes, I believe so.

> Have you installed everything from the repositories or do you have bits installed manually or from other sources?

One of the reasons I didn't clean install 10.04 was that I wanted to keep [Fontlinge]("http://www.gesindel.de/page_intro_english.php") working without needing to reinstall it. I had installed Fontlinge manually but everything else (Apache,PHP5,etc.) from the repositories.

> Apache is not configured to server php files, which is why you are getting this error. It may be a simple error in a configuration file.

Fingers crossed for finding it! Apache2 config files are default (my bad, I overwrote my custom one, I think)!

> **lisati said:**
> I had a similar problem with firefox wanting to download PHP files instead of displaying them. I found the answer here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

Following their advice:

[FONT="Courier New"]marko@mango:~$ sudo a2enmod php5
[sudo] password for marko: 
Module php5 already enabled
marko@mango:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ][/FONT]

and the problem remains. I manage the modules through Webmin, fwiw.

Thanks all!

---

### Post by s_ø on 2010-04-07
Edit: change the file in mods-available not in enabled. Sorry for the mistake.
Try to open the php5.conf in mods-available
```
sudo nano /etc/apache2/mods-available/php5.conf
```It should look like this
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```If the .php is not there apache will not parse the files.
Force apache to reload the module.
```
sudo a2dismod php5 
sudo service apache2 restart
sudo a2enmod php5
sudo service apache2 restart
```

---

### Post by Makrie on 2010-04-07
> **s_ø said:**
> Try to open the php5.conf in mods-enabled.
```
sudo nano /etc/apache2/mods-enabled/php5.conf
```
It should look like this
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

If the .php is not there apache will not parse the files.
Force apache to reload the module.
```
sudo a2dismod php5 
sudo service apache2 restart
sudo a2enmod php5
sudo service apache2 restart
```

Even after reloading the module as you specified, my php5.conf still looks very different:

[FONT="Courier New"]  GNU nano 2.2.2     File: /etc/apache2/mods-enabled/php5.conf                  

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
</IfModule>[/FONT]

Should I replace it with yours?

And thanks!

---

### Post by s_ø on 2010-04-07
This is a pretty fancy expression for something simple
```
[FONT=Courier New]<FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>[/FONT]
```I **think** you can safely replace it with this.
```
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps
```

Edit:
The reqex should work, so its probably not that.

---

### Post by s_ø on 2010-04-07
try to comment out the bold lines. (I think the syntax has changed to the semicolon ; for comments. 

[FONT=Courier New]# To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.[/FONT]
[B][FONT=Courier New]<IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>[/FONT][/B]

---

### Post by Makrie on 2010-04-08
> **s_ø said:**
> try to comment out the bold lines. (I think the syntax has changed to the semicolon ; for comments. 

[FONT=Courier New]# To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.[/FONT]
[B][FONT=Courier New]<IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>[/FONT][/B]

I've commented out the lines (attempted twice, using semicolons and hashes) and still no joy. I have been clearing my internet cache before and after every restart of Apache2.

Darn! Any further ideas? Am I approaching clean install time? Could it be that the program wants PHP4 not PHP5 (although I don't think the error message suggests this?

Thanks :/

---

### Post by s_ø on 2010-04-09
Dont think you should reinstall yet.
When you upgraded to lucid, you also upgraded php to version 5.3.
Look at this page about migrating from 5.2 to 5.3 [http://www.php.net/manual/en/migration53.php](http://www.php.net/manual/en/migration53.php)
One of the changes is to the php.ini files. [http://www.php.net/manual/en/migration53.ini.php](http://www.php.net/manual/en/migration53.ini.php)

I am runnning 5.2 in Karmic, so I cant help you with specifics of the php.ini files.
but look around in **/etc/php5/apache2/** for the php.ini files
In the .ini files kook for this or similar
```
; Enable the PHP scripting language engine under Apache.
engine = On
```
engine needs to be On to work.
This directive can be set from 'anywhere' so look in httpd.conf, .htaccess files for this **php_flag engine off**

---

### Post by Fenix-TX on 2010-04-09
NOW WORKS: deleting cache, history solved the issue
I have the same problem and only happens on Firefox, I've tried with Konqueror and works fine, why?

EDITED: FIXED

---

### Post by iduppe on 2010-04-18
I do have this exact same issue.. I installed lamp using tasksel.. and apache doesnt parse php files on my public_html dir..

BUT if I place the files on /var/www it works..

and phpmyadmin woks too.... any ideas?

> **Fenix-TX said:**
> NOW WORKS: deleting cache, history solved the issue
I have the same problem and only happens on Firefox, I've tried with Konqueror and works fine, why?

EDITED: FIXED

Are you the OP? 

cleaning the cache did not solve the issue for me. I tried with a clean profile, same issue.

---

### Post by iduppe on 2010-04-18
> **s_ø said:**
> try to comment out the bold lines. (I think the syntax has changed to the semicolon ; for comments. 

[FONT=Courier New]# To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.[/FONT]
[B][FONT=Courier New]<IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>[/FONT][/B]

this solved the issue

---

### Post by madtom1999 on 2010-05-05
I've had a similar problem - try replacing localhost with 127.0.0.1
it seems everytime you upgrade the localhost mapping gets lost....

---

### Post by FRuso on 2010-05-06
Hi [Makrie]("http://ubuntuforums.org/member.php?u=50048"), comment all lines with # or replace these lines in mods-available/php5.conf, and adds  these last two lines:

sudo nano /etc/apache2/mods-available/php5.conf

<IfModule mod_php5.c>
#    <FilesMatch "\.ph(p3?|tml)$">
#       SetHandler application/x-httpd-php
#    </FilesMatch>
#    <FilesMatch "\.phps$">
#       SetHandler application/x-httpd-php-source
#    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to  On as it
    # prevents .htaccess files from disabling it.
#    <IfModule mod_userdir.c>
#        <Directory /home/ruso/public_html>
#            php_admin_value engine OFF
#        </Directory>
#    </IfModule>
AddType application/x-httpd-php .php .phtml .php3 .html .xhtml
AddType application/x-httpd-php-source .phps
</IfModule>

sudo /etc/init.d/apache2 restart

It  worked for me!

---

### Post by Gaweph on 2010-05-10
This worked perfectly for me!
Much obliged.

> **FRuso said:**
> Hi [Makrie]("http://ubuntuforums.org/member.php?u=50048"), comment all lines with # or replace these lines in mods-available/php5.conf, and adds  these last two lines:

sudo nano /etc/apache2/mods-available/php5.conf

<IfModule mod_php5.c>
#    <FilesMatch "\.ph(p3?|tml)$">
#       SetHandler application/x-httpd-php
#    </FilesMatch>
#    <FilesMatch "\.phps$">
#       SetHandler application/x-httpd-php-source
#    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to  On as it
    # prevents .htaccess files from disabling it.
#    <IfModule mod_userdir.c>
#        <Directory /home/ruso/public_html>
#            php_admin_value engine OFF
#        </Directory>
#    </IfModule>
AddType application/x-httpd-php .php .phtml .php3 .html .xhtml
AddType application/x-httpd-php-source .phps
</IfModule>

sudo /etc/init.d/apache2 restart

It  worked for me!

---

### Post by dadinugroho on 2010-10-29
Hi, 

It's funny. I have spent many days to figure out why I can't used localhost while using 127.0.0.1 and hostname can work nicely.....

Anyone can have an explanation on this?

Thanks a lot.

---

### Post by bobnw on 2010-11-19
I also had this problem.  I reloaded Apache2 and it was still there.  Tried clearing the Firefox Cache as suggested in another post.  This did not work for the tools menu.  My profile was on an  NT file system.  After I emptied the Cache directory in my profile using normal file system access the problem was gone.

---

