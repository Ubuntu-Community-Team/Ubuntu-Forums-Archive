---
title: "Virtual host not working anymore"
date: 2016-04-22
forum: Server Platforms
---

### Post by ben203 on 2016-04-22
Hi,
Trying to run 2 websites on my server using the same IP. I had  this working the other day, but now both sites point to my first one.  Running Ubuntu 14.04 server using apache. Could someone point me in the  right direction to fix this? Conf file is as such:

```
NameVirtualHost *:80
<VirtualHost *:80>
ServerAdmin xxxx
ServerName firstsite.com
ServerAlias [www.firstsite.com]("http://www.firstsite.com")
 DocumentRoot /var/www/firstsite.com/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/firstsite.com/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
 <VirtualHost *:80>
ServerAdmin xxxx
ServerName secondsite.com
ServerAlias [www.secondsite.com]("http://www.secondsite.com")    
DocumentRoot /var/www/secondsite.com/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/secondsite.com/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

---

### Post by Habitual on 2016-04-22
Try this:
```
<NameVirtualHost firstsite.com:80>
<VirtualHost *:80>
ServerAdmin xxxx
ServerName firstsite.com
ServerAlias www.firstsite.com
DocumentRoot /var/www/firstsite.com/public_html
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/firstsite.com/public_html>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
</VirtualHost>

<VirtualHost secondsite.com*:80>
ServerAdmin xxxx
ServerName secondsite.com
ServerAlias www.secondsite.com
DocumentRoot /var/www/secondsite.com/public_html

