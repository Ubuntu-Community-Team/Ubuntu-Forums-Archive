---
title: "squid proxy 2.7 stable 9 slow when open 8 facebook at same time"
date: 2011-04-22
forum: Server Platforms
---

### Post by larceforever on 2011-04-22
hello i new and new to linux too 1 month half...

everytime if more that 10-15 people using internet at same time squid proxy slow to responde everyweb just keep loading...

and here my squid proxy settings
1 nic
squid proxy 2.7 stable 9
ubuntu 64bit
intel duo core
2gb
500gb 
256MB /boot
16GB /
swap 2gb
btrfs 400gb

so how to fix this problem? 

thank

---

### Post by larceforever on 2011-04-24
ok here my config and i dun get any error on my cache.log and acess log so pls any one can tell me what i done wrong???


```
##start of config

http_port 3128 transparent

server_http11 on

icp_port 0



#=============================================================================

# TAG File Squid

#=============================================================================

pid_filename /var/run/squid.pid

coredump_dir /var/spool/squid/

error_directory /usr/share/squid/errors/en/

icon_directory /usr/share/squid/icons

mime_table /usr/share/squid/mime.conf



#=============================================================================

# TAG: Log Squid

#=============================================================================

access_log /var/log/squid/access.log

cache_log /var/log/squid/cache.log

#cache_log /dev/null

cache_store_log /dev/null



log_fqdn off

log_icp_queries off

buffered_logs off

emulate_httpd_log off



#===========================================================================

# TAG: FTP section

#===========================================================================

ftp_list_width 32

ftp_passive on

ftp_sanitycheck on



#===================================================================

# TAG: ACL Section

#===================================================================

acl localnet src 10.0.0.0/8     # RFC1918 possible internal network

acl localnet src 172.0.0.0/8  # RFC1918 possible internal network

acl localnet src 192.168.0.0/16 # RFC1918 possible internal network



uri_whitespace strip



#DNS NAMESERVER

dns_nameservers 127.0.0.1




cache_mem 256 MB

maximum_object_size_in_memory 32 KB

memory_replacement_policy heap GDSF

cache_replacement_policy heap LFUDA



cache_dir aufs /cache 35000 84 256



minimum_object_size 0 bytes

maximum_object_size 32 MB

offline_mode off

cache_swap_low 98

cache_swap_high 99





```

---

