---
title: "mod_rewrite - enabled but not working!"
date: 2007-09-13
forum: Server Platforms
---

### Post by gRoberts on 2007-09-13
Hi all,

First of all, let me apologise for asking what many people have already asked, but mod_rewrite is doing my head in.

I've ran sudo a2enmod rewrite which returns a message foce-reload apache2. 

I then created a page, which runs phpinfo(); and that tells me that mod_rewrite is installed:

```

 	core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_php5 **mod_rewrite** mod_userdir

```

So, I then create an .htaccess containing: 

```

RewriteEngine on
RewriteRule ^alice.html$ phpinfo.php

```

when I run [http://192.168.57.128/alice.html](http://192.168.57.128/alice.html) I get an Error 404. 

I then changed 

AllowOverride none to AllowOverride all

and also added RewriteEngine On

in /etc/apache2/sites-available/default 

I've restarted apache each time i've made a change and its still not working...

Any advice?

TIA

---

### Post by ponar on 2007-10-04
I have the exact same issue. I tried all the things that you tried, and still can't get it to work. It shows as loaded in php_info(), but doesn't actually rewrite anything!

Does anyone have a solution?

---

### Post by ponar on 2007-10-04
I found a solution. It has to do with MultiViews: <[http://httpd.apache.org/docs/2.0/mod/mod_negotiation.html#multiviews](http://httpd.apache.org/docs/2.0/mod/mod_negotiation.html#multiviews)>. I'm not sure if this is a hack or not, but it worked for me, and MultiViews isn't something I'll ever need.

I inserted the following at the top of my .htaccess file:

```

Options -MultiViews

```

---

### Post by gRoberts on 2007-10-05
I was using a old copy of 6.06 LAMP. As soon as I downloaded 7.04 LAMP it was fine.

---

