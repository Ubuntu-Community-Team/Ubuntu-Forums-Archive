---
title: "Squid Help"
date: 2007-01-29
forum: Server Platforms
---

### Post by SVFUSiON on 2007-01-29
I am trying to install squid and set it up using webmin. How ever I can not get it to run.  My network IP range is 192.168.0.1/192.168.0.254. This is the error i get.
Failed to start Squid :

2007/01/29 11:23:05| parseConfigFile: line 4275 unrecognized: 'https_port localhost:3128'
2007/01/29 11:23:05| parseConfigFile: line 4277 unrecognized: 'httpd_accel_host virtual'
2007/01/29 11:23:05| parseConfigFile: line 4278 unrecognized: 'httpd_accel_port 80'
2007/01/29 11:23:05| parseConfigFile: line 4279 unrecognized: 'httpd_accel_with_proxy on'
2007/01/29 11:23:05| parseConfigFile: line 4280 unrecognized: 'httpd_accel_uses_host_header on'
2007/01/29 11:23:05| parseConfigFile: line 4281 unrecognized: 'httpd_accel_single_host off'

here is a link to my squid.conf since it is to long to post.
[http://www.fusionlan.com/squid.conf]("http://www.fusionlan.com/squid.conf")

THANKS! :guitar:

---

### Post by SVFUSiON on 2007-01-29
*Bump*

---

### Post by esaym on 2007-01-29
Anyway you can find a simpler config file?  That one is just way too big for even an advanced user to pick through and try to configure.


here is my "simple" [config]("http://lindsay.ath.cx/stuff/squid.conf")

It is for squid 24.  My guessing is that something in that huge config file of yours is enabled that shouldn't be and screwing up those options

---

### Post by SVFUSiON on 2007-01-30
thanks for helping me, now I am getting

Initializing the Squid cache with the command squid -f /etc/squid/squid.conf -z ..


2007/01/30 00:11:34| parseConfigFile: line 97 unrecognized: 'httpd_accel_host virtual '
2007/01/30 00:11:34| parseConfigFile: line 98 unrecognized: 'httpd_accel_port 80 '
2007/01/30 00:11:34| parseConfigFile: line 99 unrecognized: 'httpd_accel_with_proxy on'
2007/01/30 00:11:34| parseConfigFile: line 100 unrecognized: 'httpd_accel_uses_host_header on '
FATAL: Error Directory /usr/local/squid/etc/smootherrors: (2) No such file or directory
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.000 user + 0.010 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0

---

### Post by SVFUSiON on 2007-01-30
well I got passed that now I am working on this,

Initializing the Squid cache with the command squid -f /etc/squid/squid.conf -z ..


2007/01/30 00:30:59| Creating Swap Directories
FATAL: Failed to make swap directory /var/squid/cache/00: (13) Permission denied
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0

---

### Post by SVFUSiON on 2007-01-30
I do get this message when I try to install squid. Many it has something to do with it?

ââââââââââââââââââââââââââââââââââââââââââ¤ Configuring squid âââââââââââââââââââââââââââââââââââââââââââ
 â                                                                                                      â
 â Values for cache_effective_user and/or cache_effective_group in config file are incompatible with    â
 â owner/group of cache directories. Do you want to automatically fix permissions on cache directory?   â
 â                                                                                                      â
 â WARNING: If you specified a cache directory different from /var/spool/squid and selected some other  â
 â directory used by other programs (e.g. /tmp), this could affect those programs.                      â
 â                                                                                                      â
 â Fix permissions of cache_dir?                                                                        â
 â                                                                                                      â
 â                             <Yes>                                <No>

---

### Post by SVFUSiON on 2007-01-30
*bump*

---

### Post by garybrlow on 2007-01-30
Squid should run on ok on default options unless you need to Cache and Accelerate  a web server/website namely Apache, you shouldn't be turning on the Httpd Accelerate Option which actually turned off by default. Usually the only thing you need to change are the Cache Options like the Cache Directory Location etc. and the Access Lists. If you installed squid via the official Ubuntu debs  folder permissions are automatically set. If you compiled Squid yourself using the source from [www.squid-cache.org](www.squid-cache.org), you have to manually set the permissions (read and write) for both the Logs and the Cache Directories in your case "/var/squid". Squid configuration is done using sets of directive and options, for a better explainantion and understanding of these directives and options please refer to the Squid Manual located in the docs folder of the installation or the official Squid Website. Take note that Debian has changed some installation locations of files and folders for Squid and Ubuntu has inherited this, the manual might refer to specific locations you won't find in Ubuntu. :) 

Cheers!

