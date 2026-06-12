---
title: "Port Forwarding to Apache Web Server"
date: 2014-02-23
forum: Server Platforms
---

### Post by jay30 on 2014-02-23
I have setup Ubuntu 12.04 Server and installed an Apache2 web server. I have also installed Wordpress (and setup a basic web page). I can access my web page from an internal PC (ie. via my home wireless). I have an Actiontec V1000 modem/router from Telus (my ISP). I have setup port forwarding on my router in order to allow ssh access to the server. In particular I have forwarded port 22 to the IP address of my server. This works ok (I can access via an internal PC or an external one using the modem IP address).


i am now trying to setup port forwarding such that I can get to my web page from an external PC. As I understand that Telus blocks port 80, I have port forwarded port 8080 on my modem to the IP address of my server. I have also made the following changes/additions to my /etc/apache2/ports.conf and /etc/apache2/sites-available/default files:


PORTS.CONF
NameVirtualHost *:80 [this line was already here]
Listen 80 [this line was already here]
Listen 8080 [I added this line]


DEFAULT
Replaced first line of file "<VirtualHost *:80>" with "<VirtualHost *:8080>"


I then restarted Apache2.


Now, when I try to browse to my web page from an external PC via http://<modem IP>:8080 I receive the following message on my browser:


NOT FOUND
The requested URL / was not found on this server.
Apache/2.2.22 (Ubuntu) Server at 123.4.567.891 Port 8080


Any idea what I am missing? It seems encouraging that it is maybe finding the server? Are there maybe additional/different entries to be made in other Apache configuration files? Should I have somehow kept both VirtualHost lines in the default file?


Any suggestions/ideas greatly appreciated. Thank you.

---

### Post by CharlesA on 2014-02-23
Put Apache back on port 80 and just mess with the port forwarding on the router to forward port 8080 to port 80 on your web server.

---

### Post by jay30 on 2014-02-23
> **CharlesA said:**
> Put Apache back on port 80 and just mess with the port forwarding on the router to forward port 8080 to port 80 on your web server.

CharlesA, thank you for the suggestion.  I have done as you suggest (removed all the port 8080 stuff from the default and ports.conf files).  I went into my modem/router port forwarding.  It is an Actiontec V1000h.  I am not entirely certain that what I have done forwards the modem port 8080 to the web server port 80, but this is what I have entered:

1.  Set the LAN Port and IP Information
          Starting Port:  8080
          Ending Port:    8080
          Protocol:         TCP
          LAN IP Address:  <123.456.7.89> (the internal IP address of my web server)

2.  Set the Remote Port and IP Information. (Optional)
          Starting Port:  80
          Ending Port:    80
          Set Remote IP Address:  0.0.0.0 (0.0.0.0 will use any IP address)

Originally, I didn't enter anything into the section 2 optional area.  However, I have done so now.  I am not sure if this is what is needed to have it use port 80 on the web server?  Or does this have to do with the port of the external machine that is trying to make a connection?  At any rate I still am unable to connect to my web server.  Any other suggestions you may have and/or am I doing something incorrect?

Any further advice greatly appreciated.

---

### Post by thnewguy on 2014-02-23
I could be mistaken, but from the settings you posted it looks as though the information might be added backwards. I would assume (thought I may be wrong) that the LAN port should be set to 80 and the remote port should be set to 8080 on the modem. I think if you reserve your settings it might work better.

---

### Post by jay30 on 2014-02-23
> **thnewguy said:**
> I could be mistaken, but from the settings you posted it looks as though the information might be added backwards. I would assume (thought I may be wrong) that the LAN port should be set to 80 and the remote port should be set to 8080 on the modem. I think if you reserve your settings it might work better.

I had assumed it was this way.  For example I have successfully setup port forwarding for my ssh connection.  In this case I have told my server to listen on 2222 for ssh and on the port forwarding I have setup section 1 to forward 2222 to the internal IP address of my server.  This was necessary as port 22 is blocked by my ISP.  In this case I didn't put anything into the optional section 2 setup of port forwarding.  And, it works perfectly for connecting from an external.

---

### Post by Doug S on 2014-02-23
It looks backwards to me also. Try this:```
1.  Set the LAN Port and IP Information
          Starting Port: 80
          Ending Port: 80
          Protocol:         TCP
          LAN IP Address:  <123.456.7.89> (the internal IP address of my web server)

2.  Set the Remote Port and IP Information. (Optional)
          Starting Port:  8080
          Ending Port:    8080
          Set Remote IP Address:  0.0.0.0 (0.0.0.0 will use any IP address)
```And for your original posting it looks as though it was actually working but didn't find anything in the base directory or didn't know to look for index.html or whatever by default. Give us the URL you use internally.

Edit: do "/var/log/apache2/access.log" or "/var/log/apache2/error.log" reveal any useful information?

---

### Post by jay30 on 2014-02-24
I tried reversing the entries in port forwarding as suggested, however, can't get that to work.  Also, I "think" am doing the port forwarding correctly as I have done it this way to provide ssh access from outside.  In particular, I port forwarded 2222 to the internal IP address of the server by making an entry in section 1 only (forwarding port 2222 to the internal IP address of the server).  And, I have been successful connecting to the ssh by specifying the modem IP and the 2222 port from outside.

