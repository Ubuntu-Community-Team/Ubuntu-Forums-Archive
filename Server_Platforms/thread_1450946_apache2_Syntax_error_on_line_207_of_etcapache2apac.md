---
title: "apache2: Syntax error on line 207 of /etc/apache2/apache2.conf: Syntax error on line"
date: 2010-04-09
forum: Server Platforms
---

### Post by carolija on 2010-04-09
Hi all,

I need a little help here about apache2 or maybe mysql too coz i am new in making web server.
So i got this error after i try to start apache2 :

```
nani@jebe-kevu-ovaj-PC:~$ /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                              apache2: Syntax error on line 207 of /etc/apache2/apache2.conf: Syntax error on line 86 of /etc/apache2/httpd.conf: </IfModuleGT; without matching <IfModuleGT; section
```

This is output :

```
### Section 1: Global Environment
      #
      ServerType standalone
      ServerRoot "/etc/httpd"
      PidFile /var/run/httpd.pid
      ResourceConfig /dev/null
      AccessConfig /dev/null
      Timeout 300
      KeepAlive On
      MaxKeepAliveRequests 0
      KeepAliveTimeout 15
      MinSpareServers 16
      MaxSpareServers 64
      StartServers 16
      MaxClients 512
      MaxRequestsPerChild 100000

      ### Section 2: 'Main' server configuration
      #
      Port 80

      <IfDefine SSL>
      Listen 80
      Listen 443
      </IfDefine>

      User www
      Group www
      ServerAdmin admin@carolija.eu
      ServerName www.carolija.eu
      DocumentRoot "/home/httpd/nani"

      <Directory />
      Options None
      AllowOverride None
      Order deny,allow
      Deny from all
      </Directory>

      <Directory "/home/httpd/nani">
      Options None
      AllowOverride None
      Order allow,deny
      Allow from all
      </Directory>

      <Files .pl>
      Options None
      AllowOverride None
      Order deny,allow
      Deny from all
      </Files>

      <IfModule mod_dir.c>
      DirectoryIndex index.htm index.html index.php index.php3 default.html index.cgi
      </IfModule>

      #<IfModule mod_include.c>
      #Include conf/mmap.conf
      #</IfModule>

      UseCanonicalName On

      <IfModule mod_mime.c>
      TypesConfig /etc/httpd/conf/mime.types
      </IfModule>

      DefaultType text/plain
      HostnameLookups Off

      ErrorLog /var/log/httpd/error_log
      LogLevel warn
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
      SetEnvIf Request_URI \.gif$ gif-image
      CustomLog /var/log/httpd/access_log combined env=!gif-image
      ServerSignature Off

      <IfModule mod_alias.c>
      ScriptAlias /cgi-bin/  "/home/httpd/cgi-bin/"
      <Directory "/home/httpd/cgi-bin">
      AllowOverride None
      Options None
      Order allow,deny
      Allow from all
      </Directory>
      </IfModuleGT;

      <IfModule mod_mime.c>
      AddEncoding x-compress Z
      AddEncoding x-gzip gz tgz

      AddType application/x-tar .tgz
      </IfModule>

      ErrorDocument 500 "The server made a boo boo.
      ErrorDocument 404 http://192.168.1.1/error.htm
      ErrorDocument 403 "Access Forbidden no no -- Go away.

      <IfModule mod_setenvif.c>
      BrowserMatch "Mozilla/2" nokeepalive
      BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
      BrowserMatch "RealPlayer 4\.0" force-response-1.0
      BrowserMatch "Java/1\.0" force-response-1.0
      BrowserMatch "JDK/1\.0" force-response-1.0
      </IfModule>

      ### Section 3: Virtual Hosts
      #
      <IfDefine SSL>
      AddType application/x-x509-ca-cert .crt
      AddType application/x-pkcs7-crl    .crl
      </IfDefine>

      <IfModule mod_ssl.c>
      SSLPassPhraseDialog     builtin
      SSLSessionCache         dbm:/var/run/ssl_scache
      SSLSessionCacheTimeout  300

      SSLMutex  file:/var/run/ssl_mutex

      SSLRandomSeed startup builtin
      SSLRandomSeed connect builtin

      SSLLog      /var/log/httpd/ssl_engine_log
      SSLLogLevel warn
      </IfModule>

      <IfDefine SSL>
      <VirtualHost _default_:443>

      DocumentRoot "/home/httpd/nani"
      ServerName www.carolija.eu
      ServerAdmin admin@carolija.eu
      ErrorLog /var/log/httpd/error_log

      SSLEngine on
      SSLCipherSuite ALL:!ADH:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL

      SSLCertificateFile      /etc/ssl/certs/server.crt
      SSLCertificateKeyFile   /etc/ssl/private/server.key
      SSLCACertificatePath    /etc/ssl/certs
      SSLCACertificateFile    /etc/ssl/certs/ca.crt
      SSLCARevocationPath     /etc/ssl/crl
      SSLVerifyClient none
      SSLVerifyDepth  10

      SSLOptions +ExportCertData +StrictRequire
      SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
      SetEnvIf Request_URI \.gif$ gif-image
      CustomLog /var/log/httpd/ssl_request_log \
      "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b" env=!gif-image
      </VirtualHost>
      </IfDefine>

```

