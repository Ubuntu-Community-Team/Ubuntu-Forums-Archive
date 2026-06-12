---
title: "Squid Setup on 11.04"
date: 2011-06-09
forum: Server Platforms
---

### Post by terrykiwi83 on 2011-06-09
So it seems I have a tad problem.

Basically I have a small idea but not a big idea on how to get squid running.

Here is the setup.

Ubuntu 11.04 dedicated to running just squid as caching proxy server. eth0 = connected to Internet & Local Network via Router. Static IP: 192.168.1.100

Now the client machine Ubuntu 10.10 (IP: 192.168.1.5) doesn't want to know the squid setup, when I change to the proxy server in Chrome settings I just get a blank page with an error saying something about it not being able to access the internet.

When I check the squid access log there in no indication that the client connected?  Anyone got any ideas for what I can change the squid.conf to?

Other info.

I have an ADSL2+ Modem (192.168.1.1 - Default Gateway - connected to internet and connected to my wireless router).

The wireless router (IP: 192.168.1.250) serves 3 computers at my house, 2 windows clients and 1 ubuntu client. all on the IP range 192.168.1.x

The Ubuntu  11.04 squid server is connected directly to the router via ethernet.

any help would be appreciated :)

Edit:
------
When I turn off the proxy connection in my Ubuntu client and go to 192.168.1.100 (squid server) I get the Apache 'It Works Page' but when I turn on the proxy I don't get this page just the blank error.

---

### Post by terrykiwi83 on 2011-06-09
here is my squid.conf file

```


acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl internal_network src 192.168.1.0/24
http_access allow internal_network
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.1.0/24 # RFC1918 possible internal networ
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups

acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access allow localnet
icp_access deny all
visible_hostname 192.168.1.100
http_port 3128
hierarchy_stoplist cgi-bin ?
cache_mem 250 MB
cache_dir ufs /var/spool/squid 250 16 256
cache_dir diskd /cache 250 16 256
cache_access_log /var/log/squid/access.log
access_log /var/log/squid/access.log squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$       0       20%     2880
refresh_pattern .               0       20%     4320
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
acl intranet 192.168.1.1/24
http_access allow intranet
hosts_file /etc/hosts
coredump_dir /var/spool/squid

```

there has to be something wrong with above config file ?

---

### Post by wojox on 2011-06-09
Here are the main things to look at and restart squid after you edit:

```

http_port 8080

acl CONNECT method CONNECT

acl lan src 192.168.0.0/255.255.255.0

http_access allow localhost

http_access allow lan

http_access deny all

forwarded_for off

header_access Referer deny all
header_access X-Forwarded-For deny all
header_access Via deny all
header_access Cache-Control deny all 
```

---

### Post by terrykiwi83 on 2011-06-09
thanks for the reply, I tried that but still same problem.

