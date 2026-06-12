---
title: "I assume I was hacked last night so how do I find out and fix it?"
date: 2010-09-05
forum: Server Platforms
---

### Post by waloshin on 2010-09-05
For some odd reason none of my folders want to load at all.

Such as blog, forum, nothing.

Apache2.conf file

```

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

```

Apache error log

```
[Sun Sep 05 06:49:58 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 05 06:50:05 2010] [error] [client 90.225.8.253] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 06:50:05 2010] [error] [client 90.225.8.253] File does not exist: /htdocs
[Sun Sep 05 06:50:08 2010] [error] [client 90.225.8.253] File does not exist: /htdocs
[Sun Sep 05 06:50:11 2010] [error] [client 90.225.8.253] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 06:50:11 2010] [error] [client 90.225.8.253] File does not exist: /htdocs
[Sun Sep 05 06:50:14 2010] [error] [client 90.225.8.253] File does not exist: /htdocs
[Sun Sep 05 06:55:26 2010] [error] [client 67.182.203.139] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 06:55:26 2010] [error] [client 67.182.203.139] File does not exist: /htdocs
[Sun Sep 05 06:55:38 2010] [error] [client 67.182.203.139] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 06:55:38 2010] [error] [client 67.182.203.139] File does not exist: /htdocs
[Sun Sep 05 07:06:48 2010] [error] [client 124.191.120.197] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 07:07:14 2010] [error] [client 68.195.74.219] File does not exist: /htdocs
[Sun Sep 05 07:07:15 2010] [error] [client 68.195.74.219] File does not exist: /htdocs, referer: http://waloshin.com/faanpage
[Sun Sep 05 07:07:22 2010] [error] [client 68.195.74.219] File does not exist: /htdocs
[Sun Sep 05 07:07:26 2010] [error] [client 68.195.74.219] File does not exist: /htdocs
[Sun Sep 05 07:07:29 2010] [error] [client 173.60.227.113] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 07:07:33 2010] [error] [client 68.195.74.219] File does not exist: /htdocs
[Sun Sep 05 07:07:33 2010] [error] [client 68.195.74.219] File does not exist: /htdocs, referer: http://www.waloshin.com/
[Sun Sep 05 07:07:46 2010] [error] [client 68.195.74.219] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1008181
[Sun Sep 05 07:24:11 2010] [error] [client 96.22.58.137] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 07:24:50 2010] [error] [client 66.249.65.54] File does not exist: /htdocs
[Sun Sep 05 07:24:50 2010] [error] [client 66.249.65.54] File does not exist: /htdocs
[Sun Sep 05 07:25:23 2010] [error] [client 74.125.75.4] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 07:32:50 2010] [error] [client 72.197.183.137] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 07:33:05 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:05 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:05 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:05 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:10 2010] [error] [client 207.189.121.45] File does not exist: /htdocs
[Sun Sep 05 07:33:11 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:13 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:14 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:14 2010] [error] [client 173.53.184.60] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 07:33:14 2010] [error] [client 207.189.121.45] File does not exist: /htdocs
[Sun Sep 05 07:33:14 2010] [error] [client 207.189.121.46] File does not exist: /htdocs
[Sun Sep 05 07:33:14 2010] [error] [client 207.189.121.46] File does not exist: /htdocs
[Sun Sep 05 07:36:09 2010] [error] [client 86.154.232.12] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 07:36:46 2010] [error] [client 86.154.232.12] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 07:36:46 2010] [error] [client 86.154.232.12] File does not exist: /htdocs
[Sun Sep 05 07:36:49 2010] [error] [client 86.154.232.12] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 07:36:49 2010] [error] [client 86.154.232.12] File does not exist: /htdocs
[Sun Sep 05 07:41:21 2010] [error] [client 96.33.132.27] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 07:44:35 2010] [error] [client 77.88.27.27] File does not exist: /htdocs
[Sun Sep 05 07:48:32 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 07:48:33 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 07:48:34 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 07:49:55 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 07:52:55 2010] [error] [client 12.54.66.50] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 07:52:55 2010] [error] [client 12.54.66.50] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 07:58:10 2010] [error] [client 189.221.244.153] File does not exist: /htdocs, referer: http://www.google.com.mx/search?hl=es&source=hp&q=baking+life+tutorial&aq=f&aqi=&aql=&oq=&gs_rfai=
[Sun Sep 05 07:59:04 2010] [error] [client 67.9.194.73] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 08:00:02 2010] [error] [client 93.174.95.161] File does not exist: /htdocs, referer: http://waloshin.com/forum/index.php?action%3Drecent
[Sun Sep 05 08:00:03 2010] [error] [client 93.174.95.161] File does not exist: /htdocs, referer: http://waloshin.com/
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:06:12 2010] [error] [client 173.66.206.215] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 08:09:24 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10988727&highlight=
[Sun Sep 05 08:09:25 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:09:33 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://www.google.no/search?q=walo+shin+fan+page&channel=linkdoctor
[Sun Sep 05 08:09:33 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:09:38 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://www.google.no/search?q=walo+shin+fan+page&channel=linkdoctor
[Sun Sep 05 08:09:39 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:09:48 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10988727&highlight=
[Sun Sep 05 08:09:48 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:09:55 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10988727&highlight=
[Sun Sep 05 08:09:55 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:10:22 2010] [error] [client 90.149.27.3] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10988727&highlight=
[Sun Sep 05 08:10:22 2010] [error] [client 90.149.27.3] File does not exist: /htdocs
[Sun Sep 05 08:11:16 2010] [error] [client 99.13.123.217] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:22:48 2010] [error] [client 99.189.186.19] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 08:22:48 2010] [error] [client 99.189.186.19] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 08:23:05 2010] [error] [client 68.7.144.50] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:23:09 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 08:29:45 2010] [error] [client 125.45.109.166] File does not exist: /htdocs
[Sun Sep 05 08:34:44 2010] [error] [client 91.108.16.19] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:34:45 2010] [error] [client 91.108.16.19] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:41:32 2010] [error] [client 77.88.27.27] File does not exist: /htdocs
[Sun Sep 05 08:53:22 2010] [error] [client 86.174.94.76] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:53:23 2010] [error] [client 86.174.94.76] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 08:59:45 2010] [error] [client 67.202.122.32] File does not exist: /htdocs
[Sun Sep 05 09:10:04 2010] [error] [client 68.60.136.63] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:10:13 2010] [error] [client 68.60.136.63] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:10:14 2010] [error] [client 68.60.136.63] File does not exist: /htdocs
[Sun Sep 05 09:10:16 2010] [error] [client 68.60.136.63] File does not exist: /htdocs
[Sun Sep 05 09:10:21 2010] [error] [client 72.200.66.149] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1006786
[Sun Sep 05 09:12:02 2010] [error] [client 115.64.202.167] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:12:03 2010] [error] [client 115.64.202.167] File does not exist: /htdocs
[Sun Sep 05 09:12:06 2010] [error] [client 115.64.202.167] File does not exist: /htdocs
[Sun Sep 05 09:13:26 2010] [error] [client 90.184.92.45] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:13:27 2010] [error] [client 90.184.92.45] File does not exist: /htdocs
[Sun Sep 05 09:13:31 2010] [error] [client 90.184.92.45] File does not exist: /htdocs
[Sun Sep 05 09:14:04 2010] [error] [client 85.65.132.191] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?p=9803982
[Sun Sep 05 09:14:05 2010] [error] [client 85.65.132.191] File does not exist: /htdocs
[Sun Sep 05 09:14:08 2010] [error] [client 85.65.132.191] File does not exist: /htdocs
[Sun Sep 05 09:14:13 2010] [error] [client 85.65.132.191] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?p=9803982
[Sun Sep 05 09:14:13 2010] [error] [client 85.65.132.191] File does not exist: /htdocs
[Sun Sep 05 09:14:16 2010] [error] [client 85.65.132.191] File does not exist: /htdocs
[Sun Sep 05 09:15:36 2010] [error] [client 71.176.133.42] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 09:15:36 2010] [error] [client 71.176.133.42] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 09:17:08 2010] [error] [client 75.21.106.165] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 09:17:20 2010] [error] [client 58.218.204.110] File does not exist: /htdocs
[Sun Sep 05 09:21:04 2010] [error] [client 66.249.65.35] File does not exist: /htdocs
[Sun Sep 05 09:22:03 2010] [error] [client 84.26.223.203] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:22:04 2010] [error] [client 84.26.223.203] File does not exist: /htdocs
[Sun Sep 05 09:22:04 2010] [error] [client 84.26.223.203] File does not exist: /htdocs
[Sun Sep 05 09:22:11 2010] [error] [client 84.26.223.203] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:22:43 2010] [error] [client 67.160.138.213] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1008181
[Sun Sep 05 09:22:43 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:22:46 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:22:47 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:22:56 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:25:20 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:25:34 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:26:31 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:26:34 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:26:49 2010] [error] [client 76.182.21.254] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 09:28:22 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:28:54 2010] [error] [client 66.249.65.35] File does not exist: /htdocs
[Sun Sep 05 09:31:43 2010] [error] [client 74.125.44.84] File does not exist: /htdocs
[Sun Sep 05 09:36:21 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:36:22 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:36:24 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 09:36:58 2010] [error] [client 69.245.99.207] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:36:59 2010] [error] [client 69.245.99.207] File does not exist: /htdocs
[Sun Sep 05 09:37:02 2010] [error] [client 69.245.99.207] File does not exist: /htdocs
[Sun Sep 05 09:37:16 2010] [error] [client 69.245.99.207] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 09:37:17 2010] [error] [client 69.245.99.207] File does not exist: /htdocs
[Sun Sep 05 09:37:20 2010] [error] [client 69.245.99.207] File does not exist: /htdocs
[Sun Sep 05 09:37:24 2010] [error] [client 69.245.99.207] File does not exist: /htdocs
[Sun Sep 05 09:38:29 2010] [error] [client 77.88.27.27] File does not exist: /htdocs
[Sun Sep 05 09:39:28 2010] [error] [client 91.156.163.195] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 09:42:16 2010] [error] [client 81.135.16.172] File does not exist: /htdocs, referer: http://www.google.co.uk/search?hl=en&client=firefox-a&hs=PLx&rls=org.mozilla%3Aen-GB%3Aofficial&q=baking+life+xp&aq=8&aqi=g10&aql=&oq=baking+life+&gs_rfai=
[Sun Sep 05 09:47:39 2010] [error] [client 68.118.227.96] File does not exist: /htdocs
[Sun Sep 05 09:47:39 2010] [error] [client 68.118.227.96] File does not exist: /htdocs
[Sun Sep 05 09:47:45 2010] [error] [client 68.118.227.96] File does not exist: /htdocs
[Sun Sep 05 09:47:46 2010] [error] [client 68.118.227.96] File does not exist: /htdocs
[Sun Sep 05 10:04:18 2010] [error] [client 70.223.192.93] File does not exist: /htdocs, referer: http://androidforums.com/lounge/167707-looking-guest-bloggers.html
[Sun Sep 05 10:04:18 2010] [error] [client 70.223.192.93] File does not exist: /htdocs, referer: http://waloshin.com/forum/index.php/topic,10.0.html
[Sun Sep 05 10:04:20 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 10:04:40 2010] [error] [client 70.223.192.93] File does not exist: /htdocs, referer: http://androidforums.com/lounge/167707-looking-guest-bloggers.html
[Sun Sep 05 10:04:41 2010] [error] [client 70.223.192.93] File does not exist: /htdocs, referer: http://waloshin.com/blog/?p=1277
[Sun Sep 05 10:04:54 2010] [error] [client 70.223.192.93] File does not exist: /htdocs
[Sun Sep 05 10:08:54 2010] [error] [client 152.91.9.153] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 10:08:55 2010] [error] [client 152.91.9.153] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 10:08:55 2010] [error] [client 152.91.9.153] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 10:08:55 2010] [error] [client 152.91.9.153] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?t=1003418
[Sun Sep 05 10:11:23 2010] [error] [client 70.31.11.172] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 10:11:23 2010] [error] [client 70.31.11.172] File does not exist: /htdocs
[Sun Sep 05 10:11:26 2010] [error] [client 70.31.11.172] File does not exist: /htdocs
[Sun Sep 05 10:11:27 2010] [error] [client 70.31.11.172] File does not exist: /htdocs
[Sun Sep 05 10:14:11 2010] [error] [client 125.45.109.166] File does not exist: /htdocs
[Sun Sep 05 10:15:01 2010] [error] [client 71.17.126.65] File does not exist: /htdocs
[Sun Sep 05 10:15:07 2010] [error] [client 71.17.126.65] File does not exist: /htdocs
[Sun Sep 05 10:15:11 2010] [error] [client 71.17.126.65] File does not exist: /htdocs
[Sun Sep 05 10:19:09 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 10:19:38 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 10:19:41 2010] [error] [client 67.160.138.213] File does not exist: /htdocs
[Sun Sep 05 10:20:27 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:27 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:27 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:28 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:29 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:29 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:29 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:29 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:30 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:31 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:32 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:33 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:34 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:35 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:36 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:37 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:38 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:39 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:40 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:41 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:42 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:20:43 2010] [error] [client 173.201.36.135] File does not exist: /htdocs
[Sun Sep 05 10:35:26 2010] [error] [client 77.88.27.27] File does not exist: /htdocs
[Sun Sep 05 10:41:03 2010] [error] [client 94.192.171.11] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 10:41:03 2010] [error] [client 94.192.171.11] File does not exist: /htdocs, referer: http://androidforums.com/lounge/152367-post-pics-your-whips-2.html
[Sun Sep 05 10:46:42 2010] [error] [client 111.84.156.178] File does not exist: /htdocs, referer: http://www.google.co.th/imglanding?q=baking%20life&imgurl=http://3.bp.blogspot.com/_VXEXIVlkGXs/TBEELEQ_HYI/AAAAAAAABP0/26DwJwbJOvk/s1600/Baking%2BLife%2Bcheats.bmp&imgrefurl=http://blogvideohosting.blogspot.com/2010/06/baking-life-cheats-super-money.html&usg=__UO1BHoURSJyxQjUyZvSDoDGIEq0=&h=490&w=759&sz=83&hl=th&zoom=1&um=1&itbs=1&tbnid=O-EfYS9asR-7xM:&tbnh=92&tbnw=142&prev=/images%3Fq%3Dbaking%2Blife%26um%3D1%26hl%3Dth%26sa%3DN%26tbs%3Disch:1&um=1&sa=N&tbs=isch:1&start=0
[Sun Sep 05 10:48:41 2010] [error] [client 82.69.58.220] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 10:48:41 2010] [error] [client 82.69.58.220] File does not exist: /htdocs
[Sun Sep 05 10:48:56 2010] [error] [client 82.69.58.220] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 10:48:57 2010] [error] [client 82.69.58.220] File does not exist: /htdocs
[Sun Sep 05 11:00:33 2010] [error] [client 207.244.223.77] File does not exist: /htdocs
[Sun Sep 05 11:01:49 2010] [error] [client 173.29.123.43] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 11:03:06 2010] [error] [client 173.29.123.43] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 11:03:07 2010] [error] [client 173.29.123.43] File does not exist: /htdocs
[Sun Sep 05 11:04:08 2010] [error] [client 195.241.220.183] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 11:04:09 2010] [error] [client 195.241.220.183] File does not exist: /htdocs
[Sun Sep 05 11:04:12 2010] [error] [client 195.241.220.183] File does not exist: /htdocs
[Sun Sep 05 11:04:18 2010] [error] [client 195.241.220.183] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 11:11:42 2010] [error] [client 196.25.255.194] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 11:12:39 2010] [error] [client 196.25.255.195] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 11:12:40 2010] [error] [client 198.54.202.194] File does not exist: /htdocs
[Sun Sep 05 11:12:43 2010] [error] [client 198.54.202.194] File does not exist: /htdocs
[Sun Sep 05 11:12:49 2010] [error] [client 198.54.202.194] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1568293
[Sun Sep 05 11:12:51 2010] [error] [client 198.54.202.218] File does not exist: /htdocs
[Sun Sep 05 11:12:53 2010] [error] [client 198.54.202.218] File does not exist: /htdocs
[Sun Sep 05 11:14:45 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 11:17:11 2010] [error] [client 66.249.65.51] File does not exist: /htdocs
[Sun Sep 05 11:17:38 2010] [error] [client 94.170.134.113] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?t=1567594
[Sun Sep 05 11:17:38 2010] [error] [client 94.170.134.113] File does not exist: /htdocs
[Sun Sep 05 11:17:41 2010] [error] [client 94.170.134.113] File does not exist: /htdocs
[Sun Sep 05 11:19:11 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10997623
[Sun Sep 05 11:19:27 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://forums.macrumors.com/showthread.php?p=10997623
[Sun Sep 05 11:19:30 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?p=9808103
[Sun Sep 05 11:19:31 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:20:33 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:20:35 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://waloshin.com/
[Sun Sep 05 11:20:35 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:23 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:23 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:26 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://webcache.googleusercontent.com/search?q=cache:http://waloshin.com/blog/
[Sun Sep 05 11:21:27 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://webcache.googleusercontent.com/search?q=cache:http://waloshin.com/blog/
[Sun Sep 05 11:21:27 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://webcache.googleusercontent.com/search?q=cache:http://waloshin.com/blog/
[Sun Sep 05 11:21:27 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://webcache.googleusercontent.com/search?q=cache:http://waloshin.com/blog/
[Sun Sep 05 11:21:38 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:38 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:53 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:53 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:56 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:56 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:57 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:21:57 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:22:02 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:22:02 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:22:13 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://ubuntuforums.org/showthread.php?p=9808103
[Sun Sep 05 11:22:13 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:22:21 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:22:21 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:23:18 2010] [notice] caught SIGTERM, shutting down
[Sun Sep 05 11:24:48 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 05 11:25:15 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:18 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:18 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:20 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:20 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:22 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:22 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:23 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:23 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:24 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:24 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:33 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:33 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:39 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:41 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://waloshin.com/
[Sun Sep 05 11:25:41 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:42 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:25:45 2010] [error] [client 24.72.141.140] File does not exist: /htdocs, referer: http://waloshin.com/
[Sun Sep 05 11:25:45 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:26:09 2010] [error] [client 77.88.27.27] File does not exist: /htdocs
[Sun Sep 05 11:26:30 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:26:30 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:26:43 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:26:43 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:26:52 2010] [error] [client 94.228.34.231] File does not exist: /htdocs
[Sun Sep 05 11:26:53 2010] [error] [client 94.228.34.231] File does not exist: /htdocs
[Sun Sep 05 11:29:48 2010] [error] [client 24.72.141.140] File does not exist: /htdocs
[Sun Sep 05 11:29:48 2010] [error] [client 24.72.141.140] File does not exist: /htdocs

```

---

### Post by HermanAB on 2010-09-05
Well, something is probably just misconfigured.  You most probably have not been hacked, since that is rather uncommon - it does happen, but not often.

Chances are that something has been misconfigured for some time, then a power failure caused the machine to restart and now it won't work right.

You have to go back in the Apache error log untill you find the *first* error message and fix that, then restart Apache.  Rinse and repeat.  Looking at the last error messages is useless.

---

### Post by waloshin on 2010-09-05
Error.log attached

---

### Post by kulshoks2121 on 2010-09-05
**_File does not exist: /htdocs_**

Meaning your pointed your web server to a different directory or you deleted your htdocs or you dont have the permission to access htdocs directory

---

