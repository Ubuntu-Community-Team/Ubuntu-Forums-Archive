---
title: "Web page can't be viewed on local host"
date: 2010-03-07
forum: Server Platforms
---

### Post by cliftonbazaar on 2010-03-07
Hi,

Completely new to Linux so please be nice :p

I have tried to set up the desktop version of the server .
In my apache2.conf file I have changed the following lines-
```
# Include the virtual host configurations:
#Include /etc/apache2/sites-enabled/
Include /home/www/websites/
```Yes I do keep the default values commented out :)

In my virtual host file I have made the following changes to the DocumentRoot, and to one of the <Directory>; the rest of the file doesn't appear here as nothing was changed.
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    # DocumentRoot /var/www
    DocumentRoot /home/www/websites
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/www/websites/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

```I then placed one file in my websites folder - index.html
```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
```When I put [http://192.168.0.6/](http://192.168.0.6/) or [http://localhost/](http://localhost/) in my browser it gives me a 404 error-
```
**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.12 (Ubuntu) Server at 192.168.0.6 Port 80
```Please note that the server IP is 192.168.0.6 and my ISP has given me a static IP.

---

### Post by km0r3 on 2010-03-07
**REMINDER:**
Restart Apache with every change to the configuration.

Would be nice if you would post your Apache logs which you can find in /var/log/apache2 usually, using something like dpaste.com, here.

And yes, if not already done: restart your Apache Server.

---

### Post by cliftonbazaar on 2010-03-07
Restarting the apache server gives me the following -
```
 * Restarting web server apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```restarting the apache server with index.html in the websites folder gives me 
```
 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes.
This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting apache2: Syntax error on line 237 of /etc/apache2/apache2.conf:
 Syntax error on line 4 of /home/www/websites/index.html: Expected </p>The> but saw </body></html>

```this leads me to another question - why do I get HTML errors when restarting the apache server?  The index.html is the default page that Ubuntu comes with -
```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
```In  /var/log/apache2 I only have accesss.log, error.log and other_vhost_access.log.  None of these seem to have info on what is going wrong (it doesn't have any entries for when I try to restart apache).

James

---

### Post by km0r3 on 2010-03-07
>  ... waiting apache2: Syntax error on line 237 of /etc/apache2/apache2.conf:
Well that sounds strange. Could you show us your *apache2.conf*, please?

I actually cannot help you with the syntax error in your *index.html*, but your *index.html*'s markup looks clean, though.

**I will be off for today. Don't expect an answer from me earlier in the next 12h. I hope others can help.**

Happy bug hunting mate,
km0r3

---

### Post by cliftonbazaar on 2010-03-07
Full apache2.conf file.  If my memory serves me correct all I have changed is the  virtual host configurations (last line of the code).

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
Timeout 60

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
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
#Include /etc/apache2/sites-enabled/
Include /home/www/websites/
```

the files from /etc/apache2/sites-enabled/ were copied and pasted into  /home/www/websites/, yet this won't work.

---

### Post by km0r3 on 2010-03-08
**You included /home/www/websites two times in your apache2.conf** .

First in this line:
```
238 #Include /etc/apache2/sites-enabled/
239 Include /home/www/websites#

```and then again at the bottom.

Delete one of them and then try again. If still having problems, try setting ```
LogLevel debug
``` (also in your apache2.conf) replacing the existing setting which is how I see currently set to ```
LogLevel warn
``` and then your /var/logs/apache2/error.log will contain a lot of information after restarting Apache.

Please, post that log here, then.

---

### Post by cliftonbazaar on 2010-03-10
Thanks for the reply.  I redid a virtual host file and the problem is solved.

---

### Post by km0r3 on 2010-03-10
**I'm glad** you're problem is solved. I would be even more glad if you show us your Virtual Host configuration, if you don't mind of course, for being curious. :)

---

