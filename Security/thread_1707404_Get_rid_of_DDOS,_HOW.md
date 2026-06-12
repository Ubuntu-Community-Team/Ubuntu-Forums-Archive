---
title: "Get rid of DDOS, HOW?"
date: 2011-03-15
forum: Security
---

### Post by axeboy on 2011-03-15
Hello,



my server have sometimes a ddos, I have no clue how to protect my server
 against that, my internet is 1 gigabit. But still ddos shutdown my 
server.



But when I see I dont have a ddos on the whole server, still sometimes my website is lagging alot.

Im thinking someone is pinging my server or something like that,



what should I do for that. I am using linux ubuntu 10.0.4, using lighttpd.

some1 can help?


my lighttpd.conf
from etc/lighttpd

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
[/PHP]thx in advantage

---

### Post by bodhi.zazen on 2011-03-15
From your post it sounds as if you do not really know what the problem is.

You need to start by reviewing your logs. You can log packets with iptables to see if it is a DDOS.

You can use some iptables rules.

You can monitor your network traffic.

Without additional information / footwork on your part we would be guessing.

---

### Post by axeboy on 2011-03-16
> **bodhi.zazen said:**
> From your post it sounds as if you do not really know what the problem is.

You need to start by reviewing your logs. You can log packets with iptables to see if it is a DDOS.

You can use some iptables rules.

You can monitor your network traffic.

Without additional information / footwork on your part we would be guessing.


but how can I do it?
which commands do I need to insert?
my website is lagging very much and sometimes it doesnt even load because someone is doing something with my website prolly port: 80 attack or something i have no clue,
u would make me happy if u can give me the commands

---

### Post by EJeanmaire on 2011-03-16
Sounds more like a load issue, what are the server specs, type "top" and see what is using the most system resources.  Also show us the output of netstat -antp.  Also check the size of your http access logs in /var/log.  You could also look on wireshark to sniff the traffic, but as hinted above, most likely your hardware / software is misconfigured, not an "overload" of traffic.


Short version: Pull out your internet cable; does it still lag?

---

### Post by bodhi.zazen on 2011-03-16
> **axeboy said:**
> but how can I do it?
which commands do I need to insert?
my website is lagging very much and sometimes it doesnt even load because someone is doing something with my website prolly port: 80 attack or something i have no clue,
u would make me happy if u can give me the commands

Take a look at various network tools such as ntop, netstat, and look at the logs in /var/log.

Google search =)

---

### Post by BkkBonanza on 2011-03-16
If DDOS attacks could be fixed with a couple simple commands then they wouldn't be much of a threat, but they are, even for large well managed sites.

As hinted above you need to determine the actual cause of the problem before you can take steps to fix it. Without knowing concrete details about what is slowing things down it's impossible to know what commands may help.

Using top (or htop is better) first see what processes are using the most cpu resources. Is it httpd (web server) that is hogging the system? Or something else? It could be a bad script / mysql query that has caused problems. So first see what is using system resources.

Look in your access log to see if there are massive amounts of hits on certain pages and if they are coming from many, many IPs.

It's very hard to combat a true DDOS attack on your server and usually it needs attention at a network routing level. But first you need identify what's really happening.

---

