---
title: "help configuring apache2 on ubuntu dapper"
date: 2007-02-08
forum: Server Platforms
---

### Post by 95aspire on 2007-02-08
heres teh current config, this is confusing as heck lol. 

i want to create 2 sites, both just html right now.

both sites are under this dir /media/webdata/website
dir names are
cars
and notperfect

right now im having to use a port 80 redirect cause my isp blocks webserver on port 80 lol
current port is 8080. any help is welcome lol

and yes i am a newb at this but i did get my ftp server running without needing to post for help lol. this site has been helpful so far. and this linux build is awsome lol. 

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


#AddDefaultCharset	ISO-8859-1

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
AddCharset big5	       .big5 .b5
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
Include /etc/apache2/sites-enabled/[^.#]*

```

---

### Post by jtc on 2007-02-08
> **95aspire said:**
>  

i want to create 2 sites, both just html right now.

both sites are under this dir /media/webdata/website
dir names are
cars
and notperfect


Which way do you want your two sites

[http://cars.domain.tld/](http://cars.domain.tld/) and [http://notperfect.domain.tld/](http://notperfect.domain.tld/)
OR
[http://your.domain.tld/cars/](http://your.domain.tld/cars/) and [http://your.domain.tld/notperfect/](http://your.domain.tld/notperfect/)

(The later one is a lot easier, by the way).

---

### Post by 95aspire on 2007-02-08
i dont have my own web domain name, im using no-ip.org

the one for cars is 
jakes58.hopto.org
the one for notperfect is
notperfect.hopto.org

thanks for the fast reply

---

### Post by jtc on 2007-02-08
Ok, here we go...

Since you'll be using port 8080 you'll have to change ports.conf to reflect that.

You shouldn't have to do anything about apache2.conf.

Now let us first get one of the sites running, say cars.

Edit sites-available/default and do the following changes

[LIST=1]
[*]Add this line somewhere at the top, but below the <Virtualhost *>
```
ServerName jakes58.hopto.org
```
[*]At those places where you find the /var/www you change it to /media/webdata/website/cars
It should be in assocation with DocumentRoot and <Directory ....>
[/LIST]

If you now restart Apache2, the site should work.

Assuming everything worked out fine, let us continue with the second site.

copy sites-available/default  to sites-available/notperfect

Edit sites-available/notperfect and do the following changes
[LIST=1]
[*]Remove the first line, saying NameVirtualHost *
[*]Change ServerName, DocumentRoot and <Directory ...> reflecting the new site.
[/LIST]
Now run this command
```
sudo a2ensite notperfect
```
...and restart Apache2.

Tada!
(hopefully)

Actually, there are a few more details we might want to take a look at, but let us get this stuff working first.

---

### Post by 95aspire on 2007-02-08
ok, gonna take a shower real fast and ill be back and try it

---

### Post by 95aspire on 2007-02-09
i have nothing in my default file you specified, ill keep looking but nothing in the file in sites-avail folder

---

### Post by 95aspire on 2007-02-09
ok lol sorry i keep editing lol got it set up and can access from several machines, problem now is. no matter which site i go to 

jakes58.hopto.org
or notperfect.hopto.org

it pulls up the jakes58 site

now what do i do lol

---

### Post by 95aspire on 2007-02-09
bump, anyone know this issue lol? had the same issue when i had apache set up on my windows server lol dont know what to do to fix

---

### Post by jtc on 2007-02-09
The reason you experience this behavior is that jakes58 is the default vhost, making it catch all the domainnames not associated with another vhost. Now we only need to find out why the notperfect.hopto.org isn't working as it should :)

First of we should check whatever the notperfect-vhost is properly enabled. Is there a (sym)link to it in sites-enabled/ ?
(I.e. did the a2ensite-command do its job)

Unless that is the issue, it would help if I could see your two vhost-files; default and notperfect, or whatever you call them.

---

### Post by 95aspire on 2007-02-09
the terminal said that command worked lol

heres default

```
NameVirtualHost *
<VirtualHost *>
	ServerName jakes58.hopto.org
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/webdata/website/cars
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/webdata/website/cars>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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



Here is notperfect
```
NameVirtualHost *
<VirtualHost *>
	ServerName notperfect.hopto.org
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/webdata/website/notperfect
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/webdata/website/notperfect>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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

---

### Post by jtc on 2007-02-09
Well, humor me and give a list of the content in sites-enabled/  :-)

Anyhow, noticed an error in notperfect which might just screw things upp.

The first line "NameVirtualHost *" shouldn't be there. It should/needs only to be run once, and that is in the default-vhost-file.

---

### Post by 95aspire on 2007-02-09
ok, files in sites-enabled are 000-default and notperfect


removed the line u said and still wont pull up notperfect site lol.

---

### Post by jtc on 2007-02-09
Was a while since I set up an Ubuntu-server from scratch. Perhaps the vhost-module isn't loaded by default. Take a look in mods-enabled/ and see if you can find a symlink to vhost_alias. If not, you want to enable that module by running
```
sudo a2enmod vhost_alias
```
(and then restart apache2, of course)

---

### Post by 95aspire on 2007-02-09
wasnt there so ran the cmd, but still same thing lol

---

### Post by jtc on 2007-02-09
Now I've looked at the two sites/domain, and I'm pretty sure the fault is not in Apache2.

When you goto those domain you don't access you webbserver you get a page located at no-ip.com containing one big frame, loading from your ip-number. In other words, the connection to your server is always by ip-address, rendering the servername directive useless.

To use vhosts based on hostnames you'll actually have to make a DNS-entry linking those hostnames to your ip-address

---

### Post by jtc on 2007-02-09
Or, there is an entirely different approach.

If you don't mind continue running in those frames, you can simply use the same "frame-pointing" method towards [http://your-ip-address:8080/cars](http://your-ip-address:8080/cars) and [http://your-ip-number:8080/notperfect](http://your-ip-number:8080/notperfect)

Those addresses aren't shown in the browser anyhow.

---

### Post by 95aspire on 2007-02-09
so far so good, question now, how do i tell apache what types of files to open, for instance jakes58 is html, and notperfect is htm, where is this settings, i had it set on windows box but cant find it now lol

---

### Post by 95aspire on 2007-02-09
nvm found it lol

---

