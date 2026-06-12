---
title: "Internal DNS"
date: 2009-05-15
forum: Server Platforms
---

### Post by mregister on 2009-05-15
Question and this maybe a router issue. I can't resolve my website by name internally. I can bring up the site with the ip address but not with the domain name. I do not have an interanl DNS server and my router will not do hairpin truns. What I have done to patch this is use host files on the local PC's but I would like to have it reslove. Should I setup an internal DNS server or just stick with the host files? If I setup an interanl DNS does anyone have a good tutorial on this?

Thanks to all in advance,

Mark

---

### Post by drave on 2009-05-15
guess it depends on howmany hosts file you have to update, and how much of a pain the *** you consider that to be.

dns servers are implemented by "bind" so googling for "bind tutorial" will tell you all you need. really straight forward.

i had the same problem when the server is internal and reached using NAT port forwarding. trying to reach the server with the external IP from inside never worked

---

### Post by zeefreak on 2010-03-29
i know this is an old thread, but my .02 . . .

i think this is a router issue. the reason i say this is that i have a linksys wrt54g. for years i always had to get to my web server via the internal ip as the domain name would not work from inside my network. i flashed the firmware over to tomato a few years ago, and viola, i can get to my web server using my domain name.

---

### Post by capscrew on 2010-03-29
> **zeefreak said:**
> i know this is an old thread, but my .02 . . .

i think this is a router issue. the reason i say this is that i have a linksys wrt54g. for years i always had to get to my web server via the internal ip as the domain name would not work from inside my network. i flashed the firmware over to tomato a few years ago, and viola, i can get to my web server using my domain name.

It is a security issue.  Most routers will not let an internal address be used as a origin of a TCP/IP conversation enter the WAN side interface.  This would be an unusual situation. Imagine having a compromised host on your LAN and you can see the potential for problems.

---

### Post by zeefreak on 2010-03-30
yes, no router allows that, assuming you're using a non routable ip block, which most people do these days . . .

the issue here is that lets say i own the domain foo.net. it runs form a webserver at my house, as does the dns. the problem is that while the entire world can get to foo.net by typing it in their browser, from inside the network, foo.net fails to resolve, and you can't get to it via its dns name. connecting directly to the internal non routable ip, of course works fine. but it means that in putty on your laptop you have to have two profiles, one for foo.net for when you're travelling, and another for 192.168.1.xxx for when you're at home. its annoying, and as i said in my previous post, magically resolved itself when i flashed a wrt54g from the default firmware to tomato, hence my assumption that it was the router that was causing the issue.

---

### Post by capscrew on 2010-03-30
> **zeefreak said:**
> yes, no router allows that, assuming you're using a non routable ip block, which most people do these days . . .

the issue here is that lets say i own the domain foo.net. it runs form a webserver at my house, as does the dns. 
other users are directed to foo.net from the root dns server for .net. > 
the problem is that while the entire world can get to foo.net by typing it in their browser, from inside the network, foo.net fails to resolve,
I believe it does resolve to your WAN side IP address.  Your router should not accept traffic that has an origin and destination that is the same (e.g. your WAN IP address).> 
 and you can't get to it via its dns name. 
connecting directly to the internal non routable ip, of course works fine. but it means that in putty on your laptop you have to have two profiles, one for foo.net for when you're travelling, and another for 192.168.1.xxx for when you're at home. its annoying, and as i said in my previous post, magically resolved itself when i flashed a wrt54g from the default firmware to tomato, hence my assumption that it was the router that was causing the issue.

NAT has always had nasty side effects.  Sometimes misconfiguration is okay.  If it works for you, great.

---

### Post by Ryan Dwyer on 2010-03-30
You could run a local-only DNS server which resolves it to the private address.

---

### Post by Iowan on 2010-03-31
I'm fond of DNSMasq, but...
OP hasn't been around for almost a year - is this thread dead?

---

