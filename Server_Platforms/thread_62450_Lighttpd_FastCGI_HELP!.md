---
title: "Lighttpd FastCGI HELP!"
date: 2005-09-04
forum: Server Platforms
---

### Post by Protoss on 2005-09-04
Has anyone successfully gotten lighttpd+fastcgi+php to work on ubuntu? I try to start it but always get ```
2005-09-04 16:48:01: (mod_fastcgi.c.867) child signaled: 11
2005-09-04 16:48:01: (mod_fastcgi.c.1138) [ERROR]: spawning fcgi failed.
2005-09-04 16:48:01: (server.c.621) Configuration of plugins failed. Going down.
```
It seems to be a problem with fcgi. I've recompiled php4 with the fastcgi switch, and compiled fastcgi. If anyone has gotten lighttpd+php to work, can they please give me a guide to follow?



Thnx, Protoss

---

### Post by DJ_Max on 2005-09-05
I've gotten Lighttpd+PHP+FastCGI to work on Debian. Have you looked at the Lighttpd wiki?

---

### Post by Protoss on 2005-09-05
Yes I have followed the instructions on the lighttpd wiki. Can you give me a step by step guide on how to do it? 





Thnx, Protoss

---

### Post by DJ_Max on 2005-09-05
You should have everything installed. What does your config file look like?

---

### Post by Protoss on 2005-09-06
```
# lighttpd configuration file
# 
# use a it as base for lighttpd 1.0.0 and above
#
# $Id: lighttpd.conf,v 1.7 2004/11/03 22:26:05 weigon Exp $

############ Options you really have to take care of ####################

## modules to load
# at least mod_access and mod_accesslog should be loaded
# all other module should only be loaded if really neccesary
# - saves some time
# - saves memory
server.modules              = ( 
#                               "mod_rewrite", 
#                               "mod_redirect", 
			        "mod_access", 
#				"mod_auth", 
                                "mod_status", 
				"mod_fastcgi",
				"mod_simple_vhost",
#				"mod_evhost",
#				"mod_cgi",
#				"mod_compress",
#                               "mod_ssi",
#                               "mod_usertrack",
# 				"mod_rrdtool",
				"mod_accesslog" )

## a static document-root, for virtual-hosting take look at the 
## server.virtual-* options
server.document-root             = "/var/www/"

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

# files to check for if .../ is requested
server.indexfiles          = ( "index.php", "index.html", 
                                "index.htm", "default.htm" )

# mimetype mapping
mimetype.assign            = (  
  ".pdf"          =>      "application/pdf",
  ".sig"          =>      "application/pgp-signature",
  ".spl"          =>      "application/futuresplash",
  ".class"        =>      "application/octet-stream",
  ".ps"           =>      "application/postscript",
  ".torrent"      =>      "application/x-bittorrent",
  ".dvi"          =>      "application/x-dvi",
  ".gz"           =>      "application/x-gzip",
  ".pac"          =>      "application/x-ns-proxy-autoconfig",
  ".swf"          =>      "application/x-shockwave-flash",
  ".tar.gz"       =>      "application/x-tgz",
  ".tgz"          =>      "application/x-tgz",
  ".tar"          =>      "application/x-tar",
  ".zip"          =>      "application/zip",
  ".mp3"          =>      "audio/mpeg",
  ".m3u"          =>      "audio/x-mpegurl",
  ".wma"          =>      "audio/x-ms-wma",
  ".wax"          =>      "audio/x-ms-wax",
  ".ogg"          =>      "audio/x-wav",
  ".wav"          =>      "audio/x-wav",
  ".gif"          =>      "image/gif",
  ".jpg"          =>      "image/jpeg",
  ".jpeg"         =>      "image/jpeg",
  ".png"          =>      "image/png",
  ".xbm"          =>      "image/x-xbitmap",
  ".xpm"          =>      "image/x-xpixmap",
  ".xwd"          =>      "image/x-xwindowdump",
  ".css"          =>      "text/css",
  ".html"         =>      "text/html",
  ".htm"          =>      "text/html",
  ".js"           =>      "text/javascript",
  ".asc"          =>      "text/plain",
  ".c"            =>      "text/plain",
  ".conf"         =>      "text/plain",
  ".text"         =>      "text/plain",
  ".txt"          =>      "text/plain",
  ".dtd"          =>      "text/xml",
  ".xml"          =>      "text/xml",
  ".mpeg"         =>      "video/mpeg",
  ".mpg"          =>      "video/mpeg",
  ".mov"          =>      "video/quicktime",
  ".qt"           =>      "video/quicktime",
  ".avi"          =>      "video/x-msvideo",
  ".asf"          =>      "video/x-ms-asf",
  ".asx"          =>      "video/x-ms-asf",
  ".wmv"          =>      "video/x-ms-wmv"
 )

# Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
accesslog.filename          = "/var/log/lighttpd/access.log"

## deny access the file-extensions
#
# ~    is for backupfiles from vi, emacs, joe, ...
# .inc is often used for code includes which should in general not be part
#      of the document-root
url.access-deny             = ( "~", ".inc" )



######### Options that are good to be but not neccesary to be changed #######

## bind to port (default: 80)
#server.port                = 81

## bind to localhost (default: all interfaces)
#server.bind                = "grisu.home.kneschke.de"

## error-handler for status 404
#server.error-handler-404   = "/error-handler.html"
#server.error-handler-404   = "/error-handler.php"

## to help the rc.scripts
server.pid-file              = "/var/run/lighttpd.pid"


###### virtual hosts
##
##   If you want name-based virtual hosting add the next three settings and load
##   mod_simple_vhost
##
## document-root =
##   virtual-server-root + virtual-server-default-host + virtual-server-docroot or
##   virtual-server-root + http-host + virtual-server-docroot
##
$HTTP["host"] == "www.eatsleepgame.com" {
    server.document-root = "/var/www/esg/"
	} 
$HTTP["host"] == "www.andersonalbum.com" {
    server.document-root = "/var/www/family/"
	}

## 
## Format: <errorfile-prefix><status>.html
## -> ..../status-404.html for 'File not found'
#server.errorfile-prefix    = "/home/weigon/projects/lighttpd/doc/status-"

## virtual directory listings
#server.dir-listing          = "enable"

## send unhandled HTTP-header headers to error-log
#debug.dump-unknown-headers  = "enable"

### only root can use these options
#
# chroot() to directory (default: no chroot() )
#server.chroot            = "/"

## change uid to <uid> (default: don't care)
server.username            = "www-data"

## change uid to <uid> (default: don't care)
server.groupname           = "www-data"

#### compress module
#compress.cache-dir          = "/var/tmp/lighttpd/cache/compress/"
#compress.filetype           = ("text/plain", "text/html")

#### fastcgi module
## read fastcgi.txt for more info
fastcgi.server = ( \".php\" =>
  ( \"localhost\" =>
      (
            \"socket\" => \"/tmp/php-fastcgi.socket\",
	          \"bin-path\" => \"/usr/bin/php4-cgi\"
		      )
		        )
			)

#### CGI module
#cgi.assign                  = ( ".pl"  => "/usr/bin/perl",
#                                ".cgi" => "/usr/bin/perl" )

#### SSL engine
#ssl.engine                  = "enable"
#ssl.pemfile                 = "server.pem"

#### status module
# status.status-url = "/server-status"
# status.config-url = "/server-config"

#### auth module
## read authentification.txt for more info
# auth.backend                = "plain"
# auth.backend.plain.userfile = "lighttpd.user"
# auth.backend.plain.groupfile = "lighttpd.group"

# auth.backend.ldap.hostname = "localhost"
# auth.backend.ldap.base-dn  = "dc=my-domain,dc=com"
# auth.backend.ldap.filter   = "(uid=$)"

# auth.require                = ( "/server-status" => 
#                                ( 
#				  "method"  => "digest",
#				  "realm"   => "download archiv",
#				  "require" => "group=www|user=jan|host=192.168.2.10"
#				),
#				"/server-info" => 
#                                ( 
#				  "method"  => "digest",
#				  "realm"   => "download archiv",
#				  "require" => "group=www|user=jan|host=192.168.2.10"
#				)
#                              )

#### url handling modules (rewrite, redirect, access)
# url.rewrite                 = ( "^/$"             => "/server-status" )
# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#
# define a pattern for the host url finding
# %% => % sign
# %0 => domain name + tld
# %1 => tld
# %2 => domain name without tld
# %3 => subdomain 1 name
# %4 => subdomain 2 name
#
# evhost.path-pattern = "/home/storage/dev/www/%3/htdocs/"

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### ssi
# ssi.extension              = ( ".shtml" )

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"

```
Thank you for the help man!

