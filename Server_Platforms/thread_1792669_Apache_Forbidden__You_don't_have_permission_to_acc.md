---
title: "Apache Forbidden  You don't have permission to access...when theres no web files in t"
date: 2011-06-28
forum: Server Platforms
---

### Post by dalitso on 2011-06-28
I have ubuntu 10.04 server setup with LAMP installed.

I want to be able to access some files in my web directory via a web browser
[http://192.168.1.10/file](http://192.168.1.10/file)
but I am getting an error "Forbidden You don't have permission to access /file/ on this server."

When a web file say "index.html" is present in the same /file directory, it works, the index.html shows on the browser as a webpage..

```
root@nitram:~# ls -l /home/www
total 14568
drwxrwxrwx 16 www-data www-data    4096 2011-06-24 13:26 blog
drwxrwxrwx  3 www-data www-data    4096 2011-06-28 17:49 file
drwxrwxrwx  7 www-data www-data    4096 2011-06-24 12:50 invoice
-rwxrwxrwx  1 www-data www-data 6956762 2011-06-24 12:56 Joomla_1.5.23-Stable-Full_Package.zip
-rwxrwxrwx  1 www-data www-data 7920151 2011-06-24 12:56 Joomla_1.6.1-Stable-Full_Package.zip
drwxrwxrwx 16 www-data www-data    4096 2011-06-24 13:20 maxima
drwxrwxrwx 18 www-data www-data    4096 2011-06-24 13:26 test
drwxrwxrwx 16 www-data www-data    4096 2011-06-24 13:27 test2
drwxrwxrwx 16 www-data www-data    4096 2011-06-24 13:31 thunzic
drwxrwxrwx 10 www-data www-data    4096 2011-06-24 12:56 webmail

```


```
root@nitram:~# nano /etc/apache2/sites-available/default
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/www
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


```
root@nitram:~# nano /etc/apache2/apache2.conf
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
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```


I used cli to setup this server. When I used to use webmin, I was able to browse into the web server directories.


Please help me to enable the dir browsing feature.

---

### Post by Lars Noodén on 2011-06-28
Let's start with the security: The directory should be owned by someone else other than www-data, like root.  The directory should not be writable to either the world or to www-data.

```

groupadd webmasters

chown root:webmasters /home/www

find /home/www -type d -exec chmod u=rwx,g=rwxs,o=rx {} \;

find /home/www -type f -exec chmod u=rw,g=rw,o=r {} \;


```

---

### Post by dapperdanny77 on 2011-06-28
I suppose you changed your DocumentRoot from /var/www to /home/www 
you should adopt the setting for the initial DocumentRoot also

```

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>


##### new
	<Directory /home/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>


```


The Option Indexes enables viewing the directory - If not set you will get a Forbidden without having an index.html placed in this dir.

---

### Post by dalitso on 2011-06-28
To Lars Noodén

I have changed the folder ownership to root. Its a joomla site development LAN server, and its behind a router. I think leaving the permissions to 777 for site development reasons will be ok. Of course I use a dyndns hostname so the clients can view the sites in development. Its just that joomla usually gives permission errors when installing extensions, I will keep on changing the permissions because of that. Please let me know if its a wrong move.

To dapperdanny77

I have adopted the settings for the initial DocumentRoot like you suggested and it works. I can browse the files now.

Thank you very much for your help guys.

---

### Post by Lars Noodén on 2011-06-28
> **dalitso said:**
> 
I have changed the folder ownership to root. Its a joomla site development LAN server, and its behind a router. I think leaving the permissions to 777 for site development reasons will be ok.


777 is quite the security risk, especially if the group is still www-data.  755 is safe.  Otherwise, if the web server can write to those directories, there is a chance that can be exploited to your disadvantage.

---

### Post by dalitso on 2011-06-28
Changed to 755

Thank you for your advice

```

root@nitram:/var/log# ls -l /home/www
total 14568
drwxr-xr-x 16 root root    4096 2011-06-24 13:26 blog
drwxr-xr-x  3 root root    4096 2011-06-28 17:49 file
drwxr-xr-x  7 root root    4096 2011-06-24 12:50 invoice
-rwxr-xr-x  1 root root 6956762 2011-06-24 12:56 Joomla_1.5.23-Stable-Full_Package.zip
-rwxr-xr-x  1 root root 7920151 2011-06-24 12:56 Joomla_1.6.1-Stable-Full_Package.zip
drwxr-xr-x 16 root root    4096 2011-06-24 13:20 maxima
drwxr-xr-x 18 root root    4096 2011-06-24 13:26 test
drwxr-xr-x 16 root root    4096 2011-06-24 13:27 test2
drwxr-xr-x 16 root root    4096 2011-06-24 13:31 thunzic
drwxr-xr-x 10 root root    4096 2011-06-24 12:56 webmail

```

---

