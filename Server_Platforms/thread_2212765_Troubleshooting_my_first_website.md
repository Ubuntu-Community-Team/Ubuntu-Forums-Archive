---
title: "Troubleshooting my first website"
date: 2014-03-23
forum: Server Platforms
---

### Post by Drone4four on 2014-03-23
I can’t figure out how to get my new Apache server to show my homepage (index.html).

Here is what I have done so far.

I paid for a digitalocean droplet (LAMP on 12.04 image) and followed a number of guides.  

I first successfully secured my server by creating an rsa key public/private pair without a passphrase.  I used two similar guides. One was [“How To Set Up SSH Keys”]("https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2"), and the other was, [“How To Use SSH Keys with DigitalOcean Droplets”]("https://www.digitalocean.com/community/articles/how-to-use-ssh-keys-with-digitalocean-droplets"). 

As per this guide [here]("https://library.linode.com/hosting-website"), I then installed Apache, backed up apache2.conf before changing some of the IfModule values to better optimize Apache for my 512MB droplet.  Here are the default IfModule properties and values:

```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```

I changed my new apache.conf IfModule values to this:

```
<IfModule mpm_prefork_module>
    StartServers          2
    MinSpareServers       6
    MaxSpareServers      12
    MaxClients           80
    MaxRequestsPerChild  3000
</IfModule>

```

I then configured my Name-based Virtual Host using a2dissite and made a number of directories in a public folder in my home directory, like public, log and backup.  I also made the top public directory readable and accessible by all users recursively. The contents of /etc/apache2/sites-available/[withheld].com.conf look like this:
```

# domain: [withheld].com
# public: /home/thor/public/[withheld].com

<VirtualHost *:80>
  # Admin email, Server Name (domain name), and any aliases
  ServerAdmin webmaster@[withheld].com
  ServerName  www.[withheld].com
  ServerAlias [withheld].com

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/thor/public/[withheld].com/public

  # Log file locations
  LogLevel warn
  ErrorLog  /home/thor/public/[withheld].com/log/error.log
  CustomLog /home/thor/public/[withheld].com/log/access.log combined
</VirtualHost>

```

a2ensite informs me that site [withheld].com.conf is already enabled:

```
 
/etc/apache2/sites-available# a2ensite [withheld].com.conf
Site [withheld].com.conf already enabled
/etc/apache2/sites-available#

```

I installed ftpd on the host and successfully logged into my site via ftp from my PC with an ftp client (Konqueror).  It was here that I transfered my index.html, css and images to my public directory.

I restarted the apache service. Visiting my site in my browser, I don’t get a Not Found Error. Instead I get an empty root folder.  See [here]("http://i.imgur.com/JQinHBz.jpg").

I think I installed MySQL, but didn’t bother optimizing it because I don’t intend on using a database any time soon.  Ditto for PHP.

What further information could I provide here to troubleshoot and get my first website functioning the way it should?

Thanks for your attention.

---

### Post by Drone4four on 2014-03-23
Ugh:  After spending the better part of an hour and a half crafting the above post, I discovered the simple and obvious solution.  The solution was as simple as placing my index.html et. al. in this public folder: 

```
/home/thor/public/[withheld].com/public
```

...and not this one:

```
/home/thor/public/
```

---

### Post by Drone4four on 2014-04-23
I'm re-opening this thread because I destroyed my old droplet and started over by creating a new one.  I am setting up my new droplet along the same lines as my old one, with similar configuration files and such.  

First of all I was surprised to open my new apache2.conf under /etc/apache2/ to discover no instance of 'IfModule' or 'mpm_prefork_module'.  Here is my apache2.conf in full:

```

$ cat /etc/apache2/apache2.conf 
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

<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
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
$ 

```

Where are the rest of the contents of apache2.conf?

So I held my breath and continued with setting up my apache server.  I entered: $ sudo service apache2 restart and tried entering the a2dissite default command.  Here it is:

```

$ sudo service apache2 restart
 * Restarting web server apache2
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive globally to suppress this message
                                                                         [ OK ]
$ sudo a2dissite default
ERROR: Site default does not exist!
$

```
I was thinking that maybe this means I should start my webserver before trying to restart it:

```

$ sudo service apache2 start
 * Starting web server apache2                                                     * 
$ sudo a2dissite default
ERROR: Site default does not exist!
$ 

```

I figure there is no point in even trying to using a2ensite, but here it is anyway:

```

$ sudo a2ensite [withheld].com.conf
ERROR: Site [withheld].com does not exist!
$

```

It's worth noting that my old droplet was 12.04 and my new one is 14.04.

---

