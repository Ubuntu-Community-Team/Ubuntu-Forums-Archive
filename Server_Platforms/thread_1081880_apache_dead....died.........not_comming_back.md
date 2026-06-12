---
title: "apache dead....died.........not comming back"
date: 2009-02-27
forum: Server Platforms
---

### Post by danastasio on 2009-02-27
my problem lies (currently) with apache2. i tried my hand at hosting my own website. and for a little while i suceeded valiently. i followed the how to at howtoforge (perfect server ubuntu 8.10). well earlier today, i upgraded to ISPConfig from webmin. all was well. i didnt like ispconfig (couldnt figure it out...confusing) so i tried to remove it (yay problems!). the uninstall script failed, and i ended up just removing /home/admispconfig and /root/ispconfig. and re-installed webmin from the .deb file. now i cant access my webpage. neither internally or externally. localhost in FF on my server does nothing (its a tecra M2 and cant actually run the server version XD ) but i can SSH into the box and FTP files into and out of it. is it webmin? did i do something wrong from ispconfig? i know cox blocks port 80 so i have (i think) apache configed to use port 90 (i did before) and i have webforwarding set up with zoneedit to port 90. but nothing will let me view this page. and its rather important as its my home page for my (almost) brand spanking new business . anyone have any info/help?

---

### Post by volkswagner on 2009-02-27
Do you get any errors if you restart apache2?

```
sudo /etc/init.d/apache2 force-reload
```

Check your logs and post any errors.

```
cat /var/log/apache2/access.log
``` 

```
cat /var/log/apache2/error.log
```

Are your web sites enabled?

```
ls /etc/apache2/sites-enabled
```

Are you sure apache is listening on port 90?

```
cat /etc/apache2/ports.conf
```

---

### Post by danastasio on 2009-02-27
> **volkswagner said:**
> Do you get any errors if you restart apache2?

```
sudo /etc/init.d/apache2 force-reload
```

Check your logs and post any errors.

```
cat /var/log/apache2/access.log
``` 

```
cat /var/log/apache2/error.log
```

Are your web sites enabled?

```
ls /etc/apache2/sites-enabled
```

Are you sure apache is listening on port 90?

```
cat /etc/apache2/ports.conf
```

nope no errors when i restart apache2
i dont really know what im looking for in the logs so heres tail
```
dave-laptop.local - - [26/Feb/2009:10:58:05 -0500] "GET /home/danastasio/logo.jpeg HTTP/1.1" 404 334 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:08 -0500] "GET / HTTP/1.1" 200 779 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:08 -0500] "GET /home/danastasio/logo.jpeg HTTP/1.1" 404 334 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:11 -0500] "GET / HTTP/1.1" 200 779 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:11 -0500] "GET /home/danastasio/logo.jpeg HTTP/1.1" 404 334 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:13 -0500] "GET / HTTP/1.1" 200 779 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:13 -0500] "GET /home/danastasio/logo.jpeg HTTP/1.1" 404 334 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:14 -0500] "GET / HTTP/1.1" 200 779 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
dave-laptop.local - - [26/Feb/2009:10:58:14 -0500] "GET /home/danastasio/logo.jpeg HTTP/1.1" 404 334 "http://192.168.2.3:90/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6"
208.99.222.118 - - [26/Feb/2009:12:03:13 -0500] "GET / HTTP/1.1" 200 779 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

```
and errors.log, same thing, its tail
```
unable to start piped log program '/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d': No such file or directory
Unable to open logs
unable to start piped log program '/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d': No such file or directory
Unable to open logs
unable to start piped log program '/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d': No such file or directory
Unable to open logs
unable to start piped log program '/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d': No such file or directory
Unable to open logs
unable to start piped log program '/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d': No such file or directory
Unable to open logs

```
yup it is enabled
```
000-default  gelenecomputers.com.conf  webmin.1235712723.conf

```

and im positive that its listening on port 90
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

#NameVirtualHost *:90
Listen *:90

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
Listen *:90
</IfModule>

```

what should i do/any ideas from this?:confused:

---

### Post by volkswagner on 2009-02-27
From the error log, it appears ISPconfig is still interfering.

How was the following host created, webmin, ispconfig, by hand?

gelenecomputers.com.conf

You may want to simplify things.  first disable all but default and restart apache, than see if it changes things.

```
sudo a2dissite gelenecomputers.com.conf
```

```
sudo a2dissite webmin.1235712723.conf
```

```
sudo /etc/init.d/apache2 reload
```

If you get lucky and apache works with the default, than disable default and try one of the other hosts.  You may want to post the host config files.

---

### Post by danastasio on 2009-02-27
disabling those didnt do anything, but now when i restart apache i get this:


```
danastasio@www:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Fri Feb 27 12:52:13 2009] [warn] NameVirtualHost 192.168.2.3:90 has no VirtualHosts
[Fri Feb 27 12:52:13 2009] [warn] NameVirtualHost 169.254.6.170:90 has no VirtualHosts
[Fri Feb 27 12:52:13 2009] [warn] NameVirtualHost 192.168.2.3:90 has no VirtualHosts
[Fri Feb 27 12:52:13 2009] [warn] NameVirtualHost 169.254.6.170:90 has no VirtualHosts
                                                                         [fail]
