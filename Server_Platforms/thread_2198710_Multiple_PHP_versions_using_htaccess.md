---
title: "Multiple PHP versions using htaccess"
date: 2014-01-10
forum: Server Platforms
---

### Post by enboig on 2014-01-10
I am trying to use php 5.3 and php 5.4 in my development server, and choose between them using htaccess.

I have made a mix of this two guides:
[http://zgadzaj.com/how-to-install-php-53-and-52-together-on-ubuntu-1204](http://zgadzaj.com/how-to-install-php-53-and-52-together-on-ubuntu-1204)

[http://www.webhostrepo.com/blog/running-two-php5-versions-in-a-cpanel-server](http://www.webhostrepo.com/blog/running-two-php5-versions-in-a-cpanel-server)

But I am quite missing something.

[LIST=1]
[*]compiled ok
[*]installation ok
[*]create the handler
[*]modify apache config to recongize the handler
[*]create htaccess to use the handler
[/LIST]

Any hint?

---

### Post by enboig on 2014-01-10
I forgot to tell I am using ubuntu 12.04

---

### Post by Lars Noodén on 2014-01-10
.htaccess is only needed if it is not your server and you do not have access to the actual configuration files.  If you have access to the web server's configuration file, then you can use that instead.

---

### Post by enboig on 2014-01-10
I want to use htacces because I want to select php version "per site", not for the whole server.

I added at /etc/apache2/sites-available/default:
<code>
ScriptAlias /php54-cgi /usr/lib/cgi-bin/php54-cgi
Action application/x-httpd-php54 /php54-cgi
AddType application/x-httpd-php54 .php
</code>

and at .htaccess:
<code>
AddHandler application/x-httpd-php54 .php
</code>

---

### Post by Lars Noodén on 2014-01-10
per-site customizations are exactly what the configuration files are for.  A separate one is made for each vhost or else if you want separate configurations for special directories use the <Directory> configuration directive within a vhost and put the handler info inside that.  It will save trouble down the road to have everything in one place rather than scattered around in multiple (possibly conflicting) .htaccess files.  

Wherever you do put the handler information, maybe you could try [SetHandler](http://httpd.apache.org/docs/2.4/mod/core.html#sethandler) instead of AddHandler to override the default.  I haven't tried mixing PHP versions though.

---

