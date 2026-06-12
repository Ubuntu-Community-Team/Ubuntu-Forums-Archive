---
title: "l2tp over ipsec, kernel crash?"
date: 2012-04-16
forum: Server Platforms
---

### Post by lesca on 2012-04-16
Hello,

I have been tested this for several days, but what I am sure is there must be a bug.

1. Environment:
Ubuntu 11.04 Server + Linux Kernel 3.0.0-12-generic-pae + OpenSwan 2.6.28 + xl2tpd-1.2.8

Event:
When Win7 or iPhone try to connect to server over L2TP, the server fails. What I got is like this:
[IMG]http://lesca.me/blog/wp-content/uploads/2012/04/crash.jpg[/IMG]

2. ipsec.conf (almost the same like /etc/ipsec.d/examples/l2tp-psk.conf )
```

config setup
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:!192.168.1.0/24,%v4:!192.168.0.0/24
    oe=off
    protostack=netkey

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    ikelifetime=8h
    keylife=1h
    type=transport
    left=192.168.1.120
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    dpddelay=30
    dpdtimeout=120
    dpdaction=clear

```

3. /etc/xl2tpd/xl2tpd.conf
```

[global]
ipsec saref = no

[lns default]
local ip = 10.10.20.1
ip range = 10.10.20.100-10.10.20.254
require chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```

4. /etc/ppp/options.xl2tpd
```

refuse-mschap-v2
refuse-mschap
ms-dns 8.8.8.8
asyncmap 0
auth
lock
hide-password
local
#debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4

```

---

