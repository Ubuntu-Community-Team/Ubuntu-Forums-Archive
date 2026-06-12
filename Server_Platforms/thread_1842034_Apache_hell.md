---
title: "Apache hell"
date: 2011-09-10
forum: Server Platforms
---

### Post by berryboy on 2011-09-10
hello im posting out desperation really, and not really sure where to post, so here goes

im trying to add  domain1.com and domain2.com

there roots are /var/www/domain1 and /var/www/domain2

i have followed this guide to the letter

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

but i get this when i restart apache2
[HTML][Sat Sep 10 20:55:40 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
[Sat Sep 10 20:55:40 2011] [warn] NameVirtualHost *:0 has no VirtualHosts
[/HTML]

could someone point me to a working guide even? i cant seem to  find many :/

thank you

---

### Post by berryboy on 2011-09-10
this is a nightmare ive added everything but no matter what domain i use it points to the default (ie) /var/www

ive installed webmin 

and added them that way they show up in webmin fine
but still point to the default directory, please i just need a simple guide thats up to date. i really dont want this post to sink to the bottom of the forum as do so many of my post :'( i'll be reading and reading and doing the same thing over and over again with different guides that must be missing something god knows....

thanks for yer time...

---

### Post by lisati on 2011-09-10
Have you added entries in /etc/apache2/sites-available, enabled them, and reloaded apache?

---

### Post by berryboy on 2011-09-10
i have made the 'sites-available/www.example.com' file, then using using a2ensite enabled it, i really am thankful for a responce :)

 i really did follow that guide to the letter

would u like me to post up anymore info? just ask i'll get right on it.
im just missing one thing maybe, but its not in that guide or its outdated..

---

### Post by Dangertux on 2011-09-10
You did something wrong in the vhost files in sites-available.

Can you post the files for both site1 and site2.

---

### Post by Doug S on 2011-09-10
> i really did follow that guide to the letter
> there roots are /var/www/domain1 and /var/www/domain2
The guide talks about making the roots at /home/www/, not /var/www/
I wonder if making them at /var/www creates a conflict with the default stuff?
I don't have time to test it on my test machine at the moment, but I might in a few hours.

---

### Post by Dangertux on 2011-09-10
EDIT: OK forget that, here it is the simple I mean REALLY simple guide to doing this. This guide starts from the beginning so forget everything you did in the other guide. 

Assumptions :
domain1.com will be the first site
domain2.com will be the second site 
/var/www is your web root according to apache

*change these where you see them as appropriate*

Step 1 

Create the directories for your 2 websites

```

sudo mkdir /var/www/domain1.com
sudo mkdir /var/www/domain2.com

```

Step 2

Create the vhosts files for each domain

```

sudo touch /etc/apache2/sites-available/domain1.com
sudo touch /etc/apache2/sites-available/domain2.com

```

Step 3

Edit the vhosts for each domain and set them up like this.

```

sudo nano /etc/apache2/sites-available/domain1.com

```

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName  domain1.com
    DocumentRoot /var/www/domain1.com
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/domain1.com>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options -ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

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

Save that file and edit the next

```

sudo nano /etc/apache2/sites-available/domain2.com

```

set that file up like this

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName  domain2.com
    DocumentRoot /var/www/domain2.com
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/domain2.com>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options -ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

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

Save the file

Step 4 
Enable the sites and restart apache

```

sudo a2ensite domain1.com
sudo a2ensite domain2.com
sudo /etc/init.d/apache2 restart

```

Observe that there are no errors when apache restarts. Test your domains. Enjoy virtual hosts :-)

---

### Post by berryboy on 2011-09-11
thank you so much for your responses, i have tried your guide when i restart apache2 i get this 

 ```
 /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Sun Sep 11 09:34:21 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sun Sep 11 09:34:22 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]
```

