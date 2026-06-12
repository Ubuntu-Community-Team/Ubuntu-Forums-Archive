---
title: "Apache2 403 Forbidden Error"
date: 2015-02-21
forum: Server Platforms
---

### Post by Justin_Pentecost on 2015-02-21
I'm sure I've made an elementry error.

I have installed a a LAMP server on on my local network.     The IP address is 192.168.1.71 and when put that into firefox on another machine on the network I get the Apache test page.      I have setup portforwarding to the this machine and DYNDNS thing .. The address for that is portablemotioncontrol.ddns.net.      When I try to log on from that either from my phone or another DSL connection I get .   
[ATTACH=CONFIG]260122[/ATTACH]

Everything else is stock out of the box .. I've changed a few settings from reading other peoples 403 errors but none seem the same as mine  ..  as their problems seem to be affect the local network as well as the outside world.     This is an "out of the box" ubuntu and apache setup so most of the files such as .htacess are not used (and the .conf file is configured to not be over irdden by them ..   

Obviously I'm missing something obvious but could someone point me in the direction of the correct bit of them RTFM to look at ?

Apache2 conf file

```

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
ServerRoot "/etc/apache2"

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

<Directory /var/www/html>
        Options Indexes FollowSymLinks
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

---

### Post by volkswagner on 2015-02-22
So you can navigate to the UI directory on LAN by no WAN?
[http://192.168.1.71/UI](http://192.168.1.71/UI) works?

Can you navigate to web root via WAN, ie: don't include the /UI?

---

### Post by Justin_Pentecost on 2015-02-22
Thankyou so much for replying !   So right now if you navigate to 192.168.1.71 it shows "Index of /" and the directory html/   My guess is that this is because I've been messing around with the settings in the apache2.conf file   ..  (if you try you can navigate around this until you find the index page.)  This is all on the LAN 

If you try and log on with portablemotioncontrol.ddns.net/ it goes to portablemotioncontrol.ddns.net/UI and then gives the Forbidden notice .. If you try /html/index.html at the end then it says not found .. 

This is on the WAN via my Phone ..

---

### Post by volkswagner on 2015-02-22
You must have some code causing rewrite or redirect.

---

### Post by pqwoerituytrueiwoq on 2015-02-22
what is in this file
/etc/apache2/sites-available/default
it may be 
/etc/apache2/sites-available/000-default
if not just look in that folder for a file
are you using a .htaccess file?

---

### Post by Doug S on 2015-02-22
Is there any useful information in the log files? /var/log/apcahe2/access.log and error.log ? You mention an "out of the box" configuration, but it does a redirect to the "UI" subdirectory so I wonder if something is wrong with that.

Edit: I forgot to mention, you should see entries from 173.180.XXX.YYY

---

### Post by Justin_Pentecost on 2015-02-23
I can't thank you guys enough .. it now works I have NO idea why .. what i did was to install it all on another machine and then create the directory /UI and .. it works ..  Now I just have to try and install Wordpress .. So stand by for some of the strongest swearing available without prescription ..

---

