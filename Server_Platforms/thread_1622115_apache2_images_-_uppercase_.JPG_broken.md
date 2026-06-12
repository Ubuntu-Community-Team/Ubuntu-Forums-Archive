---
title: "apache2 images - uppercase .JPG broken?"
date: 2010-11-15
forum: Server Platforms
---

### Post by NathanScrivener on 2010-11-15
Hi, I have a zen-cart site hosted on bluehost at the moment. I'm wanting to migrate it to my Xen-VPS running Ubuntu 10.04.

At the moment there are a whole bunch of images that do not load on either the new Ubuntu server or on my local Ubuntu 10.04 Desktop. 

The images that will not load are those with an uppercase extension, i.e. .JPG. If I manually change the file reference in the database and then change the actual filename to lower case, it works. However it would take a very long time indeed to go through all the images that are doing this and manually correct them!

How can I fix my Apache to display the uppercase .JPG images?

Thanks for your help! :-)

---

### Post by Ryan Dwyer on 2010-11-15
What happens when you try to browse directly to an image with an uppercase extension? 404?

The capitalisation must match exactly as filenames are case sensitive on Unix systems.

---

### Post by NathanScrivener on 2010-11-15
Interesting! 

I get a 403 forbidden error, but when I change the filename to have lower case .jpg as the extension, I can view the image in the browser. Change it back and there we go, 403 forbidden again.

There must be an apache setting defining allowable image types? Or something along those lines? 

Any ideas?

---

### Post by SeijiSensei on 2010-11-15
Try adding "JPG" to the image/jpeg entry in /etc/mime.types.  I think Apache uses that file along with /etc/apache2/magic to determine the mime type for various extensions and apply the appropriate handler.

You might need to restart apache.

I will say I've run instances of Zen Cart on a CentOS server and never had this problem.  My client had lots of *.JPG files, too.

---

### Post by NathanScrivener on 2010-11-15
Hi, thanks for your input. I tried that and it didn't seem to work.

---

### Post by SeijiSensei on 2010-11-15
You could also try adding an entry to /etc/apache2/mime.conf using the "AddType" directive:

```
AddType  image/jpeg  .JPG
```

See the example for gzipped files at the top of mime.conf.

It's also weird that you get a 403 Forbidden error rather than being prompted to download the file, which should be Apache's behavior if it can't assign the file to a MIME type.

Did you take a look at the support pages for Apache at apache.org?  Does anyone else report this problem?

One other thing you might try is accessing the files as the "www-data" user, the user that Apache runs as.  Try this:

```

$ sudo su
[enter password]
# su www-data
$ ls -l /path/to/images/*.JPG

```

If you can see all the files (I suspect you can), then it's an Apache issue and not the OS.  In that case, there must be something that's denying access to files with .JPG.  Are you using the stock installation that comes from Ubuntu?  Using virtualhosts?  Have any access restrictions in there?  I'd try running:

```

cd /etc/apache2
sudo grep -i jpg *
sudo grep -i jpg */*
sudo grep -i jpg */*/*

```

to look for anything having to do with jpg or JPG in the Apache configuration files.

---

### Post by Ryan Dwyer on 2010-11-15
Look in /var/log/apache2/error.log to see why it's dishing up 403s.

---

### Post by NathanScrivener on 2010-11-16
/var/log/apache2/error.log -


