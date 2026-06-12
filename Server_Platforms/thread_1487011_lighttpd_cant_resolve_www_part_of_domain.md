---
title: "lighttpd cant resolve www part of domain"
date: 2010-05-18
forum: Server Platforms
---

### Post by digitalexpl0it on 2010-05-18
hello I have setup a ubuntu 10.04 server. I have installed Lighttpd since im running this on a vps with only 512 mb ram and apache is to much of a memory hog for my application.

Lighttpd is running and I can get to my domain but I cannot access the domain with the www. in front of the domain.

[www.daemonprojects.com](www.daemonprojects.com) = un-reachable
daemonprojects.com = reachable

Also looks like subdomains dont work either
sub.daemonprojects.com = un-reachable

I have vhosts enabled.
/etc/lighttpd/conf-enabled/10-simple-vhost.conf

> ## Simple name-based virtual hosting
##
## Documentation: /usr/share/doc/lighttpd-doc/simple-vhost.txt
##                [http://www.lighttpd.net/documentation/simple-vhost.html](http://www.lighttpd.net/documentation/simple-vhost.html)

server.modules += ( "mod_simple_vhost" )

## The document root of a virtual host isdocument-root =
##   simple-vhost.server-root + $HTTP["host"] + simple-vhost.document-root
simple-vhost.server-root         = "/var/www/srv/"
simple-vhost.document-root       = "/pages/"

## the default host if no host is sent
simple-vhost.default-host        = "www.daemonprojects.com"


/etc/lighttpd/lighttpd.conf

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
	    "mod_fastcgi",
            "mod_rewrite",
#           "mod_redirect",
            "mod_evhost",
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
 server.port               = 80

## bind to localhost only (default: all interfaces)
 server.bind                = "173.212.208.160"

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
evhost.path-pattern = "/var/www/srv/%0/pages/"

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"

#### variable usage:
## variable name without "." is auto prefixed by "var." and becomes "var.bar"
#bar = 1
#var.mystring = "daemonprojects"

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

#fastcgi.server = ( ".php" => ((
#"bin-path" => "/usr/bin/php-cgi",
#"socket" => "/tmp/php.socket"
#)))

#$HTTP["host"] =~ "^(www\.)?daemonprojects.com$" {
#$HTTP["host"] =~ "daemonprojects.com$" {
#  server.document-root = "/var/www/srv/daemonprojects.com/pages"
#  server.error-handler-404 = "/404.php"
#}

$HTTP["host"] =~ "(^|\.)daemonprojects\.com$" {
#$HTTP["host"] =~ "^(www\.)?daemonprojects\.com$" {
server.document-root = "/var/www/srv/daemonprojects.com/pages"
server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
server.error-handler-404 = "/404.php"
}

$HTTP["host"] =~ "(^|\.)sub\.daemonprojects\.com$" {
server.document-root = "/var/www/srv/daemonprojects.com/sub/"
server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
server.error-handler-404 = "/404.php"
}



my nameservers seem fine, I even have CNAME's for www. and sub.

any ideas?

---

### Post by cdenley on 2010-05-18
I'm not familiar with lighttpd, but perhaps I can help you troubleshoot.
```

getent hosts daemonprojects.com www.daemonprojects.com sub.daemonprojects.com
echo -e "GET / HTTP/1.0\nHost: daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
echo -e "GET / HTTP/1.0\nHost: www.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
echo -e "GET / HTTP/1.0\nHost: sub.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80

```

---

### Post by digitalexpl0it on 2010-05-18
> **cdenley said:**
> I'm not familiar with lighttpd, but perhaps I can help you troubleshoot.
```

getent hosts daemonprojects.com www.daemonprojects.com sub.daemonprojects.com
echo -e "GET / HTTP/1.0\nHost: daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
echo -e "GET / HTTP/1.0\nHost: www.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
echo -e "GET / HTTP/1.0\nHost: sub.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80

```