you make an excellent point that I seemed to originally be able to at least recognize there was a ubuntu server from outside.  At that time I had the ports.conf and default files set up as noted in my original post.  In trying to get back to that situation I have put those 2 files as noted in my original post.  Now when I restart apache I get the following message:

[warn] NameVirtualHost *:80 has no VirtualHosts
(I am not sure if I was getting this msg before - likely not)

Regardless, having evidently returned the setup to what I noted in my original post, I am unable to get that msg that the requested URL not found on the ubuntu server (when trying to access from external).

Also, I checked the access.log and error.log files and found nothing of particular interest.

---

### Post by CharlesA on 2014-02-24
> **jay30 said:**
> I tried reversing the entries in port forwarding as suggested, however, can't get that to work.  Also, I "think" am doing the port forwarding correctly as I have done it this way to provide ssh access from outside.  In particular, I port forwarded 2222 to the internal IP address of the server by making an entry in section 1 only (forwarding port 2222 to the internal IP address of the server).  And, I have been successful connecting to the ssh by specifying the modem IP and the 2222 port from outside.

you make an excellent point that I seemed to originally be able to at least recognize there was a ubuntu server from outside.  At that time I had the ports.conf and default files set up as noted in my original post.  In trying to get back to that situation I have put those 2 files as noted in my original post.  Now when I restart apache I get the following message:

[warn] NameVirtualHost *:80 has no VirtualHosts
(I am not sure if I was getting this msg before - likely not)

Regardless, having evidently returned the setup to what I noted in my original post, I am unable to get that msg that the requested URL not found on the ubuntu server (when trying to access from external).

Also, I checked the access.log and error.log files and found nothing of particular interest.

You have an extra NameVirtualHost somewhere. Are you still able to access it locally?

---

### Post by jay30 on 2014-02-24
Thanks again for the reply.  At this point I cannot access locally - receive the message:

the requested URL was not found on server
apache/2.2.22 (Ubuntu) Server at 123.456.7.89 port 80

i suppose it doesn't connect locally now because of the change in first line of default file to <VirtualHost *:8080> ?

i will look for other NameVirtualHost - where might I find them?

---

