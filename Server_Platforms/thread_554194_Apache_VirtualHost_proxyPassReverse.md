---
title: "Apache VirtualHost proxyPassReverse"
date: 2007-09-18
forum: Server Platforms
---

### Post by twistedtwig on 2007-09-18
how to get the proxypassreverse to be WITHIN the main domain.. where do I put the proxy bit in the config(s)


Hi all,

Ok so I have a few issues ***(3 questions, question one has been solved but 2 and 3 have not***), that I "think" are all related:

1)  [SOLVED: (see posts below for answer) ] - When I restart Apache I get the following warning:

```
root@betty:/etc/apache2# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                                                              
[Tue Sep 18 22:57:24 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Tue Sep 18 22:57:34 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                                                                                      [ OK ]

```

Here is my Vhosts file:

```
<VirtualHost *>
ServerName win.houseofhawkins.com
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass / http://192.168.10.100/
ProxyPassReverse / http://192.168.10.100/
</VirtualHost>

################### default root directory #################

<VirtualHost *>
ServerName houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

</VirtualHost>

################### Charlotte home page #################

<VirtualHost *>
ServerName charlotte.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/charlotte
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName footfaerie.me.uk
Serveralias www.footfaerie.me.uk footfaerie.me.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### gareth west home page #################

<VirtualHost *>
ServerName gareth-west.co.uk
Serveralias www.gareth-west.co.uk gareth-west.co.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/garethwest
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### dale home page #################

<VirtualHost *>
ServerName dale.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/dale
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Ethan home page #################

<VirtualHost *>
ServerName ethan.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/ethan
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Shak home page #################

<VirtualHost *>
ServerName shak.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/shak
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### test home page #################

<VirtualHost *>
ServerName test.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/test
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


```

Here is my apache2.conf:
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs-2.1/> for detailed information about
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
#
PidFile /var/run/apache2.pid

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

User www-data
Group www-data

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

TypesConfig /etc/mime.types

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

# Include generic snippets of statements
Include /etc/apache2/conf.d/

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
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

<IfModule alias_module>
    #
    # Aliases: Add here as many aliases as you need (with no limit). The format is 
    # Alias fakename realname
    #
    # Note that if you include a trailing / on fakename then the server will
    # require it to be present in the URL.  So "/icons" isn't aliased in this
    # example, only "/icons/".  If the fakename is slash-terminated, then the 
    # realname must also be slash terminated, and if the fakename omits the 
    # trailing slash, the realname must also omit it.
    #
    # We include the /icons/ alias for FancyIndexed directory listings.  If
    # you do not use FancyIndexing, you may comment this out.
    #
    Alias /icons/ "/usr/share/apache2/icons/"

    <Directory "/usr/share/apache2/icons">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

</IfModule>

#
# Directives controlling the display of server-generated directory listings.
#
<IfModule mod_autoindex.c>

    #
    # IndexOptions: Controls the appearance of server-generated directory
    # listings.
    #
    IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=*

    #
    # AddIcon* directives tell the server which icon to show for different
    # files or filename extensions.  These are only displayed for
    # FancyIndexed directories.
    #
    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

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

    #
    # DefaultIcon is which icon to show for files which do not have an icon
    # explicitly set.
    #
    DefaultIcon /icons/unknown.gif

    #
    # AddDescription allows you to place a short description after a file in
    # server-generated indexes.  These are only displayed for FancyIndexed
    # directories.
    # Format: AddDescription "description" filename
    #
    #AddDescription "GZIP compressed document" .gz
    #AddDescription "tar archive" .tar
    #AddDescription "GZIP compressed tar archive" .tgz

    #
    # ReadmeName is the name of the README file the server will look for by
    # default, and append to directory listings.
    #
    # HeaderName is the name of a file which should be prepended to
    # directory indexes. 
    ReadmeName README.html
    HeaderName HEADER.html

    #
    # IndexIgnore is a set of filenames which directory indexing should ignore
    # and not include in the listing.  Shell-style wildcarding is permitted.
    #
    IndexIgnore .??* *~ *# RCS CVS *,v *,t 
</IfModule>

<IfModule mod_mime.c>

    #
    # AddType allows you to add to or override the MIME configuration
    # file mime.types for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    # Despite the name similarity, the following Add* directives have
    # nothing to do with the FancyIndexing customization directives above.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # DefaultLanguage and AddLanguage allows you to specify the language of 
    # a document. You can then use content negotiation to give a browser a 
    # file in a language the user can understand.
    #
    # Specify a default language. This means that all data
    # going out without a specific language tag (see below) will 
    # be marked with this one. You probably do NOT want to set
    # this unless you are sure it is correct for all cases.
    #
    # * It is generally better to not mark a page as 
    # * being a certain language than marking it with the wrong
    # * language!
    #
    # DefaultLanguage nl
    #
    # Note 1: The suffix does not have to be the same as the language
    # keyword --- those with documents in Polish (whose net-standard
    # language code is pl) may wish to use "AddLanguage pl .po" to
    # avoid the ambiguity with the common suffix for perl scripts.
    #
    # Note 2: The example entries below illustrate that in some cases 
    # the two character 'Language' abbreviation is not identical to 
    # the two character 'Country' code for its country,
    # E.g. 'Danmark/dk' versus 'Danish/da'.
    #
    # Note 3: In the case of 'ltz' we violate the RFC by using a three char
    # specifier. There is 'work in progress' to fix this and get
    # the reference data for rfc1766 cleaned up.
    #
    # Catalan (ca) - Croatian (hr) - Czech (cs) - Danish (da) - Dutch (nl)
    # English (en) - Esperanto (eo) - Estonian (et) - French (fr) - German (de)
    # Greek-Modern (el) - Hebrew (he) - Italian (it) - Japanese (ja)
    # Korean (ko) - Luxembourgeois* (ltz) - Norwegian Nynorsk (nn)
    # Norwegian (no) - Polish (pl) - Portugese (pt)
    # Brazilian Portuguese (pt-BR) - Russian (ru) - Swedish (sv)
    # Simplified Chinese (zh-CN) - Spanish (es) - Traditional Chinese (zh-TW)
    #
    AddLanguage ca .ca
    AddLanguage cs .cz .cs
    AddLanguage da .dk
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage en .en
    AddLanguage eo .eo
    AddLanguage es .es
    AddLanguage et .et
    AddLanguage fr .fr
    AddLanguage he .he
    AddLanguage hr .hr
    AddLanguage it .it
    AddLanguage ja .ja
    AddLanguage ko .ko
    AddLanguage ltz .ltz
    AddLanguage nl .nl
    AddLanguage nn .nn
    AddLanguage no .no
    AddLanguage pl .po
    AddLanguage pt .pt
    AddLanguage pt-BR .pt-br
    AddLanguage ru .ru
    AddLanguage sv .sv
    AddLanguage zh-CN .zh-cn
    AddLanguage zh-TW .zh-tw
