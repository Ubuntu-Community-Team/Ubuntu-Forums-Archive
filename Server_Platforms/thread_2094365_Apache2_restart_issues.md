---
title: "Apache2 restart issues"
date: 2012-12-13
forum: Server Platforms
---

### Post by harishvarada on 2012-12-13
I unfortunately installed some apache2 plugins

```
sudo apt-get install apache2-mpm-worker
sudo apt-get install libapache2-mod-fastcgi php5-fpm php5
sudo a2enmod actions fastcgi alias
```

From that time, I my apache was not able to recognize .htaccess files properly.

Hence, I tried uninstalling the above installed once.

Since then, I couldn't even restart my apache server and run any php project :mad:

Here is the error when i try restarting my apache2 server:
```
Syntax error on line 16 of /etc/apache2/sites-enabled/000-default:
Invalid command 'ScriptAlias', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
```

Here is my /etc/apache2/apache2.conf file:
```
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives and /usr/share/doc/apache2-common/README.Debian.gz about
# Debian specific hints.
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
#	/etc/apache2/
#	|-- apache2.conf
#	|	`--  ports.conf
#	|-- mods-enabled
#	|	|-- *.load
#	|	`-- *.conf
#	|-- conf.d
#	|	`-- *
# 	`-- sites-enabled
#	 	`-- *
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
#   In order to avoid conflicts with backup files, the Include directive is
#   adapted to ignore files that:
#   - do not begin with a letter or number
#   - contain a character that is neither letter nor number nor _-.
#   - contain .dpkg
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections, and which
#   of these ports are used for name based virtual hosts.
#
# * Configuration files in the mods-enabled/ and sites-enabled/ directories
#   contain particular configuration snippets which manage modules or virtual
#   host configurations, respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite. See
#   their respective man pages for detailed information.
#
# * Configuration files in the conf.d directory are either provided by other
#   packages or may be added by the local administrator. Local additions
#   should start with local- or end with .local or .local.conf to avoid name
#   clashes. All files in conf.d are included 
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
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include list of ports to listen on and which to use for name based vhosts
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
# see the comments above for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

