---
title: "Apache2.conf help - restriction IP adresses"
date: 2008-09-04
forum: Server Platforms
---

### Post by prophet665 on 2008-09-04
Hi all,

I have currently setup my Apache server and I am trying to configure it so that the only IP that can access it through a web interface, or for that matter, any interface is 127.0.0.1

Here is my Apache2.conf file (I removed all the commented code out).  Why are other IPs allowed to see the "It Works" default Apache screen?  What the heck am I doing wrong?  The allow/deny lines are toward the bottom.


ServerRoot "/etc/apache2"

PidFile ${APACHE_PID_FILE}

Timeout 300

KeepAlive On

MaxKeepAliveRequests 100

KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
ls    Deny from all
</Files>

DefaultType text/plain

HostnameLookups Off

ErrorLog /var/log/apache2/error.log

LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Full

ServerSignature On

Include /etc/apache2/conf.d/

Include /etc/apache2/sites-enabled/

<Directory />
	Order allow,deny
	Allow from 127.0.0.1
	Deny from all
</Directory>

Include /etc/phpmyadmin/apache.conf

---

### Post by scragar on 2008-09-04
swap the bottom bit around a little:
```
<Directory />
Order deny,allow
Deny from all
Allow from 127.0.0.1
</Directory>

```
this way it blocks everything, then allows yours through, rather than allowing it localy, but then blocking it when it does everything else.

---

### Post by Iowan on 2008-09-04
[]("https://help.ubuntu.com/community/ApacheMySQLPHP")
I'm told that you can add **ServerName localhost** to **apache2.conf** file (or use 127.0.0.1).

---

### Post by prophet665 on 2008-09-05
> **Iowan said:**
> []("https://help.ubuntu.com/community/ApacheMySQLPHP")
I'm told that you can add **ServerName localhost** to **apache2.conf** file (or use 127.0.0.1).

How would that help me?  Is that jus so I can say "localhost" instead of 127.0.0.1?

---

### Post by windependence on 2008-09-05
You do realize that you will only be able to see the web site from the server itself this way right? I assume you are doing development or something. Why not just unplug the network cable? Seriously!

-Tim

---

### Post by prophet665 on 2008-09-05
> **windependence said:**
> You do realize that you will only be able to see the web site from the server itself this way right? I assume you are doing development or something. Why not just unplug the network cable? Seriously!

-Tim

I only want the local machine to have access, right now.  I will be opening it up to my intranet a little later for testing.  I never want the Apache server available to anyone outside my intranet.

This is my main non-gaming machine.  I am trying to teach myself PHP, but getting the environment setup is proving to be more of a challenge than any language I have learned before.  

Basically, I am trying to get a LAMP setup.  The MySQL 5 install locked up last night also.  I think I am cursed on this machine.  

Is it possible to use MyPHPAdmin with SQLite instead of MySQL?

---

### Post by Iowan on 2008-09-05
> **windependence said:**
>  Why not just unplug the network cable? Seriously!

-TimPerhaps the machine is more than just a web server - my LAMP is also a Samba server.

---

### Post by prophet665 on 2008-09-06
I got MySQL 5 installed and running with phpMyAdmin.  I am still having problems with the permissions for the server.  

I have the following lines in the apache2.conf file.

<Directory />
	Order deny,allow
	Deny from all
	Allow from 127.0.0.1
</Directory>

Everyone on my intranet can still see the default index.html page.  What the heck am I doing wrong?  Is there another file where I need to put these permissions?

Oh...and this machine is used to do all my non gaming tasks, so unplugging the network cable would be troublesome.

---

### Post by windependence on 2008-09-06
Change to this:

```
<Directory /var/www/>
order allow,deny
allow from 127.0.0.1
</Directory>
```

Then - IMPORTANT! restart Apache:

```
sudo /etc/init.d/apache2 restart 
```

-Tim

---

### Post by prophet665 on 2008-09-06
> **windependence said:**
> Change to this:

```
<Directory /var/www/>
order allow,deny
allow from 127.0.0.1
</Directory>
```

Then - IMPORTANT! restart Apache:

```
sudo /etc/init.d/apache2 restart 
```

-Tim

I will try that in the morning.

I do have one question.  Is the /var/www directory the only directory available to an Apache server by default?  What I am worried about is that by following what you have posted, the /var/www directory will be protected, but other directories on my file system will be wide open and accessible through Apache.

---

### Post by scragar on 2008-09-06
/var/www is the only directory apache is configured to use by default, so I can't see any problems with it, although it is best to specify / instead, since then if you change the default directory, or try to copy this part of the config to a differently configured server the settings don't compramise the security.

---

### Post by windependence on 2008-09-06
I don't think it will work using /

There is no risk in specifying the doc root because this is all that Apache can see.

-Tim

---

### Post by prophet665 on 2008-09-06
Wow...this is incredibly frustrating. I went back and changed the apache2.conf file to include the this:

```
<Directory /var/www/>
order allow,deny
allow from 127.0.0.1
</Directory>
```

