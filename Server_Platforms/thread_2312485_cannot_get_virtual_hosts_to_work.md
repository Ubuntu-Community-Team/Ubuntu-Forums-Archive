---
title: "cannot get virtual hosts to work"
date: 2016-02-04
forum: Server Platforms
---

### Post by micahpage on 2016-02-04
Our server is running Ubuntu 14.04. The server was initially intended for a single site, but i would like to add more sites. The initial site is python-gaming.com and i want to make a separate one for metulburr.com 

I went through the tutorial here 
[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

and metulburr.com still points to python-gaming.com's html


One part that mine differs from the tutorial, is i am not sure if the old site needs a conf file in addition to the new virtual host. I would assume the default.conf file would be it?

```
metulburr /etc/apache2/sites-available $ ls
000-default.conf  default-ssl.conf  domain1.com.conf  metulburr.com.conf
metulburr /etc/apache2/sites-available $ 

```
```
metulburr /etc/apache2/sites-available $ cat metulburr.com.conf 
<VirtualHost *:80>
    ServerAlias www.metulburr.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/metulburr.com
    ServerName www.metulburr.com:80
    <Directory /var/www/metulburr.com>
        Order allow,deny
        Allow from all
    </Directory>


    
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com


    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/metulburr.com


    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined


    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



```

```
metulburr /etc/apache2/sites-available $ cat 000-default.conf 
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html/blog/wordpress
    ServerName www.python-gaming.com:80
    <Directory /var/www/html>
        Order allow,deny
        Allow from all
    </Directory>


    
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com


    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html


    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined


    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



```

```
metulburr /etc/apache2/sites-available $ a2ensite metulburr.com.conf 
Site metulburr.com already enabled
metulburr /etc/apache2/sites-available $ sudo service apache2 restart
 * Restarting web server apache2                                                                   [ OK ] 
metulburr /etc/apache2/sites-available $
```

```
metulburr /var/www $ ls -ltotal 192
drwxr-xr-x 23 root root 180224 Oct 13 20:08 Dump
drwxr-xr-x  6 root root   4096 Oct 26 15:04 ftp
drwxr-xr-x 10 root root   4096 Feb  4 16:03 html
drwxr-xr-x  2 root root   4096 Feb  4 15:45 metulburr.com
metulburr /var/www $ 

```

EDIT:
Ive also made a python-gmaing.com.conf in sites-available and enabled that, and restarted apache, but to no avail, both domains point to the old site html.

---

### Post by matt_symes on 2016-02-04
Hi

> ServerName [www.python-gaming.com:80](www.python-gaming.com:80)
ServerName [www.metulburr.com:80](www.metulburr.com:80)

Try removing the :80 from both the above and reload apache.

```
ServerName www.python-gaming.com
ServerName www.metulburr.com
```

```
sudo service apache2 reload
```

Also you'll want to arrange your sites locations better.

Your *DocumentRoot* and *<Directory ...>* stanzas could use some tweaking.

Kind regards

---

### Post by micahpage on 2016-02-04
Removing the port 80 seemed to not effect anything.

im not sure my directory for the site was always modified by the /etc/apache2/apache2.conf file in which I did make more modifications to the Directory's

```
# This is the main Apache server configuration file.  It contains the# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.


# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#       /etc/apache2/
#       |-- apache2.conf
#       |       `--  ports.conf
#       |-- mods-enabled
#       |       |-- *.load
#       |       `-- *.conf
#       |-- conf-enabled
#       |       `-- *.conf
#       `-- sites-enabled
#               `-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.
# Global configuration
#


#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"


#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
Mutex file:${APACHE_LOCK_DIR} default
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
KeepAliveTimeout 5




# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


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
ErrorLog ${APACHE_LOG_DIR}/error.log


#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn


# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf


# Include list of ports to listen on
Include ports.conf

# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>


<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>

#ScriptAlias "/cgi-bin/" "/var/www/html/cgi-bin" 
<Directory "/var/www/html/cgi-bin">
    AllowOverride None
    Options +ExecCGI +MultiViews +SymLinksIfOwnerMatch +Includes +Multiviews
    Order allow,deny
    Allow from all
    AddHandler cgi-script .py 
    AddHandler cgi-script .cgi
    AddHandler wsgi-script .wsgi
</Directory>

Directory /var/www/html/>
     Options FollowSymLinks
     AllowOverride All
     Require all granted


    Options +ExecCGI +Indexes +FollowSymLinks +MultiViews +Includes
#    AllowOverride None
#    Order allow,deny
#    allow from all
    AddHandler cgi-script .py 
    AddHandler cgi-script .cgi
    AddHandler wsgi-script .wsgi
    AddHandler default-handler .html .htm  
    AddType text/html .shtml
    AddHandler server-parsed .html
    AddHandler server-parsed .shtml 
#    DirectoryIndex index.shtml index.html
    AddOutputFilter INCLUDES .shtml
    AddHandler php5-script php
</Directory>
ServerName www.python-gaming.com:80


<Directory /var/www/html/pygame/docs>
    Options +Indexes +FollowSymLinks +MultiViews +Includes
    AllowOverride All
    Order allow,deny
    allow from all
    AddHandler default-handler .html .htm  
    AddType text/html .shtml
    AddHandler server-parsed .html
    AddHandler server-parsed .shtml 
    AddOutputFilter INCLUDES .shtml
    AddHandler php5-script php


</Directory>

<Directory /var/www/html/highlighter>
    Options +Indexes +FollowSymLinks +MultiViews +Includes
    AllowOverride All
    Order allow,deny
    allow from all
    AddHandler default-handler .html .htm  
    AddType text/html .shtml
    AddHandler server-parsed .html
    AddHandler server-parsed .shtml 
    AddOutputFilter INCLUDES .shtml
    AddHandler php5-script php


</Directory>

<Directory /var/www/html/menu>
    Options +Indexes +FollowSymLinks +MultiViews +Includes
    AllowOverride All
    Order allow,deny
    allow from all
    AddHandler default-handler .html .htm  
    AddType text/html .shtml
    AddHandler server-parsed .html
    AddHandler server-parsed .shtml 
    AddOutputFilter INCLUDES .shtml
    AddHandler php5-script php


</Directory>

<Directory /var/www/html/blog/wordpress>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>


#<Directory /srv/>
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
#</Directory>

# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess


#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
        Require all denied
</FilesMatch>

#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.


# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf


# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


































```

EDIT:
when i did 
> sudo a2dissite 000-default.conf and restarted apache, i got a 403 on both sites. So i am assuming apache is for some reason not using the virtual sites, but the 000-default.conf one, I am just not sure how to switch?

I am not sure what would have a permission problem
> metulburr /etc/apache2/sites-available $ ls -ltotal 24
-rw-r--r-- 1 root root 1552 Feb  4 18:32 000-default.conf
-rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
-rw-r--r-- 1 root root  299 Oct 15 13:10 domain1.com.conf
-rw-r--r-- 1 root root 1595 Feb  4 18:32 metulburr.com.conf
-rw-r--r-- 1 root root 1552 Feb  4 18:34 python-gaming.com.conf
metulburr /etc/apache2/sites-available $ 




---

### Post by darkod on 2016-02-05
I am no expert in apache, but I don't think you need to touch /etc/apache2/apache2.conf too much, if any... The DirectoryRoot is specified for each site in it's own conf file in /etc/apache2/sites-available, so I don't know how the changes you did in apache2.conf might affect your system now. And you did not need to modify 000-default.conf at all (I see you put your python site in it). In fact, better to use the default conf file as template for all your sites, and leave it as it came with apache by default.

Also, looking at the metalburr conf, your ServerName and ServerAlias are identical. As far as I understand, the Alias should complement the Name, not be identical. For example, to accept URL with and without www you would put in your site conf:
```
ServerName   domain.com
ServerAlias   www.domain.com
```

Since you haven't achieved much (your sites are not even opening), it might be a good idea to start from scratch. I don't know if in this case purging apache2 will delete all current config that you have modified, and then installing it will give you the minimum default install. From there start over and this time, remember, START SMALL...

Do only the basics first:
1. Copy the 000-default.conf into your site files.
2. In the site files modify only the ServerName, ServerAlias (if needed) and DirectoryRoot.
3. Run the apache commands to enable the sites and restart apache.

See if that helps you to get the sites opening.

Any more specific config that you might need comes only after that... Get the basics working first.

---

### Post by micahpage on 2016-02-05
> [COLOR=#000000]Since you haven't achieved much (your sites are not even opening)[/COLOR]
I am not sure what you mean? Currently both sites for me show up in the browser.

I wasnt aware when i first created the server that you set each site in its own file. So i just modified the default and used that. And i only had one site to deal with. I added onto that as i used it. It appeared to be modifying it as i changed the default the server would respond to it. How would i go about purging apache2 to restart the process. Its been so long since i started the server with these settings.

---

### Post by darkod on 2016-02-06
Sorry, I misunderstood that they are not opening correctly at all. And it confused me further when you said that disabling the default site makes them not work. That should not happen at all, and in a way means that they are not opening (using the correct config), no?

Also in your second post I see that now in sites-available you have 000-default, metulburr and python-gaming. If the default still has the python-gaming URL then you should not have one more conf file with the same URL/domain.

I would also try to comment out (not delete, not yet) the Directory changes you did in apache2.conf. You probably remember which lines you added and what you modified. Then restart apache and see how it goes.

Also what I notice in your 000-default is that you have two DocumentRoot directives with different paths. How is it supposed to know which one to use? I would try bringing 000-default.conf to the default version. I think your only modification is the group of code on the top, so if you remove the following it should be back to default:
```
ServerAdmin webmaster@localhost
DocumentRoot /var/www/html/blog/wordpress
ServerName www.python-gaming.com:80
<Directory /var/www/html>
Order allow,deny
Allow from all
</Directory>
```

Try that and see if you get the standard apache welcome page when you put your server IP in the browser (not any domain). If you leave the default site enabled and unmodified it should always display the welcome page if I'm not mistaken, when using the server IP in browser.

If that part is OK, we can start cleaning up your conf files for both your domains.

For the purge part, usually to remove a program and all its config (when you want to start fresh), you simply use:
```
sudo apt-get purge apache2
```

After that when you install it again it should be the default installation. At least in theory... :)

But before trying something like that you can try undoing the modifications in apache2.conf and in 000-default.conf and see how that goes. Your choice...

---

