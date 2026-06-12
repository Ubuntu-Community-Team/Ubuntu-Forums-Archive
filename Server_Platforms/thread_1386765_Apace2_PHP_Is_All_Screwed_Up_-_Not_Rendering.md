---
title: "Apace2 PHP Is All Screwed Up - Not Rendering"
date: 2010-01-21
forum: Server Platforms
---

### Post by war59312 on 2010-01-21
Well thought I'd download wordpress..

So dropped the download into /usr/share/wordpress and ran 
> sudo chown -R www-data /usr/share/wordpressThen opened locahost/wordpress/

Sadly it tries to download the php file instead of servering it up.. WTF!

So took a look around and noticed:
> rob@RobsUbuntuServer:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
rob@RobsUbuntuServer:/etc/apache2$ sudo a2enmod php5
Enabling module php5.
Run '/etc/init.d/apache2 restart' to activate new configuration!
rob@RobsUbuntuServer:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load:
Invalid command 'ln', perhaps misspelled or defined by a module not included in the server configurationSo wtf?

if I delete the php5.load file then apache2 will restart just fine but still trying to download damn php files..

And to be sure its not just my computer I tried visiting page on two others pcs and same thing.

Tried adding below to .htacess and httpd.conf with no change:

> AddHandler application/x-httpd-php5 .phpThanks,

Will

---

### Post by yogesh.girikumar on 2010-02-04
Hi,[INDENT]      > Restarting web server apache2 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now! ... waiting Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Invalid command 'ln', perhaps misspelled or defined by a module not included in the server configuration   [/INDENT]It seems that you may have some extraneous content in your php5.load file. Can you post the contents of
```
 /etc/apache2/mods-enabled/php5.load
```and the contents of 
```
/etc/apache2/mods-enabled/php5.conf
```      It might help in narrowing down the possibilities that could be the cause of your issue .. Ubuntu's default installation of php and apache should work without problems.

---

### Post by war59312 on 2010-02-07
Hey,

Thanks for the help..

> ln -s ../mods-available/rewrite.load ./rewrite.confand

> <ifmodule mod_php5.c>
  addtype application/x-httpd-php .php .phtml .php3
  addtype application/x-httpd-php-source .phps
</ifmodule>Thanks again,

Will

Update: O.K I finally figured it out.

php5.load should have been:
> 
LoadModule php5_module /usr/lib/apache2/modules/libphp5.soWhy it was different is beyond me, must be a bug in apache.

In fact it looks like it's a bug with "sudo a2enmod php5". It creates the wrong link.

I had to delete the two php files and recreate them by hand, via:
> 
sudo ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load

Then everything worked. :)

---

