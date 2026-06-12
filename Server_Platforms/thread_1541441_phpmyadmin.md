---
title: "phpmyadmin"
date: 2010-07-29
forum: Server Platforms
---

### Post by Linux Lover II on 2010-07-29
Sorry, I first posted under the wrong part of the forum, bur here is my question:


Hello,

I installed phpmyadmin via the software channel, however, when trying to go via [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get the 404 error: not found. Can anyone help me with this please?


Thx in advance!

---

### Post by chrislynch8 on 2010-07-29
What happens if you use the IP address of the server rather then localhost.

[http://192.168.1.250/phpmyadmin](http://192.168.1.250/phpmyadmin)

---

### Post by noway2 on 2010-07-29
Are you running apache and when you did the install did you select apache as your HTTP server or forget and leave it as light httpd?

Check in your configuration files.  Specifically, look in /etc/apache2/conf.d.  Do you have a file (link) for phpmyadmin.conf?  If so open the file.  It should have an /alias directive and point to a location such as /usr/share/phpmyadmin.  Does myadmin exist in that location?

Have you overridden any settings with .htaccess or the directory tags that might interfere with accessing web pages, such as require it to be on an SSL port?

---

### Post by Linux Lover II on 2010-07-29
Thanks a lot for your reactions!

@chrislynch8:how can you change it than? I tried with my IP-adress but that gives the same error: > Oops! This link appears to be broken. (Google Chrome)

Localhost reports that php does work: it reports:

```
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
```

@noway2:

in the software channel, I see that "apache2.2-bin" and "apache2.2-common" are installed.

In etc/apache2/conf.d there are four files, charset, javascript-common.conf, localized-error-pages and security. That's all in that dir.

There however is no file as phpmyadmin.conf or something alike.

And no, I've not overridden something with .htaccess...

Indeed, in usr/share, there exists a folder with phpmyadmin, and quite some files in it.

For your information: I have not installed the server version of ubuntu: I tried to do a lamp install instead. I don't know if this is relevant, but I tell you in case it does.


Thank you very much!

---

### Post by Ryan Dwyer on 2010-07-29
Are you sure you installed phpmyadmin using sudo apt-get install phpmyadmin? If you did then it should have created /etc/apache2/conf.d/phpmyadmin.conf.

EDIT:
Here's the contents of my phpmyadmin.conf:

```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

```

---

### Post by Linux Lover II on 2010-07-29
Thank you very much for your help!!!

Combined with an include in the apache config file, it finally works!!!

---

### Post by Linux Lover II on 2010-07-29
At least, I think it works, now I don't know how to login, what is the standard login password for root?

Thanks once more!

Can I change something in config.default.php?

> /**
 * MySQL user
 *
 * @global string $cfg['Servers'][$i]['user']
 */
$cfg['Servers'][$i]['user'] = 'root';

/**
 * MySQL password (only needed with 'config' auth_type)
 *
 * @global string $cfg['Servers'][$i]['password']
 */
$cfg['Servers'][$i]['password'] = '';?

---

### Post by Linux Lover II on 2010-07-29
Strange, I changed cookie to http, changed root to my username and changed the default '' after password to my password. However, I still can't log in?

---

### Post by Linux Lover II on 2010-07-29
One step ahead:

I overrided the default settings in default.config.php in config.inc.php. So now, it asks for a username and password, that's perfect, however, when accepted, it gives:

phpMyAdmin - Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

and

phpMyAdmin - Error
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

Has anyone an idea?

Thanks in advance!

---

### Post by rubylaser on 2010-07-29
Can you login to mysql from a terminal?  That will be your username and password for phpmyadmin.
```
mysql -u root -p
```

---

### Post by Linux Lover II on 2010-07-29
No, it asks for a password, but quits without any more.

---

### Post by Linux Lover II on 2010-07-30
Hm, I searched the web, and the latter error is about permission problems (write/read/...) Anyone an idea?


Thanks!

---

### Post by Linux Lover II on 2010-08-01
Okay, while not reaching a solution, I tried to install xampp.

However, my splash screen does not contain any links, nor do I know how to start phpmyadmin, etc.

It looks like this:

---

### Post by Linux Lover II on 2010-08-03
At least, I got it working under Windows, when I've some more time, I try it under Ubuntu as well!

Anyway, thx for all the help I've already gotten :)

---

