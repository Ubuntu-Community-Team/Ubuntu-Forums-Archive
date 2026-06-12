---
title: "Apache w/ RoR fail: Name or service not known: Could not resolve host name &amp; URL help"
date: 2010-05-16
forum: Server Platforms
---

### Post by Zeophlite on 2010-05-16
[SIZE="6"]Apache w/ Ruby problems[/SIZE]

I'm having trouble getting my Ruby on Rails code to work.  I've installed apache, along with php and mysql, and now I've installed ruby, gems (and through that rails) and finally passenger to get ruby and apache to work together.

I've mostly worked through [this page]("http://railsforum.com/viewtopic.php?id=29596") to try and get it all working, but using apt-get to get gems.

I created a test page called myapp, and using its server stuff, I can get a page displayed in my browser (by typing http://<serverIP>:3000/ )
```

cd ~/rails
rails myapp -d mysql
cd myapp
script/generate controller hello index
script/server

```

But I can't get it to work through Apache.  I get the above "name or service not known" error, which I can't seem to remove.

I've also installed redmine to /home/daniel/redmine , which also works under its own server, but not through apache.

[SIZE="6"]URL and Domain name[/SIZE]

I don't have a domain name address yet, but eventually I want to have the following structure.  The first column is what I want to type in now, the second is where it redirects to and the third is what I want to type in once I have my domain name.

http://<serverIP>/index.html -> /var/www/index.html -> http://www.<domainname>/index.html
http://<serverIP>/phpmyadmin/ -> /var/www/phpmyadmin/ -> http://phpmyadmin.<domainname>/
http://<serverIP>/~<user>/index.html -> /home/<user>/public_html/index.html -> http://<user>.<domainname>/index.html
http://<serverIP>/redmine/ -> /home/daniel/redmine/ -> http://redmin.<domainname>/

But I'm at a loss of how to do that.  What would I need to do now to get the first two columns?  And what would I need to change to get all 3 columns.


[SIZE="6"]Output[/SIZE]
Here's the output I've been getting:

```

**daniel@Mustrum:~$ cd /etc/apache2/**
**daniel@Mustrum:/etc/apache2$ ls**
apache2.conf  conf.d  envvars  httpd.conf  magic  mods-available  mods-enabled  ports.conf  sites-available  sites-enabled

**daniel@Mustrum:/etc/apache2$ cd sites-available/**
**daniel@Mustrum:/etc/apache2/sites-available$ ls**
default  default-ssl  myapp  redmine
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite redmine**
Site redmine already disabled
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite myapp**
Site myapp disabled.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite default**
Site default already disabled
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite default-ssl**
Site default-ssl already disabled
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2ensite default**
Enabling site default.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload**
 * Reloading web server config apache2                                                                                                                 [ OK ]

[COLOR="DarkGreen"]At this point, 127.0.0.1:80 loads the default apache site perfectly[/COLOR]

**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite default**
Site default disabled.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2ensite myapp**
Enabling site myapp.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload**
 * Reloading web server config apache2                                                                                                                        [Mon May 17 00:49:34 2010] [error] (EAI 2)Name or service not known: Could not resolve host name :*80 -- ignoring!
                                                                                                                                                       [ OK ]

[COLOR="DarkGreen"]At this point, 127.0.0.1:80 doesn't work[/COLOR]

**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite myapp**
Site myapp disabled.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2ensite redmine**
Enabling site redmine.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload**
 * Reloading web server config apache2                                                                                                                        [Mon May 17 00:50:08 2010] [error] (EAI 2)Name or service not known: Could not resolve host name :*80 -- ignoring!
                                                                                                                                                       [ OK ]

[COLOR="DarkGreen"]At this point, 127.0.0.1:80 still doesn't work[/COLOR]

**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite myapp**
Site myapp already disabled
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2dissite redmine**
Site redmine disabled.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo a2ensite default**
Enabling site default.
Run '/etc/init.d/apache2 reload' to activate new configuration!
**daniel@Mustrum:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload**
 * Reloading web server config apache2                                                                                                                 [ OK ]

[COLOR="DarkGreen"]At this point, 127.0.0.1:80 is working again[/COLOR]

**daniel@Mustrum:/etc/apache2/sites-available$ cd ~**
**daniel@Mustrum:~$ cd rails/**
**daniel@Mustrum:~/rails$ ls**
myapp
**daniel@Mustrum:~/rails$ cd myapp/**
**daniel@Mustrum:~/rails/myapp$ ls**
app  config  db  doc  lib  log  public  Rakefile  README  script  test  tmp  vendor
**daniel@Mustrum:~/rails/myapp$ script/server**
=> Booting WEBrick
=> Rails 2.3.5 application starting on [http://0.0.0.0:3000](http://0.0.0.0:3000)
=> Call with -d to detach
=> Ctrl-C to shutdown server
[2010-05-17 00:51:41] INFO  WEBrick 1.3.1
[2010-05-17 00:51:41] INFO  ruby 1.8.7 (2010-01-10) [x86_64-linux]
[2010-05-17 00:51:41] INFO  WEBrick::HTTPServer#start: pid=1908 port=3000

[COLOR="DarkGreen"]At this point, 127.0.0.1:3000 is working[/COLOR]

^C[2010-05-17 00:53:43] INFO  going to shutdown ...
[2010-05-17 00:53:43] INFO  WEBrick::HTTPServer#start done.
Exiting

```


[SIZE="6"]Files[/SIZE]
Here are my important files.  If you need to see any more, please just ask.

```

**daniel@Mustrum:/etc/apache2/mods-enabled$ cat passenger.load**
LoadModule passenger_module /var/lib/gems/1.8/gems/passenger-2.2.11/ext/apache2/mod_passenger.so
**daniel@Mustrum:/etc/apache2/mods-enabled$ cat passenger.conf**
PassengerRoot /var/lib/gems/1.8/gems/passenger-2.2.11
PassengerRuby /usr/bin/ruby1.8
**daniel@Mustrum:/etc/apache2/mods-enabled$ cd ../sites-available**
**daniel@Mustrum:/etc/apache2/sites-available$ cat myapp**
<VirtualHost :*80>
   ServerName myapp
   DocumentRoot /home/daniel/rails/myapp/public
</VirtualHost>

**daniel@Mustrum:/etc/apache2/sites-available$ cat redmine**
<VirtualHost :*80>
   DocumentRoot /home/daniel/redmine/public
   RailsEnv production
   RailsBaseURI /redmine
</VirtualHost>

**daniel@Mustrum:/etc/apache2/sites-available$ cat default**
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
**daniel@Mustrum:/etc/apache2/sites-available$ cd ../**
**daniel@Mustrum:/etc/apache2$ ls**
apache2.conf  conf.d  envvars  httpd.conf  magic  mods-available  mods-enabled  ports.conf  sites-available  sites-enabled
**daniel@Mustrum:/etc/apache2$ cat httpd.conf**
ServerName localhost

**daniel@Mustrum:/etc/apache2$ cat ports.conf**
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

#NameVirtualHost *:80
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

**daniel@Mustrum:/etc/apache2$ cat apache2.conf**
#
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
**daniel@Mustrum:/etc/apache2$**

```

Thanks for your help

---

### Post by Zeophlite on 2010-05-19
Hi,

I fixed it myself, mainly by reading the Apache documentation, as well as Redmine's.  I decided to post it in case anyone else has this problem.

I ended up fixing this problem by first making symbolic links in /var/www to my applications (public folder in ruby apps (redmine)), and then only having one site enabled:

```

[B]daniel@Mustrum:/var/www$ ls -l
[/B]total 8
-rw-r--r-- 1 root root 182 2010-05-13 05:33 index.html
-rw-r--r-- 1 root root  20 2010-05-13 07:41 info.php
lrwxrwxrwx 1 root root  21 2010-05-13 09:13 phpmyadmin ->  /usr/share/phpmyadmin
lrwxrwxrwx 1 root root  26 2010-05-18 20:07 redmine ->  /usr/share/redmine/public/
[B]daniel@Mustrum:/etc/apache2/sites-enabled$ ls -l
[/B]total 0
lrwxrwxrwx 1 root root 26 2010-05-18 19:40 000-default ->  ../sites-available/default

```
Specifically:

```

[B]daniel@Mustrum:~$ cat /etc/apache2/sites-available/default
[/B]<VirtualHost *:80>
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

    RailsEnv production
    RailsBaseURI /redmine
    <Directory "/var/www/redmine/">
        Allow from all
        Options -MultiViews
    </Directory>

</VirtualHost>

```Mainly the last paragraph in default.

My guess is that I simply create a new Virtual Host when I get my domain name, but I'll ask questions when I get there.

---