Restarted the service and still no luck.  Another computer on the intranet can still see the /var/www/index.html page.

So I changed it to:

```
<Directory /var/www/>
order allow,deny
allow from 127.0.0.1
deny from all
</Directory>
```

Restarted the service again and still no luck.

I then found this line in the apache2.conf 

```
Include /etc/apache2/httpd.conf
```

It was an empty file.  I put the allow, deny code inside of it.  Restarted the service, but that didn't help.

What in the world am I doing wrong?

---

### Post by windependence on 2008-09-06
Hmmmm, can you post your apache2.conf? I wonder if your doc root really IS /var/www.

Oh and remember, you need to clear the cache on their browsers or it will SEEM like they can read it and they can't all along. Maybe THAT is the problem. ;)

-Tim

---

### Post by prophet665 on 2008-09-06
Before I post anything, I just wanted to say "thanks" for all the help.  I would be so lost without it.

I changed the index.html page in /var/www to have a custom message, so i know that it is the file that is being served.

I also cleared my cache on every test.  

Oh. So. Frustrating.

Here is my apache2.conf file in all it's commented glory:

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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
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
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

<Directory /var/www/>
	Order allow,deny
	Allow from 127.0.0.1
	Deny from all
</Directory>

# Enable PHPMyAdmin
Include /etc/phpmyadmin/apache.conf

---

### Post by windependence on 2008-09-06
Is this the only site you have on this machine or do you have virtual hosts set up?

-Tim

---

### Post by prophet665 on 2008-09-06
> **windependence said:**
> Is this the only site you have on this machine or do you have virtual hosts set up?

-Tim

No virtual hosts that I am aware of, it should be the standard default Apache2 setup.  Other than modifying the apache2.conf file, I haven't done anything.  

Even after applying the permissions, other computers are able to see my modified index.html file, so I am pretty sure they are not hitting some other web directory.

I was looking at the directory and saw that I have  a httpd.conf~ and a httpd.conf file (without the tilde).  I also have a apache2.conf~ and a apache2.conf file.  What do the tilded files represent?

---

### Post by prophet665 on 2008-09-07
Sorry for the double post.  I was looking through the security documents at [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) and it said something along the lines of look for .htaccess files that can override your security settings.  I only found one on my system at /usr/share/phpmyadmin/libraries and all it contains is

```
# This folder does not require access over HTTP
# (the following directive denies access by default)
Order allow,deny

```

It is a long shot, but is this affecting anything?

---

### Post by MikeCheck on 2008-10-19
I am having the opposite problem.  After installing apache, the "It works" page is only visible from my machine.  I want to be able to see it from the rest of the intranet.

I tried adding this:
```
<Directory /var/www>
Order allow,deny
Allow from all
</directory>
```

---

### Post by prophet665 on 2008-10-19
Wonderful.  Its funny how we can opposite problems from, I assume, the same default installations.

---

### Post by MikeCheck on 2008-10-20
I'm assuming my issue is something with my iptables, because I wasn't able to get to my samba share from any other computer on my intranet either.

---

### Post by cariboo on 2008-10-21
I may be barking up the wrong tree, but wouldn't it better to set the restrictions in /etc/apache2/sites-available/default?

Jim

---

### Post by prophet665 on 2008-10-21
I submitted this question to protonic.com and here is the response they gave back.  it looks like it has a lot of good information.

> Thank you for contacting protonic.com on September 28th.
My name is Bjorn, and I will be helping you solve this problem.

By far the easiest way to do this is to simply set your firewall to not allow external access to port 80 of your machine. This will prevent others from accessing the web server, whilst still allowing you to use 127.0.0.1 yourself.

If you insist on using the Apache configuration, then there are several things to be aware of:

0. You MUST have the Apache module 'mod_access' installed for this to work.

1. Some versions of Apache use the /etc/apache2/http.conf. Check this file for conflicting configurations.

2. <Directory /var/www/> should have an asterisk, e.g. <Directory /var/www/*> to signify anything in /var/www/, not just the directory. Also, the AllowOverride None is effective only for the root directory. (/). You need to specify this for /var/www/ as well.

3. Using .htaccess might be a better way to do this- you can then specify settings on a per-folder basis without editing the master configuration file.
There are many tutorials that can be easily found with google. I can link you a few if you like.

4. You MUST restart Apache for config file changes to take effect.

I hope this information is helpful, and I look forward to hearing from you. Best wishes!

You can use the link below to reply to my message.

Please be careful not to use the reply button in your mail program! Doing so will not register your reply in our system, and will make it difficult for others to track the progress of the ticket, should there be a need.

For your reference, we have assigned your question "Apache2 Permissions Problems" Ticket # 203646.

Thanks again,
Bjorn W, Certified Computer Repair technician.

I have to say, just the idea of a sites like ubuntuforums.org and protonic.com is cool.  I will be giving this a try and see what happens.  Fingers crossed everyone.

---

