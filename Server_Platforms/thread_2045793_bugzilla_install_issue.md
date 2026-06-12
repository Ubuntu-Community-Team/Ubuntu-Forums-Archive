---
title: "bugzilla install issue"
date: 2012-08-21
forum: Server Platforms
---

### Post by infinitezero on 2012-08-21
Trying to install bugzilla on Ubuntu 12.04 (this is a fresh install) and I get the following when I goto [https://myserver/bugzilla/:](https://myserver/bugzilla/:)

#!/usr/bin/perl -wT
# -*- Mode: perl; indent-tabs-mode: nil -*-
#
# The contents of this file are subject to the Mozilla Public
# License Version 1.1 (the "License"); you may not use this file
# except in compliance with the License. You may obtain a copy of
# the License at [http://www.mozilla.org/MPL/](http://www.mozilla.org/MPL/)
#
# Software distributed under the License is distributed on an "AS
# IS" basis, WITHOUT WARRANTY OF ANY KIND, either express or
# implied. See the License for the specific language governing
# rights and limitations under the License.
#
# The Original Code is the Bugzilla Bug Tracking System.
#
# The Initial Developer of the Original Code is Netscape Communications
# Corporation. Portions created by Netscape are
# Copyright (C) 1998 Netscape Communications Corporation. All
# Rights Reserved.
#
# Contributor(s): Jacob Steenhagen <jake@bugzilla.org>
#                 FrÃ©dÃ©ric Buclin <LpSolit@gmail.com>

###############################################################################
# Script Initialization
###############################################################################


Here are the this instructions that I am using:



wget http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-$BZ_VERSION.tar.gz --output-document=/tmp/bugzilla-$BZ_VERSION.tar.gz

And we untar them :

tar --directory /var/www -xzf /tmp/bugzilla-$BZ_VERSION.tar.gz

We rename the created folder :

mv /var/www/bugzilla-$BZ_VERSION /var/www/bugzilla

And, in order to create a basic configuration file, we run the checksetup script :

cd /var/www/bugzilla
./checksetup.pl

This script show you the missing dependencies. If you want a LDAP or XML-RPC support, you can install the needed packages :

apt-get install libnet-ldap-perl
apt-get install libsoap-lite-perl

For the other missing dependencies, there is no Debian packages, and you need to install them using CPAN, but this is not mandatory.
Database

You can install a MySQL server and / or create a BUGZILLA database on an existing MySQL server by following this guide: MySQL for Debian 4.0 Etch.

Once this done, if you have followed the guide before, you can jump this step, otherwine, you need to setup the database connection parameters :


mysql -u root -p

MYSQL_DB=BUGZILLA
MYSQL_USERNAME=bugzilla
MYSQL_USERPWD=my_password
mysql> EXIT

And we configure Bugzilla to use the created database :

sed -i -e "s/^\$db_name = '.*';/\$db_name = '$MYSQL_DB';/" \
       -e "s/^\$db_user = '.*';/\$db_user = '$MYSQL_USERNAME';/" \
       -e "s/^\$db_pass = '.*';/\$db_pass = '$MYSQL_USERPWD';/" /var/www/bugzilla/localconfig

Setup

We will now fit Bugzilla to our needs. First, we setup the Apache server group :

sed -i -e "s/^\$webservergroup = '.*';/\$webservergroup = 'www-data';/" /var/www/bugzilla/localconfig

We launch a last time the Bugzilla configuration script that will create tables in the database, and add a administrator account :

cd /var/www/bugzilla
./checksetup.pl

We setup Apache 2 in order for Bugzilla to run properly :

sed -i -e '/<\/VirtualHost>/i\
  <Directory "\/var\/www\/bugzilla">\
    Options +ExecCGI\
    AllowOverride Limit\
    DirectoryIndex index.cgi\
    AddHandler cgi-script .cgi\
  <\/Directory>' /etc/apache2/sites-available/default

And we reload the new Apache 2 configuration :

/etc/init.d/apache2 reload

You can now access to your Bugzilla by using the URL :

[http://localhost/bugzilla](http://localhost/bugzilla)

---

### Post by spjackson on 2012-08-22
> **infinitezero said:**
> We setup Apache 2 in order for Bugzilla to run properly :

sed -i -e '/<\/VirtualHost>/i\
  <Directory "\/var\/www\/bugzilla">\
    Options +ExecCGI\
    AllowOverride Limit\
    DirectoryIndex index.cgi\
    AddHandler cgi-script .cgi\
  <\/Directory>' /etc/apache2/sites-available/default

And we reload the new Apache 2 configuration :

/etc/init.d/apache2 reload

It looks like this bit hasn't worked properly. Is there anything relevant in /var/log/apache2/error.log ? Please Post /etc/apache2/sites-available/default

---

### Post by infinitezero on 2012-08-22
**/var/log/apache2/error.log:**

[Tue Aug 21 18:37:30 2012] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Tue Aug 21 18:37:30 2012] [error] python_init: Python executable found '/usr/bin/python'.
[Tue Aug 21 18:37:30 2012] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Tue Aug 21 18:37:30 2012] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Tue Aug 21 18:37:30 2012] [notice] mod_python: using mutex_directory /tmp 
[Tue Aug 21 18:38:59 2012] [error] [client 12.88.74.90] File does not exist: /var/www/bugzilla
[Tue Aug 21 19:14:19 2012] [error] [client 12.88.74.90] PHP Notice:  Undefined variable: adminDetails in /var/www/msc/index.php on line 109
[Tue Aug 21 19:14:20 2012] [error] [client 12.88.74.90] File does not exist: /var/www/favicon.ico
[Tue Aug 21 19:14:36 2012] [error] [client 12.88.74.90] PHP Fatal error:  Call to undefined function curl_init() in /var/www/msc/admin.php on line 975, referer: 
[Tue Aug 21 19:33:25 2012] [notice] caught SIGTERM, shutting down
[Tue Aug 21 19:33:26 2012] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue Aug 21 19:33:26 2012] [notice] FastCGI: process manager initialized (pid 9969)
[Tue Aug 21 19:33:26 2012] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Tue Aug 21 19:33:26 2012] [error] python_init: Python executable found '/usr/bin/python'.
[Tue Aug 21 19:33:26 2012] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Tue Aug 21 19:33:26 2012] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Tue Aug 21 19:33:26 2012] [notice] mod_python: using mutex_directory /tmp 
[Tue Aug 21 19:33:26 2012] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue Aug 21 19:33:26 2012] [warn] mod_wsgi: Compiled for Python/2.7.2+.
[Tue Aug 21 19:33:26 2012] [warn] mod_wsgi: Runtime using Python/2.7.3.
[Tue Aug 21 19:33:26 2012] [notice] Apache/2.2.22 (Ubuntu) DAV/2 SVN/1.6.17 mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch mod_python/3.3.1 Python/2.7.3 mod_ssl/2.2.22 OpenSSL/1.0.1 mod_wsgi/3.3 mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Wed Aug 22 05:50:23 2012] [error] [client 66.211.31.212] File does not exist: /var/www/favicon.ico
[Wed Aug 22 05:50:33 2012] [error] [client 66.211.31.212] File does not exist: /var/www/var






