---
title: "ERROR .htaccess: &lt;IfModule not allowed here error after upgrade to 13.10"
date: 2014-04-12
forum: Server Platforms
---

### Post by maxchock2 on 2014-04-12
Hi,

Previously was running on 13.04. Did an upgrade this morning and the first error is actually telling 

> AH00526: Syntax error on line 26 of /etc/apache2/conf.d/awstats.conf:Invalid command 'AuthMYSQL', perhaps misspelled or defined by a module not included in the server configuration




and the apache2 is not able to start. Because while upgrading, the system told me some package is obsolete and i have remove it. Can't find a solution on that, so I comment out every configuration files under /etc/apache2/conf.d/ which contain line such as 

AuthMySQL_Password_Table mailbox
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field password

by doing that, apache2 can finally start. But i'm in a multiple virtual host environment, my main website [www.victoria.my]("http://www.victoria.my/") can access just fine, but others website such as foxono.me and buddyjoy.com will show 500 internal server error. Here is my apache2.conf file
```

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
    MaxClients          250
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
# If you are behind a reverse proxy, you might want to change %h into %
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


ServerName localhost


NameVirtualHost *:80


<VirtualHost *:80>
DocumentRoot /var/www
ServerName www.victoria.my
ServerAlias victoria.my
</VirtualHost>




<VirtualHost *:8080>
DocumentRoot /var/www1
ServerName www.foxono.me
ServerAlias foxono.me
</VirtualHost>


<VirtualHost *:80>
DocumentRoot /var/www1
ServerName www.victoriagallery.com.my
ServerAlias victoriagallery.com.my
</VirtualHost>


<VirtualHost *:8080>
DocumentRoot /var/www1
ServerName www.buddyjoy.com
ServerAlias buddyjoy.com
</VirtualHost>


<VirtualHost *:80>
DocumentRoot /var/www1
ServerName www.titantech.com.my
ServerAlias titantech.com.my
</VirtualHost>

# MySQL auth (libapache2-mod-auth-apache2).
# Global config of MySQL server, username, password.
#Auth_MySQL_Info 127.0.0.1 vmail kUSDJrTPRagz1LXL6O8HWlnJSvsDe3
#Auth_MySQL_General_DB vmail
# MySQL auth (libapache2-mod-auth-apache2).
# Global config of MySQL server, username, password.
#Auth_MySQL_Info 127.0.0.1 vmail kUSDJrTPRagz1LXL6O8HWlnJSvsDe3
#Auth_MySQL_General_DB vmail




```


and /var/log/apache2/error.log only give log such as:


> [Sat Apr 12 21:17:45.520896 2014] [core:alert] [pid 6855] [client 127.0.0.1:53592] /var/www1/.htaccess: <IfModule not allowed here, referer: [http://www.foxono.me/](http://www.foxono.me/)







I have googling around but no luck. Hope someone from here can point out some solutions. 

Thanks.

---

### Post by SeijiSensei on 2014-04-12
If you control the server, you should move any directives in an .htaccess file to the virtual host configuration itself. You should also review the [discussion]("http://httpd.apache.org/docs/2.2/mod/core.html#ifmodule") of the <IfModule> directive on the Apache site to make sure you're using it correctly.  Also make sure the module referenced in that statement actually exists in /etc/apache2/mods-available/ and is activated in /etc/apache2/mods-enabled/.

As for MySQL auth, you probably need to install the **libapache2-mod-auth-mysql** package.

---

### Post by maxchock2 on 2014-04-13
Hi,

Thanks for your reply. Actually I own the server, but unfortunately i'm not very good in apache configuration. 

However, because of this > [COLOR=#000000]you should move any directives in an .htaccess file to the virtual host configuration itself[/COLOR], I remove the .htaccess file in the /var/www1/ and now everything back to normal!

THANKS!!

---

### Post by maxchock2 on 2014-04-13
I'm too early to be happy.. I just found out the clean URL doesn't work anymore after I remove the .htaccess file...

---

### Post by Habitual on 2014-04-14
Max...

Just put the contents of the former .htaccess file in your site's .conf file under the <directory> stanza:
Example:
```
<Directory "/var/www1">
...
    RewriteEngine on
    RewriteCond stuff here
    RewriteRule here.
...
</Directory>
```

If you still have the contents of the deleted, or removed .htaccess file, post those contents here and we can help.
Sanitize if necessary.

---

