---
title: "403 Forbidden - No access to /."
date: 2016-07-09
forum: Server Platforms
---

### Post by nurgie3 on 2016-07-09
Hey.
I've been trying to solve this for ages. I've seen things like "allow www-data to the folder and root", and "add permissions to the folders from root" and "change [those two lines in the VirtualHosts file] to 'Require all granted'". I've done all that. I've restarted apache, and...

Nothing. Still get the error. Generic 403 Forbidden. Here are all of the relevant files and permissions (I hope.)
My thinking is that somebody here will be able to spot what I've done wrong. This is really aggravating.

Okay, here we go:
This is the custom file in "/etc/apache2/sites-available/", named "graysite.conf".
```

<VirtualHost *:8080>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName anter-gerang.org
        ServerAlias 192.168.1.50

        ServerAdmin webmaster@localhost
        DocumentRoot /mnt/smb/website
        <Directory /mnt/smb/website/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Require all granted
        </Directory>

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
I have done a2ensite on this file, and en2dissite on 000-default, in the same folder as the file above.

This is the main Apache2 configuration file, apache2.conf
```
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
I've cut down the whitespace in this, for compaction of the post.

Here is the .htaccess file, in the /mnt/smb/website folder.
```
Allow all granted
```

Here are a few results of "sudo ls -l /mnt/smb/*".
 > sudo ls -l /mnt/smb/
```

total 28
drwxr-sr-x 2 rtzi     users     4096 Jul  8 16:48 JOAT
drwxr-sr-x 4 rtzi     users     4096 Jun 13 18:21 MC Servers
drwxr-sr-x 2 rtzi     users    12288 Jun  3 16:37 Music
-rwxr-xr-x 1 rtzi     users        0 Jul  8 16:33 test
-rwxr-xr-x 1 rtzi     users      114 May 31 15:25 USTVNow.html
drwxr-sr-x 7 www-data www-data  4096 Jul  9 19:34 website

```
 > sudo ls -l /mnt/smb/website/
```

total 24
drwxr-sr-x  2 www-data www-data 4096 Jun 12 15:01 css
drwxr-sr-x  2 www-data www-data 4096 Jun 12 17:59 downloads
drwxr-sr-x  2 www-data www-data 4096 Jun 12 15:01 fonts
drwxr-sr-x  2 www-data www-data 4096 Jun 12 17:29 images
-rwxr-xr-x+ 1 www-data www-data 4056 Jun 12 17:29 index.html
drwxr-sr-x  2 www-data www-data 4096 Jun 12 15:01 js

```

I cannot think of anything else. If anyone needs more command results, I'll happily post them.

Thanks in advance.

---

### Post by spjackson on 2016-07-09
Welcome to the forums.

Have you checked what is in the error.log?

What are the permissions on /mnt/smb (and /mnt)? www-data needs at least execute permission on these folders.

---

### Post by Doug S on 2016-07-09
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=2263268") thread. In particular, [this]("http://ubuntuforums.org/showthread.php?t=2263268&p=13219014#post13219014") post.

---

### Post by nurgie3 on 2016-07-15
> Have you checked what is in the error.log?
The error.log file in /var/log/apache2 says:
```
[Fri Jul 15 19:54:16.522369 2016] [authz_core:error] [pid 1253:tid 140225728034560] [client ::1:46536] AH01630: client denied by server configuration: /var/www/html/
```
This is quite strange, I a2dissite-d 000-default, and nothing is pointing towards /var/www/html anymore.

> What are the permissions on /mnt/smb?
sudo ls -l /mnt/:
```
drwxr-xr-x 2 root root 4096 Jul  8 16:54 smb
```

Hm.

> Have a look at [this]("http://ubuntuforums.org/showthread.php?t=2263268") thread. In particular, [this]("http://ubuntuforums.org/showthread.php?t=2263268&p=13219014#post13219014") post.
Adding the Directory directive to the Apache2 main file had no effect.

Thanks for the suggestions. 

Also, bump.

---