# Include Phpmyadmin
Include /etc/phpmyadmin/apache.conf
```

Here is my /etc/apache2/sites-enabled/000-default file:
```
<VirtualHost *:80>
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
```

I'm completely stuck now. Please help me on this.

Best Regards,
Harish.V

---

### Post by anonymouschief on 2012-12-13
What does the apache log say?

---

### Post by harishvarada on 2012-12-14
Latest Apache error log shows nothing.
Here is my error.log.1 file, hope which has some data:
```
[Tue Dec 04 10:35:43 2012] [notice] FastCGI: process manager initialized (pid 5821)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Tue Dec 04 10:35:43 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Tue Dec 04 12:50:31 2012] [notice] FastCGI: process manager initialized (pid 1392)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Tue Dec 04 12:50:31 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Tue Dec 04 17:26:11 2012] [alert] [client 127.0.0.1] /var/www/sampledotnet/.htaccess: Invalid command 'Show', perhaps misspelled or defined by a module not included in the server configuration
[Tue Dec 04 19:34:02 2012] [notice] caught SIGTERM, shutting down
[Tue Dec 04 19:35:00 2012] [notice] FastCGI: process manager initialized (pid 1393)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Tue Dec 04 19:35:00 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Tue Dec 04 21:50:38 2012] [notice] caught SIGTERM, shutting down
[Tue Dec 04 22:34:27 2012] [notice] FastCGI: process manager initialized (pid 1397)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Tue Dec 04 22:34:27 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Wed Dec 05 02:16:53 2012] [notice] caught SIGTERM, shutting down
[Wed Dec 05 10:53:42 2012] [notice] FastCGI: process manager initialized (pid 1383)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Wed Dec 05 10:53:42 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Wed Dec 05 18:08:37 2012] [notice] caught SIGTERM, shutting down
[Wed Dec 05 19:20:23 2012] [notice] FastCGI: process manager initialized (pid 1357)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Wed Dec 05 19:20:23 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Wed Dec 05 19:22:15 2012] [notice] caught SIGTERM, shutting down
[Wed Dec 05 20:31:27 2012] [notice] FastCGI: process manager initialized (pid 1386)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Wed Dec 05 20:31:27 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Thu Dec 06 02:41:30 2012] [notice] caught SIGTERM, shutting down
[Thu Dec 06 09:19:28 2012] [notice] FastCGI: process manager initialized (pid 1572)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Thu Dec 06 09:19:29 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Thu Dec 06 09:33:42 2012] [notice] caught SIGTERM, shutting down
[Thu Dec 06 10:38:34 2012] [notice] FastCGI: process manager initialized (pid 1281)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Thu Dec 06 10:38:34 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Thu Dec 06 14:40:38 2012] [notice] caught SIGTERM, shutting down
[Thu Dec 06 14:41:36 2012] [notice] FastCGI: process manager initialized (pid 1259)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Thu Dec 06 14:41:36 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Thu Dec 06 22:57:49 2012] [notice] caught SIGTERM, shutting down
[Fri Dec 07 11:59:15 2012] [notice] FastCGI: process manager initialized (pid 1341)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Fri Dec 07 11:59:15 2012] [notice] Apache/2.2.22 (Ubuntu) mod_fastcgi/mod_fastcgi-SNAP-0910052141 PHP/5.4.6-1ubuntu1.1 configured -- resuming normal operations
[Fri Dec 07 15:05:04 2012] [notice] caught SIGTERM, shutting down
```

---

### Post by volkswagner on 2012-12-15
> **harishvarada said:**
> I unfortunately installed some apache2 plugins

```
sudo apt-get install apache2-mpm-worker
sudo apt-get install libapache2-mod-fastcgi php5-fpm php5
sudo a2enmod actions fastcgi alias
```

From that time, I my apache was not able to recognize .htaccess files properly.

Hence, I tried uninstalling the above installed once.

...

Best Regards,
Harish.V

You say you uninstalled all the above... did you disable alias?  You will need to enable it if you did as it is needed for ScriptAlias to work as [per apache2 docs]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html").

---

### Post by harishvarada on 2012-12-15
Hello,

As suggested, I also tried disabling the activated alias using following command:
```
harish@harish-Ideapad-Z460:~$ sudo a2dismod actions fastcgi alias
[sudo] password for harish: 
Module actions disabled.
Module fastcgi already disabled
Module alias already disabled
```

After that, I tried reloading and restarting apache:
```
harish@harish-Ideapad-Z460:~$ sudo service apache2 reload 
 * Reloading web server config                                                                                                             [ OK ] 
harish@harish-Ideapad-Z460:~$ sudo service apache2 restart 
Syntax error on line 16 of /etc/apache2/sites-enabled/000-default:
Invalid command 'ScriptAlias', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
```

Even now, error.log has nothing and my Apache restart failed. Please advice.

---

### Post by volkswagner on 2012-12-15
I see, but I said you need to enable it.

```
sudo a2enmod alias
```

```
sudo service apache2 start
```

---

### Post by harishvarada on 2012-12-15
Hey volkswagner,

Thank you very much. My apache restart's now and could access my basic php files.

But, I still couldn't access my projects build in Codeigniter (all links say 404 error :-|) which I could access when I was using my Ubuntu 11.10. I'm facing this problem since I upgraded my PC from 11.10 to 12.10.

Also please suggest me resolving this..

Thanks in advance.

-Harish.V

---

### Post by harishvarada on 2012-12-15
Also, when I try restarting my apache, it says ```
sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                          [ OK ]
```

I googled and tried adding the line
```
ServerName localhost
```

in my
```
/etc/apache2/httpd.conf
```

Even still, the warning remains the same..

Is that creeping any issue for making my Codeigniter not working(I mean not reading my .htaccess file)..?

---

