---
title: "Squid Proxy not connecting with FTP protocol"
date: 2010-05-13
forum: Server Platforms
---

### Post by ganfun on 2010-05-13
Hi 
 
i am unable to make my SQUID proxy connect with ftp protocol the machine connects directly but not from client side i tried everything all the netsearch 
 
> acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 10.0.0.0/8 # RFC1918 possible internal network
acl localnet src 172.16.0.0/12 # RFC1918 possible internal network
acl localnet src 198.168.0.0/16 # RFC1918 possible internal network
acl SSL_ports port 443 21 # https
acl SSL_ports port 563 # snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl bad url_regex "/etc/squid/squid-block.acl"
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access allow !Safe_ports
http_access allow CONNECT !SSL_ports
acl ftp_ports src 21
http_access allow localhost
http_access deny bad
http_access allow all
icp_access allow localnet
icp_access deny all
http_port 198.168.0.13:3128 transparent
http_port 127.0.0.1:3128 transparent
htcp_port 4827
hierarchy_stoplist cgi-bin ?
cache_mem 0 MB
cache_dir ufs /var/spool/squid 8 16 256
access_log /var/log/squid/access.log squid
ftp_user [EMAIL="Squid@domain1.com"][COLOR=#22229c]Squid@domain1.com[/COLOR][/EMAIL]
ftp_passive off
acl ftpusers src 0.0.0.0/0.0.0.0
http_access allow ftpusers ftp_ports
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern (Release|Package(.gz)*)$ 0 20% 2880
refresh_pattern . 0 20% 4320
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
acl FTP proto FTP
always_direct allow FTP
check_hostnames off
hosts_file /etc/hosts
visible_hostname minfolin
 
icp_port 3130
 
always_direct allow all
 
forwarded_for off
coredump_dir /var/spool/squid
 
when i try from my windows client i get error : connection timeout

---

