---
title: "lighttpd 404 error"
date: 2010-07-07
forum: Server Platforms
---

### Post by skaramanger on 2010-07-07
Greetings,

I am experiencing a curious problem.  I installed lighttpd to be able to view cgi files that display the status of my UPS.  For the most part is has worked w/o incident i.e. until recently when the UPS battery failed on my APC backups xs 1500 lcd.

I could not view the multimon.cgi file via the localhost or 127.0.0.1 url e.g.:

[http://locahost/cgi-gin/apcupsd/multimon.cgi](http://locahost/cgi-gin/apcupsd/multimon.cgi)

I'd get 404 page not found message.  After checking links here and on the web, I tried:

[http://the_static_ip_address_my_router_sees/cgi-bin/apcupsd/multimon.cgi](http://the_static_ip_address_my_router_sees/cgi-bin/apcupsd/multimon.cgi)

and wahla! The page is displayed.  From this discovery, I'm not sure that this is a web server configuration or a network host configuration issue or what. I'm running Lucid with all updates, no mods to lighttpd except I added the mod_fastcgi line to the lighttpd.conf file 

Thanks in advance

I have included my lighttpd.conf as an attachment

---

### Post by Iowan on 2010-07-07
> **skaramanger said:**
> I have included my lighttpd.conf as an attachmentWhere? :)

---

### Post by skaramanger on 2010-07-08
> **Iowan said:**
> Where? :)

I uploaded it.  Sorry about that. I'll just put it right here:

```
# Debian lighttpd configuration file
#

############ Options you really have to take care of ####################

## modules to load
# mod_access, mod_accesslog and mod_alias are loaded by default
# all other module should only be loaded if neccesary
# - saves some time
# - saves memory

server.modules              = (
            "mod_access",
            "mod_alias",
            "mod_accesslog",
            "mod_compress",
            "mod_fastcgi",
#           "mod_rewrite",
#           "mod_redirect",
#           "mod_evhost",
#           "mod_usertrack",
#           "mod_rrdtool",
#           "mod_webdav",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive"
)

## a static document-root, for virtual-hosting take look at the
## server.virtual-* options
server.document-root       = "/var/www/"

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

```

Thanks for your reply

---

### Post by skaramanger on 2010-07-10
How about a Bump!

---

### Post by Iowan on 2010-07-10
Nothing obvious (to someone who's never seen a *lighttpd.conf* before). Just to cover some other bases, what's in *etc/hosts*?

---

### Post by skaramanger on 2010-07-11
> **Iowan said:**
> Nothing obvious (to someone who's never seen a *lighttpd.conf* before). Just to cover some other bases, what's in *etc/hosts*?

Let me see,

```
 cat /etc/hosts
127.0.0.1	localhost mydesktopname

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I don't get it. If my local non-routable ip address allows access to my web page, but localhost or 127.0.0.1 doesn't. I must be the hosts file or perhaps my firewall? I wouldn't think my firewall. It allows a connection to go out to my router and back to my box to render the page.

I don't think that this file would have anything to do with it:

```
$ cat /etc/resolv.conf
nameserver 192.168.1.1
domain home
search home

```

---

### Post by Iowan on 2010-07-12
I doubt this will help, but in **/etc/hosts** try:```
127.0.0.1	localhost localhost.home
127.0.1.1       mydesktopname

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Restart networking or reboot.

---

### Post by skaramanger on 2010-07-12
> **Iowan said:**
> I doubt this will help, but in **/etc/hosts** try:```
127.0.0.1	localhost localhost.home
127.0.1.1       mydesktopname

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Restart networking or reboot.

Iowan,

Well, I made the changes and force-reload on networking and still doesn't work using localhost or localhost.home or 127.0.0.1. But,,, it works using 127.0.1.1, mydesktopname or my local non-routable ip. What gives? Just plain localhost should work! 

Thanks again,

Skaramanger

How's about a bump?

---

