---
title: "PPTP vpn server Internet access problem"
date: 2009-05-21
forum: Server Platforms
---

### Post by heffebaycay on 2009-05-21
Hello everyone.

I've recently set up a VPN server using poptop and I have some problem when I try to access the Internet from a remote computer through the VPN.

The client (Windows XP fully updated) is able to connect the VPN server and ping any local IP address. However, browsing the Internet with this connection on is really slow, so slow that sometimes pages don't even load. If I try to ping any address the first three pings will time out while the last ping will go through.

Here's my /etc/pptpd.conf file : 

> 
option /etc/ppp/pptpd-options
logwtmp
listen 91.121.101.195
localip 192.168.0.9
remoteip 192.168.0.10-14 And the /etc/ppp/pptpd-options file : 
> name *
debug debug
logfd 2
lock
mtu 1450
mru 1450
proxyarp
auth
ipcp-accept-local
ipcp-accept-remote
lcp-echo-failure 3
lcp-echo-interval 5
deflate 0
require-mschap-v2
require-mppe-128Thanks in advance for your help.

---

### Post by jcmtnez on 2011-01-27
I noticed that this is an old post but for those who landed here, I've posted an explanation and a solution to the issue of slow internet connection after connecting to a PPTP VPN network on [http://ubuntuforums.org/showthread.php?p=10402574#post10402574]("http://ubuntuforums.org/showthread.php?p=10402574#post10402574")

---

