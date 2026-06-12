---
title: "Squid Proxy Server"
date: 2009-05-05
forum: Server Platforms
---

### Post by AndyXS on 2009-05-05
As part of my office server I setup the easiest part first, squid. The server seems to work fine but before I move on to the next part (samba), I would like for you to double check my conf file to make sure I haven't missed anything.

The "restricted-sites.squid" just contains a list of blacklisted domains names, somewhere in the range of 133,333.

```

# Squid port
http_port 8555

# disable icp
icp_port 0

# some acls
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

# Recommended minimum configuration:
acl all src all
acl localhost src 127.0.0.1/255.255.255.0
acl localnet src 192.168.1.0/24
acl SSL_ports port 443
acl Safe_ports port 80                # http
#acl Safe_ports port 21                # ftp
#acl Safe_ports port 443 563           # https, snews
#acl Safe_ports port 70                # gopher
#acl Safe_ports port 210               # wais
#acl Safe_ports port 1025-65535        # unregistered ports
#acl Safe_ports port 280               # http-mgmt
#acl Safe_ports port 488               # gss-http
#acl Safe_ports port 591               # filemaker
#acl Safe_ports port 631               # cups
#acl Safe_ports port 777               # multiling http
#acl Safe_ports port 901               # SWAT
acl purge method PURGE
acl CONNECT method CONNECT


# Deny requests to unknown ports
http_access deny !Safe_ports

# Deny websites
acl blocksites dstdomain "/etc/squid/restricted-sites.squid"
http_access deny blocksites

# my own rules
http_access allow localhost
http_access allow localnet

```

---

### Post by Dr Small on 2009-05-05
Looks fine to me.

---