### Post by sandyd on 2014-04-23
The changes are due to apache 2.2 (ubuntu 12.04) being upgrade to 2.4 (ubuntu 14.04).
Please read [http://httpd.apache.org/docs/2.4/upgrading.html](http://httpd.apache.org/docs/2.4/upgrading.html)

The configuration is now located in /etc/apache2/mods-enabled (though event seems to be the default mpm now!)
The default mpm can be changed through the use of a2enmod/a2dismod. Only one mpm should be enabled at a time.

---

### Post by Drone4four on 2014-04-26
Thank-you, **sandyd**, for the clarification on the Apache 2.2 setup differing from Apache 2.4.  I find the Apache upgrading docs you pointed out to be a little over my head.  I'll just wait for Linode to update their documentation for getting Apache up and running on Ubuntu 14.04.  In the meantime I'll just run Ubuntu 12.04.  

I'll mark this thread as solved again.

---

### Post by Drone4four on 2014-05-18
I'm at it again.  

This time I am setting up my webserver on Ubuntu 14.04 x64 server edition.  

I followed a guide called, "[How To Install Linux, Apache, MySQL, PHP (LAMP) stack on Ubuntu 14.04]("https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04")", except I didn’t bother with PHP or MySQL.  I was surprised to discover that this guide doesn’t describe to readers how to actually configure the server to create demo pages and a public_html file tree in /var/www/ .  There are other guides for 12.04  which describe how to do this.  optimize apache for 512MBs servers .  Maybe apache 2.4.x doesn’t need optimization.  This DigitalOcean article also doesn’t describe how to use the a2ensite tool to enable my site, nor how to reload/restart apache.  To perform these tasks, I found a guide called, “[How To Set Up Apache Virtual Hosts on Ubuntu 14.04 LTS]("https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts")”  used it because it is more thorough and does most of the things the initial guide doesn’t.  Since this guide is actually tailored to beginner sysadmins who want to set up two or more Virtual Hosts, I was mindful to avoid duplicating every recommended command.  Like I only created one directory structure, not two.  Likewise for granting permissions to said directory structure.

So yeah, by the end of this guide I can’t access my homepage.  When I enter my ip address in my browser, I get the Apache2 Ubuntu Default Page.  So this indicates that apache was installed successfully.  But what I am trying to do is access the index.html I placed in /var/www/[withheld].com/public_html/ .  What am I doing wrong?

Here are the steps I performed so far.

```
sudo mkdir -p /var/www/[withheld].com/public_html 
```
```
sudo chown -R $USER:$USER /var/www/[withheld].com/public_html 
```

```
sudo chmod -R 755 /var/www 
```

With vim, I created a fiile called, 

```
/var/www/example.com/public_html/index.html 
```

...with these contents:
```

<html>
  <head>
    <title>Welcome to my Humble Abode</title>
  </head>
  <body>
    <h1>Success!  My virtual host is working!</h1>
  </body>
</html>

```
Then I entered:```
 sudo cp /etc/apache2/sites-available/000-default.conf  /etc/apache2/sites-available/[withheld].com.conf 
```
With root privileges with vim I opened /etc/apache2/sites-available/example.com.conf
By default it looked like this:
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
I made changes to that file so it now looks like this:
```

<VirtualHost *:80>
        ServerAdmin webmaster@[withheld].com
        DocumentRoot /var/www/html
        ServerAlias www.[withheld].com
        DocumentRoot /var/www/[withheld].com/public_html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
```
sudo a2ensite [withheld].com.conf
```
The output for this command: ```
sudo service apache2 restart
```
was:
```
[OK]
```
The contents of my /etc/hosts is:
```

127.0.0.1       localhost
127.0.1.1       1404ange 1404ange
107.170.8.119   [withheld].com

```

Now when I test my results by entering my ip in the address bar in my browser, I get Apache2 Ubuntu Default Page and not my index.html.  What am I doing wrong?

---

### Post by thnewguy on 2014-05-18
Why did you declare DocumentRoot twice in the same VirtualHost and point it at two different places? You should have just one DocumentRoot declaration. Also, if you are addressing the server by IP address then it will always take you to the default website/page. Make sure you use your proper hostname, like [http://something.com](http://something.com), otherwise the ServerName and ServerAlias options will not work. Third: make sure you declare ServerName. You already have ServerAlias, but you are missing ServerName. Typically, if your ServerAlias is "www.somedomain.com" then ServerName will be "somedomain.com".

---

### Post by Drone4four on 2014-05-21
I commented out the first my two DocumentRoot declarations.  I also entered a ServerAlias. My /etc/apache2/sites-available/[withheld].com.conf now looks like this:

```
<VirtualHost *:80>
 
       ServerAdmin webmaster@[withheld].com
        # DocumentRoot /var/www/html
        ServerAlias [withheld].com
        ServerName [withheld].com
        DocumentRoot /var/www/[withheld].com/public_html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

My index.html still isn't showing the contents of /var/www/example.com/public_html/index.html

I don't understand your second point, **thnewguy**.  You wrote:
> Also, if you are addressing the server by IP address then it will always take you to the default website/page.
I have been addressing the server by IP address in my web browser.  This takes me to the Ubuntu Default Page.  Should I be typing into the address bar, [http://myhostname.com](http://myhostname.com) ? As in, the same hostname indicated in my /var/www/[withheld].com/public_html ? 

If I understand you correctly, then there I see a major conflict.  

The hostname I have been playing with in this droplet that I am troubleshooting, is actually a domain name I have already bound successfully to a different droplet (a 12.04 server). This is me being shortsighted and stupid.  Should I destroy my 14.04 droplet and go through the apache custimization process again with a different domain name?

By the way, **thenewguy**, could you please elaborate on what you mean by this: >  Make sure you use your proper hostname, like [http://something.com](http://something.com), otherwise the ServerName and ServerAlias options will not work

---

### Post by SeijiSensei on 2014-05-22
"Name-based" virtual hosts use the hostname specified in the URL to determine which configuration file to use.  Suppose you were hosting [www.example.com](www.example.com).  You'd need a <VirtualHost> stanza like this:
```

<VirtualHost *:80>
    ServerName www.example.com
    DocumentRoot /path/to/some/directory
    [other stuff if needed]
</VirtualHost>

```
If you use an IP address in the URL, then there is nothing to match the "ServerName" on, and you get the default web page as a result.

For testing purposes, you can create an entry in /etc/hosts on the client machine.  Edit that file as root with sudo and add:
```

10.10.10.10     www.yourdomain.com

```
replacing "10.10.10.10" with the IP address of your test server, and "www.yourdomain.com" with the hostname you wish to use when accessing the site over the Internet.

---

