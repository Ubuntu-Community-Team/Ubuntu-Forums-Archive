---
title: "Apache: Too many clients?...not true"
date: 2008-02-09
forum: Server Platforms
---

### Post by saltydog on 2008-02-09
I am running my apache web server (Dapper) since 2 years, but today I am experiencing a big problem. 
I found the server down, do I looked at the error.log, and the last message was:

"[Sat Feb 09 18:28:07 2008] [error] server reached MaxClients setting, consider raising the MaxClients setting"

I have checked the conf file, but it is normal and good. Then I have restarted apache. It worked for a minute, during while I have browsed thru pages, and then it stoipped again with the same error message, but in the access log I had only my (1) connection! So it is not true that MaxClients has been reached, but something stops my server...

Anyone can help me, as it is now down?

---

### Post by faulkes on 2008-02-09
> **saltydog said:**
> I am running my apache web server (Dapper) since 2 years, but today I am experiencing a big problem. 
I found the server down, do I looked at the error.log, and the last message was:

"[Sat Feb 09 18:28:07 2008] [error] server reached MaxClients setting, consider raising the MaxClients setting"

I have checked the conf file, but it is normal and good. Then I have restarted apache. It worked for a minute, during while I have browsed thru pages, and then it stoipped again with the same error message, but in the access log I had only my (1) connection! So it is not true that MaxClients has been reached, but something stops my server...

Anyone can help me, as it is now down?

Can you paste the relevant (full) section the conf file here, as well as a 

```

ps -ef

and 

netstat -ant

```

Also, do you have server-status configured, this would allow you to see more directly what is happening with the server (before it dies of course), if you do I'd also include that here.

Faulkes

---

### Post by saltydog on 2008-02-09
This is the conf:

```

# Based upon the NCSA server configuration files originally by Rob McCool.
# Changed extensively for the Debian package by Daniel Stone <daniel@sfarc.net>
# and also by Thom May <thom@debian.org>.

# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation
# (available at <URL:http://www.apache.org/docs/mod/core.html#lockfile>);
# you will save yourself a lot of trouble.

ServerRoot "/etc/apache2"

# The LockFile directive sets the path to the lockfile used when Apache
# is compiled with either USE_FCNTL_SERIALIZED_ACCEPT or
# USE_FLOCK_SERIALIZED_ACCEPT. This directive should normally be left at
# its default value. The main reason for changing it is if the logs
# directory is NFS mounted, since the lockfile MUST BE STORED ON A LOCAL
# DISK. The PID of the main server process is automatically appended to
# the filename. 

LockFile /var/lock/apache2/accept.lock

# PidFile: The file in which the server should record its process
# identification number when it starts.

PidFile /var/run/apache2.pid

# Timeout: The number of seconds before receives and sends time out.

Timeout 300

# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.

KeepAlive On

# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.

MaxKeepAliveRequests 100

# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.

KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers ......... number of server processes to start
# MinSpareServers ...... minimum number of server processes which are kept spare
# MaxSpareServers ...... maximum number of server processes which are kept spare
# MaxClients ........... maximum number of server processes allowed to start
# MaxRequestsPerChild .. maximum number of requests a server process serves
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          40
MaxRequestsPerChild  0
</IfModule>

# pthread MPM
# StartServers ......... initial  number of server processes to start
# MaxClients ........... maximum  number of server processes allowed to start
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# ThreadsPerChild ...... constant number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of requests a server process serves
<IfModule worker.c>
StartServers         5
MaxClients         150 
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>

# perchild MPM
# NumServers ........... constant number of server processes
# StartThreads ......... initial  number of worker threads in each server process
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# MaxThreadsPerChild ... maximum  number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of connections per server process (then it dies)
<IfModule perchild.c>
NumServers           5
StartThreads         5
MinSpareThreads      5
MaxSpareThreads     10
MaxThreadsPerChild  20
MaxRequestsPerChild  0
AcceptMutex fcntl
</IfModule>

User www-data
Group www-data

# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


# Global error log.
ErrorLog /var/log/apache2/error.log

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/[^.#]*

#Let's have some Icons, shall we?
Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

# Set up the default error docs.
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
# Putting this all together, we can Internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line;
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/local/apache2/error/include/ files and
# copying them to /your/include/path/, even on a per-VirtualHost basis.
#

<IfModule mod_negotiation.c>
<IfModule mod_include.c>
    Alias /error/ "/usr/share/apache2/error/"

    <Directory "/usr/share/apache2/error">
        AllowOverride None
        Options IncludesNoExec
        AddOutputFilter Includes html
        AddHandler type-map var
        Order allow,deny
        Allow from all
        LanguagePriority en es de fr
        ForceLanguagePriority Prefer Fallback
    </Directory>

    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
    ErrorDocument 410 /error/HTTP_GONE.html.var
    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
    ErrorDocument 415 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

</IfModule>
</IfModule>

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
#	AllowOverride FileInfo AuthConfig Limit
#	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

UseCanonicalName off

TypesConfig /etc/mime.types
DefaultType text/plain

HostNameLookups on

IndexOptions FancyIndexing VersionSort

AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

AddIconByType (TXT,/icons/text.gif) text/*
AddIconByType (IMG,/icons/image2.gif) image/*
AddIconByType (SND,/icons/sound2.gif) audio/*
AddIconByType (VID,/icons/movie.gif) video/*

# This really should be .jpg.

AddIcon /icons/binary.gif .bin .exe
AddIcon /icons/binhex.gif .hqx
AddIcon /icons/tar.gif .tar
AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
AddIcon /icons/a.gif .ps .ai .eps
AddIcon /icons/layout.gif .html .shtml .htm .pdf
AddIcon /icons/text.gif .txt
AddIcon /icons/c.gif .c
AddIcon /icons/p.gif .pl .py
AddIcon /icons/f.gif .for
AddIcon /icons/dvi.gif .dvi
AddIcon /icons/uuencoded.gif .uu
AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
AddIcon /icons/tex.gif .tex
AddIcon /icons/bomb.gif core

AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^


# This is from Matty J's patch. Anyone want to make the icons?
#AddIcon /icons/dirsymlink.jpg ^^SYMDIR^^
#AddIcon /icons/symlink.jpg ^^SYMLINK^^

DefaultIcon /icons/unknown.gif

ReadmeName README.html
HeaderName HEADER.html

IndexIgnore .??* *~ *# HEADER* RCS CVS *,t

AddEncoding x-compress Z
AddEncoding x-gzip gz tgz

AddLanguage da .dk
AddLanguage nl .nl
AddLanguage en .en
AddLanguage et .et
AddLanguage fr .fr
AddLanguage de .de
AddLanguage el .el
AddLanguage it .it
AddLanguage ja .ja
AddLanguage pl .po
AddLanguage ko .ko
AddLanguage pt .pt
AddLanguage no .no
AddLanguage pt-br .pt-br
AddLanguage ltz .ltz
AddLanguage ca .ca
AddLanguage es .es
AddLanguage sv .se
AddLanguage cz .cz
AddLanguage ru .ru
AddLanguage tw .tw
AddLanguage zh-tw .tw

LanguagePriority  it en da nl et fr de el ja ko no pl pt pt-br ltz ca es sv tw


#AddDefaultCharset	ISO-8859-1

AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
# AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
# AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb	
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
# AddCharset ISO-2022-JP .iso2022-jp .jis
# AddCharset ISO-2022-KR .iso2022-kr .kis
# AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
# AddCharset KOI8-r      .koi8-r .koi8-ru
# AddCharset KOI8-ru     .koi8-uk .ua
# AddCharset ISO-10646-UCS-2 .ucs2
# AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-8       .utf8

AddCharset GB2312      .gb2312 .gb 
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5	       .big5 .b5
AddCharset EUC-TW      .euc-tw	
# AddCharset EUC-JP      .euc-jp
AddCharset EUC-KR      .euc-kr
AddCharset shift_jis   .sjis

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps

AddType application/x-tar .tgz

# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi

# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>

# If you wish to use server-parsed imagemap files, use
#
#AddHandler imap-file map

BrowserMatch "Mozilla/2" nokeepalive
BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
BrowserMatch "RealPlayer 4\.0" force-response-1.0
BrowserMatch "Java/1\.0" force-response-1.0
BrowserMatch "JDK/1\.0" force-response-1.0

#
# The following directive disables redirects on non-GET requests for
# a directory that does not include the trailing slash.  This fixes a 
# problem with Microsoft WebFolders which does not appropriately handle 
# redirects for folders with DAV methods.
#

BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^gnome-vfs" redirect-carefully
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully

# Allow server status reports, with the URL of http://servername/server-status
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-status>
#    SetHandler server-status
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Allow remote server configuration reports, with the URL of
#  http://servername/server-info (requires that mod_info.c be loaded).
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-info>
#    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*
DocumentRoot /var/www
ServerAdmin xxxxxxxxxxxxxxxxxxxxx
ServerName xxxxxxxxxxxxxxxxxxxxxxx


ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/var/www/webalizer">
AuthName "webalizer"
AuthType Basic
require user xxxxxxxxx
</Directory>



```

