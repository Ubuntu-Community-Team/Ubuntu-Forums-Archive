---
title: "Apache2 won't start, httpd not running."
date: 2008-07-12
forum: Server Platforms
---

### Post by LPomfrey on 2008-07-12
I'm having some trouble starting Apache2.

Running
```
/etc/init.d/apache2 start
```
fails with no error message at all. Running
```
/etc/init.d/apache2 restart
```
fails with the message:
```
* Restarting web server htcacheclean
...not running
httpd (no pid file) not running
```

/var/log/apache2/error.log contains the following:
```
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\input\t\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\section\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\setlength\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\documentstyle\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\chapter\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type search/400\t\\\\documentclass\ttext/x-tex invalid
[Sat Jul 12 15:33:54 2008] [error] mod_mime_magic: type regex\t\t[Cc]onstant[[:space:]]+[Ss]tory\ttext/x-inform invalid
[Sat Jul 12 15:33:54 2008] [error] Init: Private key not found
[Sat Jul 12 15:33:54 2008] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Sat Jul 12 15:33:54 2008] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Sat Jul 12 15:33:54 2008] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Sat Jul 12 15:33:54 2008] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
```
Which I'm guessing isn't the cause of the problem since removing mod_mime_magic from mods-enabled, and removing the only site that requires SSL from sites-enabled doesn't seem to make a difference.

Here is my apache.conf:
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
MaxClients          20
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
StartServers         2
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

NameVirtualHost *

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
Include /etc/apache2/conf.d

#Let's have some Icons, shall we?
#Alias /icons/ "/usr/share/apache2/icons/"
#<Directory "/usr/share/apache2/icons">
#    Options Indexes MultiViews
#    AllowOverride None
#    Order allow,deny
#    Allow from all
#</Directory>

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

#UserDir public_html

#<Directory /home/*/public_html>
#       AllowOverride FileInfo AuthConfig Limit
#       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

UseCanonicalName Off

TypesConfig /etc/mime.types
DefaultType text/plain

HostnameLookups Off

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

LanguagePriority en da nl et fr de el it ja ko no pl pt pt-br ltz ca es sv tw


AddDefaultCharset       ISO-8859-1
AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-8       .utf8

AddCharset GB2312      .gb2312 .gb
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5        .big5 .b5
AddCharset EUC-TW      .euc-tw
AddCharset EUC-JP      .euc-jp
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
Include /etc/apache2/sites-enabled

```

In /etc/apache/conf.d/ I have:
[LIST]
[*]proxy.conf
 ```
<IfModule mod_proxy.c>
      #turning ProxyRequests on and allowing proxying from all may allow
      #spammers to use your proxy to send email.
      ProxyRequests Off
      #<Proxy *>
      #       Order deny,allow
      #       Deny from all
      #       #Allow from .your_domain.com
      #</Proxy>
      # allow to connect to localhost with port ending with 80 and 90 (www, webdav)
      # the having at least 2 digets before the 80 or 90
      <ProxyMatch http://localhost:[0-9]{2,}?[8|9]0/.*>
              Order deny,allow
              Allow from all
      </ProxyMatch>
      # Enable/disable the handling of HTTP/1.1 "Via:" headers.
      # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
      # Set to one of: Off | On | Full | Block
      ProxyVia On
      # To enable the cache as well, edit and uncomment the following lines:
      # (no cacheing without CacheRoot)
      #CacheRoot "/var/cache/apache2/proxy"
      # 300MB
      #CacheSize 307200
      # in hours
      #CacheGcInterval 4
      CacheMaxExpire 24
      CacheLastModifiedFactor 0.1
      CacheDefaultExpire 1
      #CacheForceCompletion 100
      # Again, you probably should change this.
      #NoCache a_domain.com another_domain.edu joes.garage_sale.com
</IfModule>

```
[*]deflate.conf
 ```
<IfModule mod_deflate.c>
 DeflateCompressionLevel 3
 DeflateFilterNote Input instream
 DeflateFilterNote Output outstream
 DeflateFilterNote Ratio ratio
 LogFormat '"%r" %{outstream}n/%{instream}n (%{ratio}n%%)' deflate
 # Netscape 4.x has some problems...
 BrowserMatch ^Mozilla/4 gzip-only-text/html
 # Netscape 4.06-4.08 have some more problems
 BrowserMatch ^Mozilla/4\.0[678] no-gzip
 # MSIE masquerades as Netscape, but it is fine
 #BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
 # NOTE: Due to a bug in mod_setenvif up to Apache 2.0.48
 # the above regex won't work. You can use the following
 # workaround to get the desired effect:
 BrowserMatch \bMSI[E] !no-gzip !gzip-only-text/html
 # Don't compress images, java scripts and style sheets
 SetEnvIfNoCase Request_URI \
   \.(?:gif|jpe?g|png|js|css)$ no-gzip dont-vary
 # Make sure proxies don't deliver the wrong content
 # this needs mod_headers but it's very important
 # so I don't add a IfModule around it
 Header append Vary User-Agent env=!dont-vary
</IfModule>

