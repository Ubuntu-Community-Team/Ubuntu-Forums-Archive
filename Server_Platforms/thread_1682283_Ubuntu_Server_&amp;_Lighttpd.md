---
title: "Ubuntu Server &amp; Lighttpd"
date: 2011-02-05
forum: Server Platforms
---

### Post by fellixombc on 2011-02-05
Ubuntu Server 10.10 32 bit

I have setup ssh fine, and ftp fine, except for lighttpd. Every time I try accessing it from my private network (e.g, 190.168.*.***), it gives me a 403 error. Now, it even does this for .html files.

Any ideas on how to fix this? I've been looking for hours for solutions, yet I have not found any. 

I can access the default lighttpd page though, for some odd reason.

I also tried nginx, and I got the same error =/

/etc/lighttpd/lighttpd.conf
```
# Debian lighttpd configuration file
#

############ Options you really have to take care of ####################

## modules to load
server.modules = (
            "mod_alias",
            "mod_compress",
#           "mod_rewrite",
#           "mod_redirect",
#           "mod_usertrack",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive"
)

## a static document-root, for virtual-hosting take look at the
## server.virtual-* options
server.document-root       = "/home/sam/public_html/"

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

### only root can use these options
#
# chroot() to directory (default: no chroot() )
#server.chroot            = "/"

## change uid to <uid> (default: don't change)
server.username            = "www-data"

## change gid to <gid> (default: don't change)
server.groupname           = "www-data"

#### compress module
compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ("text/plain", "text/html", "application/x-javascript", "text/css")

#### url handling modules (rewrite, redirect, access)
# url.rewrite                 = ( "^/$"             => "/server-status" )
# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### external configuration files
## mimetype mapping
include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files,
## read /etc/lighttpd/conf-available/README first
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

```

---

### Post by lisati on 2011-02-05
I have found with Apache2 that whenever I get a 403 error on one of my web pages, it's usually a permissions problem. I've even managed to cause it myself with a misguided chmod command.

I'm not familiar with using Lighttpd but suspect that something similar could be happening for you, and would suggest changing permissions on files to 666. For example:
```

chmod 666 index.html

```

---

### Post by rudelgurke on 2011-02-05
Do NOT chmod your webroot 666 - anyone will then have write permission there and that's a really really bad idea.

Related to your problem - your webroot is /home/sam/public_html[FONT=monospace] - [/FONT]does the user or group www-data your Lighty is using has read permission there ?

Changes a high that a look into /var/log/lighttpd/error.log will show exactly the error message that Lighty is unable to access the folder.

---

### Post by fellixombc on 2011-02-05
> **rudelgurke said:**
> Do NOT chmod your webroot 666 - anyone will then have write permission there and that's a really really bad idea.

Related to your problem - your webroot is /home/sam/public_html[FONT=monospace] - [/FONT]does the user or group www-data your Lighty is using has read permission there ?

Changes a high that a look into /var/log/lighttpd/error.log will show exactly the error message that Lighty is unable to access the folder.
I'm check as of right now, and it seems that may be true. 

```
2011-02-05 13:57:33: (log.c.166) server started 
2011-02-05 14:03:30: (server.c.1389) [note] graceful shutdown started 
2011-02-05 14:03:30: (log.c.166) server started 
2011-02-05 14:03:30: (server.c.1503) server stopped by UID = 0 PID = 1841 
2011-02-05 14:04:51: (server.c.1389) [note] graceful shutdown started 
2011-02-05 14:04:51: (log.c.166) server started 
2011-02-05 14:04:53: (server.c.1503) server stopped by UID = 0 PID = 1870 
```

thats my error.log, and thats the only log there.

I know that in the /var/www/index.lighttpd.html has -rw-r--r--

and so I did chmod 644 on index.html, and no success. Same with the /home/sam/public_html/ folder


edit: I just removed lighttpd and deleted /etc/lighttpd/ folder along with /var/www/

the lighttpd index page works fine. I'm going to enable lighty-enable-mod userdir and add index.html to see what happens

---

### Post by rudelgurke on 2011-02-05
And if you run Lighty in foreground ? With the -D option ?

---

### Post by fellixombc on 2011-02-05
> **rudelgurke said:**
> And if you run Lighty in foreground ? With the -D option ?

I'm confused with your question, as you see I'm not the most experienced with all of this. Now I have an another issue: I cannot upload to /var/www/, before though, I did do a mount bind and that did the trick.

---

### Post by fellixombc on 2011-02-05
Anyways, If I chmod 644 the file upon creation, it works out just fine :popcorn:

But how can I make it so I wouldn't have to do that every single time?

nvm solved

---

### Post by ionplay on 2012-04-18
had the same problem on fresh lighttpd on ubuntu 10.04 install

triple checked permissions
and copying fastcgi.conf to enabled directory
etc....

ultimately the modules were not loaded (not sure how or why), but executed the following and it works properly now

sudo lighttpd-enable-mod fastcgi fastcgi-php

hope this helps anyone else landing on this page

---

### Post by lisati on 2012-04-18
Closed.

Please do not bump old threads.

---