Google Chrome simply just gives me the error cannot connect to proxy server :(

Any more suggestions? does my squid.conf file look ok have I missed anything

---

### Post by terrykiwi83 on 2011-06-10
ok am getting somewere, have edited my file down to a tee but now get this unusual and confusing error:

```

2011/06/10 16:43:29| ACL name 'all' not defined!
FATAL: Bungled (null) line 180: http_reply_access allow all
Squid Cache (Version 2.7.STABLE9): Terminated abnormally.

```

Now I have looked at my squid.conf file and can't work out why its pointing to line 180, when i haven't mentioned 'all' at all.

Here is my new squid.conf file

```


http_port 192.168.1.100:3128

visible_hostname the-matrix.local
mail_from terryones1983@gmail.com
client_netmask 255.255.255.255
snmp_incoming_address 0.0.0.0
snmp_outgoing_address 255.255.255.255
udp_incoming_address 0.0.0.0
udp_outgoing_address 255.255.255.255
icp_port 3130 proxy-only
cache_replacement_policy lru
memory_replacement_policy lru
cache_dir ufs /var/spool/squid 100 16 256
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
hosts_file /etc/hosts
icon_directory /usr/share/squid/icons
error_directory /usr/share/squid/errors/en
diskd_program /usr/lib/squid/diskd-daemon
unlinkd_program /usr/lib/squid/unlinkd
debug_options ALL,1
ftp_user Squid@
uri_whitespace strip
cache_effective_user squid
cache_effective_group squid
cache_mgr root
mail_program mail
umask 027
announce_host tracker.ircache.net
as_whois_server whois.ra.net
wccp_address 0.0.0.0
wccp2_address 0.0.0.0
wccp_router 0.0.0.0
store_dir_select_algorithm least-load
coredump_dir /var/spool/squid
icp_query_timeout 0
maximum_icp_query_timeout 2000
mcast_icp_query_timeout 2000
dead_peer_timeout 10 seconds
forward_timeout 4 minutes
connect_timeout 1 minutes
peer_connect_timeout 30 seconds
read_timeout 15 minutes
request_timeout 5 minutes
persistent_request_timeout 1 minutes
pconn_timeout 120 seconds
ident_timeout 10 seconds
dns_timeout 2 minutes
dns_retransmit_interval 5 seconds
snmp_port 0
cache_mem 250 MB
cache_swap_low 90
cache_swap_high 95
maximum_object_size 4096 KB
minimum_object_size 0 KB
maximum_object_size_in_memory 8 KB
ipcache_size 1024
ipcache_low 90
ipcache_high 95
fqdncache_size 1024
ftp_list_width 32
memory_pools_limit 5 MB
request_header_max_size 20 KB
request_body_max_size 0 KB
quick_abort_min 16 KB
quick_abort_max 16 KB
quick_abort_pct 95
read_ahead_gap 16 KB
negative_ttl 5 minutes
positive_dns_ttl 6 seconds
negative_dns_ttl 1 seconds
range_offset_limit 0 KB
client_lifetime 1 day
shutdown_lifetime 30 seconds
reply_header_max_size 20 KB
announce_period 50 seconds
announce_port 3131
logfile_rotate 0
tcp_recv_bufsize 0 bytes
minimum_direct_hops 4
minimum_direct_rtt 400
store_avg_object_size 13 KB
store_objects_per_bucket 20
netdb_low 900
netdb_high 1000
netdb_ping_period 5 minutes
maximum_single_addr_tries 1
wccp_version 4
wccp2_forwarding_method 1
wccp2_return_method 1
wccp2_assignment_method 1
wccp2_service standard 0
wccp2_weight 10000
max_open_disk_fds 0
digest_bits_per_entry 5
digest_rebuild_period 1 seconds
digest_rewrite_period 1 seconds
digest_swapout_chunk_size 4096 bytes
digest_rebuild_chunk_percentage 10
high_response_time_warning 0
high_page_fault_warning 0
high_memory_warning 60 MB
sleep_after_fork 0
minimum_expiry_time 60 seconds
authenticate_cache_garbage_interval 1 seconds
authenticate_ttl 1 seconds
authenticate_ip_ttl 20 seconds
check_hostnames on
dns_defnames off
emulate_httpd_log off
log_ip_on_direct on
log_mime_hdrs off
log_fqdn off
ftp_passive on
ftp_sanitycheck on
ftp_telnet_protocol on
allow_underscore on
memory_pools on
half_closed_clients on
httpd_suppress_version_string off
via on
forwarded_for on
log_icp_queries on
client_db on
icp_hit_stale off
query_icmp off
test_reachability off
buffered_logs off
reload_into_ims off
global_internal_static on
short_icon_urls off
offline_mode off
nonhierarchical_direct on
prefer_direct off
strip_query_terms on
redirector_bypass off
ignore_unknown_nameservers on
client_persistent_connections on
server_persistent_connections on
persistent_connection_after_error off
detect_broken_pconn off
balance_on_multiple_ip on
pipeline_prefetch off
request_entities off
ie_refresh off
vary_ignore_expire off
relaxed_header_parser on
retry_on_error off
wccp2_rebuild_wait on
digest_generation on

acl our_networks src 192.168.0.0/24 192.168.1.0/24 10.8.0.0/32
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl manager proto cache_object
acl QUERY urlpath_regex cgi-bin \?
acl apache rep_header Server ^Apache
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

http_access allow localhost
http_access allow our_networks
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
cache deny QUERY ** Line 180**

```

Any see what am missing here?

---

### Post by laufwerkfehler on 2011-11-28
Any chance you figured this one out? I'm running into the same issue and my config doesn't even have 180 lines!

---

