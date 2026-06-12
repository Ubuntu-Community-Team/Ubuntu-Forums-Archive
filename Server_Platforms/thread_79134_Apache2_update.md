---
title: "Apache2 update"
date: 2005-10-19
forum: Server Platforms
---

### Post by theQmaster on 2005-10-19
Hi,

Took me a while to decide to write about it. 

I have this domain that is hosted behind a router and was working very nice till two weeks ago when I decided to update to Apache 2.0.53.

I run Apache2 and mod_jk. Before I had apache 2.0.45.

After update it didn't stop working but it became very, very, very slow - only from outside of the intranet. Intranet calls to the server are very fast. My ISP says that I have 6Mbps dowload and at least 256Kbps upload. So the bandwidth wouldn't not be a problem.

It behaves that there is a bottleneck somewhere and all facts point to router and apache2 tandem. It's funny that if I browse intranet ip address is very fast.

What do I miss here, did my router got bad or the requests coming from my router are treated different then the ones from intranet. It shouldn't...

I have hard time testing this whole thing since only from outside I face the problem.

Anyone ? Any idea would be great!

My best,
theQmaster

---

### Post by theQmaster on 2005-10-19
This may be related to the ipv6&router&latest kernel . Here below the connection waiting( seems that they wait to revolve names)

tcp6       0      0 ::ffff:192.168.1.20:www proxy.site.com:5554   TIME_WAIT
tcp6       0   4315 ::ffff:192.168.1.20:www proxy.site.com:5712   FIN_WAIT1
tcp6       0   1728 ::ffff:192.168.1.20:www proxy.site.com:4959   FIN_WAIT1
tcp6       0   1951 ::ffff:192.168.1.20:www proxy.site.com:6248   FIN_WAIT1
tcp6       0   1625 ::ffff:192.168.1.20:www proxy.site.com:4102   FIN_WAIT1

All the calls from outside of network are coming as IPV6 while those called from local net are plain IPV4 and are working.

Anyone can tell me how to fix this ? I did turned the ipv6 off in the aliases folder by postfixing it with off but it didn't do any good.

Any hints ?
theQMaster

---

### Post by theQmaster on 2005-10-20
Okay - hope people will not have to deal with this matter...

It's not about apache2 upgrade but rather about the kernel upgrade that seems to be set ipv6 as default. It seems that once that is set all the incoming request from outside of the intranet would have the ip converted to ipv6 ffff:1.2.3.4 and   that I assume creates some issues while resolving names...

Anyone have a better explanation ? What about a solution for the feature ? Why the bottleneck when apache2 deals with ipv6 ?

My best,
theQmaster :) 
Affordable Stock Photography
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by pksings on 2005-10-20
I removed the module ipv6 from /lib/modules/2.6.12.xx/wherever.

I haven't had and IPV6 problem since.

Yes it's somewhat drastic, and probably not proper. But it works.

PK

---

### Post by theQmaster on 2005-10-20
I did use the aliasses file to disable it.

Did you have similar problems with mine ? I'm was not alone in my missery ?
So you're saying you removed the entire ipv6 module ?

Are you using ubuntu as a server ? 

There are still some issues on my side - it's still slow sometimes when connecting from the internet. Intranet lightning fast.

---

