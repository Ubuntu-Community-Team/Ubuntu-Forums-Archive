---
title: "Please help config squid"
date: 2012-03-01
forum: Server Platforms
---

### Post by andhix on 2012-03-01
Hello, 
i just setting a network with squid transparent and a 3grouter.

My network topology
> [IMG]http://cdn-u.kaskus.us/71/djiihmk4.jpg[/IMG]My squid setting
```
#==================================$
# Proxy Server Versi 2.7.Stable7
#==================================$
#################################################################
# Port
#################################################################
http_port 8080 transparent
icp_port 0
#prefer_direct off

#################################################################
# Cache & Object
#################################################################
cache_mem 8 MB
cache_swap_low 98
cache_swap_high 99
max_filedesc 8192
maximum_object_size 8 MB
minimum_object_size 0 KB
maximum_object_size_in_memory 4 bytes
ipcache_size 4096
ipcache_low 98
ipcache_high 99
fqdncache_size 4096
cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF
#################################################################
# cache_dir <type> <Directory-Name> <Space in Mbytes> <Level1> <Level2> <options>
cache_dir ufs /home/squid 9000 32 128

cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
cache_store_log none
pid_filename /var/run/squid.pid
cache_swap_log /var/log/squid/swap.state
dns_nameservers 208.67.222.222 208.67.220.220
emulate_httpd_log off
hosts_file /etc/hosts
half_closed_clients off
negative_ttl 1 minutes
#################################################################
# Rules: Safe Port
#################################################################
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 873
acl Safe_ports port 80            # https snews rsync
acl Safe_ports port 20 21        # http
acl Safe_ports port 70            # ftp
acl Safe_ports port 210            # gopher
acl Safe_ports port 1025-65535        # wais
acl Safe_ports port 631            # unregistered ports
acl Safe_ports port 10000        # cups
acl Safe_ports port 901            # webmin
acl Safe_ports port 280            # SWAT
acl Safe_ports port 488            # http-mgmt
acl Safe_ports port 591            # gss-http
acl Safe_ports port 777            # multiling http
acl Safe_ports port 873            # rsync
acl Safe_ports port 110            # POP3
acl Safe_ports port 25            # SMTP
acl Safe_ports port 2095 2096        # webmail from cpanel
acl Safe_ports port 2082 2083        # cpanel

acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports !SSL_ports
http_access deny CONNECT !SSL_ports !Safe_ports
#################################################################
# Refresh Pattern
#################################################################
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440

refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|mpg|swf|flv|x-flv)$ 43200 90% 432000 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(deb|rpm|exe|ram|bin|pdf|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(zip|gz|arj|lha|lzh|tar|tgz|cab|rar)$ 10080 95% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(html|htm|css|js|php|asp|aspx|cgi) 1440 40% 40320
refresh_pattern .        0    20%    4320

#################################################################
# HIERARCHY (BYPASS CGI)
#################################################################
#hierarchy_stoplist cgi-bin ? .js .jsp
#acl QUERY urlpath_regex cgi-bin \? .js .jsp
#no_cache deny QUERY
#################################################################

#################################################################
# ALLOWED ACCESS
#################################################################
acl server src 192.168.1.2/24
acl client src 192.168.1.3-192.168.1.15/24
http_access allow server
http_access allow client
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow server
icp_access allow client
icp_access allow localhost
icp_access deny all

always_direct deny all
#################################################################
# Cache CGI & Administrative
#################################################################
cache_mgr my@mail.com
cachemgr_passwd none
visible_hostname xcodex-desktop
cache_effective_user squid
cache_effective_group squid
coredump_dir /var/spool/squid
shutdown_lifetime 10 seconds
logfile_rotate 14

```But my squid doesn't work
```
xcodex@xcodex-desktop:~$ sudo squid -N d
WARNING: Cannot write log file: /var/log/squid/cache.log
/var/log/squid/cache.log: Permission denied
         messages will be sent to 'stderr'.
2012/03/01 21:46:00| WARNING: Closing open FD    2
2012/03/01 21:46:00| Starting Squid Cache version 2.7.STABLE7 for i386-debian-linux-gnu...
2012/03/01 21:46:00| Process ID 1697
2012/03/01 21:46:00| With 8192 file descriptors available
2012/03/01 21:46:00| Using epoll for the IO loop
2012/03/01 21:46:00| Performing DNS Tests...
2012/03/01 21:46:00| Successful DNS name lookup tests...
2012/03/01 21:46:00| DNS Socket created at 0.0.0.0, port 33346, FD 5
2012/03/01 21:46:00| Adding nameserver 208.67.222.222 from squid.conf
2012/03/01 21:46:00| Adding nameserver 208.67.220.220 from squid.conf
2012/03/01 21:46:00| User-Agent logging is disabled.
2012/03/01 21:46:00| Referer logging is disabled.
2012/03/01 21:46:00| logfileOpen: opening log /var/log/squid/access.log
FATAL: Cannot open '/var/log/squid/access.log' for writing.
    The parent directory must be writeable by the
    user 'squid', which is the cache_effective_user
    set in squid.conf.
Squid Cache (Version 2.7.STABLE7): Terminated abnormally.
CPU Usage: 0.016 seconds = 0.004 user + 0.012 sys
Maximum Resident Size: 7776 KB
Page faults with physical i/o: 0
Aborted

```What's wrong with my squid config? thank you...

