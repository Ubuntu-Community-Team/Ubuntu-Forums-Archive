---
title: "Tunnnel IPSEC"
date: 2016-01-18
forum: Server Platforms
---

### Post by marco.bonfante on 2016-01-18
Hi all guys i have this problem with IPSEC tunnel.


I had configured a IPSEC tunnel site to site between Ubuntu Server(14.04) and a Mikrotik Router,  the issue is:

The tunnel is ok is up, there's some configuration:

Ubuntu Server:
IP:192.168.1.11
GW:192.168.1.1

Mikrotik:
IP:192.168.5.0
GW192.168.5.254


From the ubuntu server i can ping all host on the right subnet(192.168.1.xxx-->192.168.5.xxx is ok), but the users are connected from the mikrotik can ping only the server not all host on subnet

In the server there aren't enableb firewall(ufw disable,iptables --flush) 

this is mine ipsec.conf
```
# Add connections here
config setup
 nat_traversal=yes
 protostack=netkey
 force_keepalive=yes
 keep_alive=60
 oe=off
 nhelpers=0


conn Grant
#left=10.100.10.10
 left=192.168.1.11
 leftsubnets=192.168.1.0/16
 leftid=xxx.xxx.xxx.70
 leftsourceip=192.168.1.11
 right=xxx.xxx.xxx.138
 rightsubnets=192.168.5.0/24
 rightid=xxx.xxx.xxx.138
 pfs=no
 forceencaps=yes
 authby=secret
 auto=start
```

i hope somebady could help me.

thanks Marco

---