my vhost files are as follows

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName  www.debshandmadejewellery.co.uk
    DocumentRoot /var/www/www.debshandmadejewellery.co.uk
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/www.debshandmadejewellery.co.uk>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options -ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

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

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName  www.loanbox.org
    DocumentRoot /var/www/www.loanbox.org
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/www.loanbox.org>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options -ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

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

placed these in /etc/apache2/sites-available

then enabled with 

```
a2ensite www.debshandmadejewellery.co.uk

 a2ensite www.loanbox.org

 /etc/init.d/apache2 restart ( no need for sudo using root acc)


```

default vhost 

```
<VirtualHost *>
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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
	
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



</VirtualHost>
```


apache2.conf file 

```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```


ur guide is so simple how could i mess up? maybe some setting in apache? how could i reset apache to all default then start again ? hope my vhosts/conf have a visable error in them that someone can see. thanks again you have no idea how frustrated was with this yesterday

---

### Post by berryboy on 2011-09-11
i have tried to uninstall apache2 with 

apt-get remove --purge apache2 then deleted ect/apache2 to hopefuly get rid of a bad config file, i then 

apt-get install apache2

but etc/apache2 still does not exist, also when i did 

apt-get remove --purge apache2 the server continued to serve pages?? 

so now i have a some what functioning apache2 with no config files? but still serving up pages o_0

also im unable to restart it now 


/etc/init.d/apache2 restart
/etc/init.d/apache2: line 45: /etc/apache2/envvars: No such file or directory

---

### Post by berryboy on 2011-09-11
i managed to get apache2 installed correctly i had to 

apt-get remove --purge apache2 apache2-utils

then apt-get install apache2.

brilliant 

i then ftp'd my vhost files over and 

a2ensite [www.debshandmadejewellery.co.uk](www.debshandmadejewellery.co.uk)

a2ensite [www.loanbox.org](www.loanbox.org)

/etc/init.d/apache2 restart

no errors with apache2 restart now but it is still only offering pages from /var/www  dont i have to add 

virtual.conf to /etc/apache2/conf.d with

```
#
#  We're running multiple virtual hosts.
#
NameVirtualHost *
```

inside? this tells apache look for virtual hosts?

---

### Post by berryboy on 2011-09-11
is there another way of adding domains?

this is just crazy i wasted all of yesterday and 5 hours (so far)of today with this poxy thing, its bloody simple yet it fails.......... with nothing much to go on other than the error


[Sun Sep 11 15:19:38 2011] [warn] NameVirtualHost *:0 has no VirtualHosts
 ... waiting [Sun Sep 11 15:19:39 2011] [warn] NameVirtualHost *:0 has no VirtualHosts


blah blah useless

maybe nginx webserver would be a more reliable solution?

---

### Post by berryboy on 2011-09-11
maybe this is the issue? im having a little trouble understanding it 

```
Using the same Listen and/or NameVirtualHost multiple times.

Example:


# Can happen when using multiple config files.
# In one config file:
Listen 80
# In another config file:
Listen 80

# Like above, can happen when using multiple config files.
# In one config file:
NameVirtualHost *:80
# In another config file:
NameVirtualHost *:80
In the case of multiple Listen directives, Apache will bind to port 80 the first time and then try to bind to port 80 a second time. This yields a nice "Could not bind to port" error on start up. This seems to happen with newbies and Debian based distros, where Debian based distros have Listen 80 defined in ports.conf. Newbies don't realize this and create another Listen 80 line in apache2.conf.


Multiple NameVirtualHost lines will yield a "NameVirtualHost *:80 has no VirtualHosts" warning. Apache will ignore the second directive and use the first defined NameVirtualHost line, though. This seems to happen when one is using multiple virtual host configuration files and doesn't understand that you only need to define a particular NameVirtualHost line once. As above, this can occur in the debian ports.conf file, especially after an upgrade.
```

my ports.conf

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *
NameVirtualHost *:80
Listen *:80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

