---
title: "Correct Owner and Permissions for public+html"
date: 2018-07-22
forum: Server Platforms
---

### Post by astarmathsandphysics on 2018-07-22
I destroyed the permissions on my entire filesystem with a syntax error (left a space before / at the end of chown command)  so reinstalled.
I am using this opportunity to solve some issues. I am running out of disk space on the operating system disk, so am using some rid disks for the website files.
I have created a symlink from /media/paul-smith/RAIDSYSTEM/public_html to /var/www which is working and I can see the files and folders.
Ownership is set to paul-smith:www-data and permissions to 644 on files 755 on folders.
Followsymlinks is set tp in /var/www
Allowoverrides is set to all

Whenever I try to test in localhost/astarmathsandphysics I get a 403 error.

Where am I going wrong?

---

### Post by TheFu on 2018-07-22
Can't tell from the provided information.  Facts are preferred. Run commands and show output please.
What are all the permissions from the top of /media down - each level is required.
What are the website configs? Which web server is being used?

Show your work and please,please, use "code tags."

---

### Post by astarmathsandphysics on 2018-07-22
owner and permissions are paul-smith:www-data and 644/755 all the way down.

apache2.conf

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
#	/etc/apache2/
#	|-- apache2.conf
#	|	`--  ports.conf
#	|-- mods-enabled
#	|	|-- *.load
#	|	`-- *.conf
#	|-- conf-enabled
#	|	`-- *.conf
# 	`-- sites-enabled
#	 	`-- *.conf
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


<Directory /usr/share/phpmyadmin>
	AllowOverride All
	Require all granted
</Directory>

<Directory /var/www/>
	Options -Indexes +FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>

#<Directory /srv/>
#	Options Indexes FollowSymLinks
#	AllowOverride None
#	Require all granted
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

ServerSignature Off
ServerTokens Prod
```

astarmathsandphysics.com.conf

```
<VirtualHost 192.168.0.21:80>
	ServerName astarmathsandphysics.com
	ServerAlias www.astarmathsandphysics.com
   Redirect permanent / https://astarmathsandphysics.com
</VirtualHost>
<VirtualHost 192.168.0.21:443>
SSLEngine      on
SSLCertificateFile        /etc/ssl/certs/astarmathsandphysics.com.pem
SSLCertificateKeyFile     /etc/ssl/private/astarmathsandphysics.com.key
Alias /awstatsclasses "/usr/share/awstats/lib/"
Alias /awstats-icon "/usr/share/awstats/icon/"
Alias /awstatscss "/usr/share/doc/awstats/examples/css"
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	ServerAdmin admin@astarmathsandphysics.com
	ServerName astarmathsandphysics.com
	ServerAlias www.astarmathsandphysics.com
	DocumentRoot /var/www/astarmathsandphysics
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/astarmathsandphysics/>
		Options ExecCGI Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin/">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

<IfModule mod_security2.c>
  SecRuleEngine Off
</IfModule>

	Errorlog /var/www/astarmathsandphysics_error_log
#	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/astarmathsandphysics.log combined

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

---

### Post by TheFu on 2018-07-22
Which Ubuntu version and Apache version?   The way that access is granted changed a few releases ago.
[https://httpd.apache.org/docs/2.4/upgrading.html](https://httpd.apache.org/docs/2.4/upgrading.html)   I suspect this is the issue.

I would just setup apache to point directly at
	DocumentRoot /var/www/astarmathsandphysics
to
/media/paul-smith/RAIDSYSTEM/public_html

But what you've done should work fine.

---

### Post by astarmathsandphysics on 2018-07-22
ubuntu 18.04
Apache/2.4.29

I am trying to configure for 8 websites.
The symlink works, still I get a 403 error

---

### Post by TheFu on 2018-07-22
> **astarmathsandphysics said:**
> I am trying to configure for 8 websites.
The symlink works, still I get a 403 error

Did you fix your apache 2.4 permissions problem?  The link I provided shows the vastly different way those must be configured.

18.04 is too new for me. Sorry.

---

### Post by astarmathsandphysics on 2018-07-22
There cannot be any differences in permissions between 16.04 and 18.04.
As far as I can see, the permissions are correct.
Owner is paul-smith and group is www-data right down the paths, and permissions are 644/755

---

### Post by astarmathsandphysics on 2018-07-22
While I was working through this problem I rea;lised the symlink would not survive a reboot without an entry in /etc/fstab for the source drive so that this would mount on boot.

---

### Post by TheFu on 2018-07-22
> **astarmathsandphysics said:**
> There cannot be any differences in permissions between 16.04 and 18.04.
As far as I can see, the permissions are correct.
Owner is paul-smith and group is www-data right down the paths, and permissions are 644/755
```

		AllowOverride All
		Order allow,deny
		allow from all
```

are incorrect for apache 2.4.  The link already provided says that and shows the correct settings.

/media is for automatically mounted storage of a temporary nature according to the file system hierarchy specs.  Permanent mounts belong elsewhere.   /mnt/ is for administrative, temporary, storage use, BTW.  

Much of Unix knowledge is knowing how to do things that have worked for prior generations of admins, because not doing that will lead to hardships.   Just because something works, that doesn't mean it is the best solution.

If you don't manually validate all the permissions, then don't assume *there cannot be any differences.*.  And don't ask others to believe the statement without proof. Everyone makes mistakes. Everyone.

---

### Post by astarmathsandphysics on 2018-07-23
Edited apache files for 2.4
403 error persists

---

### Post by astarmathsandphysics on 2018-07-23
Can load localhost/phpmyadmin

---

### Post by astarmathsandphysics on 2018-07-23
Here is apache2 configuration file for one of my websites

[HTML]<VirtualHost 192.168.0.21:80>
	ServerName astarmathsandphysics.com
	ServerAlias www.astarmathsandphysics.com
   Redirect permanent / https://astarmathsandphysics.com
</VirtualHost>
<VirtualHost 192.168.0.21:443>
SSLEngine      on
SSLCertificateFile        /etc/ssl/certs/astarmathsandphysics.com.pem
SSLCertificateKeyFile     /etc/ssl/private/astarmathsandphysics.com.key
Alias /awstatsclasses "/usr/share/awstats/lib/"
Alias /awstats-icon "/usr/share/awstats/icon/"
Alias /awstatscss "/usr/share/doc/awstats/examples/css"
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	ServerAdmin admin@astarmathsandphysics.com
	ServerName astarmathsandphysics.com
	ServerAlias www.astarmathsandphysics.com
	DocumentRoot /var/www/astarmathsandphysics
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/astarmathsandphysics/>
		Options ExecCGI Indexes FollowSymLinks MultiViews
		AllowOverride All
		Require all granted
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin/">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Require all granted
	</Directory>

<IfModule mod_security2.c>
  SecRuleEngine Off
</IfModule>

	Errorlog /var/www/astarmathsandphysics_error_log
#	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/astarmathsandphysics.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
	Require all denied
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>[/HTML]

---

### Post by astarmathsandphysics on 2018-07-23
After so much pfaffing around I have fixed this part of my problem.
It seemed what I had to do was move my sources files to /media/paul-smith/RAIDSYSTEM/public_html

I DON'T KNOW WHY!

---

### Post by TheFu on 2018-07-23
> **astarmathsandphysics said:**
> After so much pfaffing around I have fixed this part of my problem.
It seemed what I had to do was move my sources files to /media/paul-smith/RAIDSYSTEM/public_html

I DON'T KNOW WHY!

> Show your work 

Cannot say, because none of the requests to show permissions was provided.

---