And yes i own carolija.eu domain so point is to make it on my home serverand i have this folder "nani" DocumentRoot "/home/httpd/nani.

Thank you for time and help,

Regards,

---

### Post by Ryan Dwyer on 2010-04-09
</IfModuleGT; should be </IfModule>

---

### Post by carolija on 2010-04-09
> **Ryan Dwyer said:**
> </IfModuleGT; should be </IfModule>

umm but there is also :

```
 <IfModule mod_dir.c>
      DirectoryIndex index.htm index.html index.php index.php3 default.html index.cgi
      </IfModule>
```

I don't understand ;/

---

### Post by carolija on 2010-04-09
I was changed this one but no change after start apache2 ```
<IfModuleGT>
``` - I have put > on the and of IfModuleGT .. coz i have no idea what is problem in here ...

---

### Post by FuturePilot on 2010-04-09
> **carolija said:**
> I was changed this one but no change after start apache2 ```
<IfModuleGT>
``` - I have put > on the and of IfModuleGT .. coz i have no idea what is problem in here ...

As the poster above said it should be 
```
</IfModule>
```

and not

```
</IfModuleGT
```

---

### Post by carolija on 2010-04-09
> **FuturePilot said:**
> As the poster above said it should be 
```
</IfModule>
```

and not

```
</IfModuleGT
```

Even if i already have one </IfModule> like you can see in output up, just to change it and I have to have 2 of </IfModule> ?

Regards and tnx

---

### Post by s_ø on 2010-04-10
Yes yo should do as they say:)
The syntax is
<IfModule module_name>
Do something
</IfModule>

Just like Directories.
<Directory path/to/directory>
Do something
</Directory>

---

### Post by carolija on 2010-04-11
> **s_ø said:**
> Yes yo should do as they say:)
The syntax is
<IfModule module_name>
Do something
</IfModule>

Just like Directories.
<Directory path/to/directory>
Do something
</Directory>

Right, that was strange, didn't know is it sure like that or no.
Thank you very much!

Regards,

---

### Post by carolija on 2010-04-11
Hi,

I need help with this please who know what i have to change or add .. ?
This
Like you see first is result of starting Apache2 and second is httpd.conf file.
And if you see something bad in file which is not the part of thread please let me know, or some advice etc ... 

Thank you all for time and understanding !!!



```
Starting web server apache2                                                                                                              Syntax error on line 3 of /etc/apache2/httpd.conf:
Invalid command 'ServerType', perhaps misspelled or defined by a module not included in the server configuration
```

httpd.conf :