</IfModule>

<IfModule mod_negotiation.c>
    #
    # LanguagePriority allows you to give precedence to some languages
    # in case of a tie during content negotiation.
    #
    # Just list the languages in decreasing order of preference. We have
    # more or less alphabetized them here. You probably want to change this.
    #
    LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW

    #
    # ForceLanguagePriority allows you to serve a result page rather than
    # MULTIPLE CHOICES (Prefer) [in case of a tie] or NOT ACCEPTABLE (Fallback)
    # [in case no accepted languages matched the available variants]
    #
    ForceLanguagePriority Prefer Fallback

</IfModule>

<IfModule mod_mime.c>
    #
    # Specify a default charset for all pages sent out. This is
    # always a good idea and opens the door for future internationalisation
    # of your web site, should you ever want it. Specifying it as
    # a default does little harm; as the standard dictates that a page
    # is in iso-8859-1 (latin1) unless specified otherwise i.e. you
    # are merely stating the obvious. There are also some security
    # reasons in browsers, related to javascript and URL parsing
    # which encourage you to always set a default char set.
    #
    #AddDefaultCharset ISO-8859-1

    #
    # Commonly used filename extensions to character sets. You probably
    # want to avoid clashes with the language extensions, unless you
    # are good at carefully testing your setup after each change.
    # See http://www.iana.org/assignments/character-sets for the
    # official list of charset names and their respective RFCs.
    #
    AddCharset us-ascii    .ascii .us-ascii
    AddCharset ISO-8859-1  .iso8859-1  .latin1
    AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
    AddCharset ISO-8859-3  .iso8859-3  .latin3
    AddCharset ISO-8859-4  .iso8859-4  .latin4
    AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
    AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
    AddCharset ISO-8859-7  .iso8859-7  .grk .greek
    AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
    AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
    AddCharset ISO-8859-10  .iso8859-10  .latin6
    AddCharset ISO-8859-13  .iso8859-13
    AddCharset ISO-8859-14  .iso8859-14  .latin8
    AddCharset ISO-8859-15  .iso8859-15  .latin9
    AddCharset ISO-8859-16  .iso8859-16  .latin10
    AddCharset ISO-2022-JP .iso2022-jp .jis
    AddCharset ISO-2022-KR .iso2022-kr .kis
    AddCharset ISO-2022-CN .iso2022-cn .cis
    AddCharset Big5        .Big5       .big5 .b5
    AddCharset cn-Big5     .cn-big5
    # For russian, more than one charset is used (depends on client, mostly):
    AddCharset WINDOWS-1251 .cp-1251   .win-1251
    AddCharset CP866       .cp866
    AddCharset KOI8      .koi8
    AddCharset KOI8-E      .koi8-e
    AddCharset KOI8-r      .koi8-r .koi8-ru
    AddCharset KOI8-U      .koi8-u
    AddCharset KOI8-ru     .koi8-uk .ua
    AddCharset ISO-10646-UCS-2 .ucs2
    AddCharset ISO-10646-UCS-4 .ucs4
    AddCharset UTF-7       .utf7
    AddCharset UTF-8       .utf8
    AddCharset UTF-16      .utf16
    AddCharset UTF-16BE    .utf16be
    AddCharset UTF-16LE    .utf16le
    AddCharset UTF-32      .utf32
    AddCharset UTF-32BE    .utf32be
    AddCharset UTF-32LE    .utf32le
    AddCharset euc-cn      .euc-cn
    AddCharset euc-gb      .euc-gb
    AddCharset euc-jp      .euc-jp
    AddCharset euc-kr      .euc-kr
    #Not sure how euc-tw got in - IANA doesn't list it???
    AddCharset EUC-TW      .euc-tw
    AddCharset gb2312      .gb2312 .gb
    AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
    AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
    AddCharset shift_jis   .shift_jis .sjis

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    AddHandler cgi-script .cgi .pl

    #
    # For files that include their own HTTP headers:
    #
    #AddHandler send-as-is asis

    #
    # For server-parsed imagemap files:
    #
    #AddHandler imap-file map

    #
    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .text/htm .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# Action lets you define media types that will execute a script whenever