GaryBrlow :biggrin:

---

### Post by SVFUSiON on 2007-01-30
I installed Squid using apt-get, still can't figure it out. Thanks for the reply.

Here is my new squid .conf

visible_hostname GateKepper

http_port 192.168.0.187:3128

acl localnet src 192.168.0.0/255.255.255.0

cache_mem 32 MB
maximum_object_size_in_memory 8 KB

cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF

half_closed_clients off

cache_swap_high 100%
cache_swap_low 90%

shutdown_lifetime 3 seconds
icp_port 0

acl QUERY urlpath_regex cgi-bin \?
acl QUERY urlpath_regex [http://www.kwtx.com/weather/radar](http://www.kwtx.com/weather/radar)
acl QUERY urlpath_regex [http://www.weather.com/weather/map](http://www.weather.com/weather/map)
acl QUERY urlpath_regex [http://radar.weather.gov](http://radar.weather.gov)
acl QUERY urlpath_regex [http://www.weather.gov](http://www.weather.gov)
acl QUERY urlpath_regex [http://image.weather.com](http://image.weather.com)
acl QUERY urlpath_regex [http://gray.ftp.clickability.com/kwtxwebftp](http://gray.ftp.clickability.com/kwtxwebftp)
acl QUERY urlpath_regex [http://www.kxxv.com/live](http://www.kxxv.com/live)
acl QUERY urlpath_regex [http://www.mysanantonio.com/multimedia/webcams/superdoppler/images/](http://www.mysanantonio.com/multimedia/webcams/superdoppler/images/)
acl QUERY urlpath_regex [http://mysanantonio.com/multimedia/webcams/superdoppler/images/](http://mysanantonio.com/multimedia/webcams/superdoppler/images/)
no_cache deny QUERY

cache_effective_user fusion
#cache_effective_group 1005

pid_filename /var/run/squid.pid

cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
cache_store_log none
error_directory /usr/local/squid/etc/smootherrors
emulate_httpd_log on
log_mime_hdrs off

forwarded_for off

acl all src 0.0.0.0/0.0.0.0
acl localhost src 127.0.0.1/255.255.255.255

acl SSL_ports port 445 443 441 563
acl Safe_ports port 80  	  	# http
acl Safe_ports port 81  	  	# smoothwall http
acl Safe_ports port 21  	  	# ftp 
acl Safe_ports port 445 443 441 563	# https, snews
acl Safe_ports port 70     		# gopher
acl Safe_ports port 210    	   	# wais  
acl Safe_ports port 1025-65535		# unregistered ports
acl Safe_ports port 280       		# http-mgmt
acl Safe_ports port 488       		# gss-http 
acl Safe_ports port 591       		# filemaker
acl Safe_ports port 777       		# multiling http
acl CONNECT method CONNECT

http_access allow localhost
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access deny all

connect_timeout 5 seconds

refresh_pattern -i \.jpg$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.bmp$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.gif$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.png$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.ico$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.mpg$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.wma$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.mp3$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.wmv$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.avi$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.m3u$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.asx$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.swf$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.asf$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.pdf$ 9000000 100% 9000009 override-expire
refresh_pattern -i \.mpeg$ 9000000 100% 9000009 override-expire

maximum_object_size 2048 KB
minimum_object_size 0 KB

cache_dir diskd /var/squid/cache 3000 16 256

request_body_max_size 0 KB
reply_body_max_size 0 allow all

---

### Post by esaym on 2007-01-31
> **SVFUSiON said:**
> well I got passed that now I am working on this,

Initializing the Squid cache with the command squid -f /etc/squid/squid.conf -z ..


2007/01/30 00:30:59| Creating Swap Directories
FATAL: Failed to make swap directory /var/squid/cache/00: (13) Permission denied
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0

Hmm looks like a simple permissions problem??

sudo chmod -R 777 /var/squid/cache/

That might work.

Also I see you copied my squid config.  I was just posting that so you could see an example of a working config.  I don't think all my options in the config will work with you.  Feel free to try and see though.  I doubt all the directories will be the same since that config came from a firewall running redhat7.

---

### Post by andytof47 on 2007-02-02
Hi 

I have this happening as well


2007/01/30 00:11:34| parseConfigFile: line 97 unrecognized: 'httpd_accel_host virtual '
2007/01/30 00:11:34| parseConfigFile: line 98 unrecognized: 'httpd_accel_port 80 '
2007/01/30 00:11:34| parseConfigFile: line 99 unrecognized: 'httpd_accel_with_proxy on'
2007/01/30 00:11:34| parseConfigFile: line 100 unrecognized: 'httpd_accel_uses_host_header on '
FATAL: Error Directory /usr/local/squid/etc/smootherrors: (2) No such file or directory
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.


When I comment out these lines and try to connect to the internet I get an error telling me squid can't forward the request  and that  squid doesn't allow direct connections  


I also have Dansguardian installed if I try to connect to a bad page e.g Microsoft.com

which is in my bad sites list DG blocks the page - so it is working, 

also i can connect to webmin, and gnump3 servers on my local ubuntu system just not to the outside world

I would like to post my config file but i'm in windows now......... can anyone help


i'll get my config in a minute actually

---

### Post by esaym on 2007-02-02
> **andytof47 said:**
> Hi 

I have this happening as well


2007/01/30 00:11:34| parseConfigFile: line 97 unrecognized: 'httpd_accel_host virtual '
2007/01/30 00:11:34| parseConfigFile: line 98 unrecognized: 'httpd_accel_port 80 '
2007/01/30 00:11:34| parseConfigFile: line 99 unrecognized: 'httpd_accel_with_proxy on'
2007/01/30 00:11:34| parseConfigFile: line 100 unrecognized: 'httpd_accel_uses_host_header on '
FATAL: Error Directory /usr/local/squid/etc/smootherrors: (2) No such file or directory
Squid Cache (Version 2.6.STABLE1): Terminated abnormally.


When I comment out these lines and try to connect to the internet I get an error telling me squid can't forward the request  and that  squid doesn't allow direct connections  


I also have Dansguardian installed if I try to connect to a bad page e.g Microsoft.com

which is in my bad sites list DG blocks the page - so it is working, 

also i can connect to webmin, and gnump3 servers on my local ubuntu system just not to the outside world

I would like to post my config file but i'm in windows now......... can anyone help


i'll get my config in a minute actually

I guess I should clarify, **the config file I posted is not for ubuntu!**  I simply posted to show an example of how to make the config file easier to manage.  Start off with the stock config file and post any errors and then we can work from there....

---

### Post by esaym on 2007-02-02
> **SVFUSiON said:**
> I am trying to install squid and set it up using webmin. How ever I can not get it to run.  My network IP range is 192.168.0.1/192.168.0.254. This is the error i get.
Failed to start Squid :

2007/01/29 11:23:05| parseConfigFile: line 4275 unrecognized: 'https_port localhost:3128'
2007/01/29 11:23:05| parseConfigFile: line 4277 unrecognized: 'httpd_accel_host virtual'
2007/01/29 11:23:05| parseConfigFile: line 4278 unrecognized: 'httpd_accel_port 80'
2007/01/29 11:23:05| parseConfigFile: line 4279 unrecognized: 'httpd_accel_with_proxy on'
2007/01/29 11:23:05| parseConfigFile: line 4280 unrecognized: 'httpd_accel_uses_host_header on'
2007/01/29 11:23:05| parseConfigFile: line 4281 unrecognized: 'httpd_accel_single_host off'

here is a link to my squid.conf since it is to long to post.
[http://www.fusionlan.com/squid.conf]("http://www.fusionlan.com/squid.conf")

THANKS! :guitar:

Ok I just did some reading and it looks like all the "httpd_accel" options are left over from the upgrade from squid 25 and they are deprecated.

It looks like you can replace all of this:

```
https_port localhost:3128
httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on
httpd_accel_single_host off
```

with only this:

```
http_port 3128 transparent
always_direct allow all 
```

I don't have any way to varify this as I still use squid 24 and 25 and NOT 26.  So be sure to back up your config before messing with it.

Links:

[http://itreporter.bloghost.ro/2006/10/19/transparent-proxy-with-squid-26-ubuntu-edgy-caveats/](http://itreporter.bloghost.ro/2006/10/19/transparent-proxy-with-squid-26-ubuntu-edgy-caveats/)
[http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1](http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1)
[http://www.deckle.co.za/squid-users-guide/Transparent_Caching/Proxy](http://www.deckle.co.za/squid-users-guide/Transparent_Caching/Proxy)

---

### Post by ifrflyer on 2007-02-04
Also, not sure your http_port needs the whole IP, just the port? SOunds dumb but might be a problem?

---

### Post by esaym on 2007-02-05
> **ifrflyer said:**
> Also, not sure your http_port needs the whole IP, just the port? SOunds dumb but might be a problem?


I saw it done both ways in documentation.  I just upgraded to squid 2.6 and it replaced all the http_accel stuff with just: http_port 10.36.36.1:800 transparent  


You also have to stick "allow all" somewhere in your config too.

---