[Tue Nov 16 18:20:14 2010] [error] [client ::1] client denied by server configuration: /var/www/images/Black Organza Sash scaled.JPG, referer: [http://localhost/](http://localhost/)

and similar for each image that has uppercase JPG extension.

I checked permissions, all images are 744 so www-data has no problem reading the images. And that wouldn't explain why uppercase JPG's have a problem but lowercase don't.

I tried the 'sudo grep -i jpg *' commands as suggested and they did not show up anything. 

This seems to be an apache configuration issue, which is in the default configuration for Ubuntu 10.04, as it is repeated across two different installs.

---

### Post by Ryan Dwyer on 2010-11-16
Please post the contents of:

/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
...as well as the vhost file the vhost is using in /etc/apache2/sites-enabled/.

---

### Post by NathanScrivener on 2010-11-16
Apache2.conf:

```
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

httpd.conf is empty.

On my desktop machine, I am using default so, the contents of 000-default in /etc/apache2/sites-enabled is:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

This is happening on both my Ubuntu 10.04 Xen VPS and my Desktop machine. 

Thanks for your help :-)

---

### Post by wongo888 on 2010-11-16
The case of the extension does not matter. It will map to the mime type all the same.

[http://httpd.apache.org/docs/2.0/mod/mod_mime.html#typesconfig](http://httpd.apache.org/docs/2.0/mod/mod_mime.html#typesconfig)

This 403 error will result in two log entries. One in the error log which you found. You should also check the access log.

```
client denied by server configuration
```

"client denied by server configuration" means that the server has been configured to deny the client access. Some general info is here...

[http://wiki.apache.org/httpd/ClientDeniedByServerConfiguration](http://wiki.apache.org/httpd/ClientDeniedByServerConfiguration) 

You should check your server configuration files (there are a lot of them) and make sure that your settings are as intended.

[http://httpd.apache.org/docs/current/logs.html#errorlog](http://httpd.apache.org/docs/current/logs.html#errorlog)

Had this been a dir permission error, you would have seen this in the error log: 
```
(13)Permission denied: access to PATH denied
```

Check your Directory stanzas in particular ("deny from all" is a common culprit) and be aware of the default settings.

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html#default-settings](https://help.ubuntu.com/10.04/serverguide/C/httpd.html#default-settings)

---

### Post by NathanScrivener on 2010-11-16
Hi, none of those comments seem to solve my issue.

> The case of the extension does not matter. It will map to the mime type all the same.

[http://httpd.apache.org/docs/2.0/mod...ml#typesconfig](http://httpd.apache.org/docs/2.0/mod...ml#typesconfig)

I wonder whether this may not apply in Ubuntu 10.04? I've noticed that if I create any other random file extension name, I get the same permission error. There are no issues with other images in the same folder, and all have the same group ownership and file system permission settings. But according to the above, the .JPG should be read by Apache as identical to .jpg.


> 
This 403 error will result in two log entries. One in the error log which you found. You should also check the access log.


Here is an example:

```
127.0.0.1 - - [16/Nov/2010:18:28:12 +1300] "GET /images//MIdnight%20blue%20two-tone%20scaled.JPG HTTP/1.1" 403 525 "http://localhost/" "Mozilla/5.0 (X11; U;$
```

> You should check your server configuration files (there are a lot of them) and make sure that your settings are as intended.

I've checked as many as I can find, but I'm a beginner so am finding this a bit daunting. I think this may be related to the distribution, as it is happening on two separate installs. 

> [http://httpd.apache.org/docs/current/logs.html#errorlog](http://httpd.apache.org/docs/current/logs.html#errorlog)


I had a look at this page, and couldn't find anything that I think would help.

:confused:

---

### Post by wongo888 on 2010-11-16
You have set:

```
AllowOverride All
```

This will allow the server to read .htaccess files. Within the webroot and in the images folders are there any .htaccess files? If so what is in there?

Anything like this?

```

<Files ~ "\.(gif|jpe?g|png)$">

or

<FilesMatch "\.(gif|jpe?g|png)$">

```

---

### Post by NathanScrivener on 2010-11-16
You sir, are a genius! There was an entry in the .htaccess with a comment about preventing inappropriate browsing, listing the file types that should be accessible. I added the uppercase JPG and it all works now!

Thanks
:P:P:P

---

### Post by SeijiSensei on 2010-11-17
That must be a custom rule you or someone else added to your ZenCart installation.  I just reviewed a stock 1.3.8a installation that I had sitting around, and the only <Files> directives I see in the half-dozen or so .htaccess files control access to the .php files or, in one case, to .pem certificates.

---

