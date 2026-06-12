---
title: "About 443 block in firewall"
date: 2019-04-19
forum: Server Platforms
---

### Post by secooonder on 2019-04-19
Hello
i installed squid and iptable and bind dns server on ubuntu 16.04  lts firewall,i have a 200 client.
i am blocked port 80 very nice from squid.
But i can not block 443 port properly in squid .Different web browser created problem.Ssl certificates vb...
Some web pages have a lot of ip addreses.i have to write a lot of ip address in iptables.

i am thinking blocking in bind dns server.
For example,  i will return the 127.0.0.1 response to a client who is querying facebook.
but i have to create  a lot of thousands zone file.

Shortly; How can i best do 443 port blocking
Thank you very much for your help

---

### Post by darkod on 2019-04-19
You want to block all traffic to 443 or just directed to specific websites?

If you want to block all traffic to 443 you can easily do that in any firewall.

Blocking only specific websites will be much more complicated.

---

### Post by secooonder on 2019-04-19
Darkod thank you.
I want to block only spesific url by used 443 port

---

### Post by TheFu on 2019-04-20
If you want to block by IP and URL, there is a project called pi-hole which makes this easy. It doesn&#8217;t use squid, but does it at the DNS layer using blocklists that you can select from online sources.

Not sure if this is something you can really control, but it is a best practice not to allow external DNS to any desktops, only to the proxy server that the desktops use.

Anyways, it is a different option.

---

### Post by secooonder on 2019-04-26
TheFu thank you.
i will search pi-hole project.
i created a lot of zone for blocking.For example i want to block facebook.com.
i created new zone file.
> 
$TTL 3W
@          IN    SOA      **facebook.com.**   hostmaster.abcde.com. (
                                              20190422 ;  Serial
                                                 12H       ;  Refresh
                                                  2H        ;  Retry
                                                  5W       ;  Expire
                                                  1D  )

@        IN     NS        a.abcde.com.tr.
@        IN     NS        b.abcde.com.tr.

www      IN      A          127.0.0.1



Thank you very much for your help

---

### Post by TheFu on 2019-04-26
[https://category5.tv/shows/clips_tech/episode/599-block-ads-porn-pi-hole-odroid-xu4/](https://category5.tv/shows/clips_tech/episode/599-block-ads-porn-pi-hole-odroid-xu4/) is a how-to clip using an ARM SBC for pi-hole.  There are intel versions and you can run it inside a VM.  Best not to install it on a system doing other things.

Blocking facebook means blocking 200+ domains and different subnets worldwide.  It is non-trivial.  By blocking the main 50, you can do a reasonable job of breaking all the others, it seems, but I would expect FB to work hard to get the data, by any means required.  That's their business model.

---

