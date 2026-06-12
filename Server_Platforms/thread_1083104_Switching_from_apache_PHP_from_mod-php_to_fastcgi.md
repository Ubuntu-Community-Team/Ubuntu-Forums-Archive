---
title: "Switching from apache PHP from mod-php to fastcgi?"
date: 2009-02-28
forum: Server Platforms
---

### Post by jeffk on 2009-02-28
I am obliged to migrate from mod-php to one of the fastcgi implementations. in order to use mod-wsgi with the apache-worker version, etc.

I have been running DaviCal with mod-php in a virtualhost at root:

```
# Virtual Host def for Debian packaged DAViCal
<VirtualHost 192.168.10.99 >
  DocumentRoot /usr/share/davical/htdocs
  DirectoryIndex index.php index.html
  ServerName server1
  ServerAlias server1
  Alias /images/ /usr/share/davical/htdocs/images/
  php_value include_path /usr/share/awl/inc
  php_value magic_quotes_gpc 0
  php_value register_globals 0
  php_value error_reporting "E_ALL & ~E_NOTICE"
  php_value default_charset "utf-8"
</VirtualHost>
```

Which will need to be reworked with a FastCGI implementation. Do I want to use libapache2-mod-fastcgi, or libapache2-mod-fcgid, libfcgi, etc.

Any suggestions would be welcome, I'm long away from PHP configuration, and new to FastCGI entirely.

Thanks.

---

### Post by jeffk on 2009-02-28
I opted for fcgid, and have it configured except for the equivalent to php_value from my virtual host config:
```
# Virtual Host def for Debian packaged DAViCal
<VirtualHost 192.168.10.99 >
  DocumentRoot /usr/share/davical/htdocs
  DirectoryIndex index.php index.html
  ServerName server1
  ServerAlias server1
  Alias /images/ /usr/share/davical/htdocs/images/
  FCGIWrapper /usr/lib/cgi-bin/php5 .php
  AddHandler fcgid-script .php
  Options ExecCGI Indexes
  # php_value include_path /usr/share/awl/inc
  # php_value magic_quotes_gpc 0
  # php_value register_globals 0
  # php_value error_reporting "E_ALL & ~E_NOTICE"
  # php_value default_charset "utf-8"
</VirtualHost>
```
I thought I had it, need to set environment variables with uppercased spelling:
```
#
# Virtual Host def for Debian packaged DAViCal
<VirtualHost 192.168.10.99 >
  DocumentRoot /usr/share/davical/htdocs
  DirectoryIndex index.php index.html
  ServerName server1
  ServerAlias server1
  Alias /images/ /usr/share/davical/htdocs/images/
  FCGIWrapper /usr/lib/cgi-bin/php5 .php
  AddHandler fcgid-script .php
  Options ExecCGI Indexes
  DefaultInitEnv PHP_INCLUDE_PATH /usr/share/awl/inc
  DefaultInitEnv PHP_MAGIC_QUOTES_GPC 0
  DefaultInitEnv PHP_REGISTER_GLOBALS 0
  DefaultInitEnv PHP_ERROR_REPORTING "E_ALL & ~E_NOTICE"
  DefaultInitEnv PHP_DEFAULT_CHARSET "utf-8"
</VirtualHost>
```
But that doesn't work, same error as before:
```
Warning: require_once(AWLUtilities.php)
[function.require-once]: failed to open stream: No such      
file or directory in /usr/share/davical/inc/always.php on line 43

Fatal error: require_once()
[function.require]: Failed opening required 'AWLUtilities.php'           
(include_path='../inc:.:/usr/share/php:/usr/share/pear') in 
/usr/share/davical/inc/always.php on line 43
```
Any ideas?

Thanks.

---

### Post by jeffk on 2009-02-28
OK, I have a workaround:
```
$ cat /etc/apache2/sites-available/davical
#
# Virtual Host def for Debian packaged DAViCal
<VirtualHost 192.168.10.99 >
  DocumentRoot /usr/share/davical/htdocs
  DirectoryIndex index.php index.html
  ServerName server1
  ServerAlias server1
  Alias /images/ /usr/share/davical/htdocs/images/
  FCGIWrapper /usr/lib/cgi-bin/php5 .php
  AddHandler fcgid-script .php
  Options ExecCGI Indexes
</VirtualHost>
```
```
$ tail /etc/php5/cgi/php.ini 
; Custom settings for Davical
include_path = ".:/usr/share/awl/inc"
magic_quotes_gpc = Off
register_globals = Off
error_reporting = "E_ALL & ~E_NOTICE"
default_charset = "utf-8"

```
I searched high and low for some way to include those lines of custom .ini from the apache config while still including the original/stock php.ini.

The above gets the DaviCAL application back online, but if there's a technique I can use to move this custom config into the virtualhost configuration, I would very much prefer it.

Thanks for any suggestions.

---

