---
title: "Apache2 &amp; apache2lib-mod-php5 -- PHP stopped working"
date: 2007-12-01
forum: Server Platforms
---

### Post by DappledOne on 2007-12-01
Hello.

I recently built an Ubuntu Server system and set up Apache2 and mod_php (libapache2-mod-php5) on it. After some work I was able to get PHP to run phpmyadmin and some other PHP based programs neatly as it should.

The links currently in 'mods-enabled' are: 
```

alias.conf            autoindex.conf  mime.load         setenvif.conf
alias.load            autoindex.load  mime_magic.conf   setenvif.load
auth_basic.load       cgi.load        mime_magic.load   speling.load
authn_file.load       dir.conf        negotiation.conf  ssl.conf
authz_default.load    dir.load        negotiation.load  ssl.load
authz_groupfile.load  env.load        php5.conf         status.conf
authz_host.load       include.load    php5.load         status.load
authz_user.load       mime.conf       rewrite.load

```

php5.load:
```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

php5.conf:
```

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

And apache2ctl status reports:
```

Server Version: Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.1 mod_ssl/2.2.4  OpenSSL/0.9.8e

```
So PHP should definitely be loaded.


This is possibly unrelated, but some days ago a security fix was released for PHP, which was installed followingly:

```

Preparing to replace php5-cli 5.2.3-1ubuntu6 (using .../php5-cli_5.2.3-1ubuntu6...
Unpacking replacement php5-cli ...
Preparing to replace php5-mysql 5.2.3-1ubuntu6 (using .../php5-mysql_5.2.3-1ubu...
Unpacking replacement php5-mysql ...
Preparing to replace libapache2-mod-php5 5.2.3-1ubuntu6 (using .../libapache2-m...
Unpacking replacement libapache2-mod-php5 ...
Preparing to replace php5-common 5.2.3-1ubuntu6 (using .../php5-common_5.2.3-1u...
Unpacking replacement php5-common ...
Preparing to replace php5 5.2.3-1ubuntu6 (using .../php5_5.2.3-1ubuntu6.1_all.d...
Unpacking replacement php5 ...

Setting up php5-common (5.2.3-1ubuntu6.1) ...
Setting up php5-cli (5.2.3-1ubuntu6.1) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.1) ...
Setting up php5-mysql (5.2.3-1ubuntu6.1) ...
Setting up php5 (5.2.3-1ubuntu6.1) ...

```

Soon, if not directly after which PHP stopped working. Other than that I had been working on an ACL setup, which I promptly disabled as well as made a clean reboot to make sure it was not affecting the service. I have by now even apt-get purged Apache2 and PHP5 and re-installed, but this neither provided a solution. And as mentioned the configuration files for the websites worked perfectly before.

Neither phpadmin with it's default config nor another site that I set up a virtual host for myself are executing PHP. Here's for example the site that I set up:

```

<IfModule mod_php5.c>
        <VirtualHost *>
                ServerName <REMOVED>
                DocumentRoot /var/www/smf

                # Enable PHP for smf
                php_value engine on
                # Limit PHP's file access to path and subdirs
                php_value open_basedir /var/www/smf

                <Directory /var/www/smf>
                        Options -Indexes FollowSymLinks
                        DirectoryIndex index.php
                </Directory>
        </VirtualHost>
</IfModule>

```

Note the fact that the site does get set up even with the <IfModule mod_php5.c>.

I've spent a good while already trying to figure the problem out, and I thought I'd drop by here to see if anyone would have any good ideas or if there's something that I've missed. Has anyone else experienced problems after installing the security update?

I would need to get the site running again as soon as possible since it's associated with a project.

Thanks for any help you can provide.

- Dappled One

---

### Post by moorezilla on 2007-12-01
I think I have a related problem. Since the recent php update, some isolated php scripts are returning a "connection reset by server error." This usually has to do with logging into the admin area of certain php applications, or uploading xml. That's all I have so far. Nothing shows up in my apache error log, so it's a bit of a mystery to me.

gutsy server running whatever apt-get update & apt-get upgrade has running!

here's an example:

[http://chs.chelseaschools.com/surveys/admin/admin.php](http://chs.chelseaschools.com/surveys/admin/admin.php)  fires a reset connections error, but
[http://chs.chelseaschools.com/surveys/](http://chs.chelseaschools.com/surveys/)  runs the php script properly, even though it fires a script-generated warning

---

### Post by bitumen on 2007-12-02
[SIZE="3"]AHHHHHHHHhhhhhhhhh[/SIZE]
this will explain why my new reinstall of ubuntu 7.10 64-bit and apache2 web development server is going so badly 
php 5.* running but no phpmyadmin pages thought i had screwed the install so reinstalled and now got no php whats so ever

ohhh will ill have to use windows (booooooooo)

---

### Post by moorezilla on 2007-12-02
Yeah... I'm thinking now that my issue may be a firewall issue, rather than one with php. Works fine inside the school network, but fires errors outside.

---

### Post by DappledOne on 2007-12-02
moorezilla:
It's possible that it's an issue either with the firewall/http proxy that allows traffic into the network, or any host based limitations set up for those administrative tools.


Still no luck with mod_php5 so I'm not very happy... after some further hours of trying to figure out what's going wrong with it, here's at least a work around until new updates or something else comes up:
**Install mod_fastcgi**: [http://ubuntuforums.org/showthread.php?t=341164](http://ubuntuforums.org/showthread.php?t=341164)

There are certain gains to using mod_fastcgi, for example being able to split the virtualdomains between different users and use Unix permissions controls to restrict PHP access if you have multiple sites.

Now the site at least is working, but only through a work around. I'd still like to hear if anyone has any ideas on why the normal mod_php5 isn't working.

---

### Post by bitumen on 2007-12-02
i seem to working OK now except phpmyadmin is still showing blank pages 
decided to try webmin instead

---

### Post by DappledOne on 2007-12-04
This would appear to likely have been the cause of the problem :/

[http://www.linuxcompatible.org/USN-549-2_PHP_regression_p101819.html](http://www.linuxcompatible.org/USN-549-2_PHP_regression_p101819.html)

I might test if it's working properly now, at some point. But mod_php's already disabled and worked around so it'd be inconvenient to go back just for a check.

---