---

### Post by DJ_Max on 2005-09-07
When you do ```
php -v
``` what is the output? In your php.ini there's a part that says ```
 cgi.fix_pathinfo = 1
```.

My lighttpd.conf fascgi part looks like.
```

fastcgi.server = ( ".php" => ((
                     "bin-path" => "/usr/local/bin/php",
                     "socket" => "/tmp/php.socket",
                     "min-procs" => 1,
                     "max-procs" => 4,
                     "max-load-per-proc" => 4,
                     "idle-timeout" => 20,
                    # "bin-environment" => (
                     #  "PHP_FCGI_CHILDREN" => "16",
                      # "PHP_FCGI_MAX_REQUESTS" => "10000"
                    # ),
                     "bin-copy-environment" => (
                       "PATH", "SHELL", "USER"
                     ),
                     "broken-scriptfilename" => "enable"
                 )))

```
Of course my PHP path may be different.

---

### Post by DJ_Max on 2005-09-07
BTW, make sure you did a ```
make clean
``` before you did ./configure

---

### Post by Protoss on 2005-09-07
[QUOTE=DJ_Max]BTW, make sure you did a ```
make clean
``` before you did ./configure[/QUOTE]
 Um...I didnt do that, but it still works fine. Thank you for all your help! You're the best!

---

### Post by DJ_Max on 2005-09-07
[QUOTE=Protoss]Um...I didnt do that, but it still works fine. Thank you for all your help! You're the best![/QUOTE]
 Yeah, well sometimes make clean is required, sometimes it isn't, it's best to run when debugging installs.

Glad you got LightTPD running. You'll like it.

---

### Post by Protoss on 2005-09-07
[QUOTE=DJ_Max]Yeah, well sometimes make clean is required, sometimes it isn't, it's best to run when debugging installs.

Glad you got LightTPD running. You'll like it.[/QUOTE]
 I already do like it. It's alot more user friendly than Apache2...that this was hell to configure. And it has a huge speed difference, Mambo now takes about 5 seconds, instead of 10!

---

### Post by DJ_Max on 2005-09-07
[QUOTE=Protoss]I already do like it. It's alot more user friendly than Apache2...that this was hell to configure. And it has a huge speed difference, Mambo now takes about 5 seconds, instead of 10![/QUOTE]

I've made the switch to LightTPD from Apache2, and I've been wondering where LightTPD has been all my life. To be honest Apache is a overkill for most sites on the net. It's ease of configuration and deployment, and the fact thats it's a lot lighter, with less bloat Apache has.

The reason I looked into LightTPD was because of the superior Ruby & Ruby on Rails support.

---