taken from here: [http://wiki.apache.org/httpd/CommonMisconfigurations](http://wiki.apache.org/httpd/CommonMisconfigurations)

please help

---

### Post by berryboy on 2011-09-11
i no longer get errors when restarting apache2

with this as my ports.conf
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

#NameVirtualHost *
NameVirtualHost *:80
Listen *:80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

however the domains are still pointing to /var/www

:'(

---

### Post by Doug S on 2011-09-11
I was just writting about the two NameVirtualHost lines when your post came.
My ports.conf file has "Listen 80" instead of Listen *:80"
see also: [http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html) 
a little while ago one of your links was going to a different spot, now they both go to "nothing to see here".

---

### Post by berryboy on 2011-09-11
thanks doug and others,

i think i have fixed it

default had 

<VirtualHost *>

changed to 
<VirtualHost *:80>

now they seem to be working 

well debshandmadejewellery.co.uk not points to the correct place but loanbox.org does not (still pointing to /var/www)

i guess i can live with that for now, my eyes really hurt ive spent so much time reading 20+hours really!

just tried ur suggestion unfortunately it has had no effect but thanks for posting :)

---

### Post by Doug S on 2011-09-11
It is still not clear to me that there is not a potential conflict with /etc/apache2/sites-available/default (if you still have it). Also see this line in my above reference:
>  
The ServerName and DocumentRoot included in this virtual host should be the same as the global ServerName and DocumentRoot. List this virtual host first in the configuration file so that it will act as the default host.


---

### Post by Dangertux on 2011-09-11
[LEFT]Two things to note.

1 -- You need to have DNS A records for www if you are going to use your domain as [www.whatever.com]("http://www.whatever.com") , otherwise you need to just use whatever.com (this might be part of your problem).
 

2 -- If you disable default, it should fix it.

```

sudo a2dissite default
sudo /etc/init.d/apache2 restart

```And all of your domains should point to the right places.
[/LEFT]

---

### Post by berryboy on 2011-09-11
ah yes much closer to the problem here, 

if i put [http://debshandmadejewellery.co.uk/](http://debshandmadejewellery.co.uk/) i get the wrong page 
if i put [http://www.debshandmadejewellery.co.uk/](http://www.debshandmadejewellery.co.uk/) i get the correct page.

i have disabled default  a2dissite default but get the same effect

should the name in vhost be 

ServerName *loanbox.org or *.loanbox.org ?? or both?

---

### Post by Doug S on 2011-09-11
It seems to be working, I see three different sites now, two by the names given and one, I think at /var/www, by ip address. (I assume the loanbox one is restricted access on purpose.)
Sorry it was such a saga for you.

---

### Post by Doug S on 2011-09-11
I think you will need to add server alias directives, this:
>  
ServerName [www.debshandmadejewellery.co.uk](www.debshandmadejewellery.co.uk)
 
would become this:
>  
ServerName [www.debshandmadejewellery.co.uk](www.debshandmadejewellery.co.uk)
ServerAlias debshandmadejewellery.co.uk

see also: [http://ubuntuforums.org/showthread.php?t=1739173](http://ubuntuforums.org/showthread.php?t=1739173)

---

### Post by berryboy on 2011-09-11
> **Doug S said:**
> It seems to be working, I see three different sites now, two by the names given and one, I think at /var/www, by ip address. (I assume the loanbox one is restricted access on purpose.)
Sorry it was such a saga for you.

yep seems to be working correctly now well debshandmadejewellery.co.uk is with and with out www oddly loanbox.org is  pointing to /var/www/www.debshandmadejewellery.co.uk where as [www.loanbox.org](www.loanbox.org) is pointing to the restricted page (both should be going here really)

got it  
ServerName  [www.loanbox.org](www.loanbox.org)
ServerAlias *loanbox.org

thanks again for taking the time and helping me out :)

---

### Post by Dangertux on 2011-09-11
Thanks for the private message, I mistyped it SHOULD be A record not C  I have edited my previous post and am updating so as not to cause confusion.

Life lesson : don't post when you first wake up :-P

---