root@daemonprojects:~# getent hosts daemonprojects.com [www.daemonprojects.com](www.daemonprojects.com) sub.daemonprojects.com
127.0.0.1       localhost.localdomain localhost daemonprojects.com daemonprojects daemonprojects daemonprojects daemonprojects.com
173.212.208.160 localhost.localdomain localhost daemonprojects.com daemonprojects daemonprojects daemonprojects daemonprojects.com
173.212.208.160 daemonprojects.com [www.daemonprojects.com](www.daemonprojects.com)
173.212.208.160 daemonprojects.com sub.daemonprojects.com
root@daemonprojects:~# echo -e "GET / HTTP/1.0\nHost: daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
root@daemonprojects:~# echo -e "GET / HTTP/1.0\nHost: www.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
root@daemonprojects:~# echo -e "GET / HTTP/1.0\nHost: sub.daemonprojects.com\n"|nc -q 1 -w 2 127.0.0.1 80
root@daemonprojects:~#

---

### Post by cdenley on 2010-05-18
I see that your server will resolve daemonprojects.com to 127.0.0.1, while any subdomains will be resolved to 173.212.208.160. Do you have a router between the server and the internet? If so, many router will not use port forwarding rules for connections originating from within your LAN.
```

nc -z -v -w 2 173.212.208.160 80

```

This must not be the case, though, since you're binding to 173.212.208.160.
```

sudo netstat -tlnp
nc -z -v -w 2 127.0.0.1 80
ifconfig

```

---

### Post by digitalexpl0it on 2010-05-18
> **cdenley said:**
> I see that your server will resolve daemonprojects.com to 127.0.0.1, while any subdomains will be resolved to 173.212.208.160. Do you have a router between the server and the internet? If so, many router will not use port forwarding rules for connections originating from within your LAN.
```

nc -z -v -w 2 173.212.208.160 80

```

This must not be the case, though, since you're binding to 173.212.208.160.
```

sudo netstat -tlnp
nc -z -v -w 2 127.0.0.1 80
ifconfig

```

not sure, this is a VPS hosted solution.

here is my hosts file

root@daemonprojects:/etc/lighttpd# cat /etc/hosts
127.0.0.1 localhost.localdomain localhost daemonprojects.com daemonprojects
# Auto-generated hostname. Please do not remove this comment.
173.212.208.160 daemonprojects.com daemonprojects
root@daemonprojects:/etc/lighttpd#

> root@daemonprojects:/etc/lighttpd# nc -z -v -w 2 173.212.208.160 80
DNS fwd/rev mismatch: daemonprojects.com != localhost.localdomain
daemonprojects.com [173.212.208.160] 80 (www) open
root@daemonprojects:/etc/lighttpd# netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      28519/mysqld    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      3087/lighttpd   
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      28651/perl      
tcp        0      0 173.212.208.161:53      0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 173.212.208.160:53      0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      28458/sshd      
tcp6       0      0 :::53                   :::*                    LISTEN      9282/named      
tcp6       0      0 :::22                   :::*                    LISTEN      28458/sshd      
root@daemonprojects:/etc/lighttpd# nc -z -v -w 2 127.0.0.1 80
localhost.localdomain [127.0.0.1] 80 (www) open
root@daemonprojects:/etc/lighttpd# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:935808 (935.8 KB)  TX bytes:935808 (935.8 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:44854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7967016 (7.9 MB)  TX bytes:7371869 (7.3 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:173.212.208.160  P-t-P:173.212.208.160  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:173.212.208.161  P-t-P:173.212.208.161  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

root@daemonprojects:/etc/lighttpd# 


---

### Post by cdenley on 2010-05-18
I would try commenting out this line in /etc/lighttpd/lighttpd.conf.
```

server.bind = "173.212.208.160"

```
Either that, or remove any /etc/hosts entries for your domain which would resolve it to 127.0.0.1.

The netstat output you posted shows it is binding to all interfaces, but perhaps it simply ignores connections coming from other interfaces. It is accepting connections on 127.0.0.1, but hasn't given you any responses to your HTTP requests.