```
[*]namedvirtualhost.conf
 ```
NameVirtualHost *:80
<IfModule mod_ssl.c>
  NameVirtualHost *:443
</IfModule>

```
[*]ssl.conf
 ```
<IfModule mod_ssl.c>
  SSLEngine on
  SSLCipherSuite ALL:!ADH:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
  # path to a directory containing the ssl ca keyring and revocation list
  # you must create hash symlinks using the right Makefile!
  SSLCACertificatePath    /etc/apache2/ssl/crt/
  SSLCARevocationPath     /etc/apache2/ssl/crl/
  SSLSessionCache shm:/var/log/apache2/ssl_scache(128000)
  SSLMutex sem
  SSLRandomSeed startup file:/dev/urandom 512
  SSLRandomSeed connect file:/dev/urandom 512
</IfModule>

```
[/LIST]

And in /etc/apache2/site-available/ I have:
[LIST]
[*]default
 ```
#NameVirtualHost *
<VirtualHost *>
        ServerName lukepomfrey.org
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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
        ServerSignature On

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
[*]lukepomfrey.org
 ```
<VirtualHost *:80>
  ServerName lukepomfrey.org
  ServerAlias   www.lukepomfrey.org
  ServerAdmin   webmaster@lukepomfrey.org
  ServerSignature On

  # we don't need a DocumentRoot for a zope only sites
  #DocumentRoot  /var/www/lukepomfrey.org

  CustomLog     /var/log/apache2/lukepomfrey.org-access.log combined
  ErrorLog      /var/log/apache2/lukepomfrey.org-error.log
  LogLevel warn

  # log the deflate compression rate to a file
  #CustomLog /var/log/apache2/deflate_log deflate

  <IfModule mod_rewrite.c>
    RewriteEngine On

    # use RewriteLog to debug problems with your rewrite rules
    # disable it after you found the error our your harddisk will be filled *very fast*
    # RewriteLog "/var/log/apache2/rewrite_log"
    # RewriteLogLevel 2

    # serving icons from apache 2 server
    RewriteRule ^/icons/ - [L]

    # rewrite any access to manage to a secure server
    RewriteRule ^/(.*)/manage(.*) https://secure.lukepomfrey.org/zope/lukepomfrey/lukepomfrey/$1/manage$2 [NC,R=301,L]
    RewriteRule ^/manage(.*) https://secure.lukepomfrey.org/zope/lukepomfrey/lukepomfrey/manage$1 [NC,R=301,L]


   # rewrite any other access to the zope server using a proxy [P] and add the VMH magic keywords
   # use %{SERVER_NAME} instead of example.com to avoid busting the ServerAlias
   # %{HTTP_HOST} is bad because it may contain the port
   RewriteRule ^/(.*) http://localhost:8100/VirtualHostBase/http/%{SERVER_NAME}:80/lukepomfrey/lukepomfrey/VirtualHostRoot/$1 [L,P]
</IfModule>

  <IfModule mod_proxy.c>
    ProxyVia On

    # prevent the webserver from beeing used as proxy
    <LocationMatch "^[^/]">
      Deny from all
    </LocationMatch>
  </IfModule>
  # caching (disabled)
  # this caches every file with the correct caching informations starting at /
  <IfModule mod_disk_cache.c>
    #CacheEnable disk /
  </IfModule>

  # compression (disabled)
  <IfModule mod_deflate.c>
    #SetOutputFilter DEFLATE
  </IfModule>
</VirtualHost>

```
[*]secure.lukepomfrey.org
 ```
<VirtualHost *:80>
 ServerName secure.lukepomfrey.org
 ServerAlias    secure.lukepomfrey.org
 ServerAdmin   webmaster@lukepomfrey.org
 ServerSignature On
 # we don't need a DocumentRoot for zope only sites
 #DocumentRoot /var/www/secure.lukepomfrey.org
 CustomLog     /var/log/apache2/secure.lukepomfrey.org-access.log combined
 ErrorLog      /var/log/apache2/secure.lukepomfrey.org-error.log
 LogLevel warn
 <IfModule mod_rewrite.c>
   RewriteEngine On
   # use RewriteLog to debug problems with your rewrite rules
   # disable it after you found the error our your harddisk will be filled *very fast*
   # RewriteLog "/var/log/apache2/rewrite_log"
   # RewriteLogLevel 2
   # Rewrite with redirect moved permanently
   RewriteRule ^/(.*) https://secure.lukepomfrey.org/$1 [R=301,L]
 </IfModule>
</VirtualHost>
<IfModule mod_ssl.c>
<VirtualHost *:443>
 ServerName     secure.lukepomfrey.org
 ServerAdmin    webmaster@lukepomfrey.org
 ServerSignature On
 #DocumentRoot   /var/www/secure.lukepomfrey.org-ssl
 CustomLog      /var/log/apache2/secure.lukepomfrey.org-ssl-access.log combined
 ErrorLog       /var/log/apache2/secure.lukepomfrey.org-ssl-error.log
 LogLevel warn
 SSLEngine On
 SSLCertificateFile /etc/apache2/ssl/crt/lukepomfrey.crt
 SSLCertificateKeyFile /etc/apache2/ssl/key/host.key
 <Location />
    # Force usage of ssl encryption
    SSLRequireSSL
    # SSL client certs: none, optional, require
    # Note: optional doesn't work with all browsers
    SSLVerifyClient optional
    SSLVerifyDepth 1
    SSLOptions +StdEnvVars +StrictRequire
    #optional +ExportCertData
 </Location>
 <IfModule mod_rewrite.c>
  RewriteEngine On
  #  use RewriteLog to debug problems with your rewrite rules
  #  disable it after you found the error our your harddisk will be filled *very fast*
  #  RewriteLog "/var/log/apache2/rewrite_log"
  #  RewriteLogLevel 2
  # The following rules will rewrite any access to https://secure.lukepomfrey.org/zope/lukepomfrey/
  # to the root of the zope instance running at localhost:8100
  RewriteRule ^/zope/main_instance$ http://localhost:8100/VirtualHostBase/https/secure.lukepomfrey.org:443/VirtualHostRoot/_vh_zope/_vh_lukepomfrey [L,P]
  RewriteRule ^/zope/main_instance/(.*) http://localhost:8100/VirtualHostBase/https/secure.lukepomfrey.org:443/VirtualHostRoot/_vh_zope/_vh_lukepomfrey/$1 [L,P]
 </IfModule>
 <IfModule mod_proxy.c>
  ProxyVia On
  # prevent the webserver from beeing used as proxy
  <LocationMatch "^[^/]">
     Deny from all
  </LocationMatch>
 </IfModule>
 # don't try to cache ssl!
 # compression (disabled)
 <IfModule mod_deflate.c>
    #SetOutputFilter DEFLATE
 </IfModule>
</VirtualHost>
</IfModule>

```

