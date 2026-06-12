---
title: "php scripts not processed by browser on 12.04.1"
date: 2013-01-22
forum: Server Platforms
---

### Post by alex2356 on 2013-01-22
I am running Ubuntu 12.04.1 and trying to get a php script to work within the browser. I am not very experienced with these things, and searching the issue on the net brought no real clue what I am missing. If, for any reason, this problem is nor well described or belongs to another forum, please let me know!

On the system I seem to have apache2 running, the file /etc/apache2/httpd.conf is empty, and a httpd service does not seem to exist. What do I need to check/enable/install to be able to get a php script interpreted by the browser (current firefox).

---

### Post by jonedney on 2013-01-22
Hey Alex,

On Ubuntu, things are in different locations that say CentOS.  The service name for Apache is apache2, you can test to see if it is running by using the following command:

```
service apache2 status
```

Did you install services on this server?  Did you install PHP?   Examples may be helpful also.

---

### Post by alex2356 on 2013-01-22
Here is the requested output: 

```

service apache2 status
Apache2 is running (pid 7197).

```

Here is the test file (located in /var/www - do I have to store the php file there or can I store it anywhere?):

```

<html>
<body>

<?php
echo "Hello World<br>";
echo $_SERVER['HTTP_USER_AGENT'];
phpinfo();
?>

</body>
</html> 

```

and the command 

```

php5 -r 'phpinfo();'

```

gives a lot of output.

---

### Post by olegio on 2013-01-22
Maybe this can help.. 