---

### Post by digitalexpl0it on 2010-05-18
> **cdenley said:**
> I would try commenting out this line in /etc/lighttpd/lighttpd.conf.
```

server.bind = "173.212.208.160"

```
Either that, or remove any /etc/hosts entries for your domain which would resolve it to 127.0.0.1.

The netstat output you posted shows it is binding to all interfaces, but perhaps it simply ignores connections coming from other interfaces. It is accepting connections on 127.0.0.1, but hasn't given you any responses to your HTTP requests.

so now [http://sub.daemonprojects.com](http://sub.daemonprojects.com) works but it forwards to [http://daemonprojects.com](http://daemonprojects.com) and not its sub folder

> root@daemonprojects:/etc/lighttpd# nc -z -v -w 2 173.212.208.160 80
daemonprojects.com [173.212.208.160] 80 (www) open
root@daemonprojects:/etc/lighttpd# netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      28519/mysqld    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      27669/lighttpd  
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      28651/perl      
tcp        0      0 173.212.208.161:53      0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 173.212.208.160:53      0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      9282/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      28458/sshd      
tcp6       0      0 :::53                   :::*                    LISTEN      9282/named      
tcp6       0      0 :::22                   :::*                    LISTEN      28458/sshd      
root@daemonprojects:/etc/lighttpd# nc -z -v -w 2 127.0.0.1 80
localhost.localdomain [127.0.0.1] 80 (www) open
root@daemonprojects:/etc/lighttpd#

> root@daemonprojects:/etc/lighttpd# cat lighttpd.conf 
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
            "mod_rewrite",
#           "mod_redirect",
            "mod_evhost",
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
 server.port               = 80

## bind to localhost only (default: all interfaces)
# server.bind                = "173.212.208.160"
# server.bind                = "127.0.0.1"

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
evhost.path-pattern = "/var/www/srv/%0/pages/"

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"

#### variable usage:
## variable name without "." is auto prefixed by "var." and becomes "var.bar"
#bar = 1
#var.mystring = "daemonprojects"

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

##$HTTP["host"] =~ "(^|\.)daemonprojects\.com$" {
#$HTTP["host"] =~ "^(www\.)?daemonprojects\.com$" {
##$HTTP["host"] =~ "www.daemonprojects.com" {
#server.document-root = "/var/www/srv/daemonprojects.com/pages"
#server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
#accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
#server.error-handler-404 = "/404.php"
#}

#$HTTP["host"] =~ "sub\.daemonprojects\.com" {
#server.document-root = "/var/www/srv/daemonprojects.com/sub/"
#server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
#accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
#server.error-handler-404 = "/404.php"
#}

$HTTP["host"] =~ "(^|www\.)daemonprojects\.com" { 
    server.document-root = "/var/www/srv/daemonprojects.com/pages/"
    server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
    accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
}

$HTTP["host"] == "sub.daemonprojects.com" {
    server.document-root = "/var/www/srv/daemonprojects.com/sub/"
    server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
    accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
}


> root@daemonprojects:/etc/lighttpd# cat /etc/hosts
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
173.212.208.160 daemonprojects.com daemonprojects
root@daemonprojects:/etc/lighttpd#

---

### Post by digitalexpl0it on 2010-05-18
ok looks like [www.daemonprojects.com](www.daemonprojects.com) and daemonprojects.com is working...now I just need to get sub.daemonprojects.com working


going to try this in lighttpd.conf
> $HTTP["host"] =~ "(^|\.)sub\.daemonprojects\.com$" {
    server.document-root = "/var/www/srv/sub.daemonprojects.com/pages/"
    server.errorlog = "/var/log/lighttpd/daemonprojects/error.log"
    accesslog.filename = "/var/log/lighttpd/daemonprojects/access.log"
}


---

### Post by digitalexpl0it on 2010-05-18
ok so I cant get sub domains working now

---

