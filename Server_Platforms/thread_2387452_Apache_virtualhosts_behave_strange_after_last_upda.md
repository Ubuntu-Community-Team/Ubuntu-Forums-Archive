---
title: "Apache virtualhosts behave strange after last update"
date: 2018-03-19
forum: Server Platforms
---

### Post by dezsip88 on 2018-03-19
Hi,

I have a LAMP installation: ubuntu 16.04, apache 2.4, php 7.1, mysql 5.6 and I set a virtualhost config file for custom domain names, which I added to /etc/hosts. They worked fine after the last ubuntu update. since then All of my sites redirect to a https version and I get  "Unable to connect" messages from the browser.

Could someone please help me?

/etc/hosts I added
127.0.0.1       test.dev
127.0.0.1       [www.test.dev](www.test.dev)

/etc/apache2/sites-enabled/test.dev.conf

<VirtualHost *:80>
        <Directory /var/www/test.dev>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ServerName test.dev
        ServerAlias [www.test.dev](www.test.dev)

        ServerAdmin [email]webmaster@test.dev[/email]
        DocumentRoot /var/www/test.dev/

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by dragonfly41 on 2018-03-19
I think you will find that Ubuntu 16.04 Apache document root is now /var/www/html/ and not the older /var/www/ path.

[https://www.digitalocean.com/community/tutorials/how-to-move-an-apache-web-root-to-a-new-location-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-move-an-apache-web-root-to-a-new-location-on-ubuntu-16-04)

---

### Post by dezsip88 on 2018-03-19
Thanks, but that's not the case, because i did not upgraded to 16.04 it was 16.04 when it worked, I just applied the "normal" updates (maybe it was a kernel update in there), I think it's more a networking type issue rather than apache kind, but I'm not sure what could possibly went wrong.
But I tried to copy my folder into /var/www/html/ and edited the virtualhost file, and reload/restart apache but it didn't work :(

---

### Post by wildmanne39 on 2018-03-19
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-03-19
> **dragonfly41 said:**
> I think you will find that Ubuntu 16.04 Apache document root is now /var/www/html/ and not the older /var/www/ path.
That has nothing to do with his configuration.

He has is own site config file (separate from default).  His config specifies where to look for the root of the site...which can be anywhere on the server...doe not even have to be in /var (but does need to have appropriate owner/file permissions)

The 1st thing I normally do on my web servers is to disable default site and create site-specific config files which are tied to domain names for proper redirection.

> **dezsip88 said:**
> They worked fine after the last ubuntu update.  since then All of my sites redirect to a https version and I get   "Unable to connect" messages from the browser.
On the server, you don't need to edit the /etc/hosts file, but you do on the client PC.  When you use the browser, you plug in the domain URL (not the IP) and the server will see the domain URL and access the correct site config based on that.

Your config shows nothing about SSL or SSL redirects so I'm assuming you have other sites (000-default or default-ssl) that is getting picked up.

To see what site config files you have, type this:
```
ls -l /etc/apache2/sites-available
```

To see which of those site configs are enabled, type this:
```
ls -l /etc/apache2/sites-enabled
```

I'll bet your SSL re-direct is being fired off in one of the other enabled sites.  Once you figure out which site is being called, you can then determine what you are doing that is causing it to be called instead of the expected site configuration.

**EDIT:** Just checked one of my Apache servers that runs a non-ssl site (and is still working and fully patched as of right now)

Server Info:
```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:        16.04
Codename:       xenial

# uname -a
Linux srv-mediawiki 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

# apache2 -v
Server version: Apache/2.4.18 (Ubuntu)
Server built:   2017-09-18T15:09:02

# php -v
PHP 7.0.28-0ubuntu0.16.04.1 (cli) ( NTS )
Copyright (c) 1997-2017 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
    with Zend OPcache v7.0.28-0ubuntu0.16.04.1, Copyright (c) 1999-2017, by Zend Technologies


```

LHammonds

---

### Post by Habitual on 2018-03-19
```
apache2ctl -S
``` is a decent, basic diagnostic.
Can we see that output? You may want to sanitize "server name" or namevhost values before posting output.
Thank you.

Was there any editing of /etc/apache2/apache2.conf?

---

### Post by dezsip88 on 2018-03-19
First thank you guys

So I only have one conf enabled, all the others are disabled


#apache2ctl -S

H00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
VirtualHost configuration:
*:80                   test.dev (/etc/apache2/sites-enabled/test.dev.conf:1)
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www/html"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex watchdog-callback: using_defaults
Mutex rewrite-map: using_defaults
Mutex proxy: using_defaults
Mutex default: dir="/var/run/apache2/" mechanism=default 
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
Define: ENABLE_USR_LIB_CGI_BIN
User: name="www-data" id=33 not_used
Group: name="www-data" id=33 not_used

The weird thing is when I enter [http://localhost](http://localhost) into the browser it works normally so the problem only appears on virtualhosts or it could be something network anomaly but I can't figure it out :(

---

### Post by LHammonds on 2018-03-19
Localhost?   Is this a desktop with a GUI + server services?  In other words, are you browsing directly on the server?

**EDIT:** Also, a difference between mine and yours regarding the apache2ctl output is the "not_used" words on the last 2 lines of output.  Does your www-data user account exist?

```

# grep www-data /etc/passwd
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

# grep www-data /etc/group
www-data:x:33:

# getent passwd www-data
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

# getent group www-data
www-data:x:33:

# id -u www-data
33

```

---

### Post by dezsip88 on 2018-03-20
Yeah it's a local machine for development, as you can see the user is exists and there is not different from yours 

```

# grep www-data /etc/passwd
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

# grep www-data /etc/group
www-data:x:33:

# getent passwd www-data
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

# getent group www-data
www-data:x:33:

# id -u www-data
33

```

---

### Post by dezsip88 on 2018-03-20
Guys I found the solution: the problem was the name

So I tried to open it in lynx and it worked. After many google search minutes i found in some forum that firefox and chrome has now something to do with .dev

[https://ma.ttias.be/chrome-force-dev-domains-https-via-preloaded-hsts/](https://ma.ttias.be/chrome-force-dev-domains-https-via-preloaded-hsts/)

So I changed the .dev to .test and everything started to work again....

Thank you all for your help, and have a good day ;)

---

