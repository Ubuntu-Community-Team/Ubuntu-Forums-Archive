---
title: "Trouble with Apache"
date: 2007-07-22
forum: Server Platforms
---

### Post by M$LOL on 2007-07-22
After installing Webmin, I can now no longer access [http://localhost](http://localhost) (Firefox can't establish a connection to the server at localhost). I have no idea how to even start trying to fix this, can anyone help me?

---

### Post by p_quarles on 2007-07-22
Have you tried restarting Apache?```
sudo /etc/init.d/apache2 restart
```

---

### Post by M$LOL on 2007-07-22
Here's what I get:

* Forcing reload of web server (apache2)...                                    
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

---

### Post by p_quarles on 2007-07-22
Hmm. Okay, first, are you able to access Webmin? What port is it using (this is shown in the URL; directly after localhost: )? 

Second, check your Apache config file:```
gksudo gedit /etc/apache2/apache2.conf
```
Look for the line that says "Listen" and tell us what it says there.

---

### Post by M$LOL on 2007-07-22
> **p_quarles said:**
> Hmm. Okay, first, are you able to access Webmin? What port is it using (this is shown in the URL; directly after localhost: )? 

Second, check your Apache config file:```
gksudo gedit /etc/apache2/apache2.conf
```
Look for the line that says "Listen" and tell us what it says there.

Well, it had been using port 10000, but I uninstalled it. I can reinstall it though, if I need to, and I was able to access it OK.

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
    #AddHandler cgi-script .cgi

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
    AddType text/html .shtml
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
```

I can't find any line saying "Listen" in there, I take it that means there's something wrong?

---

### Post by p_quarles on 2007-07-22
> I can't find any line saying "Listen" in there, I take it that means there's something wrong?

It might be the problem. Unfortunately, Ubuntu's Apache configuration is really screwy. Now look for the "Listen" line in both httpd.conf and ports.conf in the same directory.

If you look at the lines using "Include", you'll see that these configuration files are being used as additional information. That's why I said it's screwy. In the default Apache build, *all *of these settings are in httpd.conf.

---

### Post by M$LOL on 2007-07-22
Well, they were both blank, but I decided to try putting in "Listen 80" into ports.conf, and now I can navigate to localhost, but where it used to show me the list of directories, I now get "The requested URL / was not found on this server".

---

### Post by p_quarles on 2007-07-22
Okay, at least that changed something. A couple more things to try. 

Instead of "Listen 80," try "Listen LAN-IP:80"

Obviously, replace the LAN-IP part with your machine's address -- 192.168 etc. 

Next, make sure there's something in the document root (most likely /var/www/). If there isn't, just create a "Hello World" page and call it index.html.

---

### Post by M$LOL on 2007-07-22
Yeah, there's a load of stuff in there. I tried that, and [http://localhost](http://localhost) gives me "Firefox can't establish a connection to the server at localhost", while [http://192.168.1.4](http://192.168.1.4) gives me "The requested URL / was not found on this server".

---

### Post by p_quarles on 2007-07-22
Hmm. This may be obvious, but you need to restart Apache again after changing the configuration files.

If you did that already, I'm going to suggest just reinstalling it (unless someone else here has a better idea). In order to do that, I think you'll need to "apt-get remove apache2", then manually delete the configuration files in /etc/apache2/. Uninstalliing will leave everything in your document root intact, so no worries there. After that, do "apt-get autoremove" to get rid of dependencies. 

After that, you should be able to reinstall a clean copy.

By, the way, how did you install Webmin? Did you use the .deb package or did you use their repository?

---

### Post by M$LOL on 2007-07-22
Yeah, I managed to get that about restarting Apache alright ;)

I installed via the .deb, but I removed via apt-get.

I'll reinstall now and see how it goes. Thanks for the help :)

---

### Post by p_quarles on 2007-07-22
No problem. 

You know, I had a weird problem with the .deb package. In my case, I got an error like yours, only on port 10000. It didn't mess up Apache, but I compiled Apache from source, so it wasn't where the package manager would have expected. 

If you still want Webmin, I suggest getting it from their repository:
```
deb http://download.webmin.com/download/repository sarge contrib
```
After I got it from there, it worked fine.

---

### Post by M$LOL on 2007-07-22
Hmm, I removed apache and deleted the files, but when I reinstall it it just says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/38.4kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 124209 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2build1_all.deb) ...
Setting up apache2 (2.2.3-3.2build1) ...


but it doesn't seem to actually do anything, it doesn't recreate anything in /etc/apache2.

---

### Post by p_quarles on 2007-07-22
D'oh. I thought that would work.

Okay, re-remove Apache, then run the auto-remove command again, and then run```
sudo apt-get clean
```
Then reinstall again.

Argh. I knew this package could be a pain, but I didn't think it would be this hard to fix. Hope it works better with clean.

---

### Post by M$LOL on 2007-07-22
No, I'm still getting the same thing :(

---

### Post by p_quarles on 2007-07-22
S***.

Umm, I do have another idea, but first, tell me something about your setup. Do you use much PHP or SQL in your web pages? Because, if not it would be pretty easy to compile the latest version of Apache from the source code, which will definitely work. If you do use those other components, it can still be done, but gets a lot more complicated (I know, because I spent my weekend doing this). But, if you just need Apache to run HTML pages, it's not bad at all.

FYI, I'll be away from my computer for a couple hours, but I will check this thread after I get back.

---

### Post by M$LOL on 2007-07-22
Yeah, pretty much all of them are dependent on PHP and MySQL, unfortunately. :(

np, I'm delighted that you answered my question so quickly and that you're helping me this much, thanks :)

---

### Post by p_quarles on 2007-07-22
All right, I'm back. Like I said, I just installed and integrated these three programs from source over the weekend. It takes a little while, but it does work, and has the added benefit of being a lot closer in configuration to the non-Debian/Ubuntu based instruction manuals for LAMP.

I'm going to go look for a tutorial online, and if I don't find one, I'll take a shot at writing it.

---

### Post by pgupta on 2007-08-15
I am actually having this exact same problem -- does anybody have an idea about what's going on in this situation?

---

