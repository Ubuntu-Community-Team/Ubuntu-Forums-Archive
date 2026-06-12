---
title: "Webpage w/HTTP on Apache w/Ubuntu 16.04.1 sometimes accessible then not"
date: 2017-07-09
forum: Server Platforms
---

### Post by lukeborg on 2017-07-09
Hi,

I am having problems accessing the website hosted on my server from outside my network (Internal network works fine) , sometimes my webpage is accessible from the outside then after a while it stops being accessible I am not understanding the issue here.

I am hosting a server from home with:

Ubuntu 16.04
Apache/2.4.18
PHP 7
Have successfully forwarded port 80 as can be seen on canyouseeme.org
I can SSH to the webserver at any time and it works without a problem
I turned off my UFW and still it doesn't allow access to the website from outside until all of a sudden it does and then it stops working again.

I have edit my ports.conf:

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 0.0.0.0:80

<IfModule ssl_module>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


and have edited apache2.conf:

```
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
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
    AllowOverride All
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

#<Directory /srv/>
#    Options Indexes FollowSymLinks
#    AllowOverride All
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

ServerName 77.71.242.95
```

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I am not understanding the issue. Sometimes the website is accessible from the outside then all of a sudden it stops , and the server is still on just idle with no changes made to it. 
I'd appreciate any insight you might have. If you need any more information please ask.
PS: I am not so experienced with Ubuntu so I appreciate every detail given. Thanks

---

### Post by Habitual on 2017-07-09
> **lukeborg said:**
> I am hosting a server from home with:
First place I'd check is with your ISP. They may not allow "servers" and/or block port 80.

---

### Post by lukeborg on 2017-07-09
Hi, thanks for your reply.

No that's not the case, as port 80 is open because I checked on canyouseeme.org and further to that the website is sometimes accessible like I stated, I asked a couple of friends to enter my public IP in their browser's URL and they had access to it. The problem is that it randomly goes offline again after 2 minutes of being up and I'm sure that I didn't do any changes and when I SSH to the server it always works. I used netstat -lntp and port 80 is being listened to. Any ideas? Thanks again

---

### Post by Habitual on 2017-07-10
This, I think, may be an issue, seems incorrect.
> ServerName 77.71.242.95 in /etc/apache2/apache2.conf
Stands out.

I recognize its directive and I think it was meant to suppress
Apache error &#8220;Could not reliably determine the server's fully qualified domain name&#8221;

If that was the case, 
I always fixed that using ```
 echo "ServerName localhost" >> /etc/apache2/apache2.conf
```
and I've used it for years, every where. 

Either way, yours stands out. *I don't know if that directive is correctly formatted.*
I have mine elsewhere, and I'm not using an IP
/etc/apache2/sites-enabled/000-default.conf
```
#NameVirtualHost *:80

<VirtualHost *:80>
        ServerName domain.com
```


I advise you remark and replace
> ServerName 77.71.242.95
with
> ServerName localhost in /etc/apache2/apache2.conf

This change should not affect any site you currently have.
After the edit, do a fre-flight check of the syntax using
```
sudo apache2ctl -t
```
followed by a restart using
```
sudo apache2ctl graceful
```

Watch the logs.

Wish I had more. Good Luck and have a Great Day!

---

### Post by lukeborg on 2017-07-10
Ok I will do that! Thanks a lot for your time and assistance!

---

### Post by Habitual on 2017-07-11
You are very welcome.
BTW: there are few reasons to edit /etc/apache2/apache2.conf 
in my experience.
This would be the one exception, In my experience.

---