```
### Section 1: Global Environment
      #
      ServerType standalone
      ServerRoot "/etc/httpd"
      PidFile /var/run/httpd.pid
      ResourceConfig /dev/null
      AccessConfig /dev/null
      Timeout 300
      KeepAlive On
      MaxKeepAliveRequests 0
      KeepAliveTimeout 15
      MinSpareServers 16
      MaxSpareServers 64
      StartServers 16
      MaxClients 512
      MaxRequestsPerChild 100000

      ### Section 2: 'Main' server configuration
      #
      Port 80

      <IfDefine SSL>
      Listen 80
      Listen 443
      </IfDefine>

      User www
      Group www
      ServerAdmin [email]admin@carolija.eu[/email]
      ServerName [www.carolija.eu](www.carolija.eu)
      DocumentRoot "/home/httpd/nani"

      <Directory />
      Options None
      AllowOverride None
      Order deny,allow
      Deny from all
      </Directory>

      <Directory "/home/httpd/nani">
      Options None
      AllowOverride None
      Order allow,deny
      Allow from all
      </Directory>

      <Files .pl>
      Options None
      AllowOverride None
      Order deny,allow
      Deny from all
      </Files>

      <IfModule mod_dir.c>
      DirectoryIndex index.htm index.html index.php index.php3 default.html index.cgi
      </IfModule>

      #<IfModule mod_include.c>
      #Include conf/mmap.conf
      #</IfModule>

      UseCanonicalName On

      <IfModule mod_mime.c>
      TypesConfig /etc/httpd/conf/mime.types
      </IfModule>

      DefaultType text/plain
      HostnameLookups Off

      ErrorLog /var/log/httpd/error_log
      LogLevel warn
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
      SetEnvIf Request_URI \.gif$ gif-image
      CustomLog /var/log/httpd/access_log combined env=!gif-image
      ServerSignature Off

      <IfModule mod_alias.c>
      ScriptAlias /cgi-bin/  "/home/httpd/cgi-bin/"
      <Directory "/home/httpd/cgi-bin">
      AllowOverride None
      Options None
      Order allow,deny
      Allow from all
      </Directory>
     # </IfModule>

      <IfModule mod_mime.c>
      AddEncoding x-compress Z
      AddEncoding x-gzip gz tgz

      AddType application/x-tar .tgz
      </IfModule>

      ErrorDocument 500 "The server made a boo boo.
      ErrorDocument 404 [http://192.168.1.1/error.htm](http://192.168.1.1/error.htm)
      ErrorDocument 403 "Access Forbidden no no -- Go away.

      <IfModule mod_setenvif.c>
      BrowserMatch "Mozilla/2" nokeepalive
      BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
      BrowserMatch "RealPlayer 4\.0" force-response-1.0
      BrowserMatch "Java/1\.0" force-response-1.0
      BrowserMatch "JDK/1\.0" force-response-1.0
      </IfModule>

      ### Section 3: Virtual Hosts
      #
      <IfDefine SSL>
      AddType application/x-x509-ca-cert .crt
      AddType application/x-pkcs7-crl    .crl
      </IfDefine>

      <IfModule mod_ssl.c>
      SSLPassPhraseDialog     builtin
      SSLSessionCache         dbm:/var/run/ssl_scache
      SSLSessionCacheTimeout  300

      SSLMutex  file:/var/run/ssl_mutex

      SSLRandomSeed startup builtin
      SSLRandomSeed connect builtin

      SSLLog      /var/log/httpd/ssl_engine_log
      SSLLogLevel warn
      </IfModule>

      <IfDefine SSL>
      <VirtualHost _default_:443>

      DocumentRoot "/home/httpd/nani"
      ServerName [www.carolija.eu](www.carolija.eu)
      ServerAdmin [email]admin@carolija.eu[/email]
      ErrorLog /var/log/httpd/error_log

      SSLEngine on
      SSLCipherSuite ALL:!ADH:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL

      SSLCertificateFile      /etc/ssl/certs/server.crt
      SSLCertificateKeyFile   /etc/ssl/private/server.key
      SSLCACertificatePath    /etc/ssl/certs
      SSLCACertificateFile    /etc/ssl/certs/ca.crt
      SSLCARevocationPath     /etc/ssl/crl
      SSLVerifyClient none
      SSLVerifyDepth  10

      SSLOptions +ExportCertData +StrictRequire
      SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
      SetEnvIf Request_URI \.gif$ gif-image
      CustomLog /var/log/httpd/ssl_request_log \
      "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b" env=!gif-image
      </VirtualHost>
      </IfDefine>
```

apache2.conf :

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
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
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
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
# CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

/etc/apache2/sites-enabled/000-defauls  :

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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

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

/etc/apache2/sites-available/carolija.eu/defauls :

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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

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

### Post by new_tolinux on 2010-04-11
I don't see any need to configure "ServerType", as it isn't in my apache2.conf (Jaunty), so I guess removing that line does no harm.
By the way, my httpd.conf is empty.

---

### Post by Ryan Dwyer on 2010-04-11
Yeah, the ServerType directive was removed in Apache 2.0.

---

### Post by carolija on 2010-04-11
> **new_tolinux said:**
> I don't see any need to configure "ServerType", as it isn't in my apache2.conf (Jaunty), so I guess removing that line does no harm.
By the way, my httpd.conf is empty.

Okey thank you for advice, Ryan Dwyer ty too;)

But about httpd.conf , i have to delete all u think ?

---

### Post by Ryan Dwyer on 2010-04-11
If it works I don't see any reason to remove it.

Did you set this up using a tutorial or something? Do you know you can install Apache and friends with one command and it will work?

---

### Post by new_tolinux on 2010-04-11
> **Ryan Dwyer said:**
> If it works I don't see any reason to remove it.
I second that.
Keep it if it works, only try something if it doesn't work (and even then: don't delete without backup).

I installed apache (and MySQL/PHP) from the repositories. I guess the use of apache2.conf instead of httpd.conf is an ubuntu-specific decision.
I don't know what repositories I had enabled at that time, but at least I did not add any repository. Although it could be that I somewhere enabled a repository that is disabled in a default Jaunty-install.

---

### Post by s_ø on 2010-04-11
If you look in your apache2.conf file you will see that it includes various files

```
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

--

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```
It makes it easier to administer when the config is split up in functions.

