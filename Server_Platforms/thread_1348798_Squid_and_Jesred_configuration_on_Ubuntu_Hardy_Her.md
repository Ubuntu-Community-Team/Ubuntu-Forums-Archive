---
title: "Squid and Jesred configuration on Ubuntu Hardy Heron"
date: 2009-12-07
forum: Server Platforms
---

### Post by sanyu on 2009-12-07
Hello,

Would appreciate your help with my Ubuntu Squid configuration. Until recently I had a single dedicated Fedora server for my development needs. Currently I am trying to migrate to an Ubuntu EC2 instance for my server requirements.

Background:
- The single Ubuntu EC2 instance will have multiple services/domains running on different ports.
- The server has Apache running on port 5000
- Squid is configured on port 80. The idea is Squid will process all incoming HTTP/HTTPS requests and redirect to the appropriate service on the same server.
- As for redirector, I have configured jesred.

Configuration so far:
- installed Apache2
- install squid (sudo apt-get install squid)
- install jesred (sudo apt-get install jesred)
- editted the squid.conf and jesred.conf, jesred.rules file

Unfortunately, All my HTTP requests result in "TCP_DENIED/400 1962 GET error:invalid-request" error.

Any suggestions on what might be causing this?

Thanks  a bunch.


Here are my configuration files:
squid.conf - (a long paste)
# ========= BEGIN OF SQUID.CONF
http_port 80
# hostname is set to 'hostname' from the ec2 instance
visible_hostname domU-1-2-3-4-C9-54

tcp_outgoing_address 127.0.0.1

hierarchy_stoplist cgi-bin ?
hierarchy_stoplist banner

acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
cache_store_log none

acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

cache_mem 128 MB

maximum_object_size 0 KB

minimum_object_size 0 KB
maximum_object_size_in_memory 8 KB

cache_dir ufs /var/spool/squid 1024 16 256
logformat squid %tl %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
access_log /var/log/squid/access.log squid

url_rewrite_program /usr/lib/squid/jesred
url_rewrite_children 10
url_rewrite_host_header on

refresh_pattern . 0  20%  4320

############### begin access controls 

acl MyNetwork src localhost
acl myLocalhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl hostsToBlock src 204.9.65.186
acl all src 0.0.0.0/0.0.0.0

acl ValidDomains dstdomain .domain1.com .domain2.com  .amazonaws.com

acl HTTPports port 80
acl Safe_ports port 80
acl Safe_ports port 443
acl SSL_ports port 443

acl CONNECT method CONNECT
acl Safe_proto proto HTTP HTTPS
acl buggy_server url_regex ^[http://.](http://.)...

redirector_access deny !ValidDomains
redirector_access deny hostsToBlock

http_access deny !Safe_proto
http_access deny !ValidDomains
http_access deny hostsToBlock
http_access deny !Safe_ports
http_access allow MyNetwork
http_access allow CONNECT SSL_ports
http_access allow myLocalhost
http_access deny CONNECT
http_access allow all

############################ end access controls

nonhierarchical_direct off
broken_posts allow buggy_server

icp_access allow all

coredump_dir /var/spool/squid

############# Start of cache_peer definitions
# TODO

# ========= END OF SQUID.CONF

---

