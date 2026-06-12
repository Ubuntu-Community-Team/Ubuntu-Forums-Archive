---
title: "Problem with Ubuntu 10.0.4 [LIGHTTPD IPV6]"
date: 2011-03-15
forum: Security
---

### Post by axeboy on 2011-03-15
Hello,

I am using linux ubuntu 10.0.4 and using lighttpd,
atm it is setted with ipv4, but my server is also able to have ipv6.

at the moment my lighttpd.conf  is running with IPV4,
but I have no clue how to have it running with ipv6,
please someone can help with this?
maybe some1 can give me the lighttpd.conf with the ipv6?


my lighttpd.conf from [etc/lighttpd]


[PHP]# Debian lighttpd configuration file
#

############ Options you really have to take care of ####################

## modules to load
# mod_access, mod_accesslog and mod_alias are loaded by default
# all other module should only be loaded if neccesary
# - saves some time
# - saves memory



## a static document-root, for virtual-hosting take look at the
## server.virtual-* options
connection.kbytes-per-second = 32
server.document-root       = "/var/www/"

## [Znote multiple web hosting]
$HTTP["host"] =~ "kentana.hopto.org" {
            server.document-root = "/var/k66/"
}
$HTTP["host"] =~ "blackhearts.servegame.com" {
            server.document-root = "/var/k77/"
}
## [/Znote multiple web hosting]

## where to upload files to, purged daily.
server.upload-dirs = ( "/var/cache/lighttpd/uploads" )

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.php", "index.html",
                               "index.htm", "default.htm",
                               "index.lighttpd.html" )


## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
accesslog.filename         = "/var/log/lighttpd/access.log"

## deny access the file-extensions
#
# ~    is for backupfiles from vi, emacs, joe, ...
# .inc is often used for code includes which should in general not be part
#      of the document-root
url.access-deny            = ( "~", ".inc" )

##
# which extensions should not be handle via static-file transfer
#
# .php, .pl, .fcgi are most often handled by mod_fastcgi or mod_cgi
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )


######### Options that are good to be but not neccesary to be changed #######

## Use ipv6 only if available. (disabled for while, check #560837)
#include_shell "/usr/share/lighttpd/use-ipv6.pl"

## bind to port (default: 80)
# server.port               = 81

## bind to localhost only (default: all interfaces)
## server.bind                = "localhost"

## error-handler for status 404
#server.error-handler-404  = "/error-handler.html"
#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts
server.pid-file            = "/var/run/lighttpd.pid"

##
## Format: <errorfile-prefix><status>.html
## -> ..../status-404.html for 'File not found'
#server.errorfile-prefix    = "/var/www/"

## virtual directory listings
dir-listing.encoding        = "utf-8"
server.dir-listing          = "enable"

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
compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ("text/plain", "text/html", "application/x-javascript", "text/css")


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

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"

#### variable usage:
## variable name without "." is auto prefixed by "var." and becomes "var.bar"
#bar = 1
#var.mystring = "foo"
evasive.max-conns-per-ip = 4
## integer add
#bar += 1
## string concat, with integer cast as string, result: "www.foo1.com"
#server.name = "www." + mystring + var.bar + ".com"
## array merge
#index-file.names = (foo + ".php") + index-file.names
#index-file.names += (foo + ".php")


#### external configuration files
## mimetype mapping
include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files,
## read /etc/lighttpd/conf-available/README first
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

#### handle Debian Policy Manual, Section 11.5. urls
## by default allow them only from localhost
## (This must come last due to #445459)
## Note: =~ "127.0.0.1" works with ipv6 enabled, whereas == "127.0.0.1" doesn't
$HTTP["remoteip"] =~ "127.0.0.1" {
    alias.url += (
        "/doc/" => "/usr/share/doc/",
        "/images/" => "/usr/share/images/"
    )
    $HTTP["url"] =~ "^/doc/|^/images/" {
        dir-listing.activate = "enable"
    }
}
[/PHP]thanks in advantage,

---

### Post by bodhi.zazen on 2011-03-15
[http://www.cyberciti.biz/tips/linux-unix-lighttpd-ipv6-support.html](http://www.cyberciti.biz/tips/linux-unix-lighttpd-ipv6-support.html)

---

### Post by axeboy on 2011-03-16
> **bodhi.zazen said:**
> [http://www.cyberciti.biz/tips/linux-unix-lighttpd-ipv6-support.html](http://www.cyberciti.biz/tips/linux-unix-lighttpd-ipv6-support.html)


mmm not so clear how to do it,
u got the full script of it? with the ipv6

im not so good at linux

---

### Post by bodhi.zazen on 2011-03-16
> **axeboy said:**
> mmm not so clear how to do it,
u got the full script of it? with the ipv6

im not so good at linux

The link explains exactly how to do this in the lighty config file.

What part do you not understand ?

---