It looks like you have an entire server config in your httpd.conf file. There are several directives set more than once.
For example in httpd.conf
[B]ServerRoot "/etc/httpd"
[/B]In apache2.conf
**ServerRoot "/etc/apache2"**

I dont know if apache allows setting these directives more than once, if it ignores the second or overwrites the first. But i dont think its a good setup.
Also which DocumentRoot should it serve? Looking at the config I think Apache will use both /var/www and /home/httpd/nani

I think you should cleanup your config files.
Make backups of all of them. Then remove all duplicate entries in you httpd.conf file and copy the rest to the relevant files.
**Listen** directives goes in **ports.conf**
**user** and **group** goes in **envvars** - if you installed apache from the repositories a user called **www-data** was created for it, use that user instead of www.
If you dont need to run virtualhosts, put everything host specific in **sites-available/default** and for ssl in **sites-available/default-ssl **(DocumentRoot, <Directory> ...)

I also think you should work on getting  the server up and running and secured on localhost, before you use it to serve the world.

---

### Post by Ryan Dwyer on 2010-04-11
If you're going to clean up the config as suggested above, you may as well uninstall Apache, remove the /etc/apache2 directory, then install it from the repository.

---

### Post by carolija on 2010-04-12
Thank you guys , I'm closer now to understanding this apache2 & httpd conf files , for what are they , why I have httpd & apache2 etc.. 
So i guess will be more easy to set it up.
-

> It looks like you have an entire server config in your httpd.conf file. There are several directives set more than once.
For example in httpd.conf
ServerRoot "/etc/httpd"
In apache2.conf
ServerRoot "/etc/apache2"

I dont know if apache allows setting these directives more than once, if it ignores the second or overwrites the first. But i dont think its a good setup.
Also which DocumentRoot should it serve? Looking at the config I think Apache will use both /var/www and /home/httpd/nani


I don't know wich one to use really, the point is to i can make for every user one web so i guess it will be /home/httpd/nani because nani is user, am I right on this one ?
I think if i put direction on /var/www it will be fix site just [www.domain.com](www.domain.com) but if I put /home/httpd/nani i could use [www.domain.com~nani/](www.domain.com~nani/) , just say and let me know if I'm wrong please.

I was reading 2-3 different tutorials and it mes-st up with my head like u can see lol.. This one the first [http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server#Testing_the_Web_Server]("http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server#Testing_the_Web_Server") and this one too [http://www.debian-administration.org/articles/412]("http://www.debian-administration.org/articles/412")
> Did you set this up using a tutorial or something? Do you know you can install Apache and friends with one command and it will work?
And i don't know if it's important i have dynamic IP.

And no i don't know how and that is possible to set up with one commands line, you can share it with me if it's not a secret. 
-
In meanwhile today i got 2 CD-s from ubuntu one ubuntu and one server ubuntu so I'll try to fix this just to learn it and i guess after this ill try to set up ubuntu server and the best idea after i mest up all conf files is to make new one and delete all old one like you said. 
Ill keep you posted and yes now ssh event wont work damn ..thats why i decide to make all new ( i don't have important files in here this is brend new so I have nothing to lose just to learn ) and not from 2-3 tutorials ofc :)

Thanks again people for your time!

Best Regards,

---

### Post by s_ø on 2010-04-12
There is a LAMP (Apache, MySQL, PHP) package available as a task in ubuntu. To install use tasksel.
```
sudo tasksel install lamp-server
```

If you only need apache without MySQL/PHP you can install the package from the repository.
```
sudo apt-get install apache2
```

If you need to have multiple users have separate sites, you could set up per-user web directories. There is a howto in the apache documentation [http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)
If you just have one user, you wont really gain anything.

Apache will map urls to filenames straightforward. As an example
If **DocumentRoot** is set to **/var/www** this is the directory apache will serve when you go to [http://localhost](http://localhost)
If there is a file called index.html apache will serve this, otherwise you will see a directory structure.
If you have site1, site2, site3 ... directories inside /var/www these will be mappes to [http://localhost/site1](http://localhost/site1) [http://localhost/site2](http://localhost/site2) and so on.
If you want to restrict acces to a directory you can do this with the **<Directory>** directive in the config files.
Lets say you make a directory called **private_html** in /var/www. To restrict access you would need the following.
```
<Directory /var/www/private_html>
Order Deny,Allow
Deny from All
</Directory>
```
This will block http access, but your scripts will still be able to access it.
You can use regex in the the <Directory> directive, so to deny access to private_html directories in site1, site2, ... you can do this.
```
<Directory ~ "^/var/www/.+/private_html">
Order Deny,Allow
Deny from All
</Directory>
```

A dynamic IP is not a problem. And regardless of static/dynamic you will need to get a dns server to associate the domain with the IP

---

