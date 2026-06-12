---
title: "forwarders address"
date: 2008-03-20
forum: Server Platforms
---

### Post by fnkhan on 2008-03-20
what is forworders address in dns
I m using command line and very confuse
i want to configure local dns
using sudo vi /etc/bind/named.conf.options
Is forworder is my system IP
for creating only local domain
PLZ guid me

---

### Post by pana.corbului on 2008-03-20
Hi. The forwarders option in ISC's bind is a option statement that means: If local dns can't find example.com domain it should ask the following servers [servers that are mentioned in forwarders { 192.168.0.1; 192.168.0.2 ; };

If no forwarder is specified bind will use the root hints [root DNS servers] that are built-in; 
There's a good ideea to use this option and add your ISP DNS as forwarder ;)

---

### Post by koenn on 2008-03-20
> **pana.corbului said:**
> 
If no forwarder is specified bind will use the root hints [root DNS servers] that are built-in; 
There's a good ideea to use this option and add your ISP DNS as forwarder ;)
... or a free name service such as OpenDNS
(servers : 208.67.222.222 , 208.67.220.220 )

---

