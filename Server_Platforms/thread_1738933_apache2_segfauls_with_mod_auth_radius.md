---
title: "apache2 segfauls with mod_auth_radius"
date: 2011-04-25
forum: Server Platforms
---

### Post by hgfischer on 2011-04-25
Hi,

I've setup apache2 + libapache2-mod-auth-radius in a Ubuntu Server 10.10 AMD64 and I'm getting only segfaults when trying to authenticate. Any hint on this issue?

I've also tried to report a bug on that but looks there is a problem with Ubuntu bug reporting tool also.

Here is the bug report I tried to post there:

1) ```
# lsb_release -rd
Description:	Ubuntu 10.10
Release:	10.10
```

2) ```
# apt-cache policy libapache2-mod-auth-radius
libapache2-mod-auth-radius:
Installed: 1.5.8-1
Candidate: 1.5.8-1
Version table:
*** 1.5.8-1 0
500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe amd64 Packages
100 /var/lib/dpkg/status
```

3) Expect that module work without segfaulting apache, or at least give a proper error

4) However module crashes apache when trying to authenticate. see following error.log:

```
[Mon Apr 25 10:51:15 2011] [notice] Apache/2.2.16 (Ubuntu) mod_wsgi/3.2 Python/2.6.6 configured -- resuming normal operations
[Mon Apr 25 10:51:18 2011] [error] Internal error: pcfg_openfile() called with NULL filename
[Mon Apr 25 10:51:18 2011] [error] [client 10.110.60.22] (9)Bad file descriptor: Could not open password file: (null)
[Mon Apr 25 10:51:18 2011] [debug] mod_auth_radius-2.0.c(1185): Radius Auth for: ***.***.com requests / : file=/var/www/
[Mon Apr 25 10:51:18 2011] [debug] mod_auth_radius-2.0.c(1216): No cookie found. Trying RADIUS authentication.\n
[Mon Apr 25 10:51:18 2011] [notice] child pid 13094 exit signal Segmentation fault (11)
```

And the /etc/apache2/sites-available/default I've configured to use mod_auth_radius:

```
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www
  AddRadiusAuth ***.***.com.br:1812 **secret** 5:3
  AddRadiusCookieValid 1
  <Directory />
    Options FollowSymLinks
    AllowOverride None
  </Directory>
  <Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    AuthType Basic
    AuthName "RADIUS authentication"
    AuthBasicAuthoritative Off
    AuthRadiusAuthoritative on
    AuthRadiusActive on
    Require valid-user
  </Directory>
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
  <Directory "/usr/lib/cgi-bin">
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
  </Directory>
  ErrorLog ${APACHE_LOG_DIR}/error.log
  # Possible values include: debug, info, notice, warn, error, crit,
  # alert, emerg.
  LogLevel debug
  CustomLog ${APACHE_LOG_DIR}/access.log combined
  Alias /doc/ "/usr/share/doc/"
  <Directory "/usr/share/doc/">
    Options Indexes MultiViews FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    Allow from 127.0.0.0/255.0.0.0 ::1/128
  </Directory>
</VirtualHost>
```

---

