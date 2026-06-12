---
title: "Apache + Radius"
date: 2008-11-19
forum: Security
---

### Post by Sarmacid on 2008-11-19
I have an apache2 server, and I would like to set up authentication to a radius server. I've searched a lot and still nothing, so I would really appreciate if someone can point me at some documentation or tell me how they've done it.

---

### Post by cariboo on 2008-11-19
Is this:

[http://www.howtoforge.com/apache_radius_two_factor_authentication](http://www.howtoforge.com/apache_radius_two_factor_authentication)

What you are looking for?

Jim

---

### Post by Sarmacid on 2008-11-19
Thanks, but no, I already saw that, and it's made for Fedora. I tried doing something similar with mod_auth_radius but it didn't work.

---

### Post by Sarmacid on 2008-11-21
After a week of fighting, I finally managed to wrestle apache into submission... Sort of.

Had to ```
apt-get install libapache2-mod-auth-radius
```

And here are my .htaccess and httpd.conf

```
more .htaccess /etc/apache2/httpd.conf
::::::::::::::
.htaccess
::::::::::::::
AuthType Basic
AuthName "RADIUS authentication"
AuthBasicAuthoritative Off
AuthRadiusAuthoritative on
AuthRadiusCookieValid 1
AuthRadiusActive On

Require valid-user
::::::::::::::
/etc/apache2/httpd.conf
::::::::::::::
LoadModule radius_auth_module modules/mod_auth_radius.so

AddRadiusAuth <ip>:<port> <shared secret> 5:3
AddRadiusCookieValid 1

```

Now I'm having another issue. If I get authenticated, it will stay authenticated (forever apparently, but I've only been in for about an hour) in both FF and IE, also if I misstype username or password, I get a "Authorization Required" response (that apparently stays forever too). The only way I've found to get around this is telling FF to clear my authenticated sessions and then I can try to get authenticated again.

---

### Post by nowen on 2008-12-10
> **Sarmacid said:**
> After a week of fighting, I finally managed to wrestle apache into submission... Sort of.

Had to ```
apt-get install libapache2-mod-auth-radius
```

And here are my .htaccess and httpd.conf

```
more .htaccess /etc/apache2/httpd.conf
::::::::::::::
.htaccess
::::::::::::::
AuthType Basic
AuthName "RADIUS authentication"
AuthBasicAuthoritative Off
AuthRadiusAuthoritative on
AuthRadiusCookieValid 1
AuthRadiusActive On

Require valid-user
::::::::::::::
/etc/apache2/httpd.conf
::::::::::::::
LoadModule radius_auth_module modules/mod_auth_radius.so

AddRadiusAuth <ip>:<port> <shared secret> 5:3
AddRadiusCookieValid 1

```

Now I'm having another issue. If I get authenticated, it will stay authenticated (forever apparently, but I've only been in for about an hour) in both FF and IE, also if I misstype username or password, I get a "Authorization Required" response (that apparently stays forever too). The only way I've found to get around this is telling FF to clear my authenticated sessions and then I can try to get authenticated again.

FYI.  I have posted an updated version for Ubuntu on HTF:
[http://www.howtoforge.net/how-to-configure-apache-to-use-radius-for-two-factor-authentication-on-ubuntu](http://www.howtoforge.net/how-to-configure-apache-to-use-radius-for-two-factor-authentication-on-ubuntu)

HTH,

Nick

---

### Post by hgfischer on 2011-04-25
Hi,

I've setup apache2 + libapache2-mod-auth-radius in a Ubuntu Server 10.10 AMD64 and I'm getting only segfaults when trying to authenticate. Any hint on this issue?

I've also tried to report a bug on that but looks there is a problem with Ubuntu bug reporting tool also.

Here is the bug report I tried to post there:


1) # lsb_release -rd
Description:	Ubuntu 10.10
Release:	10.10

2) # apt-cache policy libapache2-mod-auth-radius
libapache2-mod-auth-radius:
  Installed: 1.5.8-1
  Candidate: 1.5.8-1
  Version table:
 *** 1.5.8-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe amd64 Packages
        100 /var/lib/dpkg/status

3) module work without segfaulting apache, or at least give a proper error

4) module crashes apache when trying to authenticate. see following error.log:

[Mon Apr 25 10:51:15 2011] [notice] Apache/2.2.16 (Ubuntu) mod_wsgi/3.2 Python/2.6.6 configured -- resuming normal operations
[Mon Apr 25 10:51:18 2011] [error] Internal error: pcfg_openfile() called with NULL filename
[Mon Apr 25 10:51:18 2011] [error] [client 10.110.60.22] (9)Bad file descriptor: Could not open password file: (null)
[Mon Apr 25 10:51:18 2011] [debug] mod_auth_radius-2.0.c(1185): Radius Auth for: ***.***.com requests / : file=/var/www/
[Mon Apr 25 10:51:18 2011] [debug] mod_auth_radius-2.0.c(1216):  No cookie found.  Trying RADIUS authentication.\n
[Mon Apr 25 10:51:18 2011] [notice] child pid 13094 exit signal Segmentation fault (11)

And the /etc/apache2/sites-available/default I've configured to use mod_auth_radius:

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

---