# a matching file is called. This eliminates the need for repeated URL
# pathnames for oft-used CGI file processors.
# Format: Action media/type /cgi-script/location
# Format: Action handler-name /cgi-script/location
#

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

<IfModule mod_setenvif.c>
    #
    # The following directives modify normal HTTP response behavior to
    # handle known problems with browser implementations.
    #
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
    # Same deal with Apple's DAV filesystem and Gnome VFS support for DAV.
    #
    BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
    BrowserMatch "MS FrontPage" redirect-carefully
    BrowserMatch "^WebDrive" redirect-carefully
    BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
    BrowserMatch "^gnome-vfs/1.0" redirect-carefully
    BrowserMatch "^XML Spy" redirect-carefully
    BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

#<IfModule mod_status.c>
    #
    # Allow server status reports generated by mod_status,
    # with the URL of http://servername/server-status
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-status>
    #    SetHandler server-status
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

#<IfModule mod_info.c>
    #
    # Allow remote server configuration reports, with the URL of
    #  http://servername/server-info (requires that mod_info.c be loaded).
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-info>
    #    SetHandler server-info
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

Alias /awstats-icon/ /usr/share/awstats/icon/

<Directory /usr/share/awstats/icon>
 Options None
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>

Alias /cgi-bin/ /usr/lib/cgi-bin/

<Directory /usr/lib/cgi-bin>
 Options FollowSymLinks +ExecCGI
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>
```

the httpd.conf has only this line:

```
Include vhosts.conf

```

It takes a while to get the second line of the error to appear..



2)   I am trying to get the apache server to point part of the site to a windows 2003 server which is inside my network (internal static IP).  I tried to get this to work a few months ago but failed misserably.  Since then I have completely reinstalled ubuntu server with 7.04 and want to get this working to allow further projects to happen.

As far as I understand from:

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html")

I need to use ProxyPassReverse.

the windows server is on a static IP of 192.168.10.100.  when you type that IP into a computer on the lan it comes up with the default page which works just fine.

I have the following modules enabled:

```
jon@betty:/etc/apache2/mods-enabled$ ls
alias.load       authz_default.load    authz_user.load  dir.conf  mime.load         php5.load           proxy_html.load  rewrite.load
auth_basic.load  authz_groupfile.load  autoindex.load   dir.load  negotiation.load  proxy.conf          proxy_http.load  setenvif.load
authn_file.load  authz_host.load       cgi.load         env.load  php5.conf         proxy_connect.load  proxy.load       status.load

```

I am using dynamic dns with easydns and have setup the win.houseofhawkins.com domain to point at houseofhawkins.com (as usual, I have a number of subdomains working just fine).  It resolves and tries to pull back the page but with no success.

It tries to load for a LONG time and eventually times out with the following error in the /var/log/apache2/error.log file:

```
[Tue Sep 18 22:25:36 2007] [error] (70007)The timeout specified has expired: proxy: HTTP: attempt to connect to 192.168.10.100:80 (192.168.10.100) failed
[Tue Sep 18 22:25:36 2007] [error] ap_proxy_connect_backend disabling worker for (192.168.10.100)
[Tue Sep 18 22:29:45 2007] [error] (70007)The timeout specified has expired: proxy: HTTP: attempt to connect to 192.168.10.100:80 (192.168.10.100) failed

```

Firefox comes back with:

error 503:

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.

Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 Server at win.houseofhawkins.com Port 80

How do I go about getting this to work Please?



3)  This is really an extension of question 2:

At present I am using a subdomain to try and point at a different server.  How do I try and use proxypassreverse so it is WITHIN [www.houseofhawkins.com](www.houseofhawkins.com).

For example [www.houseofhawkins.com/foo](www.houseofhawkins.com/foo) where foo is on the other server.

Where would I put this code, i.e. which config file?  Also how do I put it in there?  I presume it would not be inside a virtualHost?!?

Well.. that was a bit. I hope it was not info overload.  Thanks in advance for any and all help and advice

Thanks again

Twiggy

---

### Post by twistedtwig on 2007-09-19
I believe I may have found the asnwer to the first question.

it looks like it is probably set up in the default site.  Need to have a look for it tonight when I get in.  If that is the case removing it should get rid of that error.

Does anyone have any thoughts on the proxy pass reverse situation please?  

Thank you

---

### Post by twistedtwig on 2007-09-19
Yes problem one solved.  I commented out the first line of the "default" site in sites-enabled folder and no error now.

now to figure out my EVIL proxypassreverse issue

---

### Post by twistedtwig on 2007-09-19
Ok so I am moving on slowly...

I have removed the information from the Virtualhosts section and moved to the apache2.conf file.

here is what I phave put at the end of the conf file:

```
ProxyRequests Off
<Proxy *>
  Order deny,allow
#  Deny from all
  Allow from all
</Proxy>


ProxyPass        /wiggly/ http://192.168.10.100:80/
ProxyPassReverse /wiggly/ http://192.168.10.100:80/

```

When I request the page / folder where the proxypass should happen I wait for a LONG time and eventually get 503 error.  here is what the /var/log/apache2/error.log file has:

```
[Wed Sep 19 23:17:27 2007] [notice] caught SIGTERM, shutting down
[Wed Sep 19 23:17:38 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 configured -- resuming normal operations
[Wed Sep 19 23:20:10 2007] [error] [client 66.249.65.44] File does not exist: /var/www/root/foo
[Wed Sep 19 23:22:40 2007] [error] (70007)The timeout specified has expired: proxy: HTTP: attempt to connect to 192.168.10.100:80 (192.168.10.100) failed
[Wed Sep 19 23:22:40 2007] [error] ap_proxy_connect_backend disabling worker for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)
[Wed Sep 19 23:22:40 2007] [error] proxy: HTTP: disabled connection for (192.168.10.100)