---

### Post by andhix on 2012-03-01
Hello, 
i just setting a network with squid transparent and a 3grouter.

My network topology
> [IMG]http://cdn-u.kaskus.us/71/djiihmk4.jpg[/IMG]My squid setting
```
#==================================$
# Proxy Server Versi 2.7.Stable7
#==================================$
#################################################################
# Port
#################################################################
http_port 8080 transparent
icp_port 0
#prefer_direct off

#################################################################
# Cache & Object
#################################################################
cache_mem 8 MB
cache_swap_low 98
cache_swap_high 99
max_filedesc 8192
maximum_object_size 8 MB
minimum_object_size 0 KB
maximum_object_size_in_memory 4 bytes
ipcache_size 4096
ipcache_low 98
ipcache_high 99
fqdncache_size 4096
cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF
#################################################################
# cache_dir <type> <Directory-Name> <Space in Mbytes> <Level1> <Level2> <options>
cache_dir ufs /home/squid 9000 32 128

cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
cache_store_log none
pid_filename /var/run/squid.pid
cache_swap_log /var/log/squid/swap.state
dns_nameservers 208.67.222.222 208.67.220.220
emulate_httpd_log off
hosts_file /etc/hosts
half_closed_clients off
negative_ttl 1 minutes
#################################################################
# Rules: Safe Port
#################################################################
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 873
acl Safe_ports port 80            # https snews rsync
acl Safe_ports port 20 21        # http
acl Safe_ports port 70            # ftp
acl Safe_ports port 210            # gopher
acl Safe_ports port 1025-65535        # wais
acl Safe_ports port 631            # unregistered ports
acl Safe_ports port 10000        # cups
acl Safe_ports port 901            # webmin
acl Safe_ports port 280            # SWAT
acl Safe_ports port 488            # http-mgmt
acl Safe_ports port 591            # gss-http
acl Safe_ports port 777            # multiling http
acl Safe_ports port 873            # rsync
acl Safe_ports port 110            # POP3
acl Safe_ports port 25            # SMTP
acl Safe_ports port 2095 2096        # webmail from cpanel
acl Safe_ports port 2082 2083        # cpanel

acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports !SSL_ports
http_access deny CONNECT !SSL_ports !Safe_ports
#################################################################
# Refresh Pattern
#################################################################
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440

refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|mpg|swf|flv|x-flv)$ 43200  90% 432000 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(deb|rpm|exe|ram|bin|pdf|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(zip|gz|arj|lha|lzh|tar|tgz|cab|rar)$ 10080 95% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(html|htm|css|js|php|asp|aspx|cgi) 1440 40% 40320
refresh_pattern .        0    20%    4320

#################################################################
# HIERARCHY (BYPASS CGI)
#################################################################
#hierarchy_stoplist cgi-bin ? .js .jsp
#acl QUERY urlpath_regex cgi-bin \? .js .jsp
#no_cache deny QUERY
#################################################################

#################################################################
# ALLOWED ACCESS
#################################################################
acl server src 192.168.1.2/24
acl client src 192.168.1.3-192.168.1.15/24
http_access allow server
http_access allow client
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow server
icp_access allow client
icp_access allow localhost
icp_access deny all

always_direct deny all
#################################################################
# Cache CGI & Administrative
#################################################################
cache_mgr my@mail.com
cachemgr_passwd none
visible_hostname xcodex-desktop
cache_effective_user squid
cache_effective_group squid
coredump_dir /var/spool/squid
shutdown_lifetime 10 seconds
logfile_rotate 14

```But my squid doesn't work

