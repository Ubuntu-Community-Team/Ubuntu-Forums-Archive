---
title: "squid config problem - LAMP server"
date: 2006-11-05
forum: Server Platforms
---

### Post by satimis on 2006-11-05
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
dynamic IP

This is only a test.

I followed the "server guide"
[https://help.ubuntu.com/ubuntu/serverguide/C/squid.html](https://help.ubuntu.com/ubuntu/serverguide/C/squid.html)

to install and configure squid and encourtered following problem;

$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid
* Creating squid spool directory structure
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'biz_hours'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'M'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'T'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'W'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'T'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: 'F'
2006/11/05 23:52:25| aclParseIpData: Bad host/IP: '9:00-17:00'
2006/11/05 23:52:25| ACL name 'biz_hours' not defined!
FATAL: Bungled squid.conf line 1886: http_access allow biz_network biz_hours
Squid Cache (Version 2.5.STABLE12): Terminated abnormally.
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'biz_hours'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'M'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'T'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'W'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'T'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: 'F'
2006/11/05 23:52:52| aclParseIpData: Bad host/IP: '9:00-17:00'
2006/11/05 23:52:52| ACL name 'biz_hours' not defined!
FATAL: Bungled squid.conf line 1886: http_access allow biz_network biz_hours
Squid Cache (Version 2.5.STABLE12): Terminated abnormally.    [fail]

```

$ sudo cat /etc/squid/squid.conf```

# NETWORK OPTIONS
# -----------------------------------------------------------------------------

#  TAG: http_port
#       Usage:  port
#               hostname:port
#               1.2.3.4:port
#
#Default:
http_port 8888

#  TAG: no_cache
#We recommend you to use the following two lines.
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY


#Default:
# hosts_file /etc/hosts
#
hosts_file /etc/hosts

#Suggested default:
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320


# ACCESS CONTROLS
# -----------------------------------------------------------------------------

#  TAG: acl
#       Defining an Access List
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
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
acl fortytwo_network src 192.168.24.0/24
acl biz_network src 10.1.42.0/24 acl biz_hours time M T W T F 9:00-17:00

#  TAG: http_access
#
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow biz_network biz_hours
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# Deny requests to unknown ports
http_access deny !Safe_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
#
#http_access allow our_networks
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all
http_access allow fortytwo_network   # added


# TAT: http_reply_acess

#Recommended minimum configuration:
#
# Insert your own rules here.
#
# and finally allow by default
http_reply_access allow all

#  TAG: unique_hostname
#
#Default:
# none
visible_hostname weezie


#  TAG: coredump_dir
#
#Default:
# coredump_dir none
#
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

```

Please advise how to fix this problem.  TIA


B.R.
satimis

---

### Post by sgenchev on 2006-11-05
The line below should actually be 2 lines
acl network src 10.1.42.0/24 acl biz_hours time M T W T F 9:00-17:00
 Change to
acl biz_network src 10.1.42.0/24 
acl biz_hours time M T W T F 9:00-17:00

---

### Post by satimis on 2006-11-05
Hi sgenchev,

Tks for your advice.  I got my problem fixed already

> The line below should actually be 2 lines
acl network src 10.1.42.0/24 acl biz_hours time M T W T F 9:00-17:00
 Change to
acl biz_network src 10.1.42.0/24 
acl biz_hours time M T W T F 9:00-17:00
Yes, you are right.  I made a typo previously.

Tks again.


B.R.
satimis

---

