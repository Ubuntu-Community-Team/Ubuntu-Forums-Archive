---
title: "ubuntu firewall ufw port nat 80 to www server - log ip addresses=ip of firewall"
date: 2013-05-20
forum: Server Platforms
---

### Post by tellme on 2013-05-20
Hello to all,

i have an gateway\firewall ufw server conncted to the internet with ip: 85.17.60.xxx on eth0
On the same gateway\firewall server i have a virtual network adatpter for the inside network 192.168.1.254 on eth2

In the internal network i have a webserver running 192.168.1.123

i have put the following rule in my ufw:
# HTTP 80
-A PREROUTING -p tcp -i eth0 -d 85.17.60.xxx --dport 80 -j DNAT --to-destination 192.168.1.123

When connecting from the internet to my webpage from ip 195.241.244.263 the log on my webserver only logs ipaddress 192.168.1.254 instead of  195.241.244.263

see picture: 
see access.log apache2:

192.168.1.254 - - [20/May/2013:22:17:36 +0200] "GET /beveiliging/img/admin/up.gif HTTP/1.1" 200 55 "http://homeg.nl/beveiliging/adminpanel/index.php?tab=AdminCatalog&token=61b45b76bfa96d5116a6a0f844d1e2a7" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; InfoPath.3; .NET4.0C; .NET4.0E; SlimBrowser/7.00.024)"
192.168.1.254 - - [20/May/2013:22:17:36 +0200] "GET /beveiliging/img/admin/up_d.gif HTTP/1.1" 200 55 "http://homeg.nl/beveiliging/adminpanel/index.php?tab=AdminCatalog&token=61b45b76bfa96d5116a6a0f844d1e2a7" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; InfoPath.3; .NET4.0C; .NET4.0E; SlimBrowser/7.00.024)"
192.168.1.254 - - [20/May/2013:22:17:36 +0200] "GET /beveiliging/img/admin/details.gif HTTP/1.1" 200 954 "http://homeg.nl/beveiliging/adminpanel/index.php?tab=AdminCatalog&token=61b45b76bfa96d5116a6a0f844d1e2a7" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; InfoPath.3; .NET4.0C; .NET4.0E; SlimBrowser/7.00.024)"
Any idea how i can log the internet ip of the visitor to my website, what should i have to configure on the gateway\firewall ufw server ?

---