<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/secondsite.com/public_html>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
</VirtualHost> 
```

See also [https://httpd.apache.org/docs/2.2/vhosts/name-based.html](https://httpd.apache.org/docs/2.2/vhosts/name-based.html)
[https://wiki.apache.org/httpd/CommonMisconfigurations](https://wiki.apache.org/httpd/CommonMisconfigurations)

---

### Post by ben203 on 2016-04-22
Thanks. I tried that and read the links but no luck. I had this working fine the other day, and made a change to one of the virtual hosts when I got a new URL. This is when the issue started. I deleted the 2nd host and readded to match the new URL, but it still shows the first site.

---

### Post by Habitual on 2016-04-22
I always use separate confs for separate sites in /etc/apache2/sites-available/

Sorry it didn't work out.

Where are you editing?

---

### Post by ben203 on 2016-04-22
I started with seperate configs, but at the moment they are in 000-default. It seems that whichever site has the wild card is the only one that displays. I can't get them to display separately.

---

### Post by volkswagner on 2016-04-22
+1 for separate conf files.

I'm not sure what "<VirtualHost secondsite.com*:80>" is supposed to do for you.
You should lead all of your vhost files with <VirtualHost *:80>
The asterisk indicates any ip address. I never used a domain name there, so I'm not sure how that behaves.

Technically you don't need a wildcard at all. When using separate vhost files, just make sure that your "default" site or "wildcard"
enabled site comes alphanumerically first in /etc/apache2/sites-available.

The way Apache responds to requests are as follows, it reads entire config file or directory, and displays the first match. If not match is
found then it displays/returns the site config file which comes first alphanumerically (which is why default install uses 000-default.conf).

Please remove the wild card, and list the site first in the file if that's the one you want displayed when no matching hostname is found.

NOTE: all responses so far (including this one) assume browser cache is not causing a problem, and you are correctly reloading or restarting apache2.

---

### Post by nerdtron on 2016-04-23
> **ben203 said:**
> Thanks. I tried that and read the links but no luck. I had this working fine the other day, and made a change to one of the virtual hosts when I got a new URL. This is when the issue started. I deleted the 2nd host and readded to match the new URL, but it still shows the first site.

And can you specify what errors are you having when accessing the new virtual host? Does the webpage returns an error? Does the apache error logs shows any error?

---

### Post by SeijiSensei on 2016-04-23
> **volkswagner said:**
> I'm not sure what "<VirtualHost secondsite.com*:80>" is supposed to do for you.
You should lead all of your vhost files with <VirtualHost *:80>
The asterisk indicates any ip address. I never used a domain name there, so I'm not sure how that behaves.

I think this is the crux of the problem.  If you have "*:80" then Apache interprets the site as a virtual host and relies on the ServerName/Alias directives.  If you specify a hostname or IP address like "www.example.com:80" or "10.10.10.10:80", then Apache binds that virtual host specification to the specified hostname or IP address.  This can be very useful on multi-homed machines.  For instance, on a gateway you can bind sites to the internal IP address so they can only be viewed by machines on the local network.

---

### Post by ben203 on 2016-04-23
> **volkswagner said:**
> +1 for separate conf files.

I'm not sure what "<VirtualHost secondsite.com*:80>" is supposed to do for you.
You should lead all of your vhost files with <VirtualHost *:80>
The asterisk indicates any ip address. I never used a domain name there, so I'm not sure how that behaves.

Technically you don't need a wildcard at all. When using separate vhost files, just make sure that your "default" site or "wildcard"
enabled site comes alphanumerically first in /etc/apache2/sites-available.

The way Apache responds to requests are as follows, it reads entire config file or directory, and displays the first match. If not match is
found then it displays/returns the site config file which comes first alphanumerically (which is why default install uses 000-default.conf).

Please remove the wild card, and list the site first in the file if that's the one you want displayed when no matching hostname is found.

NOTE: all responses so far (including this one) assume browser cache is not causing a problem, and you are correctly reloading or restarting apache2.

Ok,  I have re-seperated the entries and they are lead with <VirtualHost *:80>. I am using Ctrl+F5 to reset the browser, and am using webmin to restart apache.
This still isn't working.

Viewing the virtual host through webmin indicates that the hosts are there, and are somewhat correct, but I still cant get to the second site.
There are no errors, the url of the second site just displays the first.

---

### Post by volkswagner on 2016-04-23
Thanks for mentioning Webmin.

My last experience with Webmin was nearly 10 years ago. I got unexpected results, not
unlike what you are having. My particular problem was related to manually editing
apache files and also using webmin to create or modify vhosts.

I'm not sure if Webmin is your problem, but I can say diagnosing can be frustrating.

Webmin hasn't been supported by Ubuntu for many years. Yes you can install it and may never
realize any problems, but my personal experience was not good.

---

### Post by ben203 on 2016-04-24
> **volkswagner said:**
> Thanks for mentioning Webmin.

My last experience with Webmin was nearly 10 years ago. I got unexpected results, not
unlike what you are having. My particular problem was related to manually editing
apache files and also using webmin to create or modify vhosts.

I'm not sure if Webmin is your problem, but I can say diagnosing can be frustrating.

Webmin hasn't been supported by Ubuntu for many years. Yes you can install it and may never
realize any problems, but my personal experience was not good.

Now this actually makes sense. Assuming that this is the problem, how did you fix it? Was it an uninstall of webmin? I'm fairly new to Ubuntu so being able to see a GUI has helped me understand the system somewhat. Do you think another webserver would have less problems? Or maybe a reinstall of apache?

---

### Post by darkod on 2016-04-24
Right now I don't need to do any of that. If I'm not mistaken, webmin is not doing any actions unless you use it to perform an action. So for the time being you can simply leave it there and try not to use it.

Simply log in using ssh session and use the nano editor to edit the .conf files of both sites. Then save them and restart apache. Check if that helped.

---

### Post by ben203 on 2016-04-24
Tried this, no luck. Even did an uninstall/reinstall of apache to see if that helped, still no luck. It will still only let me bring up one site or the other. This is really frustrating.

---

### Post by volkswagner on 2016-04-25
Please post output of the following.

```
ls -alt /etc/apache2/sites-available
```
```
ls -alt /etc/apache2/sites-enabled
```
```
ls -alt /etc/apache2/conf-enabled
```
```
cat /etc/apache2/ports.conf
```
```
cat /etc/apache2/apache2.conf
```

Where did this line come from in your conf file?
```
NameVirtualHost *:80
```

I just checked my entire apache2 directory and that string doesn't exist in any files. I'm not sure it's a problem, but
it seems that directive may be deprecated or no longer needed.

Just to confirm, you are now using separate config files for each host, yes?

---

### Post by SeijiSensei on 2016-04-25
> **volkswagner said:**
> ```
NameVirtualHost *:80
```

I just checked my entire apache2 directory and that string doesn't exist in any files. I'm not sure it's a problem, but
it seems that directive may be deprecated or no longer needed.

NameVirtualHost is indeed deprecated in Apache 2.4. I don't know whether including it just produces a warning or whether it creates an error. I believe it is simply superfluous in 2.4, but it doesn't hurt to remove it.

---

### Post by ben203 on 2016-04-26
> **volkswagner said:**
> Please post output of the following.

```
ls -alt /etc/apache2/sites-available
```
  ```
total 28

  -rw-r--r-- 1 root root 1866 Apr 25 08:24 000-default.conf
  -rw-r--r-- 1 root root  426 Apr 25 07:45 firstsite.com.conf

  -rw-r--r-- 1 root root  452 Apr 25 07:38 secondsite.com.conf

  drwxr-xr-x 8 root root 4096 Apr 25 07:10 ..
  drwxr-xr-x 2 root root 4096 Apr 25 07:10 .
  -rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf
```

  
> ```
ls -alt /etc/apache2/sites-enabled
```
```
  total 8
  drwxr-xr-x 2 root root 4096 Apr 25 07:13 .
  lrwxrwxrwx 1 root root   48 Apr 25 07:13 secondsite.com.conf -> ../sites-available/secondsite.com.conf

  lrwxrwxrwx 1 root root   41 Apr 25 07:13 firstsite.com.conf -> ../sites-available/firstsite.com.conf

  lrwxrwxrwx 1 root root   35 Apr 25 07:10 000-default.conf -> ../sites-available/000-default.conf
  drwxr-xr-x 8 root root 4096 Apr 25 07:10 ..
  