then the rest:

```
 $ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 17:47 ?        00:00:01 init [2]         
root         2     1  0 17:47 ?        00:00:00 [migration/0]
root         3     1  0 17:47 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 17:47 ?        00:00:00 [watchdog/0]
root         5     1  0 17:47 ?        00:00:00 [migration/1]
root         6     1  0 17:47 ?        00:00:00 [ksoftirqd/1]
root         7     1  0 17:47 ?        00:00:00 [watchdog/1]
root         8     1  0 17:47 ?        00:00:00 [events/0]
root         9     1  0 17:47 ?        00:00:00 [events/1]
root        10     1  0 17:47 ?        00:00:00 [khelper]
root        11     1  0 17:47 ?        00:00:00 [kthread]
root        14    11  0 17:47 ?        00:00:00 [kblockd/0]
root        15    11  0 17:47 ?        00:00:00 [kblockd/1]
root        16    11  0 17:47 ?        00:00:00 [kacpid]
root       130    11  0 17:47 ?        00:00:00 [pdflush]
root       131    11  0 17:47 ?        00:00:00 [pdflush]
root       132     1  0 17:47 ?        00:00:00 [kswapd0]
root       133    11  0 17:47 ?        00:00:00 [aio/0]
root       134    11  0 17:47 ?        00:00:00 [aio/1]
root       722    11  0 17:47 ?        00:00:00 [kseriod]
root       807     1  0 17:47 ?        00:00:00 [kirqd]
root      1769    11  0 17:47 ?        00:00:00 [ata/0]
root      1770    11  0 17:47 ?        00:00:00 [ata/1]
root      1771    11  0 17:47 ?        00:00:00 [ata_hotplug/0]
root      1772    11  0 17:47 ?        00:00:00 [ata_hotplug/1]
root      1776    11  0 17:47 ?        00:00:00 [scsi_eh_0]
root      1778    11  0 17:47 ?        00:00:00 [scsi_eh_1]
root      1892    11  0 17:47 ?        00:00:00 [khubd]
root      2273    11  0 17:47 ?        00:00:00 [md0_raid1]
root      2299    11  0 17:47 ?        00:00:00 [md1_raid1]
root      2326    11  0 17:47 ?        00:00:00 [md2_raid1]
root      2354    11  0 17:47 ?        00:00:00 [md3_raid1]
root      2422     1  0 17:47 ?        00:00:00 [kjournald]
root      2638     1  0 17:47 ?        00:00:00 /sbin/udevd --daemon
root      3474     1  0 17:47 ?        00:00:00 [shpchpd_event]
root      3928     1  0 17:47 ?        00:00:00 [kjournald]
root      3929     1  0 17:47 ?        00:00:00 [kjournald]
root      3930     1  0 17:47 ?        00:00:00 [kjournald]
root      4320     1  0 17:47 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
syslog    4420     1  0 17:47 ?        00:00:00 /sbin/syslogd -u syslog
root      4443     1  0 17:47 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4445     1  0 17:47 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
100       4473     1  0 17:47 ?        00:00:11 /usr/bin/dbus-daemon --system
110       4486     1  0 17:47 ?        00:00:09 /usr/sbin/hald
root      4487  4486  0 17:47 ?        00:00:00 hald-runner
110       4492  4487  0 17:47 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
110       4560  4487  0 17:47 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      4583     1  0 17:47 ?        00:00:00 /usr/sbin/inetd
root      4587     1  0 17:47 ?        00:00:00 /bin/sh /usr/sbin/iptotald
root      4612     1  0 17:47 ?        00:00:00 /usr/bin/perl -w /usr/sbin/ddcli
root      4624     1  0 17:47 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4688  4624  0 17:47 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr
root      4689  4624  0 17:47 ?        00:00:00 logger -p daemon.err -t mysqld_s
root      4832     1  0 17:47 ?        00:00:00 /usr/bin/python /usr/bin/landsca
root      4833  4832  0 17:47 ?        00:01:12 /usr/bin/python /usr/bin/landsca
root      4837     1  0 17:47 ?        00:00:00 /usr/lib/postfix/master
root      4848     1  0 17:47 ?        00:00:00 /usr/sbin/powernowd -q
postfix   4855  4837  0 17:47 ?        00:00:00 qmgr -l -t fifo -u -c
root      4866     1  0 17:47 ?        00:00:00 /usr/sbin/sshd
root      4880     1  0 17:47 ?        00:00:02 /usr/lib/jvm/java-1.5.0-sun//bin
daemon    4884     1  0 17:47 ?        00:00:00 /usr/sbin/uptimed
root      4895     1  0 17:47 ?        00:00:00 /usr/sbin/vsftpd
root      4960     1  0 17:47 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
daemon    4973     1  0 17:47 ?        00:00:00 /usr/sbin/atd
root      4985     1  0 17:47 ?        00:00:00 /usr/sbin/cron
root      5043     1  0 17:47 tty1     00:00:00 /sbin/getty 38400 tty1
root      5044     1  0 17:47 tty2     00:00:00 /sbin/getty 38400 tty2
twilight 13234     1  0 18:00 ?        00:00:00 /usr/bin/python /usr/bin/supybot
postfix  21666  4837  0 19:27 ?        00:00:00 pickup -l -t fifo -u -c
root     22453     1  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22454 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22455 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22456 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22457 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22458 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22459 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22461 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22462 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22463 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22467 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22469 22453  0 19:59 ?        00:00:00 /usr/sbin/apache2 -k start
root     22530  4866  0 20:07 ?        00:00:00 sshd: fabio [priv]
fabio    22532 22530  0 20:07 ?        00:00:00 sshd: fabio@notty
fabio    22533 22532  0 20:07 ?        00:00:00 /usr/lib/openssh/sftp-server
root     22628  4587  0 20:17 ?        00:00:00 /usr/sbin/iptotal -r 60 eth0
root     22629  4866  0 20:17 ?        00:00:00 sshd: fabio [priv]
fabio    22631 22629  0 20:17 ?        00:00:00 sshd: fabio@pts/0
fabio    22632 22631  0 20:17 pts/0    00:00:00 -bash
fabio    22641 22632  0 20:17 pts/0    00:00:00 ps -ef

```

