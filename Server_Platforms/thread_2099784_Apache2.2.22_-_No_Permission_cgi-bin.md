---
title: "Apache/2.2.22 - No Permission /cgi-bin/"
date: 2012-12-30
forum: Server Platforms
---

### Post by expensne on 2012-12-30
Hello,

after a long time struggling around with this problem, I decided to write a topic now. I read a lot of other topics related to this problem, but nothing helps me.

**I just tried to get a cgi/pl opened with Apache, here's what I did and what became of it:**

Opening:
[http://127.0.0.1/index.html](http://127.0.0.1/index.html)
No Problem!

Opening:
[http://127.0.0.1/ANY](http://127.0.0.1/ANY) OTHER FOLDER
No Problem!

BUT

Opening: 
[http://127.0.0.1/cgi-bin/](http://127.0.0.1/cgi-bin/)
Error: 
Forbidden
You don't have permission to access /cgi-bin/ on this server.

Opening:
[http://127.0.0.1/cgi-bin/hello.cgi](http://127.0.0.1/cgi-bin/hello.cgi)
Error:
Internal Server Error (500)

**Last few lines of the Apache2 Error.log:**

> [Sun Dec 30 20:14:56 2012] [notice] caught SIGTERM, shutting down
[Sun Dec 30 20:14:57 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Sun Dec 30 20:14:59 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:15:00 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:15:01 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:15:04 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:15:05 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:17 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:18 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:18 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:19 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:20 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:20 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:26:21 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:28:54 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:29:00 2012] [notice] caught SIGTERM, shutting down
[Sun Dec 30 20:29:01 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Sun Dec 30 20:29:05 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:29:06 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:29:07 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:29:45 2012] [error] [client 127.0.0.1] malformed header from script. Bad header=Hello World: hello.cgi
[Sun Dec 30 20:29:48 2012] [error] [client 127.0.0.1] malformed header from script. Bad header=Hello World: hello.cgi
[Sun Dec 30 20:29:50 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:29:52 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:30:05 2012] [error] [client 192.168.0.101] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:30:05 2012] [error] [client 192.168.0.101] File does not exist: /var/www/favicon.ico
[Sun Dec 30 20:30:18 2012] [error] [client 192.168.0.101] script not found or unable to stat: /var/www/cgi-bin/hello
[Sun Dec 30 20:30:18 2012] [error] [client 192.168.0.101] File does not exist: /var/www/favicon.ico
[Sun Dec 30 20:30:23 2012] [error] [client 192.168.0.101] malformed header from script. Bad header=Hello World: hello.cgi
[Sun Dec 30 20:30:23 2012] [error] [client 192.168.0.101] File does not exist: /var/www/favicon.ico
[Sun Dec 30 20:30:38 2012] [notice] SIGHUP received.  Attempting to restart
[Sun Dec 30 20:30:38 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Sun Dec 30 20:30:48 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:30:48 2012] [error] [client 127.0.0.1] attempt to invoke directory as script: /var/www/cgi-bin/
[Sun Dec 30 20:37:58 2012] [error] [client 127.0.0.1] malformed header from script. Bad header=Hello World: hello.cgi

**Apache2 sites-enabled > 000-default:**

> <VirtualHost *:80>
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

	ScriptAlias /cgi-bin/ /var/www/cgi-bin/
	<Directory /var/www/cgi-bin/>
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		allow from all
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

</VirtualHost>

**Apache2 sites-available > default:**
Btw: its the right folder, I got my files right in /var/www

> <VirtualHost *:80>
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

	ScriptAlias /cgi-bin/ /var/www/cgi-bin/
	<Directory /var/www/cgi-bin/>
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		allow from all
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

</VirtualHost>

**Apache2 httpd.conf:**

> ServerName localhost

**Apache2 apache2.conf:**

> #
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
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
# with "/", the value of ServerRoot is prepended -- so "foo.log"
# with ServerRoot set to "/etc/apache2" will be interpreted by the
# server as "/etc/apache2/foo.log".
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
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock

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
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
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
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
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
    allow from all
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
# It is also possible to omit any default MIME type and let the
# client's browser guess an appropriate action instead. Typically the
# browser will decide based on the file's extension then. In cases
# where no good assumption can be made, letting the default MIME type
# unset is suggested  instead of forcing the browser to accept
# incorrect  metadata.
#
DefaultType None


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
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

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

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

**And the Permissions (just tried to give 777):**

[IMG]http://i.imagebanana.com/img/i7xoc7qj/Unbenannt.jpg[/IMG]



I would really appreciate any help!
Mfg Fabian

---