```
> ```
ls -alt /etc/apache2/conf-enabled
```
```
  total 8
  drwxr-xr-x 2 root root 4096 Apr 25 07:10 .
  lrwxrwxrwx 1 root root   36 Apr 25 07:10 serve-cgi-bin.conf -> ../conf-available/serve-cgi-bin.conf
  lrwxrwxrwx 1 root root   31 Apr 25 07:10 security.conf -> ../conf-available/security.conf
  lrwxrwxrwx 1 root root   46 Apr 25 07:10 other-vhosts-access-log.conf -> ../conf-available/other-vhosts-access-log.conf
  lrwxrwxrwx 1 root root   44 Apr 25 07:10 localized-error-pages.conf -> ../conf-available/localized-error-pages.conf
  lrwxrwxrwx 1 root root   30 Apr 25 07:10 charset.conf -> ../conf-available/charset.conf
  drwxr-xr-x 8 root root 4096 Apr 25 07:10 ..
  
```

> ```
cat /etc/apache2/ports.conf
```
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf
 
Listen 80
 
<IfModule ssl_module>
        Listen 443
</IfModule>
 
<IfModule mod_gnutls.c>
        Listen 443
</IfModule>
 
# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```
> ```
cat /etc/apache2/apache2.conf
```
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
#       /etc/apache2/
#       |-- apache2.conf
#       |       `--  ports.conf
#       |-- mods-enabled
#       |       |-- *.load
#       |       `-- *.conf
#       |-- conf-enabled
#       |       `-- *.conf
#       `-- sites-enabled
#               `-- *.conf
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
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
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


```
> Where did this line come from in your conf file?
```
NameVirtualHost *:80
```

I just checked my entire apache2 directory and that string doesn't exist in any files. I'm not sure it's a problem, but
it seems that directive may be deprecated or no longer needed.

Originally it was in the apache2.conf but it was commented. One of the guides i was following said to uncomment that line.

> Just to confirm, you are now using separate config files for each host, yes?

Yes, seperate file for each host

---

### Post by volkswagner on 2016-04-26
> **ben203 said:**
> 

Originally it was in the apache2.conf but it was commented. One of the guides i was following said to uncomment that line.



What version of Apache and Ubuntu are you using?

I assumed you were on 14.04, but this does not seem to be the case.

Please post the contents for all three vhost files.

Do you have anything interesting in log files?

Also with all three of your sites enabled, which one always displays? This may be difficult to answer since you are masking domains and filenames (using siteOne, siteTwo). What
I'm really interested is which site is displayed compared to alphanumeric order in the vhost filename (eg 000-default.conf would likely be the first alphanumeric). So I'm hoping your can answer like siteOne or siteTwo and give the first few characters of file name or at least let us know how they compare alphanumerically.

---

### Post by Graham_Willis on 2016-04-27
[QUOTE="ben203"]Tried this, no luck. Even did an uninstall/reinstall of apache to see if  that helped, still no luck. It will still only let me bring up one site  or the other. This is really frustrating[/QUOTE]

Are you aware of the fact that the standard uninstall won't remove the configuration files? Try - of course first of all make backup of your configuration files and data if you need - (as far as I remember apt-get purge app doesn't remove user's data, but first I'm not sure, second it's better to be safe than sorry) **apt-get purge *app ***(in the place of ***app ***you of course enter the name of the application you want to purge). Then reinstall and add virtual hosts by hand. Should work.

---

### Post by ben203 on 2016-04-28
> **volkswagner said:**
> What version of Apache and Ubuntu are you using?

I assumed you were on 14.04, but this does not seem to be the case.

Ubuntu 14.04.4 LTS
Apache 2.4.7

> Please post the contents for all three vhost files.
000-default.conf
```
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        #ServerAdmin webmaster@localhost
        #DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        #ErrorLog ${APACHE_LOG_DIR}/error.log
        #CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



```
First Site -- Starts with 'B'
```
<VirtualHost *:80>
ServerAdmin xxxx
ServerName firstsite.com
ServerAlias www.firstsite.com

DocumentRoot /var/www/firstsite.com/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/firstsite.com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```
Second Site -- Starts with 'C'
```
<VirtualHost *:80>
ServerName secondsite.com
ServerAlias www.secondsite.com
ServerAdmin xxxx
DocumentRoot /var/www/secondsite.com/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/secondsite.com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


```

> Do you have anything interesting in log files?
No, there doesnt appear to be.

> Also with all three of your sites enabled, which one always displays? This may be difficult to answer since you are masking domains and filenames (using siteOne, siteTwo). What
I'm really interested is which site is displayed compared to alphanumeric order in the vhost filename (eg 000-default.conf would likely be the first alphanumeric). So I'm hoping your can answer like siteOne or siteTwo and give the first few characters of file name or at least let us know how they compare alphanumerically.
The first site displays, starting with B, the second site (starting with C) redirects to the first.

---

### Post by volkswagner on 2016-04-28
I would disable the default site since you're not using it (its completely commented out).

```
sudo a2dissite 000-default.conf
```

```
sudo service apache2 restart
```

Your configs look like they should work. I would suggest purge apache2 and webmin, or reinstall would be the preferred method. This should just work.

---

