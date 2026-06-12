---
title: "Squid3 on Ubuntu 8.04.1 donwload &gt;2gb files problem."
date: 2008-12-03
forum: Server Platforms
---

### Post by Dubolomov on 2008-12-03
Hi. I'm using Squid 3.0.STABLE1 on Ubuntu 8.04.1 Server i386. I have problem with downoading files through proxy more than 2gb. For example i'm trying to download DVD-iso image and at 2gb of downloading through wget in cache.log file i see "WARNING: preventing off_t overflow for [url_to_file]".
Filesystem is ReiserFS.
Wget download this file well if no proxy is used.

/etc/squid3/squid.conf file:
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl localnet src 192.168.0.0/24
acl to_localhost dst 127.0.0.0/8
acl FTP proto FTP
acl SSL_ports port 443
acl CONNECT method CONNECT

http_access allow manager localhost
http_access allow localnet
http_access allow FTP
http_access deny manager

http_access allow localhost
http_access deny all

icp_access deny all
htcp_access deny all

http_port 3128 transparent

hierarchy_stoplist cgi-bin ?

cache_mem 64 MB

cache_dir ufs /store/squid-swap 8192 16 256

maximum_object_size 32768 KB

access_log /var/log/squid3/access.log squid

acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY

refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320

icp_port 3130

always_direct allow FTP

coredump_dir /var/spool/squid3

---

### Post by szef666 on 2009-01-15
Hello,
Try to recompile squid-3 from source.

After downloading and unpacking squid-3 first check which build options has your current installation with command
squid -v

and then configure sources with
./configure **--with-large-files** <here copy options that showed "squid -v", of course without quotes>

I have compiled squid with:
> Squid Cache: Version 3.0.STABLE10
configure options:  '--with-large-files' '--enable-async-io' '--with-default-user=proxy' '--enable-ssl' '--enable-linux-netfilter' '--enable-storeio=aufs' '--enable-removal-policies=lru,heap' '--enable-icmp' '--enable-useragent-log' '--enable-referer-log' '--enable-arp-acl' '--enable-ipf-transparent'

and from now it allowed to download files larger than 2GB [with internet explorer and squid set as transparent proxy]

---

### Post by pastoreerrante on 2009-08-03
> **szef666 said:**
> Hello,
Try to recompile squid-3 from source.
 
After downloading and unpacking squid-3 first check which build options has your current installation with command
squid -v
 
and then configure sources with
./configure **--with-large-files** <here copy options that showed "squid -v", of course without quotes>
 
I have compiled squid with:
 
and from now it allowed to download files larger than 2GB [with internet explorer and squid set as transparent proxy]
 
Hi szef666,
 
I have exactly the same problem, but on my Ubuntu server 8.04.03 system the "squid3 -v" command already have the '--enable-large-files' flag, so why I cannot dowload files greater than 2GB?
 
Thank you, Daniele

---

