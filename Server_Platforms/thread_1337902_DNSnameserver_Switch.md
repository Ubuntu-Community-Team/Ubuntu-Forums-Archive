---
title: "DNS/nameserver Switch"
date: 2009-11-25
forum: Server Platforms
---

### Post by hankinator on 2009-11-25
I like to think I'm not an extreme noob when it comes to domains and things of that nature. 

I'm currently switching domains and name-servers from a old centOS box to a new ubuntu (9.04) box. On where I bought the domains from I switched [http://ubuntuforums.org/newthread.php?do=newthread&f=339the](http://ubuntuforums.org/newthread.php?do=newthread&f=339the) name-server settings too ns3.domain.com and ns4.domain.com as my new domains. My old domains were ns1.domain.com and ns2.domain.com. I checked the records and everything seems to be syntax correct, which is good.

For a quick fix, I just have the old serve running the domains and they are being forwarded to the new box. I also have the new box running the domains with the new name-server records. (ns3,ns4). Its been over 72+ hours and they are not switching over. Any idea what the problem is? Each of the domains are being forwarded to their own name-server(running on the same box). would that be the problem or would what be?

---

### Post by Vegan on 2009-11-26
I am assuming you are using BIND9 as the DNS daemon.  If you old machine is setup to be a primary server, make the new machine a secondary one.

Make sure you also copy all of the A records over to the new machine too.

This also applies to any MX records too.

---

### Post by hankinator on 2009-12-02
Yeah, I did all that. The problem is I needed a domain for the server so I could link it with a name-server and have all the sites forwarding to that domain(name server).

---