What's wrong with my squid config? thank you...

---

### Post by andhix on 2012-03-02
SOLVED, thanks i changed my squid.conf like below
```
#==================================$
# Proxy Server Versi 2.7.Stable7
#==================================$
#################################################################
# Port
#################################################################
http_port 8080 transparent
icp_port 3130
#prefer_direct off
udp_incoming_address 0.0.0.0
udp_outgoing_address 255.255.255.255

#################################################################
# Cache & Object
#################################################################
cache_mem 8 MB
cache_swap_low 98
cache_swap_high 99
max_filedesc 8192
maximum_object_size 10 MB
minimum_object_size 0 KB
maximum_object_size_in_memory 4096 KB
ipcache_size 1024
ipcache_low 98
ipcache_high 99
fqdncache_size 1024
cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF
#################################################################
# cache_dir <type> <Directory-Name> <Space in Mbytes> <Level1> <Level2> <options>
cache_dir ufs /home/squid 9000 32 128

cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
log_ip_on_direct on
cache_store_log none
pid_filename /var/run/squid.pid
cache_swap_log /var/log/squid/swap.state
dns_nameservers 208.67.222.222 208.67.220.220
#emulate_httpd_log off
#hosts_file /etc/hosts
#half_closed_clients off
negative_ttl 5 minutes
#################################################################
# Rules: Safe Port
#################################################################
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 6667 7000
acl Safe_ports port 80            # https snews rsync
acl Safe_ports port 20 21        # http
acl Safe_ports port 70            # ftp
acl Safe_ports port 210            # gopher
acl Safe_ports port 1025-65535        # wais
acl Safe_ports port 631            # unregistered ports
acl Safe_ports port 10000        # cups
acl Safe_ports port 901            # webmin
acl Safe_ports port 280            # SWAT
acl Safe_ports port 488            # http-mgmt
acl Safe_ports port 591            # gss-http
acl Safe_ports port 777            # multiling http
acl Safe_ports port 873            # rsync
acl Safe_ports port 110            # POP3
acl Safe_ports port 25            # SMTP
acl Safe_ports port 2095 2096        # webmail from cpanel
acl Safe_ports port 2082 2083        # cpanel

acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow localhost
http_access deny !Safe_ports !SSL_ports
http_access deny CONNECT !SSL_ports !Safe_ports

#################################################################
# Refresh Pattern
#################################################################
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440

refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|mpg|swf|flv|x-flv)$ 43200 90% 432000 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(deb|rpm|exe|ram|bin|pdf|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(zip|gz|arj|lha|lzh|tar|tgz|cab|rar)$ 10080 95% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(html|htm|css|js|php|asp|aspx|cgi) 1440 40% 40320
refresh_pattern .        0    20%    4320

#################################################################
# HIERARCHY (BYPASS CGI)
#################################################################
hierarchy_stoplist cgi-bin ? .js .jsp
acl QUERY urlpath_regex cgi-bin \? .js .jsp
no_cache deny QUERY
#################################################################

#################################################################
# ALLOWED ACCESS
#################################################################
acl jaringan src 192.168.1.0-192.168.1.20
acl server src 192.168.1.2
acl kost src 192.168.1.1 192.168.1.7 192.168.1.9 192.168.1.10 

http_access allow jaringan
http_access allow server
http_access allow kost
http_access deny all
http_reply_access allow all
icp_access allow all

#################################################################
#Pembatasan
#################################################################

delay_pools 1

delay_class 1 2
delay_parameters 1 100000/100000 10000/4096000
delay_access 1 allow kost
delay_access 1 deny jaringan

#always_direct deny all
## Sesuaikan
#################################################################
# Cache CGI & Administrative
#################################################################
cache_mgr my@mail.com
cachemgr_passwd none
visible_hostname xcodex-desktop
cache_effective_user squid
cache_effective_group squid
coredump_dir /var/spool/squid
read_timeout 15 minutes
request_timeout 5 minutes
client_lifetime 5 day
persistent_request_timeout 1 minutes
pconn_timeout 120 seconds
shutdown_lifetime 20 seconds
logfile_rotate 14
```and it works

