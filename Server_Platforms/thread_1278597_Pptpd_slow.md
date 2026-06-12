---
title: "Pptpd slow"
date: 2009-09-29
forum: Server Platforms
---

### Post by flopdude on 2009-09-29
Hey guys,

I have installed and configured pptpd on a vps box I have bought.
All works well except speed. I have a 10MB line in the vps and a 3 MB line home.
Can get the more then 100KB from the vpn connection. :confused:

Any ideas to why?
Did any one compiled accel-pptp for ubuntu 9.04 server? 
[SIZE=1]
cat /etc/pptpd.conf:

option /etc/ppp/pptpd-options
[/SIZE]localip 174.143.174.90
remoteip 10.100.1.1-254

cat /etc/ppp/pptpd-options:

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
proxyarp
nodefaultroute
nobsdcomp

Thanks!

---

