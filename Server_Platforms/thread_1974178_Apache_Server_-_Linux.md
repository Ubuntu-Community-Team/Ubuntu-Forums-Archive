---
title: "Apache Server - Linux"
date: 2012-05-05
forum: Server Platforms
---

### Post by EdMarx on 2012-05-05
Hey Folks,

I have a server i control with Webmin. I am trying to create virtual  hosts in the create new virtual host tab on webmin. Everything is fine as I set it up, however, when I so to start the server it gives me this error.

> **Starting web server: apache2apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory  failed!**

These are the only lines around 281 in apache2.conf

> 

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
When I go to 
**/etc/apache2/sites-enabled/000-default**

 I see a file but if I try to edit it with webmin it says it can onluy edit normal files

and when I open it with vim it is blank.

Can anyone help me???

---

### Post by Habitual on 2012-05-05
```
file /etc/apache2/sites-enabled/000-default
```output please.

---

### Post by EdMarx on 2012-05-06
> **Habitual said:**
> ```
file /etc/apache2/sites-enabled/000-default
```output please.
What do you mean?

@Habitual
On a different note is it pelican bay, CA? Are you in prison?

---

### Post by EdMarx on 2012-05-06
I cant read the file. it is there but there is nothing in it when I open with vim.

vim gives me an alert saying
> 
E325: ATTENTION
Found swap file by the name /etc/apache2/sites-available/.default.swp
owned by root.
process id: 8446

process still running


I kill the process open with vim but nothing

There is another file in sites-available

"MYUSERNAME.com.conf"

could that be the problem. Are they conflicting.


Im sure my problem is due to the fact that I have no idea what Im doing. 
Im familiar enough with sudo and terminal to completely screw things up.

---

### Post by poolet on 2012-05-06
> **EdMarx said:**
> I cant read the file. it is there but there is nothing in it when I open with vim.

vim gives me an alert saying


I kill the process open with vim but nothing

There is another file in sites-available

"MYUSERNAME.com.conf"

could that be the problem. Are they conflicting.


Im sure my problem is due to the fact that I have no idea what Im doing. 
Im familiar enough with sudo and terminal to completely screw things up.



Open the terminal and type the following::

```
sudo su
```it will ask you for a password to login as admin then 

```
killall 8446
``` -->> ```
killall --group 8446
``````
cd /etc/apache2/sites-available
```

```
gedit .default.swp[
```OR before opening a file thru terminal make sure that isn't used by any other process to see all your process  ```
ps -A
``````
vim .default.swp
```at the end make sure that you have make a correct installation of apache see the links below::

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

Permissions and directories::

[http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09](http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09)

---

### Post by SeijiSensei on 2012-05-06
On a standard Ubuntu Apache installation, /etc/apache2/sites-enabled/000-default is a symbolic link to /etc/apache2/sites-available/default.  Does that file exist?  Maybe you renamed it along the way?

---

### Post by EdMarx on 2012-05-06
> **poolet said:**
> Open the terminal and type the following..
[/09]("http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09")

I did this it doesn't work. I dont think there is the file there.

I am using Debian without a GUI and I am told there are few differences.

I also dont think I mentioned that a single sight works on my server. I wanted to now host multiple sites though and when someone went to the second site it would send them to the first.

Thanks for the responses.
I will keep looking and post my results.

---

### Post by EdMarx on 2012-05-06
Here is the config file in /etc/apache2/apache2.conf

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
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
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

```

---

### Post by EdMarx on 2012-05-06
> **SeijiSensei said:**
> On a standard Ubuntu Apache installation, /etc/apache2/sites-enabled/000-default is a symbolic link to /etc/apache2/sites-available/default.  Does that file exist?  Maybe you renamed it along the way?
There is a file there but not that one. My file says 


MYURL.conf

---

### Post by EdMarx on 2012-05-06
Im not opposed to uninstalling Apache and reinstalling using virtual hosts from the start.
Does anyone know a good tutorial for this?

---

### Post by SeijiSensei on 2012-05-06
No, you don't need to reinstall, just fix the links.

```

sudo rm -f /etc/apache/sites-enabled/000-default
sudo ln -s /etc/apache/sites-available/MYURL.conf
sudo service apache2 restart

```

Ignore any errors from the "rm" command.  Now see if it works using the URL you defined.

I'd avoid Webmin if it mangles the standard Ubuntu defaults in this manner. 

If you want to restore the default (important on a publicly-visible site; not a big deal on a private one), then re-create the file /etc/apache2/sites-available/default in an editor (as root with sudo) and copy this into it:

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
Now run these commands
```

cd /etc/apache2/sites-enabled
sudo ln -s ../sites-available/default 000-default
sudo service apache2 restart

```

If you then go to [http://localhost/](http://localhost/) you should see the default "It Works!" page.

If you really want to reinstall Apache, it's not that hard:

```

sudo apt-get purge apache2
sudo apt-get install apache2

```

And stay away from Webmin.  Figure out how to create the <VirtualHost> files yourself from looking at the example here and the one that was created for you.

---

### Post by nowashburn on 2012-05-14
> **SeijiSensei said:**
> No, you don't need to reinstall, just fix the links.

```

sudo rm -f /etc/apache/sites-enabled/000-default
sudo ln -s /etc/apache/sites-available/MYURL.conf
sudo service apache2 restart

```

Ignore any errors from the "rm" command.  Now see if it works using the URL you defined.

I'd avoid Webmin if it mangles the standard Ubuntu defaults in this manner. 

If you want to restore the default (important on a publicly-visible site; not a big deal on a private one), then re-create the file /etc/apache2/sites-available/default in an editor (as root with sudo) and copy this into it:

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
Now run these commands
```

cd /etc/apache2/sites-enabled
sudo ln -s ../sites-available/default 000-default
sudo service apache2 restart

```

If you then go to [http://localhost/](http://localhost/) you should see the default "It Works!" page.

If you really want to reinstall Apache, it's not that hard:

```

sudo apt-get purge apache2
sudo apt-get install apache2

```

And stay away from Webmin.  Figure out how to create the <VirtualHost> files yourself from looking at the example here and the one that was created for you.

thanks for this, i also accidentally deleted /etc/apache2/sites-available/default while messing around in webmin.

---