### Post by CharlesA on 2014-02-24
Please post your configuration inside code tags. (Hit # in advanced editor)

---

### Post by jay30 on 2014-02-24
Which files - ports.conf?

---

### Post by jay30 on 2014-02-25
Ports.conf file:

```

NameVirtualHost *:80Listen 80
Listen 8080


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

---

### Post by CharlesA on 2014-02-25
> **jay30 said:**
> Ports.conf file:

```

**NameVirtualHost *:80**Listen 80
Listen 8080


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

Take the bolded bit out.

You should have a file with your virtualhost in /etc/apache2/sites-available/somefile

---

### Post by jay30 on 2014-02-25
The file in the sites-available directory is the default file.  It's contents are as follows:

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

---

### Post by CharlesA on 2014-02-25
That looks right. Do you still get that warning when you restart apache?

Also, you get you any error if you try to access the site locally?

---

### Post by jay30 on 2014-02-25
No longer get warning since I changed the first line of default file to read "80" rather than "8080".  Also, the change back to "80" has the internal access working again.  But, not able to access from outside (or even get an indication of a ubuntu server - as I once did as noted in original post).

---

### Post by CharlesA on 2014-02-25
Double check your port forwarding on the router.

Check here to see how to set port forwarding up correctly.
[http://portforward.com/](http://portforward.com/)

And here to test it.
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by jay30 on 2014-02-25
Thank you, I will double check my port forwarding setup.  Although I see that now I am back to receiving the following message when trying to access from outside on a browser (via the modem IP address 207.6.156.121 and port 8080):

Not Found
The requested URL / was not found on this server.
Apache/2.2.22 (Ubuntu) Server at 207.6.156.121 Port 8080

To recap, I have port forwarded 8080 on the modem to the internal IP address of my web server.  To the best of my knowledge I have done the port forwarding correctly as per the doc/link you provided - although I have port forwarded 8080 rather than 80 because 80 is blocked by my ISP.  Also the doc does suggest port forwarding 443 as well (I gave not done this yet).

---

### Post by CharlesA on 2014-02-25
Check your Apache logs to see what it is returning. You would not be getting that message if you aren't hitting the web server.

---

### Post by jay30 on 2014-02-25
The last entries in the error.log file shows:

File does not exist:  /etc/apache2/htdocs

I have checked the apache2 directory and the file isn't there.  Might it be elsewhere?

---

### Post by Doug S on 2014-02-25
> **jay30 said:**
> The last entries in the error.log file shows:
File does not exist:  /etc/apache2/htdocs
I have checked the apache2 directory and the file isn't there.  Might it be elsewhere?It does not make any sense that apache is looking for such a non-existent file. I have no such file anywhere on any of my computers. Nor do I have any reference to such a file anywhere in any of the apache configuration or *-available directories.

---

### Post by CharlesA on 2014-02-25
I remember seeing something like that before but I don't remember what the cause was.

The only reason I can think of that it is throwing a 404 error is because the RootDirectory directive is incorrect, but then it wouldn't work locally either.

---

### Post by Doug S on 2014-02-25
CharlesA is right. Evidently, if there is no "DocumentRoot" directive in your /etc/apache2/sites-available/default file then the apache web server will look in "ServerRoot" (typically "/etc/apache2") for a file called htdocs. Example from my test computer with that line removed:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]tail -1 /var/log/apache2/error.log[/COLOR]
[Tue Feb 25 16:44:12 2014] [error] [client 192.168.111.101] File does not exist: /etc/apache2/htdocs
```

---

### Post by jay30 on 2014-02-25
The default file does have the following line:

DocumentRoot /var/www

So, is this causing the problem?  If so, what do I need to do to correct?

---

### Post by CharlesA on 2014-02-25
That looks right. Have you changed any of the other config files?

---

### Post by jay30 on 2014-02-26
There seem to be so many configuration files. Any changes I did make I did as I was following directions setting up the server.  I think I made a few.  Which config files are of primary concern.

---

### Post by jay30 on 2014-02-26
The changes I made to config files are as follows:

_Apache2.conf_
     Added:   Include /etc/phpmyadmin/apache.conf

_Httpd.conf_ (added the following line to the otherwise empty file)
     Added:   ServerName Localhost

_Ports.conf_
     Removed:  NameVirtualHost *:80
     Added:       Listen 8080

I think that these were the only changes I have made. 

The contents of the /etc/phpmyadmin/apache.conf file noted above is as follows:

```



Alias /phpmyadmin /usr/share/phpmyadmin


<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php


<IfModule mod_php5.c>
AddType application/x-httpd-php .php


php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_admin_flag allow_url_fopen Off
php_value include_path .
 php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
 php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/
</IfModule>


</Directory>


# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
<IfModule mod_authn_file.c>
AuthType Basic
AuthName "phpMyAdmin Setup"
AuthUserFile /etc/phpmyadmin/htpasswd.setup
</IfModule>
Require valid-user
</Directory>


# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
Order Deny,Allow
Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
Order Deny,Allow
Deny from All
</Directory>




```

---

### Post by Doug S on 2014-02-26
Delete the stuff you put in http.conf. That file is supposed to be empty and is only present for legacy reasons. It is not even there at all in the more recent Ubuntu.

Restore ports.conf. I think that is why you are getting the strange file fetch location.

I don't know about the changes you made to apache2.conf, but I don't see such changes mentioned in the phpmyadmin chapter of the ubuntu serverguide, which is the only reference I use.

---

### Post by CharlesA on 2014-02-26
Here's what the default 12.04 apache config looks like:

**/etc/apache2/apache2.conf**
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

**/etc/apache2/ports.conf**
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

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

**/etc/apache2/sites-available/default**
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

**/etc/apache2/sites-available/default-ssl**
```

<IfModule mod_ssl.c>
<VirtualHost _default_:443>
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

        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on

        #   A self-signed (snakeoil) certificate can be created by installing
        #   the ssl-cert package. See
        #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
        #   If both key and certificate are stored in the same file, only the
        #   SSLCertificateFile directive is needed.
        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

        #   Server Certificate Chain:
        #   Point SSLCertificateChainFile at a file containing the
        #   concatenation of PEM encoded CA certificates which form the
        #   certificate chain for the server certificate. Alternatively
        #   the referenced file can be the same as SSLCertificateFile
        #   when the CA certificates are directly appended to the server
        #   certificate for convinience.
        #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt

        #   Certificate Authority (CA):
        #   Set the CA certificate verification path where to find CA
        #   certificates for client authentication or alternatively one
        #   huge file containing all of them (file must be PEM encoded)
        #   Note: Inside SSLCACertificatePath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        #SSLCACertificatePath /etc/ssl/certs/
        #SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt

        #   Certificate Revocation Lists (CRL):
        #   Set the CA revocation path where to find CA CRLs for client
        #   authentication or alternatively one huge file containing all
        #   of them (file must be PEM encoded)
        #   Note: Inside SSLCARevocationPath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        #SSLCARevocationPath /etc/apache2/ssl.crl/
        #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

        #   Client Authentication (Type):
        #   Client certificate verification type and depth.  Types are
        #   none, optional, require and optional_no_ca.  Depth is a
        #   number which specifies how deeply to verify the certificate
        #   issuer chain before deciding the certificate is not valid.
        #SSLVerifyClient require
        #SSLVerifyDepth  10

        #   Access Control:
        #   With SSLRequire you can do per-directory access control based
        #   on arbitrary complex boolean expressions containing server
        #   variable checks and other lookup directives.  The syntax is a
        #   mixture between C and Perl.  See the mod_ssl documentation
        #   for more details.
        #<Location />
        #SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
        #            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
        #            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
        #            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
        #            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
        #           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
        #</Location>

        #   SSL Engine Options:
        #   Set various options for the SSL engine.
        #   o FakeBasicAuth:
        #     Translate the client X.509 into a Basic Authorisation.  This means that
        #     the standard Auth/DBMAuth methods can be used for access control.  The
        #     user name is the `one line' version of the client's X.509 certificate.
        #     Note that no password is obtained from the user. Every entry in the user
        #     file needs this password: `xxj31ZMTZzkVA'.
        #   o ExportCertData:
        #     This exports two additional environment variables: SSL_CLIENT_CERT and
        #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
        #     server (always existing) and the client (only existing when client
        #     authentication is used). This can be used to import the certificates
        #     into CGI scripts.
        #   o StdEnvVars:
        #     This exports the standard SSL/TLS related `SSL_*' environment variables.
        #     Per default this exportation is switched off for performance reasons,
        #     because the extraction step is an expensive operation and is usually
        #     useless for serving static content. So one usually enables the
        #     exportation for CGI and SSI requests only.
        #   o StrictRequire:
        #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
        #     under a "Satisfy any" situation, i.e. when it applies access is denied
        #     and no other module can change it.
        #   o OptRenegotiate:
        #     This enables optimized SSL connection renegotiation handling when SSL
        #     directives are used in per-directory context.
        #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>

        #   SSL Protocol Adjustments:
        #   The safe and default but still SSL/TLS standard compliant shutdown
        #   approach is that mod_ssl sends the close notify alert but doesn't wait for
        #   the close notify alert from client. When you need a different shutdown
        #   approach you can use one of the following variables:
        #   o ssl-unclean-shutdown:
        #     This forces an unclean shutdown when the connection is closed, i.e. no
        #     SSL close notify alert is send or allowed to received.  This violates
        #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
        #     this when you receive I/O errors because of the standard approach where
        #     mod_ssl sends the close notify alert.
        #   o ssl-accurate-shutdown:
        #     This forces an accurate shutdown when the connection is closed, i.e. a
        #     SSL close notify alert is send and mod_ssl waits for the close notify
        #     alert of the client. This is 100% SSL/TLS standard compliant, but in
        #     practice often causes hanging connections with brain-dead browsers. Use
        #     this only for browsers where you know that their SSL implementation
        #     works correctly.
        #   Notice: Most problems of broken clients are also related to the HTTP
        #   keep-alive facility, so you usually additionally want to disable
        #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
        #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
        #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
        #   "force-response-1.0" for this.
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
</IfModule>

```

---

### Post by jay30 on 2014-02-26
> **Doug S said:**
> Delete the stuff you put in http.conf. That file is supposed to be empty and is only present for legacy reasons. It is not even there at all in the more recent Ubuntu.

Restore ports.conf. I think that is why you are getting the strange file fetch location.

I don't know about the changes you made to apache2.conf, but I don't see such changes mentioned in the phpmyadmin chapter of the ubuntu serverguide, which is the only reference I use.

The reason I put that line in httpd.conf is because I was getting the following warning/error when I restarted Apache:
"Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName".  Someone suggested this fix (ie. putting that line in httpd.conf) and it resolved the problem.  If I take that line out now the warning/error message returns.

I added the listen 8080 to ports.conf because my ISP blocks port 80.  I removed the NameVirtualHost *:80 at the suggestion of this thread.

---

### Post by Doug S on 2014-02-26
> **jay30 said:**
> The reason I put that line in httpd.conf is because I was getting the following warning/error when I restarted Apache:
"Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName".  Someone suggested this fix (ie. putting that line in httpd.conf) and it resolved the problem.  If I take that line out now the warning/error message returns.Yes, You don't have a fqdn, so the warning is to be expected.> **jay30 said:**
> I added the listen 8080 to ports.conf because my ISP blocks port 80.Yes, but I thought we were trying to port forward from external 8080  to internal 80. Anyway, if I do that then I get the problem:```
doug@s15:/etc/apache2$ [COLOR=#ff0000]tail -5 /var/log/apache2/error.log[/COLOR]
[Wed Feb 26 08:23:29 2014] [notice] caught SIGTERM, shutting down
[Wed Feb 26 08:23:30 2014] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.9 with Suhosin-Patch mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Feb 26 08:23:55 2014] [error] [client 192.168.111.101] File does not exist: /etc/apache2/htdocs
[Wed Feb 26 08:23:55 2014] [error] [client 192.168.111.101] File does not exist: /etc/apache2/htdocs
[Wed Feb 26 08:23:55 2014] [error] [client 192.168.111.101] File does not exist: /etc/apache2/htdocs
```I suspect I would need a corresponding entry in the "/etc/apache2/sites-available/default" file. (again, but I thought we were trying to do it with port 80 internally)> **jay30 said:**
> I removed the NameVirtualHost *:80 at the suggestion of this thread.O.K. I defer to CharlesA on that one (and I tried it).

---

### Post by Doug S on 2014-02-26
> **Doug S said:**
> I suspect I would need a corresponding entry in the "/etc/apache2/sites-available/default" file.If I do that, then it works:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]head -2 default[/COLOR]
<VirtualHost *:8080>
 ServerAdmin webmaster@localhost
```

---

### Post by jay30 on 2014-02-26
I have confirmed that my apache2.conf, ports.conf, default and default-ssh files are all as default (as you have provided) with the following exceptions:

apache2.conf
     Added:  Include /etc/phpmyadmin/apache2.conf (to eliminate warning at apache restart)

ports.conf
     Added:  Listen 8080
     Removed :  NameVirtualHost *:80  (at your suggestion - should I put this back in?)

---

### Post by jay30 on 2014-02-26
What is Fndq?  So I am ok to get that warning/error on apache restart?
what you say about not needing the listen 8080 in ports.conf makes sense, however, if I remove that line and restart and try browsing to the modem address/port 8080 from outside I get a server cannot be found message.  At least when I have the listen 8080 line I can see the apache server from outside (I just can't bring up any pages).

---

### Post by jay30 on 2014-02-26
Have made some encouraging progress.  I changed the line in the default file from "<VirtualHost *:80>" to "<VirtualHost *:8080>".  I still have both Listen 80 and Listen 8080 in ports.conf.

From outside I can now browse to my info.php file (via ModemIP:8080/info.php).  I can also browse to the index.html file that says "It Works!" (via ModemIP:8080/index.html).  However, I cannot browse to the index.php file (via ModemIP:8080/index.php) - I get a google chrome could not connect.  I assume this is the file of my wordpress site.  Also, from inside I can access wp admin by going to internal IP of server followed by /wp-admin. I can't get this to work either from outside (via ModemIP:8080/wp-admin).

---

### Post by CharlesA on 2014-02-26
> **jay30 said:**
> I have confirmed that my apache2.conf, ports.conf, default and default-ssh files are all as default (as you have provided) with the following exceptions:

apache2.conf
     Added:  Include /etc/phpmyadmin/apache2.conf (to eliminate warning at apache restart)


That's fine because you have phpmyadmin installed and I don't use it. :)

> **jay30 said:**
> Have made some encouraging progress.  I changed the line in the default file from "<VirtualHost *:80>" to "<VirtualHost *:8080>".  I still have both Listen 80 and Listen 8080 in ports.conf.

From outside I can now browse to my info.php file (via ModemIP:8080/info.php).  I can also browse to the index.html file that says "It Works!" (via ModemIP:8080/index.html).  However, I cannot browse to the index.php file (via ModemIP:8080/index.php) - I get a google chrome could not connect.  I assume this is the file of my wordpress site.  Also, from inside I can access wp admin by going to internal IP of server followed by /wp-admin. I can't get this to work either from outside (via ModemIP:8080/wp-admin).

Where is info.php? /var/www/info.php?

It sounds like you need to work on your configuration. Can you post your wordpress config please.

I have never had to mess with ports with Apache or Nginx if I wanted to access it from a different port (8080, cuz my ISP blocks port 80), and set it up, so anything coming in and hitting port 8080, you be directed to the web server at 192.168.1.250, port 80.

EDIT: I just tested it on my 12.04 box and it works fine. See attached.

---

### Post by Doug S on 2014-02-26
> **CharlesA said:**
> I have never had to mess with ports with Apache or Nginx if I wanted to access it from a different port (8080, cuz my ISP blocks port 80), and set it up, so anything coming in and hitting port 8080, you be directed to the web server at 192.168.1.250, port 80.Yes, same here. And actually I have my external IP address port 8083 port forwarded to my internal test server port 80 so as to bypass my real server. I only did the stuff in my previous postings for the OP.

@ OP:
fqdn = Fully Qualified Domain Name. (I didn't think I needed to spell it out because it was right there in the line I was responding to.) And yes that warning message is O.K.

---

### Post by jay30 on 2014-02-26
Yes info.php is in /var/www.  Here is the /var/www/wp-config.php file...

```

<?php
/**
 * The base configurations of the WordPress.
 *
 * This file has the following configurations: MySQL settings, Table Prefix,
 * Secret Keys, WordPress Language, and ABSPATH. You can find more information
 * by visiting {@link http://codex.wordpress.org/Editing_wp-config.php Editing
 * wp-config.php} Codex page. You can get the MySQL settings from your web host.
 *
 * This file is used by the wp-config.php creation script during the
 * installation. You don't have to use the web site, you can just copy this file
 * to "wp-config.php" and fill in the values.
 *
 * @package WordPress
 */


// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');


/** MySQL database username */
define('DB_USER', 'wordpressuser');


/** MySQL database password */
define('DB_PASSWORD', 'xxxxxx');


/** MySQL hostname */
define('DB_HOST', 'localhost');


/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');


/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');

/**#@+
 * Authentication Unique Keys and Salts.
 *
 * Change these to different unique phrases!
 * You can generate these using the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-k$ * You can change these at any point in time to invalidate all existing cookies. This will force all users to ha$ *
 * @since 2.6.0
 */
define('AUTH_KEY','put your unique phrase here');
define('SECURE_AUTH_KEY',  'put your unique phrase here');
define('LOGGED_IN_KEY',    'put your unique phrase here');
define('NONCE_KEY','put your unique phrase here');
define('AUTH_SALT','put your unique phrase here');
define('SECURE_AUTH_SALT', 'put your unique phrase here');
define('LOGGED_IN_SALT',   'put your unique phrase here');
define('NONCE_SALT',       'put your unique phrase here');


/**#@-*/


/**
 * WordPress Database Table prefix.
 *
 * You can have multiple installations in one database if you give each a unique
 * prefix. Only numbers, letters, and underscores please!
 */
$table_prefix  = 'wp_';


/**
 * WordPress Localized Language, defaults to English.
 *
 * Change this to localize WordPress. A corresponding MO file for the chosen
 * language must be installed to wp-content/languages. For example, install
 * de_DE.mo to wp-content/languages and set WPLANG to 'de_DE' to enable German
 * language support.
 */
define('WPLANG', '');


/**
 * For developers: WordPress debugging mode.
 *
 * Change this to true to enable the display of notices during development.
 * It is strongly recommended that plugin and theme developers use WP_DEBUG
 * in their development environments.
 */
define('WP_DEBUG', false);


/* That's all, stop editing! Happy blogging. */


/** Absolute path to the WordPress directory. */
if ( !defined('ABSPATH') )
define('ABSPATH', dirname(__FILE__) . '/');


/** Sets up WordPress vars and included files. */
require_once(ABSPATH . 'wp-settings.php');



```

---

### Post by jay30 on 2014-02-26
Actually, as it turns out I can make some connection to the server from outside while leaving the line in the default file as <VirtualHost *:80> (rather than changing to 8080).  When I do leave it as 80, internal access to the server and wordpress works much better.  Otherwise I need to specify port 8080 even if accessing from internal.  Anyways with the <VirtualHost*:80> in the default file I can access the index.html (it works) file from outside by browsing to ModemIP:8080/index.html.  However, can't for whatever reason open the info.php file or get to wordpress login (ModemIP:8080/wp-login.php).

---

### Post by CharlesA on 2014-02-26
It's probably set up to redirect logins to ssl (443). Check that out.

---

### Post by jay30 on 2014-02-26
Where would I look for that and could/should it be changed?

---

### Post by CharlesA on 2014-02-26
It should be in the wordpress config, but I thought all the newer versions defaulted to SSL when accessing the login or admin areas.

How does it work when you access it locally?

---

### Post by jay30 on 2014-02-26
From the internal side I just browse to IP/wp-login.php. This takes me to the wordpress login screen from which I can login and manage the site.  Or I can browse to IP/index.php and view my web page.  Neither of these two things want to work from external using ModemIP:8080/wp-login.php (get a not found error) or ModemIP:8080/index.php.  But from outside I can browse to ModemIP:8080/index.html

---

### Post by CharlesA on 2014-02-26
But do you switch to https for wp-login.php? 

The browser should tell you. If you get an error, check the apache logs and see what they say.

Sidenote: Have you considered getting a VPS to run wordpress and whatnot on?

---

### Post by jay30 on 2014-02-27
> **CharlesA said:**
> But do you switch to https for wp-login.php? 

The browser should tell you. If you get an error, check the apache logs and see what they say.

Sidenote: Have you considered getting a VPS to run wordpress and whatnot on?


No i do not have to use https.  Also, when trying to connect to wp-login.php or index.php from external (although it won't bring up the page) does not appear to put anything into the error.log.  However, on 2 occasions now I have had something come up when trying to go to wp-login.php (and I haven't made any changes).  However it does not bring up the same wordpress login that I would get when opening wp-login.php from internal.  Rather it is a simpler screen with a login userid and password field.  When I enter my userid and password I get the browser eventually telling me it can't open page.  

I am am not sure what VPS is but I will look it up.

---

### Post by CharlesA on 2014-02-27
> **jay30 said:**
> 
I am am not sure what VPS is but I will look it up.

Have a read here:
[http://lowendbox.com/blog/ramnode-3-48-month-256mb-ssd-kvm-vps-in-atlanta-seattle-and-netherlands/](http://lowendbox.com/blog/ramnode-3-48-month-256mb-ssd-kvm-vps-in-atlanta-seattle-and-netherlands/)

VPS is just a virtual server. I have my website hosted on one.

The only issue is they are unmanaged, but then you wouldn't have to worry about dealing with port 8080 and all that other stuff.

---

### Post by jay30 on 2014-02-27
Actually I guess the login screen that comes up is a login to the website. While when opening wp-login.php from internal I get the wordpress site admin login screen.

---

### Post by CharlesA on 2014-02-27
That's kinda... odd. Are you sure it is hitting the right web server? Check the access logs for apache.

EDIT: Have you viewed the source of the page you get?

---

### Post by jay30 on 2014-02-27
Yes I only have the one web server on that machine (as far as I know).  The other thing is that from outside I cannot access anything via internet explorer although can get some of these pages via chrome and safari.  So when I do go to wp-login.php from outside it takes a minute but it does eventually bring up a login screen to my website (although not the same as the wordpress admin login I get when going from inside).  If I try to login from the outside at this page it fails because it then appears to try and open <internal IP>/wp-login.php (and of course it can't do that).  So I am lost as to what to do/try.  Frustrating because I can obviously connect to the server from outside just can't seem to access my site or any administration for it.

---

### Post by Doug S on 2014-02-27
O.K. so you seem to have gotten your port forwarding to work properly. What settings did you end up with on your router?
Wordpress is going to interpret the external forwarded requests as for a different virtual host and it should (I say "should" because your setup seems odd to me) be looking for a related config file, such as "/etc/wordpress/config-
NAME_OF_YOUR_VIRTUAL_HOST.php."

---

### Post by CharlesA on 2014-02-27
> **Doug S said:**
> O.K. so you seem to have gotten your port forwarding to work properly. What settings did you end up with on your router?
Wordpress is going to interpret the external forwarded requests as for a different virtual host and it should (I say "should" because your setup seems odd to me) be looking for a related config file, such as "/etc/wordpress/config-
NAME_OF_YOUR_VIRTUAL_HOST.php."

I'm with Doug on this one. I know I've run into issues with wordpress in the past, but nothing like what you are experiencing.

It would help to see how you have your wordpress virtualhost set up.

---

### Post by jay30 on 2014-02-27
> **CharlesA said:**
> I'm with Doug on this one. I know I've run into issues with wordpress in the past, but nothing like what you are experiencing.

It would help to see how you have your wordpress virtualhost set up.

I can't believe how patient you guys are being with me - thank you.  A couple of other things to add at this point.  As I've said, I can browse to the index.html file from outside (the 'it works' page).  Anyways I edited the /var/www/index.html file to include and additional word - in particular 'it works boy!'.  Well, when I browse to the page again from outside (via ModemIP:8080/index.html) I do not get the 'it works boy'.  So it obviously isn't calling up the /var/www/index.html file.  I'm not sure where there is another index.html file.  Also, when I browse to the file from inside (internal IP address/index.html) I do get the 'it works boy!'  So when I try to get to my server from outside it is using a different directory?  Also, I see that in addition to having all the wordpress files (eg. wp-config.php) in the /var/www directory, there is also a wordpress directory at/near the root with the same/similar set of files.  Which set of files is or should it be using? Should the others be deleted?

One more thing - I don't know anything about the wordpress virtual host setup.  Am I missing a file?

---

### Post by jay30 on 2014-02-27
I guess I can see why I have 2 copies of all the wordpress files.  The instruction I followed when installing wordpress was fro digitaocean (perhaps that was a mistake). Anyways the instructions had me:

Download wordpress (wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz))
Unzip (tar -xzvf latest.tar.gz)
Copy files to website root (sudo sync -avP ~/wordpress/ /var/www/

---

### Post by CharlesA on 2014-02-27
> **jay30 said:**
> I can't believe how patient you guys are being with me - thank you.  A couple of other things to add at this point.  As I've said, I can browse to the index.html file from outside (the 'it works' page).  Anyways I edited the /var/www/index.html file to include and additional word - in particular 'it works boy!'.  Well, when I browse to the page again from outside (via ModemIP:8080/index.html) I do not get the 'it works boy'.  So it obviously isn't calling up the /var/www/index.html file.  I'm not sure where there is another index.html file.  Also, when I browse to the file from inside (internal IP address/index.html) I do get the 'it works boy!'  So when I try to get to my server from outside it is using a different directory?  Also, I see that in addition to having all the wordpress files (eg. wp-config.php) in the /var/www directory, there is also a wordpress directory at/near the root with the same/similar set of files.  Which set of files is or should it be using? Should the others be deleted?

One more thing - I don't know anything about the wordpress virtual host setup.  Am I missing a file?

> **jay30 said:**
> I guess I can see why I have 2 copies of all the wordpress files.  The instruction I followed when installing wordpress was fro digitaocean (perhaps that was a mistake). Anyways the instructions had me:

Download wordpress (wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz))
Unzip (tar -xzvf latest.tar.gz)
Copy files to website root (sudo sync -avP ~/wordpress/ /var/www/

Judging from the above, it looks like you just installed wordpress in the default site. That should be fine.

Instructions are here btw:
[https://codex.wordpress.org/Installing_WordPress](https://codex.wordpress.org/Installing_WordPress)

That still doesn't explain why it is redirecting unless you told wordpress to use the IP of the local machine during install.

---

### Post by jay30 on 2014-02-28
My /etc/apache2/httpd.conf file has one line - ServerName Localhost.  Could this be causing the redirect?

---

### Post by Doug S on 2014-02-28
I am not an expert on wordpress, and I  only have it installed and working because I proofread the [Ubuntu serverguide wordpress]("https://help.ubuntu.com/13.10/serverguide/wordpress.html") addition (and to compound things, there are mistakes in the Serverguide stuff, [fixed]("http://bazaar.launchpad.net/~ubuntu-core-doc/serverguide/trusty/revision/172") for 14.04, but yet to be published). Since you installed a different way, things might be different for you. All of my wordpress related files are in /usr/share/wordpress, but I also have a /etc/apache2/sites-available/wordpress.conf file.

All I was trying to say in my earlier posting was that I get as shown in the attached when I try to access from outside, and another config file would be required to make it work for my case. And this is all I have now:```
doug@s15:~/sguide-1404/saucy/serverguide/C$ [COLOR=#ff0000]ls -l /etc/wordpress[/COLOR]
total 16
-rw-r--r-- 1 root root  209 Jan 14 11:52 config-localhost.php
-rw-r--r-- 1 root root  209 Jan 14 11:53 [COLOR=#ff0000]config-s15.smythies.com.php[/COLOR]   <<< That is the internal name for the server that external port 8083 forwards to.
-rw-r--r-- 1 root root  898 Jan  4  2012 htaccess
-rw-r--r-- 1 root root 1928 Jan  4  2012 wp-config.php
```For your case I'm not sure. Note: I am disabling the port 8083 forwarding on my system before posting this.

---

### Post by CharlesA on 2014-02-28
I'm pretty stumped as well.

I kinda want to install wordpress and see if mine works as expected, but I've always used nginx instead of apache.

@OP: I am assuming you are using this howto:
[https://www.digitalocean.com/community/articles/how-to-install-wordpress-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-wordpress-on-ubuntu-12-04)

Which makes no specific config for wordpress, and looks like it just uses the default apache config.

---

### Post by jay30 on 2014-02-28
Yes, that is the link I used at digital ocean to get wordpress install instruction.  I seem to be hearing I should have some sort of a virtual host name file or something.  Should there be a file somewhere (maybe in the sites-available or sites-enabled directory) that is specific to my host/site?  Because I don't have such a file. There is the default file but no file I know of that is specific to e virtual host. Should there be one somewhere?  Also, I have searched around in my server for any other index.html files and can't seem to find one.  As I have confirmed it is not calling up the /var/www/index.html one when I browse from outside.  Any idea where it might be finding this other index.html file?

---

### Post by SeijiSensei on 2014-02-28
> **CharlesA said:**
> Which makes no specific config for wordpress, and looks like it just uses the default apache config.

I have a WordPress blog (linked in my signature) that uses a name-based virtual host. Install WP itself was simply a matter of extracting the files from wordpress-someversion.zip and making the extracted wordpress directory the DocumentRoot for the site in Apache.  The index.php file in that wordpress directory becomes the index page for the blog.

The relevant parts of the configuration file look like this:
```

<VirtualHost    *:80>
ServerAdmin     webmaster@politicsbythenumbers.org
DocumentRoot    /home/seiji/sites/politicsbythenumbers/wordpress
ServerName      politicsbythenumbers.org
ErrorLog        logs/error_log-politicstats
TransferLog     logs/access_log-politicstats
CustomLog       logs/referer_log-politicstats "%h: %{referer}i -> %U"

<Directory      "/home/seiji/sites/politicsbythenumbers/wordpress">
AllowOverride   All
Options         All
</Directory>

[other stuff if relevant]

</VirtualHost>

```

Of course, the DocumentRoot can be anywhere in the file system.  For sites without name-based virtual hosts, WordPress can be installed to /var/www then referenced from the [http://server/wordpress](http://server/wordpress) URL.

---

### Post by CharlesA on 2014-02-28
Thanks, SeijiSensei. I've always set my sites up with virtualhost (or server blocks ala Nginx).

@OP: Check the admin panel locally cuz I think there is a setting that is configured when you set up the site to point to a specific host/ip address, but as I haven't really played much with wordpress, I could be wrong.

I still stand behind the idea of getting a VPS and running your wordpress install there because you won't have to mess with any (not fun) port forwarding to get around a blocked port 80.

---

### Post by jay30 on 2014-03-01
Ok, progress.  If I login to wordpress admin from inside and go to settings/general there are two fields there in which to put a web address related to the site.  They are:

Wordpress Address (URL)
Site Address (URL)

these she were both set as the internal IP address of the internal server.  If I change these both to ModemIP:8080 then I can actually access wp admin from outside (via ModemIP:8080/wp-login.php).  However, with these settings I can no longer access wp admin from inside.  Perhaps I can't have it both ways?

---

### Post by CharlesA on 2014-03-02
Set up a virtualhost and use a domain name and not an IP address.

---

### Post by jay30 on 2014-03-02
> **CharlesA said:**
> Set up a virtualhost and use a domain name and not an IP address.

How do I go about doing that...

---

### Post by CharlesA on 2014-03-02
[https://www.linode.com/wiki/index.php/Configure_apache_to_use_virtual_hosts_on_ubuntu_server](https://www.linode.com/wiki/index.php/Configure_apache_to_use_virtual_hosts_on_ubuntu_server)

---

### Post by jay30 on 2014-03-03
Thank you Charles, I will give it a go.

---

### Post by CharlesA on 2014-03-03
Good luck! Post back if you run into problems.

---

