---
title: "Problem with vboxwebsrv"
date: 2013-12-27
forum: Virtualisation
---

### Post by 3Y93E on 2013-12-27
Hi everybody,
I have a problem to run phpvirtualbox and to manage my virtual maschines.

Situation:
- I installed ubuntu server 13.10
- I installed virtualbox, apache2, php5 from the sources
- I installed phpvirtualbox and virtualbox extensions in the version 4.2.16
(I started with me research on these pages: 
1) [http://santi-bassett.blogspot.de/2013/01/installing-virtualbox-on-ubuntu-server.html](http://santi-bassett.blogspot.de/2013/01/installing-virtualbox-on-ubuntu-server.html), 
2) [http://www.heise.de/open/artikel/Toolbox-Virtualbox-im-Browser-mit-phpVirtualbox-1668019.html](http://www.heise.de/open/artikel/Toolbox-Virtualbox-im-Browser-mit-phpVirtualbox-1668019.html))

Problem:
- If I run "vboxwebsrv" it shows me the following error: 00:00:00.150329 SQPmp    #### SOAP FAULT:  [SOAP-ENV:Server] and I can not login to phpvirtualbox. The error in the browser is: could not connect to host

Strange:
- If I run "vboxwebsrv -H ::1" I can login phpvirtualbox and do everything.

Help needed:
Can explain me that strange behavior and what I have to change that I can use my virtual machines right from the beginning?

Thanks and best regards,
Christoph

---

### Post by SeijiSensei on 2013-12-28
> **3Y93E said:**
> I installed ubuntu server 13.10

That's okay for development; in production you should use a version with "[long-term]("https://wiki.ubuntu.com/LTS")" support like 12.04LTS.  Differences between server versions are much smaller than between desktop versions.  The basic server software has been around for years now.

> I installed virtualbox, apache2, php5 from the sources

I only install software from the distribution's repositories unless there is a critical item missing.  The simplest method to install Apache and PHP (along with MySQL) on Ubuntu is to use "[tasksel]("https://help.ubuntu.com/community/ApacheMySQLPHP")" like this:

```

sudo apt-get install tasksel
sudo tasksel install lamp-server

```

Some PHP modules are distributed as separate packages prefixed with "php5-".  Here's the list compliments of "apt-cache search php5-* | sort | grep ^php5":

```

php5-adodb - Extension optimising the ADOdb database abstraction library
php5-apcu - APC User Cache for PHP 5
php5-cgi - server-side, HTML-embedded scripting language (CGI binary)
php5-cli - command-line interpreter for the php5 scripting language
php5-curl - CURL module for php5
php5-dbg - Debug symbols for PHP5
php5-dev - Files for PHP5 module development
php5-enchant - Enchant module for php5
php5-exactimage - fast image manipulation library (PHP bindings)
php5-ffmpeg - audio and video support via ffmpeg for php5
php5-fpm - server-side, HTML-embedded scripting language (FPM-CGI binary)
php5-gdcm - Grassroots DICOM PHP5 bindings
php5-gd - GD module for php5
php5-geoip - GeoIP module for php5
php5-gmp - GMP module for php5
php5-imagick - ImageMagick module for php5
php5-imap - IMAP module for php5
php5-interbase - interbase/firebird module for php5
php5-intl - internationalisation module for php5
php5-json - JSON module for php5
php5-lasso - Library for Liberty Alliance and SAML protocols - PHP 5 bindings
php5-ldap - LDAP module for php5
php5-librdf - PHP5 language bindings for the Redland RDF library
php5-mapscript - php5-cgi module for MapServer
php5-mcrypt - MCrypt module for php5
php5-memcached - memcached extension module for PHP5, uses libmemcached
php5-memcache - memcache extension module for PHP5
php5-midgard2 - Midgard2 Content Repository - PHP5 language bindings and module
php5-ming - Ming module for php5
php5-mongo - MongoDB database driver
php5-mysql - MySQL module for php5
php5-mysqlnd - MySQL module for php5 (Native Driver)
php5-odbc - ODBC module for php5
php5-pgsql - PostgreSQL module for php5
php5-pinba - Pinba module for PHP 5
php5-pspell - pspell module for php5
php5-ps - ps module for PHP 5
php5-radius - PECL radius module for PHP 5
php5-readline - Readline module for php5
php5-recode - recode module for php5
php5-remctl - PECL module for Kerberos-authenticated command execution
php5-rrd - rrd module for PHP 5
php5-sasl - Cyrus SASL extension for PHP 5
php5 - server-side, HTML-embedded scripting language (metapackage)
php5-snmp - SNMP module for php5
php5-sqlite - SQLite module for php5
php5-svn - PHP Bindings for the Subversion Revision control system
php5-sybase - Sybase / MS SQL Server module for php5
php5-tidy - tidy module for php5
php5-tokyo-tyrant - PHP interface to Tokyo Cabinet's network interface, Tokyo Tyrant
php5-vtkgdcm - Grassroots DICOM VTK PHP bindings
php5-xcache - Fast, stable PHP opcode cacher
php5-xdebug - Xdebug Module for PHP 5
php5-xhprof - Hierarchical Profiler for PHP5
php5-xmlrpc - XML-RPC module for php5
php5-xsl - XSL module for php5

```

If you need any of these, run "sudo apt-get install php5-modname" to ensure that it is part of your installation.  Since this is a "LAMP" server, php5-mysql is already installed.

For VirtualBox, I use Oracle's own repositories as described [here](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  That enables apt to update VirtualBox like it does other packages.

> Problem:
- If I run "vboxwebsrv" it shows me the following error: 00:00:00.150329 SQPmp    #### SOAP FAULT:  [SOAP-ENV:Server] and I can not login to phpvirtualbox. The error in the browser is: could not connect to host

Strange:
- If I run "vboxwebsrv -H ::1" I can login phpvirtualbox and do everything.

What about "vboxwebsrv -H 127.0.0.1" or "vboxwebsrv -H localhost"?  If you can use the IPv6 address ::1 for localhost, see if you can use the IPv4 version as well.  Perhaps there is a configuration file for this program where you can specify the default server address?  I've never used it so I can't help more with that.

---

### Post by 3Y93E on 2014-01-16
Hi SeijiSensei,

thanks for your remarks. All were very helpful.
In the end after hours of trial and error I switched to 12.10 LTS and it worked Virtualbox with PHP frontend worked perfectly fine from the first moment. 

Thanks
Christoph

---

### Post by orionsune on 2014-07-10
Alternatively, you can change the url contained in config.php to point to the local hostname of the ipv6 address vboxwebsrv is using. ex config.php

```
/* SOAP URL of vboxwebsrv (not phpVirtualBox's URL) */
var $location = 'http://ip6-localhost:18083';
```

Take a look at /etc/hosts for the correct ipv6 local hostname to use. ex


```
::1     localhost ip6-localhost ip6-loopback
```

Or simply remove the "localhost" from the ::1 entry, but if vboxwebsrv is failing on binding to any ipv4 address from the command line, I don't think that will work either and will cause vboxwebsrv to simply fail with default settings. Just use the ipv6 adapter for internal web apps, unless app and server are on seperate boxes, then idk.

---