and:
```
$ netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.100:25        0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.100:55865     91.189.90.220:80        TIME_WAIT  
tcp        0      0 192.168.1.100:55864     91.189.90.220:80        TIME_WAIT  
tcp6       0      0 ::ffff:127.0.0.1:8005   :::*                    LISTEN     
tcp6       0      0 :::8009                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::8080                 :::*                    LISTEN     
tcp6       0      0 :::1402                 :::*                    LISTEN     
tcp6       0      0 :::443                  :::*                    LISTEN     
tcp6       0   0 ::ffff:192.168.1.100:1402 ::ffff:192.168.1.3:46021 ESTABLISHED
tcp6       0   0 ::ffff:192.168.1.100:1402 ::ffff:192.168.1.3:49576 ESTABLISHED
```


Concerning server-status:
```
apache2ctl status

                                   Not Found

   The requested URL /server-status was not found on this server.

```


But, as I told you, all this has happened suddenly, after 2 years of honest job! And when I restart the server it reaches MacClients in a minute..

---

### Post by faulkes on 2008-02-09
Understood that the server has been running with no problems for a long time, however there is a broad scope of possible reasons why this is happening.

When the server dies, again look at the output of the commands used last time (don't stop the server or anything, let it sit there dead while you collect information).  We don't need to look at the conf again, at least not yet.

I would also consider setting up the server-status configuration in the conf file (near the very bottom of the conf) and monitoring the output there to get a better idea what is happening internally with apache.

Faulkes

---

### Post by saltydog on 2008-02-09
I will keep looking and let you know. 
Thanks

---

### Post by saltydog on 2008-02-10
The server has restarted normal operations, without changing anything.

Would could have been happened yesterday?

---

### Post by faulkes on 2008-02-10
Without more information it would be almost impossible to say.  If it happens again, collect as much information as possible (i.e. server-status output, ps output, netstat -ant, maybe even a tcpdump thrown in) and paste it back here.

Faulkes

---

### Post by tessmonsta on 2008-04-07
The same thing is happening to me on a new install. It also looks like PHP segfaulted multiple times. This also results in a lock on mysql and sshd. I don't have physical access to the server at the moment, so I had to leave it running. About 24 hours later it consumed enough memory and finally died. After some cleanup, it was working again.

I had the maxclients setting up to 1500, so something is wrong...

---