**/etc/apache2/sites-available/default:**

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
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
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

  <Directory "/var/www/bugzilla">
    Options +ExecCGI
    AllowOverride Limit
    DirectoryIndex index.cgi
    AddHandler cgi-script .cgi
  </Directory>
  <Directory "/var/www/bugzilla">
    Options +ExecCGI
    AllowOverride Limit
    DirectoryIndex index.cgi
    AddHandler cgi-script .cgi
  </Directory>
</VirtualHost>

---

### Post by spjackson on 2012-08-23
I created a directory /var/www/bugzilla and placed a Perl script there as index.cgi. When I browsed to [http://localhost/bugzilla](http://localhost/bugzilla) and it displayed the contents of the script.

I then changed /etc/apache2/sites-available/default to be the same as yours and restarted apache. Now [http://localhost/bugzilla](http://localhost/bugzilla) executes index.cgi. In other words, that is working for me.

I can't think of much else. Is mod_cgi enabled?
```

ls -lL /etc/apache2/mods-enabled/*cgi*

```

---

### Post by infinitezero on 2012-08-23
mod_cgi is enabled. I will keep looking. If I find the solution I will post it.

iz

---

### Post by infinitezero on 2012-08-23
Found the answer.

[http://ubuntuforums.org/showthread.php?t=956052](http://ubuntuforums.org/showthread.php?t=956052)

I replaced:
<Directory "/var/www/bugzilla">
Options +ExecCGI
AllowOverride Limit
DirectoryIndex index.cgi
AddHandler cgi-script .cgi
</Directory>

With:
<Directory /var/www/bugzilla>
		AddHandler cgi-script .cgi
		Options Indexes FollowSymLinks ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>

---

