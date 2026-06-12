---
title: "404 fail when trying to access http://localhost/info.php after setting up LAMP"
date: 2016-11-28
forum: Server Platforms
---

### Post by joelrio on 2016-11-28
I installed Apache, mySQL, and PHP on Kubuntu 16.04. I also installed wordpress which seems to work fine. When I  access localhost in my browser I get to my site build front page. When I to go to [http://localhost/info.php](http://localhost/info.php) I get the 404 error:

**Not Found**

 The requested URL /info.php was not found on this server.
 [HR][/HR] Apache/2.4.18 (Ubuntu) Server at localhost Port 80


This is what's in my  /var/www/html/info.php file:

```
<?php

// Show all information, defaults to INFO_ALL
phpinfo();

?>
```

That seems right so why cant I see my info. 
Thanks Joel

---

### Post by cj13579 on 2016-11-28
Is that info.php in the same place as your Wordpress installation or are the files for that in another folder?

---

### Post by joelrio on 2016-11-28
Hi 

Yes in the same folder /var/www/html/

Joel

---

### Post by cj13579 on 2016-11-28
That's strange then. What happens if you rename the WordPress index.php and rename your file to index.php

```

cd /var/www/html
mv index.php index.php.orig  # rename index.php to index.php.orig
mv info.php index.php # rename info.php to index.php

```

What happens if you then go to [http://localhost](http://localhost) do you see the PHP Installation page?

Please can you also share the contents of your /etc/apache2/httpd.conf file?

---

### Post by yancek on 2016-11-28
Do you have the Document root set correctly in the php.ini file?

---

### Post by joelrio on 2016-11-29
Ok I tried that in Konsole first without (permission denied) and then with sudo.


```
duncan@duncan-H61M-D2H-USB3:~$ cd /var/www/html
duncan@duncan-H61M-D2H-USB3:/var/www/html$ mv index.php index.php.orig  # rename index.php to index.php.orig
mv: cannot move 'index.php' to 'index.php.orig': Permission denied
duncan@duncan-H61M-D2H-USB3:/var/www/html$ mv info.php index.php # rename info.php to index.php
mv: cannot stat 'info.php': No such file or directory
duncan@duncan-H61M-D2H-USB3:/var/www/html$ sudo mv index.php index.php.orig  # rename index.php to index.php.orig
[sudo] password for duncan: 
Sorry, try again.
[sudo] password for duncan: 
duncan@duncan-H61M-D2H-USB3:/var/www/html$
```


if I go localhost


```
Index of /


[ICO]    Name    Last modified    Size    Description
[   ]    index.php.orig    2013-09-25 01:18    418     
[TXT]    license.txt    2016-03-05 20:14    19K     
[   ]    phpinfo.php    2016-11-24 20:36    68     
[TXT]    readme.html    2016-08-16 21:39    7.2K     
[   ]    wp-activate.php    2016-05-24 22:02    5.3K     
[DIR]    wp-admin/    2016-07-05 16:37    -     
[   ]    wp-blog-header.php    2015-12-19 11:20    364     
[   ]    wp-comments-post.php    2016-05-23 17:44    1.4K     
[   ]    wp-config-sample.php    2015-12-16 09:58    2.8K     
[   ]    wp-config.php    2016-11-25 21:15    3.1K     
[DIR]    wp-content/    2012-01-08 17:01    -     
[   ]    wp-cron.php    2015-05-24 18:26    3.2K     
[DIR]    wp-includes/    2016-09-07 15:58    -     
[   ]    wp-links-opml.php    2016-05-23 17:44    2.3K     
[   ]    wp-load.php    2016-04-14 18:53    3.3K     
[   ]    wp-login.php    2016-06-14 22:51    33K     
[   ]    wp-mail.php    2016-07-13 13:37    7.6K     
[   ]    wp-settings.php    2016-08-13 17:02    14K     
[   ]    wp-signup.php    2016-05-24 21:44    29K     
[   ]    wp-trackback.php    2014-11-30 21:23    3.9K     
[   ]    xmlrpc.php    2016-07-06 13:40    3.0K     
Apache/2.4.18 (Ubuntu) Server at localhost Port 80
```


There is no httpd file in /apache2. This is /etc/apache2/apache2.conf. file




```
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.4/](http://httpd.apache.org/docs/2.4/) for detailed information about
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
#    /etc/apache2/
#    |-- apache2.conf
#    |    `--  ports.conf
#    |-- mods-enabled
#    |    |-- *.load
#    |    `-- *.conf
#    |-- conf-enabled
#    |    `-- *.conf
#     `-- sites-enabled
#         `-- *.conf
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
# e.g., [www.apache.org]("http://www.apache.org") (on) or 204.62.129.132 (off).
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


<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>


#<Directory /srv/>
#    Options Indexes FollowSymLinks
#    AllowOverride None
#    Require all granted
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


'Do you have the Document root set correctly in the php.ini file?' Not sure how to check that.

---

### Post by joelrio on 2016-11-29
Sorry I just noticed the info file is called phpinfo.php
Would this make a difference?

---

### Post by slickymaster on 2016-11-29
*Thread moved to **Server Platforms**.*

---

### Post by joelrio on 2016-11-29
Hello Chris

Really sorry that works fine if I browse to [COLOR=#000000]phpinfo.php
[/COLOR]Should I rename any of these files back or leave as is now?

Thanks Joel

---

### Post by cj13579 on 2016-11-29
Yep, the name of the file is pretty important with this stuff.

If you rename "index.php.orig" to index.php then your WordPress installation should bounce back to life when you hit [http://localhost](http://localhost) again.

If the issue is fixed, best to mark the thread as solved. Used the link in Slickymaster's signature for destructions on how to do that.

---

### Post by joelrio on 2016-11-29
Ok I,ve got that. Thanks again sorry to be such a melon.

---

### Post by cj13579 on 2016-11-29
Not at all. Glad it's working now.

---