```

I know the IP address works (on the lan)  I have tried pointing it at another apache (default config) as well as the windows 2003 server both same results.

---

### Post by twistedtwig on 2007-09-20
tested it locally and that worked straight away:

```
ProxyPass        /loc/ http://localhost/old/
ProxyPassReverse /loc/ http://localhost/old/

```

it would seem that it is the network side of things that are not working.

---

### Post by twistedtwig on 2007-09-20
I am going to try and point it at google and the like tonight to see if it is my internal network that it is not resolving or passing the info to or something.  Not really sure what is going on to be honest

---

### Post by twistedtwig on 2007-09-20
Ok so after putting this in:

```
ProxyRequests Off
<Proxy *>
  Order deny,allow
#  Deny from all
  Allow from all
</Proxy>


ProxyPass        /wiggly/ http://192.168.10.100:80/
ProxyPassReverse /wiggly/ http://192.168.10.100:80/

ProxyPass        /loc/ http://www.google.co.uk/
ProxyPassReverse /loc/ http://www.google.co.uk/

```

and force-reload of apache

houseofhawkins.com/loc/

does work and sends me to google.

From this I can only assume apache does not know of my internal network card / network and therefore can not resolve the IP or address.

Does anyone know how I could add this / correct this?

Thank you

---

### Post by twistedtwig on 2007-09-20
Ok so some more playing to report back (to my self so far :p )

```
ProxyRequests Off
<Proxy *>
  Order deny,allow
  Deny from all
  Allow from 192.168.10.0/24
</Proxy>


ProxyPass        /wiggly/ http://192.168.10.200:80/
ProxyPassReverse /wiggly/ http://192.168.10.200:80/

ProxyPass        /google/ http://www.google.co.uk/
ProxyPassReverse /google/ http://www.google.co.uk/

ProxyPass        /bobby/ http://192.168.10.100:80/
ProxyPassReverse /bobby/ http://192.168.10.100:80/

ProxyPass        /local/ http://localhost/old/
ProxyPassReverse /local/ http://localhost/old/

ProxyPass        /localIP/ http://192.168.10.1/old/
ProxyPassReverse /localIP/ http://192.168.10.1/old/

```

I was informed by a friend who showed me this post ([http://ubuntuforums.org/showthread.php?t=39328](http://ubuntuforums.org/showthread.php?t=39328)) that the proxy allow from all bit was very bad news... so changed it to what you see above (allow form 192.168.10.0/24) which is the local network which if i get it correctly means only the local network can use the proxy.

I have done a few proxy's to test bits.

I have found that the local and localIP work so it must be able to see the local network as localIP is using 192.168.10.1.  google works but wiggly and bobby do not (they are both the seperate web servers inside the network).

The error I get in /var/log/apache2/error.log is:

```
[Thu Sep 20 20:41:33 2007] [error] (70007)The timeout specified has expired: proxy: HTTP: attempt to connect to 192.168.10.100:80 (192.168.10.100) failed
[Thu Sep 20 20:41:33 2007] [error] ap_proxy_connect_backend disabling worker for (192.168.10.100)