---

### Post by andhix on 2012-03-02
SOLVED, thanks i changed my squid.conf like below
```
#==================================$
# Proxy Server Versi 2.7.Stable7
#==================================$
#################################################################
# Port
#################################################################
http_port 8080 transparent
icp_port 3130
#prefer_direct off
udp_incoming_address 0.0.0.0
udp_outgoing_address 255.255.255.255

#################################################################
# Cache & Object
#################################################################
cache_mem 8 MB
cache_swap_low 98
cache_swap_high 99
max_filedesc 8192
maximum_object_size 10 MB
minimum_object_size 0 KB
maximum_object_size_in_memory 4096 KB
ipcache_size 1024
ipcache_low 98
ipcache_high 99
fqdncache_size 1024
cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF
#################################################################
# cache_dir <type> <Directory-Name> <Space in Mbytes> <Level1> <Level2> <options>
cache_dir ufs /home/squid 9000 32 128

cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
log_ip_on_direct on
cache_store_log none
pid_filename /var/run/squid.pid
cache_swap_log /var/log/squid/swap.state
dns_nameservers 208.67.222.222 208.67.220.220
#emulate_httpd_log off
#hosts_file /etc/hosts
#half_closed_clients off
negative_ttl 5 minutes
#################################################################
# Rules: Safe Port
#################################################################
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 6667 7000
acl Safe_ports port 80            # https snews rsync
acl Safe_ports port 20 21        # http
acl Safe_ports port 70            # ftp
acl Safe_ports port 210            # gopher
acl Safe_ports port 1025-65535        # wais
acl Safe_ports port 631            # unregistered ports
acl Safe_ports port 10000        # cups
acl Safe_ports port 901            # webmin
acl Safe_ports port 280            # SWAT
acl Safe_ports port 488            # http-mgmt
acl Safe_ports port 591            # gss-http
acl Safe_ports port 777            # multiling http
acl Safe_ports port 873            # rsync
acl Safe_ports port 110            # POP3
acl Safe_ports port 25            # SMTP
acl Safe_ports port 2095 2096        # webmail from cpanel
acl Safe_ports port 2082 2083        # cpanel

acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow localhost
http_access deny !Safe_ports !SSL_ports
http_access deny CONNECT !SSL_ports !Safe_ports

#################################################################
# Refresh Pattern
#################################################################
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440

refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|mpg|swf|flv|x-flv)$ 43200  90% 432000 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(deb|rpm|exe|ram|bin|pdf|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(zip|gz|arj|lha|lzh|tar|tgz|cab|rar)$ 10080 95% 43200 override-expire ignore-no-cache ignore-private
refresh_pattern -i \.(html|htm|css|js|php|asp|aspx|cgi) 1440 40% 40320
refresh_pattern .        0    20%    4320

#################################################################
# HIERARCHY (BYPASS CGI)
#################################################################
hierarchy_stoplist cgi-bin ? .js .jsp
acl QUERY urlpath_regex cgi-bin \? .js .jsp
no_cache deny QUERY
#################################################################

#################################################################
# ALLOWED ACCESS
#################################################################
acl jaringan src 192.168.1.0-192.168.1.20
acl server src 192.168.1.2
acl kost src 192.168.1.1 192.168.1.7 192.168.1.9 192.168.1.10 

http_access allow jaringan
http_access allow server
http_access allow kost
http_access deny all
http_reply_access allow all
icp_access allow all

#################################################################
#Pembatasan
#################################################################

delay_pools 1

delay_class 1 2
delay_parameters 1 100000/100000 10000/4096000
delay_access 1 allow kost
delay_access 1 deny jaringan

#always_direct deny all
## Sesuaikan
#################################################################
# Cache CGI & Administrative
#################################################################
cache_mgr my@mail.com
cachemgr_passwd none
visible_hostname xcodex-desktop
cache_effective_user squid
cache_effective_group squid
coredump_dir /var/spool/squid
read_timeout 15 minutes
request_timeout 5 minutes
client_lifetime 5 day
persistent_request_timeout 1 minutes
pconn_timeout 120 seconds
shutdown_lifetime 20 seconds
logfile_rotate 14
```and it works

---

### Post by Iowan on 2012-03-02
Threads merged - duplicates deleted.
From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