[https://wiki.ubuntu.com/UserDirectoryPHP](https://wiki.ubuntu.com/UserDirectoryPHP)

---

### Post by alex2356 on 2013-01-22
Hi, 

I have tried the instructions in the link, but I still have the identical behavior. The browser is trying to download the php file instead of processing it.

---

### Post by Doug S on 2013-01-22
Is libapache2-mod-php5 installed? How to check:```
doug@doug-64:~$ dpkg -l | grep libapache
ii  libapache2-mod-php5              5.3.10-1ubuntu3.4            server-side, HTML-embedded scripting language (Apache 2 module)
```And if not, how to install:```
sudo apt-get install libapache2-mod-php5
```
Edit: what is the file name you are using? and will it be recognised as a php file?

---

### Post by olegio on 2013-01-22
You might also need to change DocumentRoot in 
"/etc/apache2/sites-enabled/000-default" from "/var/www" to the folder with your php file (~/public_html). (or put your index.php file in "/var/www").

The browser should be pointing to [http://localhost](http://localhost) when you try to test it locally.


> **alex2356 said:**
> Hi, 

I have tried the instructions in the link, but I still have the identical behavior. The browser is trying to download the php file instead of processing it.

---

### Post by sandyd on 2013-01-22
> **alex2356 said:**
> I am running Ubuntu 12.04.1 and trying to get a php script to work within the browser. I am not very experienced with these things, and searching the issue on the net brought no real clue what I am missing. If, for any reason, this problem is nor well described or belongs to another forum, please let me know!

On the system I seem to have apache2 running, the file /etc/apache2/httpd.conf is empty, and a httpd service does not seem to exist. What do I need to check/enable/install to be able to get a php script interpreted by the browser (current firefox).

One more thing - PHP is no interpreted client-side, it is interpreted server side.

---

### Post by alex2356 on 2013-01-23
First, libapache2-mod-php5 is installed. Second, I always tried to *open *the php file with *File -> Open File*. Third, when I navigate to the test php file through [http://localhost](http://localhost) this seem to work now. 


However, what I really wanted to do is to follow some PHP tutorial on forms, given here:[http://www.tizag.com/phpT/forms.php](http://www.tizag.com/phpT/forms.php) . Now I am at a stage where I put the two files described in this tutorial into */var/www*, but have problems to open the *order.html* file in the browser as *[http://localhost/order.html](http://localhost/order.html)*. I get an *Internal Server error*.

Why am I unable to see a simple html page now? What am I missing this time?

---

### Post by jonedney on 2013-01-23
Are you able to provide details of your error log?  Sounds like a MIME Type issue.

The error log should be located in /var/log.  You can perform a command like cat, to view the file.
```

cat /var/log/error_log
```

---

### Post by Doug S on 2013-01-23
Actually, the error file should be: /var/log/apache2/error.log

---

### Post by alex2356 on 2013-01-23
Hi, 

thanks for the help so far. I had a look in the file

```
/var/log/apache2/error.log
```which tells me something like 

```

[Wed Jan 23 17:07:39 2013] [error] [client 127.0.0.1] Syntax error in type map, no ':' in /var/www/order.html for header <html><body>\n
```

I looked for this error with google, but got only few inconsistent hits. Maybe the location for the html files is unusual/not allowed...? Any other idea?

---

### Post by alex2356 on 2013-01-23
For more information, here is my /etc/apache2/httpd.conf file:
```

# am assuming this points to the right place
LoadModule php5_module modules/libphp5.so

# this I don't know anything about - but it does work 
# with your html files - so it might have interfered when
# you added the html to the php files to parse
<Files *.html>
SetHandler type-map
</Files>

ScriptAlias /php/ "/usr/local/php/bin/"

AddType application/x-httpd-php .php
# this makes phps source files - they aren't sent to 
# the parser - least AFAIK
Addtype application/x-httpd-php-source .phps
```and the file /etc/apache2/apache2.conf (and have no idea what the entries mean. I just want to 'see' a html and php file locally, I do not want to configure web-access of a big company or something...)

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

AddType application/x-httpd-php5 .php
```

---

### Post by SeijiSensei on 2013-01-23
> **alex2356 said:**
> I looked for this error with google, but got only few inconsistent hits. Maybe the location for the html files is unusual/not allowed...? Any other idea?

Let's start with a simple test.  Create a file in /var/www like this:

```
sudo echo '<?php phpinfo() ?>' > /var/www/test.php
```

then open a browser on the machine and navigate to [http://localhost/test.php](http://localhost/test.php).  You should see the PHP info page with detailed information about your installation.

If you want a file to be parsed as a PHP script, you need to use the .php extension so it will match the AddType directive you listed above.

---

### Post by Doug S on 2013-01-23
In a previous posting you mentioned that /etc/apache2/httpd.conf was empty. It is supposed to be empty, and only exists for some backwards legacy reasons. In either Ubuntu 12.10 or 13.04 (I don't recall which) it doesn't even exist anymore. The suggestion is that you make it empty again and do your changes in the proper locations in the sub-directories of /etc/apache2. Or better still, don't make any changes at all. I cut and pasted the order.html file you referred to in the link and it works fine for me, without any special changes to default settings.

---

### Post by alex2356 on 2013-01-24
Hi, 

@SeijiSensei, @Doug S: I emptied the file  /etc/apache2/httpd.conf and followed the example by SeijiSensei, now I seem to be able to see html pages! And the order example also seems to work!

All I want, thank you very much for your help.

---

### Post by RJAllen on 2013-01-24
I checked this thread.  Also having problems with Apache2 not parsing .php.  Also, in browser have to use virtual IP address rather than localhost or 127.0.0.1.  Will parse .html.  Checking apache2 error log shows two things: 1) many favicon.ico files not found and 2, PHP parse error syntax unexpected T string line 3 or something like that.

Also, embedded <?php ?> in html file and parses html but doesn't process php script.

Any ideas.

---

### Post by teward on 2013-01-24
I know I'm late to this thread, but... did you guys actually confirm you installed the php5 module into apache?
```
$ sudo apt-get install libapache2-mod-php5
```

---

### Post by SeijiSensei on 2013-01-24
> **RJAllen said:**
> PHP parse error syntax unexpected T string line 3 or something like that.

You have a PHP syntax error on line 3 of that file.  An unexpected T string means the parser encountered a text string when it was expecting to find something else like a semicolon, parenthesis, or some other delimiter.

And, yes, make sure you have libapache2-mod-php5 installed.  It adds the code needed to invoke the PHP parser when serving files that end in .php.

---

