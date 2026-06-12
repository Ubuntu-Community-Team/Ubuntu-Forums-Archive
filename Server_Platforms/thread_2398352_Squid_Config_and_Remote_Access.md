---
title: "Squid Config and Remote Access"
date: 2018-08-10
forum: Server Platforms
---

### Post by ptmuldoon on 2018-08-10
I'm struggling with getting Remote Access to my Squid Server working, and unsure if I have my config file setup correctly or not.

I created a username and password but have also tried without it without success.  I also have dyndns address and have my router currently portforwarding to the machine that Squid is running on.  My router also uses IP addresses of 192.168.11.XX and I can connect to the Squid Proxy server within the home.

From various searches this is what my current config looks like, yet I can't get seemed to connect to it remotely.   Can anyone possibly point out where I may be going wrong?

```

#Recommended minimum configuration:

auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwd
auth_param basic children 5
auth_param basic credentialsttl 1 minute
auth_param basic casesensitive off

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.11.0/255.255.255.0
acl SSL_ports port 443
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

acl myhost srcdomain mydynaddresshere
http_access allow myhost


acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports

http_access deny to_localhost
icp_access deny all
htcp_access deny all

http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid


#Suggested default:
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern .               0       20%     4320

# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

# Allow all machines to all sites
http_access allow all

```

---

### Post by SeijiSensei on 2018-08-10
What do you mean by "remote access?" To connect to remote servers use SSH.

To access Squid from a browser you need to configure it to use a proxy.

Are you saying you can't see the proxy server from outside the network? As a test, open a terminal then type

```
telnet server_ip 3128
```

assuming you're using the default Squid port. What happens?

Plus there's this:

```
acl myhost srcdomain mydynaddresshere
http_access allow myhost

```

If myhost is a single machine, all other connections might be denied. You need a CIDR subnet address

```

acl mynetwork src 192.168.11.0/24
http_access allow mynetwork

```

Squid cannot see the router's outside address. Packets arriving on the Squid server are coming from the router's LAN-facing port with an address in 192.168.11.0/24.

Also you have two http_access directives. Just use one.

---

