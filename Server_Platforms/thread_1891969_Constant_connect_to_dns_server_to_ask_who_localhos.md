---
title: "Constant connect to dns server to ask who localhost is"
date: 2011-12-06
forum: Server Platforms
---

### Post by baz.g on 2011-12-06
Please help, this is driving me crazy and is seriously annoying the firewall admin as it is slowing down the network

For some reason my ubuntu server (running 10.04) is forever trying to ask the dns server who localhost is. I have tried changing to the internal company dns server and an outside one (opendns) but it makes no difference. i have tried replacing localhost in the hosts file with the server name but it makes no difference. this happened once before and i found a page on google that mentioned because nothing was specified in the apache httpd.conf file then it would do it, so i added the servername in there and that seemed to cure it for a while but for some reason the problem has come back :(



I am running the latest knowledgetree-ce, webmin and postfix from the server.

my interfaces file:
```

# This file describes the network interfaces available on your system
 # and how to activate them. For more information, see interfaces(5).

 # The loopback network interface
auto lo
 iface lo inet loopback

# The primary network interface

auto bond0
iface bond0 inet static
address 192.168.168.50
netmask 255.255.255.0
gateway 192.168.168.254
bond-slaves eth0 eth5

auto eth1
iface eth1 inet static
address 192.168.200.50
netmask 255.255.255.0
# gateway 192.168.200.254

 # LACP confuration

```

my resolv.conf:
```

nameserver 208.67.222.222
nameserver 8.8.8.8

```

my hosts file:
```

127.0.0.1	localhost
127.0.1.1	knowledgetree


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters

```

my apache.conf:
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

Include /etc/phpmyadmin/apache.conf

```

my httpd.conf:
```

ServerName knowledgetree

```

also fyi, in the company dns server the dns name 'knowledgetree' has been registered for my ip (192.168.168.50)

please, please, please help :)

---

### Post by jonobr on 2011-12-07
Stuuuupid question.

You running openoffice on that machine?

Also, to stop annoying the admin temporarily
maybe you could add en entry in hosts 
localhost.(none) to point to 127.0.0.1

I cant imagine that this would harm anything by adding this entry

---

### Post by jonobr on 2011-12-07
I should explain myself,

I saw [this]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=619968") bug

---

### Post by baz.g on 2011-12-08
Hi jonobr,

Thanks for the replies. I had come to my senses a short while after making the post and added localhost.(none) to my hosts file to temporarily solve the problem.

Knowledgetree requires OpenOffice to run in 'headless' mode for the PDF conversions, but in that bug link the OpenOffice employee basically tells the guy it's his problem and has nothing to do with OpenOffice. I'm hoping that this does not happen with libreoffice as I will upgrade the server OS at the end of April with the release of 12.04.

Other than that do you know of any other 'fixes'?

Many thanks,

---

### Post by jonobr on 2011-12-08
Hey there


I think once again, I can be considered to be short on info for you.

There were two bugs logged in launchpad, one was a duplicate the other was a bug translated from something that was posted in France.

[Here]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176") is the actual bug and thread.

You notice the problem was that opening openoffice took some time and that during that time there was dns requests, like the one your said going out to the DNS server.

You will notice they indicate this will not be fixed as the move has been made to libreoffice from openoffice, but again the bug seems to imply that libre has the same issue.
The last entry to this was only a month or two ago.

For me, if this is the issue, I am confused why a dns query is being made at all. Im sure there is a logical reason.

The only thing I can recommend is stopping openoffice and seeing if that is whats sending out your queries,

---

### Post by baz.g on 2011-12-08
Ok, thanks mate, will try that :-)

---

