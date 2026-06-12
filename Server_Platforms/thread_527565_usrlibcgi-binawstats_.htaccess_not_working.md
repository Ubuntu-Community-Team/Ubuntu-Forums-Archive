---
title: "/usr/lib/cgi-bin/awstats .htaccess not working"
date: 2007-08-16
forum: Server Platforms
---

### Post by twistedtwig on 2007-08-16
Hi all,

I am trying to understand why I can not get .htaccess to work in a certain situation.

I have the web main part of the web server at /var/www/root/*.* and I can put a .htaccess and .htpasswd file in a sub folder and all is well with the world, it works just fine.

In my /etc/apache2/apache2.conf file I have an Alias /cgi-bin/ /user/lib/cgi-bin/

that has

<Directory /usr/lib/cgi-bin>
 Options FollowSymLinks +ExecCGI
 AllowOverride All
 Order allow, deny
 Allow from all
</Directory>

but when I try and go to that awstats.pl file it doesn't ask for a user name and password.

I can not figure out what I am doing wrong here!!!!!

Can some one be kind enough to tell me where I am being stupid because I am sure it is me doing (not doing) something simple but I am running around in circles now and cant see it...

Thank you for your help

---

### Post by tr333 on 2007-08-19
Did you remember to restart apache to reload the config files after editing apache2.conf?  This doesn't need to be done when using .htaccess files.

```
sudo apache2ctl graceful
```

The <Directory> section you put into apache2.conf just seems to enable CGI on each file in the directory "/usr/lib/cgi-bin/".  I can't see anything there that would enable username/password access.  Password protection on a directory should contain "Auth" lines.

Instead of editing apache2.conf, try placing your stuff inside a file in the /etc/apache2/conf.d/ directory. eg: "/etc/apache2/conf.d/awstats"
There might already be a file in there for awstats, but probably not.

Here's the contents of my /etc/apache2/conf.d/awstats file:
```
Alias /awstatsclasses "/usr/share/awstats/lib/"
Alias /awstats-icon/ "/usr/share/awstats/icon/"
Alias /awstatscss "/usr/share/doc/awstats/examples/css"
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
ScriptAlias /awstats/ /usr/lib/cgi-bin/
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch

<Directory /usr/lib/cgi-bin>
<Files awstats.pl>
Order Deny,Allow
Deny from all
Allow from 192.168
</Files>
</Directory>

<Location /awstats>
DirectoryIndex awstats.pl
</Location>
```

I've set it to only allow access from internal LAN IP addresses (192.168.xxx.xxx), and an alias for "http://xxx.xxx.xxx.xxx/awstats/" to make it easier to access the awstats.pl script

---

