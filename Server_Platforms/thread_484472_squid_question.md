---
title: "squid question"
date: 2007-06-25
forum: Server Platforms
---

### Post by irwa82 on 2007-06-25
I have squid working fine with my linux computer but
there is a windows user on the network and windows
does not want to work with the proxy.

In the access.log file it lists tcp_hit/200 and
tcp_miss/200 depending on if anything is cached for
the linux boxes but nothing logged for the windows
box (windows box does not display any web pages when set to use the proxy).

I have created a cut back config with not much in it
and set the browsers to the proxy it works in linux but not
windows and I am not sure why.

Its using squid 2.6

Below is the cut back config:

access_log /var/log/squid/access.log squid
http_port 3128
maximum_object_size 153600 KB
cache_dir ufs /var/spool/squid 4000 16 256

acl all src 0.0.0.0/0.0.0.0
acl our_networks src 192.168.100.0/255.255.255.0
http_access allow our_networks
icp_access allow our_networks
http_reply_access allow all

http_access deny all
icp_access deny all

if I delete the the cache and start squid I get the
following in the cache.log file

2007/06/25 23:09:36| Starting Squid Cache version
2.6.STABLE5 for i386-debian-linux-gnu...
2007/06/25 23:09:36| Process ID 19947
2007/06/25 23:09:36| With 1024 file descriptors
available
2007/06/25 23:09:36| Using epoll for the IO loop
2007/06/25 23:09:36| DNS Socket created at 0.0.0.0,
port 3470, FD 6
2007/06/25 23:09:36| Adding nameserver 192.231.203.132
from /etc/resolv.conf
2007/06/25 23:09:36| Adding nameserver 192.231.203.3
from /etc/resolv.conf
2007/06/25 23:09:36| User-Agent logging is disabled.
2007/06/25 23:09:36| Referer logging is disabled.
2007/06/25 23:09:36| Unlinkd pipe opened on FD 11
2007/06/25 23:09:36| Swap maxSize 4096000 KB,
estimated 315076 objects
2007/06/25 23:09:36| Target number of buckets: 15753
2007/06/25 23:09:36| Using 16384 Store buckets
2007/06/25 23:09:36| Max Mem  size: 8192 KB
2007/06/25 23:09:36| Max Swap size: 4096000 KB
2007/06/25 23:09:36| Local cache digest enabled;
rebuild/rewrite every 3600/3600 sec
2007/06/25 23:09:36| Rebuilding storage in
/var/spool/squid (DIRTY)
2007/06/25 23:09:36| Using Least Load store dir
selection
2007/06/25 23:09:36| Current Directory is /
2007/06/25 23:09:36| Loaded Icons.
2007/06/25 23:09:36| Accepting proxy HTTP connections
at 0.0.0.0, port 3128, FD 12.
2007/06/25 23:09:36| Accepting ICP messages at
0.0.0.0, port 3130, FD 13.
2007/06/25 23:09:36| HTCP Disabled.
2007/06/25 23:09:36| WCCP Disabled.
2007/06/25 23:09:36| Ready to serve requests.

anyway if anyone knows why linux would work with the
proxy and not windows it would be good because I am
not having any luck with google searching and the
squid faq does not seem to have anything in there
about it either.

---

### Post by indralaily on 2007-06-25
do you have setting your windows client to use proxy??

---