danastasio@www:~$ 


```

which is why i made the virtual sites to begin with. ISPConfig kept yelling at me that they didnt exist and that apache couldnt run. im not sure where webmin came from. probably webmin though :lolflag:

---

### Post by volkswagner on 2009-02-27
Can you post your config files?

/etc/apache2/apache2.conf
/etc/apache2/httpd.conf

Do you have anything in
```
ls -alt /etc/apache2/conf.d
```

---

### Post by danastasio on 2009-02-27
> **volkswagner said:**
> Can you post your config files?

/etc/apache2/apache2.conf
/etc/apache2/httpd.conf

Do you have anything in
```
ls -alt /etc/apache2/conf.d
```


apache2.conf
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
TimeOut 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive on

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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
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
HostnameLookups On

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
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/







<Directory /var/www/sharedip>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

###############ispconfig_log###############
LogFormat "%v||||%b||||%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined_ispconfig
CustomLog "|/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d" combined_ispconfig

<Directory /var/www/*/web>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

<Directory /var/www/*/user/*/web>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>#
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
TimeOut 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive on

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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
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
HostnameLookups On

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
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/







<Directory /var/www/sharedip>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

###############ispconfig_log###############
LogFormat "%v||||%b||||%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined_ispconfig
CustomLog "|/root/ispconfig/cronolog --symlink=/var/log/httpd/ispconfig_access_log /var/log/httpd/ispconfig_access_log_%Y_%m_%d" combined_ispconfig

<Directory /var/www/*/web>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

<Directory /var/www/*/user/*/web>
    Options +Includes -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

<Directory /var/www/*/cgi-bin>
    Options ExecCGI -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

Include /etc/apache2/vhosts/Vhosts_ispconfig.conf


</Directory>

<Directory /var/www/*/cgi-bin>
    Options ExecCGI -Indexes
    AllowOverride None
    AllowOverride Indexes AuthConfig Limit FileInfo
    Order allow,deny
    Allow from all
    <Files ~ "^\.ht">
    Deny from all
    </Files>
</Directory>

Include /etc/apache2/vhosts/Vhosts_ispconfig.conf


```

httpd.conf
is completely empty

/etc/apache2/conf.d
```
total 20
drwxr-xr-x 2 root root 4096 2009-02-27 00:32 .
drwxr-xr-x 8 root root 4096 2009-02-27 00:32 ..
lrwxrwxrwx 1 root root   28 2009-02-18 10:47 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root root  237 2008-09-19 09:46 apache2-doc
-rw-r--r-- 1 root root  269 2008-09-19 09:41 charset
-rw-r--r-- 1 root root 1464 2008-09-19 09:41 security

```

and dude, your awesome, how do i give you a heap load of ubuntu?

---

### Post by volkswagner on 2009-02-27
******EDIT*****
I just re-read your original post.  It seems you are trying to access your remote server on your laptop.  You don't want to enter localhost, that would imply the machine you are on.

You should enter [http://xxx.xxx.xxx](http://xxx.xxx.xxx)  Substitute the ipaddress of your server.  You can find it by running

```
ifconfig
```

Correct me if I am wrong.

*******end edit*****

I am no expert so I help where I think I can, a leave the more complex to those with more exerience.  "I have been there", and may be there tomorrow.

As you can see apache2.conf has a lot left over from ISPconfig.

Your file still differs from mine a little. IE: You have hostname lookups=on.

What I would like to try is simple backup your apache2.conf.  Than copy mine (or search for a default to use) to create a new one.  Then enable the default site and reload apache.

Create backup.
```
 sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.feb27

```

Edit/create new apache2.conf

```
sudo nano /etc/apache2/apache2.conf.new
```

Copy and paste my file contents to the new file.

Make the new file active

```
sudo cp /etc/apache2/apache2.conf.new /etc/apache2/apache2.conf
```
  

Enable default site and restart apache.

---

### Post by danastasio on 2009-02-27
im sorry if i didnt make it clear earlier
im trying to access localhost from my server, its an old tecra M2 with a pentium m processor that is actually incapable of running any version of ubuntu server, so its got desktop in text only mode with a few mods. when i need to test things like this i:
```
sudo /etc/init.d/gdm start
```
but you are right, ISPConfig did leave alot, i will try that and report back
thanks!
:popcorn:

---

### Post by danastasio on 2009-02-27
yeah really your amazing. it works now \\:D/ \\:D/
i could never repay you enough. thank you so very much

---