```

It almost feels like I am getting close but not all at the same time.

Hope some one reads this and could provide some insight.. Please!!!!!!!!

Thank you

---

### Post by twistedtwig on 2007-09-20
the allow from all part in the proxy is not soo vitual:

> You can control who can access your proxy via the <Proxy> control block as in the following example:

<Proxy *>
Order Deny,Allow
Deny from all
Allow from 192.168.0
</Proxy>

For more information on access control directives, see mod_access.

Strictly limiting access is essential if you are using a forward proxy (using the ProxyRequests directive). Otherwise, your server can be used by any client to access arbitrary hosts while hiding his or her true identity. This is dangerous both for your network and for the Internet at large. When using a reverse proxy (using the ProxyPass directive with ProxyRequests Off), access control is less critical because clients can only contact the hosts that you have specifically configured.

from : [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)

But why leave the possiblity open so keeping the IP setitngs I have assuming it works :;

---

### Post by twistedtwig on 2007-09-20
POOOPPP!!!

just VPN'd into work network and tested my site from there.  normal page work but NONE of them work. all say forbidden... the error logs are:

```
[Thu Sep 20 21:05:34 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://www.google.co.uk/
[Thu Sep 20 21:05:44 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://localhost/old/
[Thu Sep 20 21:06:44 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://192.168.10.1/old/
[Thu Sep 20 21:06:55 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://192.168.10.200:80/

```

I would appriecate some advise on this.  I "think" I am safe with proxyrequests Off means only the proxypass I set up can be used so I am not a "zombie".

Don't want to be a bad proxy server could someone put me out of my missy if I allow all with the proxy please.

thanks

---

### Post by twistedtwig on 2007-09-21
bump!!.... does anyone know why this might happen please?

---

### Post by Brazen on 2007-09-21
> **twistedtwig said:**
> POOOPPP!!!

just VPN'd into work network and tested my site from there.  normal page work but NONE of them work. all say forbidden... the error logs are:

```
[Thu Sep 20 21:05:34 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://www.google.co.uk/
[Thu Sep 20 21:05:44 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://localhost/old/
[Thu Sep 20 21:06:44 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://192.168.10.1/old/
[Thu Sep 20 21:06:55 2007] [error] [client 82.148.58.163] client denied by server configuration: proxy:http://192.168.10.200:80/

```

I would appriecate some advise on this.  I "think" I am safe with proxyrequests Off means only the proxypass I set up can be used so I am not a "zombie".

Don't want to be a bad proxy server could someone put me out of my missy if I allow all with the proxy please.

thanks

If you have ProxyRequests off, then having the allow from all is fine, and if you want your internal sites accessible from the internet, you will WANT to have the allow from all.  The only time you need to restrict down who you allow the proxy from is if you have ProxyRequests on which allows any computer to proxy through that server to ANYWHERE.

Also, what happens if you are on a workstation on your local network and you try to browse directly to [http://192.168.1.100](http://192.168.1.100) ?  Does that bring up the webpage?  If not, then the problem is on the destination server, not the proxy server.

---

### Post by twistedtwig on 2007-09-21
Hi Brazen,

Thank you for your reply. )

when I do the IP directly inside the network it all comes up instantly.  There is no lag and the pages all display normally (no cookie or loggin in stuff to possibly block stuff).

I am pleased I understood the proxyPass bit and have set it up correctly.  Was worried that I could be used as a Proxy on the net for "naughty" things.

I am still fighting with the setup to try and get it to see / display / find the internal sites, but no joy as yet.

---

### Post by twistedtwig on 2007-09-23
Ok so I have found a possible answer, but have no idea why this might be the case. If I vnc onto the server I can ping each of the internal machines, but if I try and use firefox to view their pages directly they timeout.

I don't get why I can ping them but not view them

---

### Post by twistedtwig on 2007-09-23
was having a look at my hosts file to see if that might be the answer.

```
127.0.0.1       localhost
127.0.1.1       betty.range86-142.btcentralplus.com     betty

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

not sure why there is the 127.0.1.1 reference in there to be honest.

---

### Post by twistedtwig on 2007-09-23
I think it might be my firewall is blocking it.  I have IPTables running going to look at that.. I am very rusty on this though

---

### Post by twistedtwig on 2007-09-24
I had a go at the IPtables.  When I dropped all my rules and opened everything up I could see the webpage on the internal server straight away.  I reapplied my rules and couldn't see it again.

My next task is to find out why rule / set of rules is doing this.

---

### Post by Brazen on 2007-09-24
Wow, sorry I didn't get back with you, but looks like you've done a good job of methodically narrowing down the scope of the problem.

Does this proxy server have a gui on it (I think you said you used Firefox from it)?  Are you using Feisty or Dapper (the LTS release)?  Just a little FYI, but this doesn't apply directly to your problem: stick to the LTS releases on servers (currently Dapper), use the "Server" install media, and don't install anything you don't need to run the server.  For instance, the only extra thing you should install on this proxy server is "sudo aptitude install apache2" and maybe some php stuff if it is also to server up some php or whatever (though I like to use a proxy for just a proxy).  My few "indulgences" are screen, openssh-server, and webmin on every server (and VMWare Tools, since I put all my servers in virtual machines).

Ok, so back to fixing your firewall:  Are you using Firestarter to manage your firewall?  I haven't used Firestarter, but I have used Webmin extensively, particularly for firewall management.  If you can post your firewall config, I might be able to spot the problem.  Oh, and the point of bringing Webmin here is because I suggest using Webmin for managing your firewall.

---

### Post by twistedtwig on 2007-09-24
Hi Brazen.

I am using IPTables directly, i.e. a script file in init.d.  below is what I did to get it to work.  At the moment this server is the main one.  She does almost everything to be honest.  she is firewall, php, mysql webserver file server.  I use ssh into the server most the time but I do have a GUI on there (I feel safer when I break stuff I don't always full 100% comfy fixing it on the command line, although I am getting better.

it was the firewall.. When I allowed all traffic in and out of the internal interface on the server it was happy.  did a few online nmaps and nothing new was open, as I expected.  As I understand it allowing the internal interface to be trusted is not dangerous.

I hope what I did was not dangerous, in that it left me open to anything.

I hope to upgrade my server at some point (but money is sooo tight).  Would like to have enough power to run a base that is just the firewall and vmware and have a number of virtual servers, ubuntu and 2003 doing various jobs.

my spec below shows what she is, think she might handle one vm as long as the thing deals with 4 cores correctly.

---

### Post by Brazen on 2007-09-25
> **twistedtwig said:**
> Hi Brazen.

I am using IPTables directly, i.e. a script file in init.d.  below is what I did to get it to work.  At the moment this server is the main one.  She does almost everything to be honest.  she is firewall, php, mysql webserver file server.  I use ssh into the server most the time but I do have a GUI on there (I feel safer when I break stuff I don't always full 100% comfy fixing it on the command line, although I am getting better.

it was the firewall.. When I allowed all traffic in and out of the internal interface on the server it was happy.  did a few online nmaps and nothing new was open, as I expected.  As I understand it allowing the internal interface to be trusted is not dangerous.

I hope what I did was not dangerous, in that it left me open to anything.

I hope to upgrade my server at some point (but money is sooo tight).  Would like to have enough power to run a base that is just the firewall and vmware and have a number of virtual servers, ubuntu and 2003 doing various jobs.

my spec below shows what she is, think she might handle one vm as long as the thing deals with 4 cores correctly.

If you post your script, I'll have a look at it and let you know if I see anything bad.  Now, as I said I use Webmin to handle all my firewall configuration, but when iptables starts, it automatically looks for a file called something like "/etc/iptables-save" and loads up rules from that file (don't quote me on the name of that file though).  Once your configure your firewall by running all the iptables commands to create your rules, you can use the "iptables-save" command to save the config into the file in a format readable by iptables on startup.  I believe the command would be "iptables-save > /etc/iptables-save".

Once you create that file, it's easy to deduce the syntax and add/change your rules (then have iptables reread the file with "iptables-save").  This might be a better idea than your custom rc script.  I know I'm not certain on the name of the file to save, but if you google around you could probably find out more.

---

### Post by twistedtwig on 2007-09-25
here is my script..

will have a read up on those tonight :)

```
#!/bin/sh
#
# rc.firewall-2.4
FWVER=0.75
#
#               Initial SIMPLE IP Masquerade test for 2.4.x kernels
#               using IPTABLES.  
#
#               Once IP Masquerading has been tested, with this simple 
#               ruleset, it is highly recommended to use a stronger 
#               IPTABLES ruleset either given later in this HOWTO or 
#               from another reputable resource.
#
#
#
# Log:
#       0.75 - Added more kernel modules to the comments section
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables 
#            - Added additional formatting
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

echo -e "\n\nLoading simple rc.firewall version $FWVER..\n"


# The location of the iptables and kernel module programs
#
#   If your Linux distribution came with a copy of iptables, 
#   most likely all the programs will be located in /sbin.  If 
#   you manually compiled iptables, the default location will
#   be in /usr/local/sbin
#
# ** Please use the "whereis iptables" command to figure out 
# ** where your copy is and change the path below to reflect 
# ** your setup
#
IPTABLES=/sbin/iptables
#IPTABLES=/usr/local/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe


#Setting the EXTERNAL and INTERNAL interfaces for the network
#
#  Each IP Masquerade network needs to have at least one
#  external and one internal network.  The external network
#  is where the natting will occur and the internal network
#  should preferably be addressed with a RFC1918 private address
#  scheme.
#
#  For this example, "eth0" is external and "eth1" is internal"
#
#
#  NOTE:  If this doesnt EXACTLY fit your configuration, you must 
#         change the EXTIF or INTIF variables above. For example: 
#
#            If you are a PPPoE or analog modem user:
#
#               EXTIF="ppp0" 
#
#
EXTIF="eth0"
INTIF="eth1"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"


#======================================================================
#== No editing beyond this line is required for initial MASQ testing ==


echo -en "   loading modules: "

# Need to verify that all modules have all required dependencies
#
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

# With the new IPTABLES code, the core MASQ functionality is now either
# modular or compiled into the kernel.  This HOWTO shows ALL IPTABLES
# options as MODULES.  If your kernel is compiled correctly, there is
# NO need to load the kernel modules manually.  
#
#  NOTE: The following items are listed ONLY for informational reasons.
#        There is no reason to manual load these modules unless your
#        kernel is either mis-configured or you intentionally disabled
#        the kernel module autoloader.
#

# Upon the commands of starting up IP Masq on the server, the
# following kernel modules will be automatically loaded:
#
# NOTE:  Only load the IP MASQ modules you need.  All current IP MASQ 
#        modules are shown below but are commented out from loading.
# ===============================================================

echo "----------------------------------------------------------------------"

#Load the main body of the IPTABLES module - "iptable"
#  - Loaded automatically when the "iptables" command is invoked
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_tables, "
$MODPROBE ip_tables


#Load the IPTABLES filtering module - "iptable_filter" 
#  - Loaded automatically when filter policies are activated


#Load the stateful connection tracking framework - "ip_conntrack"
#
# The conntrack  module in itself does nothing without other specific 
# conntrack modules being loaded afterwards such as the "ip_conntrack_ftp"
# module
#
#  - This module is loaded automatically when MASQ functionality is 
#    enabled 
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack


#Load the FTP tracking mechanism for full FTP tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp


#Load the IRC tracking mechanism for full IRC tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_irc, "
$MODPROBE ip_conntrack_irc


#Load the general IPTABLES NAT code - "iptable_nat"
#  - Loaded automatically when MASQ functionality is turned on
# 
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "iptable_nat, "
$MODPROBE iptable_nat


#Loads the FTP NAT functionality into the core IPTABLES code
# Required to support non-PASV FTP.
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


#Loads the IRC NAT functionality into the core IPTABLES code
# Required to support NAT of IRC DCC requests
#
# Disabled by default -- remove the "#" on the next line to activate
#
#echo -e "ip_nat_irc"
#$MODPROBE ip_nat_irc

echo "----------------------------------------------------------------------"

# Just to be complete, here is a partial list of some of the other  
# IPTABLES kernel modules and their function.  Please note that most 
# of these modules (the ipt ones) are automatically loaded by the 
# master kernel module for proper operation and don't need to be 
# manually loaded.
# --------------------------------------------------------------------
#
#    ip_nat_snmp_basic - this module allows for proper NATing of some 
#                        SNMP traffic
#
#    iptable_mangle    - this target allows for packets to be 
#                        manipulated for things like the TCPMSS 
#                        option, etc.
#
# --
#
#    ipt_mark       - this target marks a given packet for future action.
#                     This automatically loads the ipt_MARK module
#
#    ipt_tcpmss     - this target allows to manipulate the TCP MSS
#                     option for braindead remote firewalls.
#                     This automatically loads the ipt_TCPMSS module
#
#    ipt_limit      - this target allows for packets to be limited to
#                     to many hits per sec/min/hr
#
#    ipt_multiport  - this match allows for targets within a range
#                     of port numbers vs. listing each port individually
#
#    ipt_state      - this match allows to catch packets with various
#                     IP and TCP flags set/unset
#
#    ipt_unclean    - this match allows to catch packets that have invalid
#                     IP/TCP flags set
#
#    iptable_filter - this module allows for packets to be DROPped, 
#                     REJECTed, or LOGged.  This module automatically 
#                     loads the following modules:
#
#                     ipt_LOG - this target allows for packets to be 
#                               logged
#
#                     ipt_REJECT - this target DROPs the packet and returns 
#                                  a configurable ICMP packet back to the 
#                                  sender.
# 

echo -e "   Done loading modules.\n"



#CRITICAL:  Enable IP forwarding since it is disabled by default since
#
#           Redhat Users:  you may try changing the options in
#                          /etc/sysconfig/network from:
#
#                       FORWARD_IPV4=false
#                             to
#                       FORWARD_IPV4=true
#
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward


# Dynamic IP users:
#
#   If you get your IP address dynamically from SLIP, PPP, or DHCP, 
#   enable this following option.  This enables dynamic-address hacking
#   which makes the life with Diald and similar programs much easier.
#
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr


# Enable simple IP forwarding and Masquerading
#
#  NOTE:  In IPTABLES speak, IP Masquerading is a form of SourceNAT or SNAT.
#
#  NOTE #2:  The following is an example for an internal LAN address in the
#            192.168.0.x network with a 255.255.255.0 or a "24" bit subnet mask
#            connecting to the Internet on external interface "eth1".  This
#            example will MASQ internal traffic out to the Internet but not
#            allow non-initiated traffic into your internal network.
#
#            
#         ** Please change the above network numbers, subnet mask, and your 
#         *** Internet connection interface name to match your setup
#         


#Clearing any previous configuration
#
#  Unless specified, the defaults for INPUT and OUTPUT is ACCEPT
#    The default for FORWARD is DROP (REJECT is not a valid policy)
#
echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -t nat -F

echo "   Opening loopback interface for socket based services."
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

echo "   Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A INPUT -i $INTIF -j ACCEPT
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -o $EXTIF -j ACCEPT
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG

iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

$IPTABLES -A INPUT -eth1 -j ACCEPT
$IPTABLES -A OUTPUT -o eth1 -j ACCEPT

echo "   Allowing packets with ICMP data (i.e. ping)."
$IPTABLES -A INPUT -p icmp -j ACCEPT
$IPTABLES -A OUTPUT -p icmp -j ACCEPT

echo "   Allow internal broadcast packets."
$IPTABLES -A INPUT -i $INTIF -d 192.168.10.255 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -d 192.168.10.255 -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF -d 192.168.10.255 -j ACCEPT

echo "   Port 137 is for NetBIOS."
$IPTABLES -A INPUT -i $INTIF -p udp --dport 137 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp --dport 137 -j ACCEPT

echo "   Opening port 53 for DNS queries."
$IPTABLES -A INPUT -p udp -i $EXTIF --sport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p udp -o $EXTIF --dport 53 -j ACCEPT

#echo "   Opening port 22 for remote SSH connections."
#$IPTABLES -A INPUT -p tcp -i $EXTIF --dport 22 -m state --state NEW -j ACCEPT

echo "   Opening port 80 for webserver."
$IPTABLES -A INPUT -p tcp -i $EXTIF --dport 80 -m state --state NEW -j ACCEPT

#echo "   Opening port 21 for FTP server."
#$IPTABLES -A INPUT -p tcp -i $EXTIF --dport 21 -m state --state NEW -j ACCEPT

#echo "   Opening port 5900 for VNC connections in."
#$IPTABLES -A INPUT -p tcp --dport 5900:5910 -j ACCEPT
#$IPTABLES -A OUTPUT -p tcp --dport 5900:5910 -j ACCEPT

#echo "   Diverting port 80 traffic through Squid."
#$IPTABLES -t nat -A PREROUTING -i $INTIF -p tcp --dport 80 -j REDIRECT --to-port 3128

#echo "   Opening port 1723 for VPN initiation."
#$IPTABLES -A INPUT -i $EXTIF -p TCP --dport 1723 -j ACCEPT

#echo "   opening terminal service to wiggly."
#$IPTABLES -A PREROUTING -t nat -i $EXTIF -p tcp --dport 3389 -j DNAT --to 192.168.10.99:3389
#$IPTABLES -A FORWARD -p tcp -m state --state NEW -d 192.168.10.99 --dport 3389 -j ACCEPT

#echo "   Forwarding 8866 to bobby:8866 for aspx website."
#$IPTABLES -A PREROUTING -t nat -i $EXTIF -p tcp --dport 8866 -j DNAT --to 192.168.10.100:80
#$IPTABLES -A FORWARD -p tcp -m state --state NEW -d 192.168.10.100 --dport 80 -j ACCEPT

#  NOTE THE THREE LINES BELOW ALLOW ACCESS FOR THE VPN CONNECTION...Ry.

$IPTABLES -A INPUT -i ppp+ -j ACCEPT
$IPTABLES -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o ppp+ -j ACCEPT

echo -e "\nrc.firewall-2.4 v$FWVER done.\n"

#this helps torrenting, my putter is a bit daft with the modem
echo 1024 > /proc/sys/net/ipv4/neigh/default/gc_thresh1
echo 2048 > /proc/sys/net/ipv4/neigh/default/gc_thresh2
echo 4096 > /proc/sys/net/ipv4/neigh/default/gc_thresh3

#kissd is my network dvd player
kissd -d
```

Thanks

---

### Post by Brazen on 2007-09-25
That actually looks like a pretty good overall script.  Where did you get that?

First thing I noticed, is it enables IP Forwarding by default, which is no big deal unless your machine has two network connection and you don't want it to act as a router.  I suppose as long as your have the FORWARD table do DROPs by default (which this script does) then it's the same thing.

Ok, now looking at this, it looks like this script IS meant to be used on a router.  It defines 2 interfaces: eth0 and eth1.  Do you have multiple network cards on this computer?  Are you using it for a router (ie. to connect your local network to the internet, used for you internet access?

---

### Post by twistedtwig on 2007-09-25
Your right on the money.

the server is my dns and dhcp server which takes the internet connection in on eth0 and routes it out to my local network via eth1. 

I got the script from a good friend who is way better at this stuff than me.

I really appreciate the help and guidance.

---

### Post by Brazen on 2007-09-26
I would get rid of this line > $IPTABLES -A INPUT -i $INTIF -j ACCEPT because it is completely opening up the server to your internal network.  Not a huge security risk, but if you have wireless and someone hacks it, then your server will be left wide open to them.  That's not to much of a concern on a linux box, but then why have a firewall at all, ya know?  Getting rid of this will not affect the routing.

---------------------------

Next, not a bid deal, but this line > iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
is identical to this line > $IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT

-----------------

this line > $IPTABLES -A INPUT -eth1 -j ACCEPT
has a mistake in it and is not doing anything but probably returning an error.

------------------

this line > $IPTABLES -A OUTPUT -o eth1 -j ACCEPT
is identical to this line > $IPTABLES -A OUTPUT -o $EXTIF -j ACCEPT

--------------------

this line is not necessary > $IPTABLES -A OUTPUT -p icmp -j ACCEPT
and I would probably get rid of this line also > $IPTABLES -A INPUT -p icmp -j ACCEPTso your server/router runs in "stealth mode" meaning it won't respond to pings or other ICMP request.  You could at least restrict it down by adding "-i $INTIF" to it.

--------------------

regarding this: > echo "   Allow internal broadcast packets."
$IPTABLES -A INPUT -i $INTIF -d 192.168.10.255 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -d 192.168.10.255 -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF -d 192.168.10.255 -j ACCEPT
The last two lines are not doing anything, other rules are already allowing these.  The second line (the first rule here) is not necessary and can be removed.  The only thing on this server that needs to accept broadcast packets would be the DHCP service and the only port needed for that is opened up down below.  Besides, it uses a static address so if your subnet ever changes, this rule will break anyway.

edit: oops, wait no there is not a rule allowing DHCP.  I would create a new rule allowing UPD port 67 from the internal interface, like this: > $IPTABLES -A INPUT -p udp -i $INTIF --dport 67 -m state --state NEW -j ACCEPT

-------------------------

> echo "   Port 137 is for NetBIOS."
$IPTABLES -A INPUT -i $INTIF -p udp --dport 137 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp --dport 137 -j ACCEPT
I don't know why you would enable netbios, unless you also have Samba on this server and have WINS enabled in the config.

----------------------

This line is doing nothing > $IPTABLES -A OUTPUT -p udp -o $EXTIF --dport 53 -j ACCEPT

-----------------------

I don't really know about these > #  NOTE THE THREE LINES BELOW ALLOW ACCESS FOR THE VPN CONNECTION...Ry.

$IPTABLES -A INPUT -i ppp+ -j ACCEPT
$IPTABLES -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o ppp+ -j ACCEPT
If you don't have a vpn, I would just get rid of them.

----------------------------

I have no clue about these, but they are probably not affecting security anyway > #this helps torrenting, my putter is a bit daft with the modem
echo 1024 > /proc/sys/net/ipv4/neigh/default/gc_thresh1
echo 2048 > /proc/sys/net/ipv4/neigh/default/gc_thresh2
echo 4096 > /proc/sys/net/ipv4/neigh/default/gc_thresh3

#kissd is my network dvd player
kissd -d
Personally I would just get rid of them, unless you knwo you need them.

--------------------------------

Well there ya go.  That's my evaluation on your firewall rules anyway.  I would really suggest getting familiar with Webmin though.  It makes firewall administration SOOO much easier.  You might also organize all your rules to be grouped by INPUT, OUTPUT, and FORWARD.  That would make it a LOT easier to see at a glance what is being allowed where.

---

### Post by twistedtwig on 2007-10-09
Sorry i have not been back to you in a while, life got manic.. then the server fell over.. but she is back again and all is well (at least its as it was before :) )


```
$IPTABLES -A INPUT -i $INTIF -j ACCEPT
```

This line is needed... well... thats is probably a misleading statement.... if I comment it out apache can not do its proxypassreverse through the internal network.

Could it be changed to just allow port 80 internally or something?... 

Yes your right about the wireless hacking situation, not sure which way I want to play that.. if I locked it down could programs that use unusual ports stop working?


I do have samba with wins and a vpn

the final few lines are extra stuff that is not really firewall bits but I put them there for ease (being lazy really)..

the 3 lines for th gc_thresh is to try and help bit torrent not fall over.. very odd error I get with this server... long story :/


the last just starts my kiss player server (network dvd player that streams media from the server).

I commented out all the lines you suggested bar the first one and all seems fine :)

WOOHOO thanks!!!

not sure about the first one I mention above though.

Cheers again.

---

