---
title: "2 Sites with lighttpd"
date: 2008-07-30
forum: Server Platforms
---

### Post by f37u5g0d on 2008-07-30
Title says it all.  How do you set up two websites with two different url's both pointing to the same (my) ip?  IDK if this makes it any harder or easier but I have them set up on two different ports.  I have searched the net but it seems like all of the lighttpd tutorials are for php and other advanced things.

---

### Post by dmizer on 2008-07-30
This is called "virtual hosting".  Here's the link I used to set mine up in LightTPD: [http://www.cyberciti.biz/tips/howto-lighttpd-web-server-setting-up-virtual-hosting.html](http://www.cyberciti.biz/tips/howto-lighttpd-web-server-setting-up-virtual-hosting.html)

Edit:
instead of ftpuser1 ftpuser2, use www-data

No need for different ports, your server will answer the request according to domain name.

---

### Post by f37u5g0d on 2008-07-30
Ok I tried that how to and now I am getting this error I believe because I commented out the server.document-root line near the top.
> sudo /etc/init.d/lighttpd reload
 * Reloading web server configuration lighttpd                                  2008-07-30 11:23:15: (configfile.c.1128) a default document-root has to be set 
2008-07-30 11:23:15: (server.c.591) setting default values failed 


Here is my lighttpd.conf file
> # Debian lighttpd configuration file
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
#           "mod_rewrite", 
#           "mod_redirect", 
#           "mod_status", 
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
## server.document-root       = "/home/ed/Website"

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.php", "index.html",
                               "index.htm", "default.htm",
                               "index.lighttpd.html" )


## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
#accesslog.filename         = "/var/log/lighttpd/access.log"

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

## bind to port (default: 80)
#server.port               = 75

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

#### status module
# status.status-url = "/server-status"
# status.config-url = "/server-config"

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
## server.name = hostname
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
### by default allow them only from localhost
### (This must come last due to #445459)
#$HTTP["remoteip"] == "127.0.0.1" {
#	alias.url += (
#		"/doc/" => "/usr/share/doc/",
#		"/images/" => "/usr/share/images/"
#	)
#	$HTTP["url"] =~ "^/doc/|^/images/" {
#		dir-listing.activate = "enable"
#	}
#}


$HTTP["host"] =~ "^(www\.|\.)homelinux.com$" {
server.document-root = "/home/ed/Website"
server.errorlog = "/var/log/lighttpd/personal/error.log"
accesslog.filename = "/var/log/lighttpd/personal/access.log"
server.error-handler-404 = "/e404.php"
}


$HTTP["host"] =~ "^(www\.|\.)kicks-***.org$" {
server.document-root = "/home/ed/mwp_Website"
server.errorlog = "/var/log/lighttpd/mwp/mwp-error.log"
accesslog.filename = "/var/log/lighttpd/mwp/mwp-access.log"
server.error-handler-404 = "/e404.php"
}


---

### Post by f37u5g0d on 2008-07-30
Bump

---

### Post by dmizer on 2008-07-30
I vaguely recall having this same problem.

Uncomment this line by removing the # symbols:
```
[COLOR="Red"]## [/COLOR]server.document-root = "/home/ed/Website"
```
Uncomment and change this line:
```
[COLOR="Red"]#[/COLOR]accesslog.filename = "[COLOR="Red"]/var/log/lighttpd/personal/access.log[/COLOR]"
```

Then comment this entire section by putting # symbols in front of each line like so:
```
#$HTTP["host"] =~ "^(www\.|\.)homelinux.com$" {
#server.document-root = "/home/ed/Website"
#server.errorlog = "/var/log/lighttpd/personal/error.log"
#accesslog.filename = "/var/log/lighttpd/personal/access.log"
#server.error-handler-404 = "/e404.php"
#}
```

---

### Post by f37u5g0d on 2008-08-03
Thank you for your efforts dmizer but because of time constraints I had to put this on hold.  I will def re-visit this project but I need to get my new site up and running so essentially I took down the old one and now I only serve to this address.  [http://www.mwp.kicks-***.org](http://www.mwp.kicks-***.org)

I do have another question though, not sure if it's worthy of its own thread but lighttpd prints a fantastic access log but while I am building my site I have a firefox window open so that I can hit refresh and visually check the changes I've made.  Because of this the access log is about 90% my ip local (intranet) address and 10% other people looking at the site.  Is there a way to not log my own ip?  I don't want to block access from my ip all together.  I just want to be able to tell the log "hey if you see that 192.168.1.1 has accessed the site don't log it."

Edit: Replace those "*"'s in the address with that nasty word for butt that starts with an "a." (lowercase).

---

