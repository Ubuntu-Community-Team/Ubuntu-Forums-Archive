---
title: "Apache making Firefox Loop when loading page, maybe because of https redirect?"
date: 2016-09-19
forum: Server Platforms
---

### Post by Robert_Boutin on 2016-09-19
Hello,

I built a server according to Perfect Server instructions (Ubuntu 16.04 Server,  Apache 2.4.18).

I added Let's Encrypt for mail.example.com and forced https for all connections.

My DNS record for mail.example.com correctly resolves to XXX.XXX.XXX.XXX

When I type mail.example.com into IE11, I get [https://mail.example.com](https://mail.example.com) and the Apache default page.

However, when I type mail.example.com into Firefox I get:

[https://mail.example.com/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/](https://mail.example.com/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/)

And the following error:
[SIZE=5]**Forbidden**[/SIZE]

 You don't have permission to access   /roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/  on  this server.

 [HR][/HR] *Apache/2.4.18 (Ubuntu) Server at mail.example.com Port 443*

Typing the ip address directly into the Firefox address bar gives me the Apache default page.

Now my actual goal is to eventually get mail.example.com to redirect to  [https://mail.example.com/roundcube](https://mail.example.com/roundcube), however I'm thinking I need to  address the Firefox issue first.  I've tried searching but I can't  locate something that mirrors my problem (or maybe my search skills  suck, could be).

Can anyone explain why in Firefox I keep getting   /roundcube/roundcube/... and how to possibly fix it so I at least get  the default Apache page?  And any help on redirecting all traffic to   [https://mail.example.com/roundcube](https://mail.example.com/roundcube) would be massively appreciated as  I've had to  restore my mailserver snapshot about 20 times trying  different solutions  I googled.  BTW, everything I described is _after_ going back to  the previous working state, I'm nearly certain I didn't manually change  these files up to that point.

As always, thanks!

The uncommented content of **000-default.conf** in sites-enabled is:

```
<VirtualHost *:80>
        
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

RewriteEngine on
RewriteCond %{SERVER_NAME} =mail.example.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,QSA,R=permanent]
</VirtualHost>

The uncommented content of **000-default-le-ssl.conf** in sites-enabled is:

<IfModule mod_ssl.c>
<VirtualHost *:443>

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

SSLCertificateFile /etc/letsencrypt/live/mail.example.com/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/mail.example.com/privkey.pem
Include /etc/letsencrypt/options-ssl-apache.conf
ServerName mail.example.com
</VirtualHost>

</IfModule>
```


**apache2.conf** follows (sorry it's the entire file): 
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
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
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
IncludeOptional sites-enabled/
```

---

### Post by denter2 on 2016-09-20
> **Robert_Boutin said:**
> You don't have permission to access   /roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/  on  this server.
there seems to be something in your server config that creates some sort of recursive redirection, resulting in this nonsense link.
that's what i'd concentrate on first, before sorting out IE vs FireFox problems.

---

### Post by Habitual on 2016-09-20
on this perfect server, 
```
RewriteEngine On
RewriteLog "/var/log/apache2/rewrite.log"
RewriteLogLevel 3
``` in either an .htaccess if so enabled or the /etc/apache2/sites-enabled/site.conf

restart apache2 
```
service apache2 graceful
``` or systemd-smth, IDK that thing. :(
```
tail -f /var/log/apache2/rewrite.log
```
ctrl+c gets out of the tail.

Open your browser and navigate there, when you get there, Hold shift on your keyboard and click Firefox's Reload button.
This forces fresh cache refreshed from the server, and not the browser cache.

---

### Post by Robert_Boutin on 2016-09-25
I changed my 000-default.conf file to add the lines above, but in turn got this error:

[EMAIL="root@mail:/etc/apache2/sites-enabled"]root@mail:/etc/apache2/sites-enabled[/EMAIL]# service apache2 graceful
 * Reloading Apache httpd web server apache2                                     *
 * The apache2 configtest failed. Not doing anything.
Output of config test was:
AH00526: Syntax error on line 4 of /etc/apache2/sites-enabled/000-default.conf:
Invalid command 'RewriteLog', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.

Here is my Apache error.log file:

[Sun Sep 25 06:25:41.381410 2016] [auth_digest:notice] [pid 2794] AH01757: generating secret for digest authentication ...
[Sun Sep 25 06:25:41.445501 2016] [:notice] [pid 1696] FastCGI: process manager initialized (pid 1696)
[Sun Sep 25 06:25:42.918868 2016] [:error] [pid 2794] python_init: Python version mismatch, expected '2.7.6', found '2.7.12'.
[Sun Sep 25 06:25:42.998563 2016] [:error] [pid 2794] python_init: Python executable found '/usr/bin/python'.
[Sun Sep 25 06:25:42.998619 2016] [:error] [pid 2794] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-x86_64-linux-gnu:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Sun Sep 25 06:25:42.998661 2016] [:notice] [pid 2794] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sun Sep 25 06:25:42.998687 2016] [:notice] [pid 2794] mod_python: using mutex_directory /tmp
[Sun Sep 25 06:25:44.846224 2016] [ssl:warn] [pid 2794] AH01906: mail.example.com:8080:0 server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sun Sep 25 06:25:44.847103 2016] [ssl:error] [pid 2794] AH02217: ssl_stapling_init_cert: can't retrieve issuer certificate! [Details about my certificate]
[Sun Sep 25 06:25:44.847133 2016] [ssl:error] [pid 2794] AH02604: Unable to configure certificate mail.example.com:8080:0 for stapling
[Sun Sep 25 06:25:44.985358 2016] [mpm_prefork:notice] [pid 2794] AH00163: Apache/2.4.18 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 mod_fcgid/2.3.9 mod_python/3.3.1 Python/2.7.12 OpenSSL/1.0.2g configured -- resuming normal operations
[Sun Sep 25 06:25:44.985412 2016] [core:notice] [pid 2794] AH00094: Command line: '/usr/sbin/apache2'
[Sun Sep 25 06:25:48.025079 2016] [mpm_prefork:warn] [pid 2794] AH00167: long lost child came home! (pid 13479)

One thing I should have mentioned earlier.  I have Virtualbox set up with two virtual servers.  One is my mailserver with public static ip XXX.XXX.XXX.XXX.  The other is my webserver that actually hosts example.com, with public static ip XXX.XXX.XXX.XXX+1.  So I have two A-records.  One points example.com to the webserver.  The other points mail.example.com to the mailserver.  I don't know if this makes a difference but in hindsight I think I should have pointed it out.

Thanks for your help.

---

### Post by SeijiSensei on 2016-09-25
If you just want to force redirection of http requests to https, don't use a rewrite rule.  Just use a Redirect like this:
```

<VirtualHost *:80>
ServerName mail.example.com
Redirect / https://mail.example.com/roundcube/
</VirtualHost>

<VirtualHost *:443>
ServerName mail.example.com
[etc.]
</VirtualHost>

```
If this machine is only going to be hosting Roundcube, I'd just point the DocumentRoot directly to the Roundcube directory.

---

### Post by Robert_Boutin on 2016-09-25
Thanks! Making progress...  Works perfectly in IE, but still gives the same error in Firefox.

[h=1]Forbidden[/h]
You don't have permission to access 
/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/roundcube/
on
 this server.



[HR][/HR]
Apache/2.4.18 (Ubuntu) Server at mail.XXXXX.com Port 443

---

### Post by SeijiSensei on 2016-09-25
Have you cleared the cache in Firefox?  If so, give that a try.  There really shouldn't be any difference between the browsers.

---

### Post by Robert_Boutin on 2016-09-26
That was it, thanks!!

---

