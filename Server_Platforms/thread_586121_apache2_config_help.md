---
title: "apache2 config help"
date: 2007-10-22
forum: Server Platforms
---

### Post by hcker2000 on 2007-10-22
Hey there I had an old install of apache2 working alright but I am having some issues getting it to work this time.

Here is my sites-available default file.

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin afakeemail@gmail.com
ServerName HNetInc.
DocumentRoot /var/www/html
	<Directory /var/www/html>
		Options FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/cgi-bin
	<Directory "/var/www/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

</VirtualHost>

```

---

### Post by notaloafer on 2007-10-22
Can you state any more detail on the problem that you are having?

-Eric

---

### Post by hcker2000 on 2007-10-22
After some playing around I got it working. 

Though now I need to remember which file i need to edit to change the index file names. 

by default it is index.html and i need to add index.htm

---

### Post by notaloafer on 2007-10-22
you're looking for:
DirectoryIndex

Mine is set as follows:
DirectoryIndex index.php index.html index.htm portal.html etc...... I don't feel like typing it all out =P

Regards
-Eric

---

### Post by hcker2000 on 2007-10-22
What file does the DirectoryIndex go in to be site wide?

---

### Post by MJN on 2007-10-22
**/etc/apache2/apache2.conf** - it'll be already in there so you just need to add to suit - remember order is important in case of multiple matches.
 
Mathew

---

### Post by hcker2000 on 2007-10-22
Well for some reason that was not in my apache2.conf file.

I added it but it is still not using my index.php file.

Here is my apache2.conf file.

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

DirectoryIndex index.htm index.php index.html

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
PidFile /var/run/apache2.pid

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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

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
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



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


```

---

### Post by MJN on 2007-10-23
What is actually the problem? Can you post the access and error logs, and the output of **ls -l** in whatever directory you're requesting?
 
Mathew

---

### Post by hcker2000 on 2007-10-23
Well I have a directory for my image gallery script.

There is an index.php inside /var/www/html/Images/Gallery/singapore/

When I browse to to [www.mydomain.com/Images/Gallery/singapore/](www.mydomain.com/Images/Gallery/singapore/) it gives a 403 error.

When i browse to [www.mydomain.com/Images/Gallery/singapore/index.php](www.mydomain.com/Images/Gallery/singapore/index.php) it shows my gallery like it should.

just curious but should there be a /etc/apache2/apache2/ directory?

Here is the ls -l

```

root@hcker2000t1:/var/www/html/Images/Gallery/singapore# ls -l
total 64
-rw-r--r--  1 hcker2000 root 1113 2007-10-21 00:28 admin.php
drwxrwxrwx  2 hcker2000 root 4096 2007-10-21 00:28 data
drwxr-xr-x  2 hcker2000 root 4096 2007-10-21 00:28 docs
-rw-r--r--  1 hcker2000 root 2046 2007-10-21 00:28 external.php
drwxrwxrwx 13 hcker2000 root 4096 2007-10-21 00:28 galleries
drwxr-xr-x  2 hcker2000 root 4096 2007-10-21 00:28 includes
-rw-r--r--  1 hcker2000 root 1039 2007-10-21 00:28 index.php
drwxr-xr-x  2 hcker2000 root 4096 2007-10-21 00:28 install
drwxr-xr-x  2 hcker2000 root 4096 2007-10-21 00:28 locale
-rw-r--r--  1 hcker2000 root 1312 2007-10-21 00:28 Readme.txt
-rw-r--r--  1 hcker2000 root  464 2007-10-21 00:28 secret.ini.php
-rw-r--r--  1 hcker2000 root 9360 2007-10-22 00:13 singapore.ini
drwxr-xr-x  7 hcker2000 root 4096 2007-10-21 00:28 templates
drwxr-xr-x  2 hcker2000 root 4096 2007-10-21 00:28 tools

```

---

### Post by MJN on 2007-10-23
What does your error log say?
 
It seems to me more like a permissions issue - particularly relating to the permissions of the parent directories - are they all set to be world readable/executable? Unless they are owned by www-data in which case only www-data needs read/execute access to the directory tree.
 
(And, no, by default you shouldn't have an apache2 directory inside /etc/apache2 - unless of course you've created it)
 
Mathew

---

### Post by hcker2000 on 2007-10-23
Where is the error log for apache2?

---

### Post by conjur3r on 2007-10-23
Did you restart apache after making that change to the DirectoryIndex?  This is important!

The error log should be /var/log/apache2/error.log

---

### Post by hcker2000 on 2007-10-23
I sure did. /etc/init.d/apache2 restart

Thanks I will take a look at the log file as soon as I get up.

---

### Post by hcker2000 on 2007-10-23
Ok here is my error log.

```

[Mon Oct 22 23:11:12 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/
[Mon Oct 22 23:11:14 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/
[Mon Oct 22 23:11:14 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/
[Mon Oct 22 23:11:16 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/
[Mon Oct 22 23:35:30 2007] [error] [client 61.247.217.33] File does not exist: /var/www/html/robots.txt
[Mon Oct 22 23:46:46 2007] [error] [client 193.47.80.49] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 00:19:01 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/
[Tue Oct 23 00:19:23 2007] [error] [client 74.6.28.118] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 00:19:53 2007] [error] [client 76.181.84.178] Directory index forbidden by Options directive: /var/www/html/Images/Gallery/singapore/, referer: http://ww1.hnetinc.com:82/menu.htm
[Tue Oct 23 01:42:23 2007] [error] [client 74.6.29.40] Directory index forbidden by Options directive: /var/www/html/UserSites/onsitedj/
[Tue Oct 23 03:07:41 2007] [error] [client 65.55.210.80] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 03:31:59 2007] [error] [client 66.249.70.238] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 03:43:02 2007] [error] [client 66.249.70.238] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 06:49:20 2007] [error] [client 65.55.210.72] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 08:45:47 2007] [error] [client 74.6.28.118] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 08:58:47 2007] [error] [client 68.142.212.203] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 13:24:56 2007] [error] [client 131.107.151.157] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 13:24:56 2007] [error] [client 131.107.151.157] script '/var/www/html/Images/Gallery/picture.php' not found or unable to stat
[Tue Oct 23 16:24:33 2007] [error] [client 74.6.28.118] File does not exist: /var/www/html/robots.txt
[Tue Oct 23 16:24:33 2007] [error] [client 74.6.24.112] script '/var/www/html/Images/Gallery/picture.php' not found or unable to stat
[Tue Oct 23 17:14:21 2007] [error] [client 76.181.74.80] Directory index forbidden by Options directive: /var/www/html/UserSites/onsitedj/, referer: http://www.onsitedj.com/
[Tue Oct 23 17:19:04 2007] [error] [client 76.181.74.80] Directory index forbidden by Options directive: /var/www/html/UserSites/onsitedj/, referer: http://www.onsitedj.com/
[Tue Oct 23 17:44:15 2007] [error] [client 74.6.25.78] script '/var/www/html/Images/Gallery/picture.php' not found or unable to stat
[Tue Oct 23 18:47:52 2007] [error] [client 74.6.28.36] script '/var/www/html/Images/Gallery/picture.php' not found or unable to stat

```

---

### Post by hcker2000 on 2007-10-23
Well after I deleted the /etc/apache2/apache2/ directory and went back into webmin and set it to accept index.php I got it working so all is good now. Thanks a lot for every ones help getting this up and working.

---

