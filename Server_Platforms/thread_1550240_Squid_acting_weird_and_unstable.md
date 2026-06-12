---
title: "Squid acting weird and unstable"
date: 2010-08-10
forum: Server Platforms
---

### Post by Blues- on 2010-08-10
I'm hoping some squid experts can help me with this one ..
I have a Karmic 64 bit server running at home acting as a home server.
The server is acting as a default gateway with 2 NIC'S and is running squid.

Four other computers are on the local LAN, which all are using the Squid as a proxy server.  3 Linux machines and one XP machine.
When the browsers on all these computers are set to connect through the proxy server (I'm using wpad.dat for automatic proxy discovery on the lan)
The browsers often hang, and the browsing experience can sometimes be horrible slow.  Especially on the Linux machines running Firefox.

And it keeps getting worse .. when the machine has been up for 7-14 days it seems like the Squid starts to timeout and drop connections, when that starts to happen the only way to fix the issue is to restart Squid.

My server runs on rather good hardware so I suspect this is just a misconfiguration in my squid.conf
The machine specs are the following ..
Ubuntu Karmic 64 bit, headless server
Intel Q6600 @ 2400Ghz, 8 GIG of RAM, and the OS disk is running
on a 3Ware hardware raid controller using RAID1 via 2 500gb SATA2 discs.
Total disc space on the machine is 8TB so the cache size could be increased I suppose.

Here below is my squid config file .. please point out to me what could be better tuned in the config file.

```

acl all src 0.0.0.0/0.0.0.0
acl internal_network src 10.0.10.0/24
acl vpn_network src 10.0.20.0/24

acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8

acl SSL_ports port 443 563 # https, snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
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

http_access allow manager localhost
http_access allow internal_network
http_access allow vpn_network
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all

#Allow ICP queries from local networks only
icp_access allow internal_network
icp_access deny all

visible_hostname proxy.mydomain.com
cache_mgr me@mydomain.com
forwarded_for off
http_port 10.0.10.1:3128 transparent

access_log /var/log/squid/access.log squid

cache_dir ufs /var/spool/squid 1024 16 256
hosts_file /etc/hosts
coredump_dir /var/spool/squid
cache_mem 1024 MB
cache_swap_low 94
cache_swap_high 96
maximum_object_size 16384 KB
minimum_object_size 4 KB
maximum_object_size_in_memory 2048 KB
fqdncache_size 1024

acl snmppublic snmp_community public
snmp_port 3401
snmp_access allow snmppublic all


```

Thanks in advance, 
Blues-

---

