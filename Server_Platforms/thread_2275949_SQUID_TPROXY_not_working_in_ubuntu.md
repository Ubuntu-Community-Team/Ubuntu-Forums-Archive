---
title: "SQUID TPROXY not working in ubuntu"
date: 2015-04-29
forum: Server Platforms
---

### Post by rodrigo_manrique on 2015-04-29
Hi all,

I am trying to configure SQUID in TPROXY but it doesn´t work. My environment is:

Topology with 3 docker containers(Client, Host with Squid, Server) and 1 openvswitch which connects all hosts. The traffic is sent from client to server and it passes throught the squid configured in TPROXY mode to try to do header enrichment. 

squid.conf:
#User
cache_effective_user USER
request_header_add X-Header-SF1 "SF-1a" all

# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
#acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 10.0.0.0/24
acl localnet src 10.0.1.0/24
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

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
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#

# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128
http_port 3129 tproxy

# Uncomment and adjust the following to add a disk cache directory.
#cache_dir ufs /usr/local/squid/var/cache/squid 100 16 256

# Leave coredumps in the first cache dir
coredump_dir /usr/local/squid/var/cache/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320

And the iptables are

 [FONT=Consolas, serif]ip rule add fwmark 1 lookup 100[/FONT]

      [FONT=Consolas, serif]ip route add local 0.0.0.0/0 dev lo table 100[/FONT]
      [FONT=Consolas, serif]iptables -t mangle -N DIVERT[/FONT]

      [FONT=Consolas, serif]iptables -t mangle -A PREROUTING -p tcp -m socket -j DIVERT[/FONT]

      [FONT=Consolas, serif]iptables -t mangle -A DIVERT -j MARK --set-mark 1[/FONT]

      [FONT=Consolas, serif]iptables -t mangle -A DIVERT -j ACCEPT[/FONT]

      [FONT=Consolas, serif]iptables -t mangle -m multiport -A PREROUTING -p tcp --dports 80,443,8080 -j TPROXY --on-port 3129 --tproxy-mark 0x1/0x1[/FONT]

And the system setting are


 [FONT=Consolas, serif]net.ipv4.ip_forward = 1[/FONT]

  [FONT=Consolas, serif]net.ipv4.conf.default.rp_filter = 0[/FONT]

  [FONT=Consolas, serif]net.ipv4.conf.all.rp_filter = 0[/FONT]

Other parameters are configured properly, so the enviroment is ok.


The traffic is redirected properly by the switch, but the TPROXY send NOTHING to the server. I see the message:

root@94370aed9db9:/# wget -O - 10.0.1.2
--2015-04-29 14:04:40--  [http://10.0.1.2/](http://10.0.1.2/)
Connecting to 10.0.1.2:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

Do you have any idea?

Thanks in advance,
R.

---