All three of those are symlinked in sites-enabled.

I've been googling and going through documentation all day to try and find an answer and can't seem to work it out. :(
[/LIST]

---

### Post by freebeer on 2008-07-12
Dumb question, probably... but are you starting/restarting with the sudo command?

---

### Post by windependence on 2008-07-12
Are you using named virtual hosts? If so, you cannot use SSL with those. You are getting SSL errors in the log. Try turning off SSL for now and see if you can start Apache.

-Tim

---

### Post by LPomfrey on 2008-07-12
> **windependence said:**
> Are you using named virtual hosts? If so, you cannot use SSL with those. You are getting SSL errors in the log. Try turning off SSL for now and see if you can start Apache.

-Tim

Yes, I am. And disabling SSL has worked. 

Thanks.

Is there any way to get around not being able to use SSL with named virtual hosts? I'd like to have secure access for logging on etc.

---

### Post by windependence on 2008-07-12
Logging on to where? Most applications have their ownspecific port they use for log on, such as Webmin port 10000 (or whatever you make it). This is independent of Apache. That being said if you are only hosting one domain, you can certainly set up Apache to listen on port 443 also for SSL connections and you would no need virtual hosts. It looks like you have just one domain so this might work for you.

-Tim

---

### Post by Master Chief on 2008-07-12
> **LPomfrey said:**
> Is there any way to get around not being able to use SSL with named virtual hosts? I'd like to have secure access for logging on etc.

Add port 80 to the NameVirtualHost directive, e.g.

NameVirtualHost 192.168.1.1:80

i.e. all normal traffic will now end up on port 80 and SSL traffic on port 443.  Giving you a maximum of one SSL virtual host and many non-SSL hosts (be a little creative and use that as guard for the protected web sites, just like large e-mail providers do for web mail).  Other options are to specify port numbers, e.g.

[https://my.website.org:12345](https://my.website.org:12345)

But I won't recommend using it because of the security issues involved (think port scanning and what not).  What does work, and can be used safely is to assign a simpel IP number to each virtual host.

I hope this is clear (enough) for you because I am dead tired and need sleep.  Lots of it.

---

### Post by LPomfrey on 2008-07-13
> **windependence said:**
> Logging on to where? Most applications have their ownspecific port they use for log on, such as Webmin port 10000 (or whatever you make it). This is independent of Apache. That being said if you are only hosting one domain, you can certainly set up Apache to listen on port 443 also for SSL connections and you would no need virtual hosts. It looks like you have just one domain so this might work for you.

-Tim

I'll have two Zope/Plone sites running behind Apache, so I wanted to have secure access to the management interface. From what I've read Zope doesn't "do" https access.

---

### Post by kurellajunior on 2008-09-02
> **freebeer said:**
> Dumb question, probably... but are you starting/restarting with the sudo command?
Thanks a lot :lolflag:
I was searching for 2 hours for a solution and simply forgot sudo... Was used to be root himself on Solaris. Need to get used to sudo soon. :dough:

---

### Post by freebeer on 2008-09-02
heh.  We've all done those kinds of things.  Glad I could be of help.  :D

---

### Post by thanxm on 2008-10-16
Thanx alot you guys are all great installed clavlib and all went well.

---

