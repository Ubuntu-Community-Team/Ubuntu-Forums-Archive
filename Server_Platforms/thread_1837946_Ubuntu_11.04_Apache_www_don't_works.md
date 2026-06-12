---
title: "Ubuntu 11.04 Apache www don't works"
date: 2011-09-02
forum: Server Platforms
---

### Post by evg7 on 2011-09-02
Sites [www.linktolink.ru](www.linktolink.ru) and linktolink.ru, site without www don't work.

My apache cfg:
NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin [email]linktolink@mail.ru[/email]
    ServerName [www.linktolink.ru](www.linktolink.ru)
    ServerAlias *.linktolink.ru

    ErrorLog "/var/log/apache2/linktolink-error.log"
    CustomLog "/var/log/apache2/linktolink-access.log" common

#    Alias "/media/" "/usr/local/lib/python2.7/dist-packages/django/contrib/admin/media/"
#    <Directory "/usr/local/lib/python2.7/dist-packages/django/contrib/admin/media">
#        Order allow,deny
#        Allow from all
#    </Directory>

    Alias "/main_media/" "/home/workspace/lxch/main_media/"
    <Directory "/home/workspace/lxch/main_media">
        Order allow,deny
        Allow from all
    </Directory>

    WSGIScriptAlias "/" "/home/workspace/lxch/django.wsgi"
    <Directory "/home/workspace/lxch/">
        Order allow,deny
        Allow from all
    </Directory>


    
</VirtualHost>


Why [linktolink.ru]("http://linktolink.ru") not open while [www.linktolink.ru]("http://www.linktolink.ru") works?


ps.
Also than i restart apache, it shows warning:
 * Restarting web server apache2                                                [Fri Sep 02 23:43:23 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Fri Sep 02 23:43:24 2011] [warn] NameVirtualHost *:80 has no VirtualHosts

---

### Post by volkswagner on 2011-09-02
```
ServerAdmin linktolink@mail.ru
ServerName www.linktolink.ru
ServerAlias *.linktolink.ru
```

With the code written above you have not specified linktolink.ru.

You should change the ServerName to linktolink.ru or add it to the alias list.

Like:

```
ServerAdmin linktolink@mail.ru
ServerName linktolink.ru
ServerAlias *.linktolink.ru
```

As written like above the www will be included in your wildcard alias.

Then restart apache.

The warning you are getting may have to do with what is in your ports.conf or other config file.

---

### Post by evg7 on 2011-09-02
I change it to:

```
NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin linktolink@mail.ru
    ServerName linktolink.ru
    ServerAlias *.linktolink.ru

    ErrorLog "/var/log/apache2/linktolink-error.log"
    CustomLog "/var/log/apache2/linktolink-access.log" common
...

```
bit it don't works.

Warning raise the i add NameVirtualHost *:80 at the top of cfg file. Without it - no warning.

my ports.conf:



```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```


my apache2.conf


```


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
StartServers       1
MinSpareServers    1
MaxSpareServers    5
MaxClients        10
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
StartServers       1
MinSpareThreads    1
MaxSpareThreads    4
    ThreadLimit          64
    ThreadsPerChild      25
MaxClients        10
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
StartServers       1
MinSpareThreads    1
MaxSpareThreads    4
    ThreadLimit          64
    ThreadsPerChild      25
MaxClients        10
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
```

---

### Post by evg7 on 2011-09-02
Finally I solve it with a2dissite default

default cfg with content below block it:

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

Some body can explain why this happens?

---

### Post by volkswagner on 2011-09-02
Since you disabled the default site it works because likely you have no other virtual host files enabled.

You have an issue with the virtual host directive or perhaps some dns issue or redirect?

You should add the documentroot directive to your config file.

The way apache serves virtual hosts is by name.  If no name matches it serves the first vhost file alphabetically.

What does your DNS records look like?  Do you have Arecords for both www and without?  Or do you have a CNAME for WWW pointing to your domain name?

You should remove the first line from your vhost file, since "NameVirtualHost *:80" is included in your ports.conf.

You also may need to clear your browser cache on the machine you are testing with.

---

### Post by evg7 on 2011-09-02
my dns:
* 	A 	188.241.112.178 	  			
@ 	A 	188.241.112.178

---

