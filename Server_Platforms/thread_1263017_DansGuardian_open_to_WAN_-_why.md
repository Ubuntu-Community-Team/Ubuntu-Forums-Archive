---
title: "DansGuardian open to WAN - why?"
date: 2009-09-10
forum: Server Platforms
---

### Post by DaiLaughing on 2009-09-10
I've set up DansGuardian and Squid to provide filtered Web access for my household.  That works very well.  the problem is that looking at the log I get accesses from the Internet.  I assume the second line here is an external system successfully getting a page from my system:

2009.9.10 19:41:24 - 192.168.1.19 [http://sup.live.com/whatsnew/whatsnewservice.asmx](http://sup.live.com/whatsnew/whatsnewservice.asmx) *DENIED* Weighted phrase limit of 100 : 158 ((blonde,  xxx )+ girl + xxx +$
2009.9.10 19:42:09 - 222.208.183.218 [http://proxyjudge2.proxyfire.net/fastenv](http://proxyjudge2.proxyfire.net/fastenv)  GET 531 -15  1 200 text/html   -

I can work most stuff out on Ubuntu in the end but this one has taken hours on three occasions and I just don't get it.  Surely no one from outside should be able to get at my proxy as a client?

Any pointers appreciated.

---

### Post by jondkent on 2009-09-10
What are you firewall (iptables) rules?

---

### Post by DaiLaughing on 2009-09-10
Unchanged at:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

which seems wrong as I remember setting rules but not how.

---

### Post by jondkent on 2009-09-10
That does seems a tad open.

If you are not that up to speed with iptables it might be worth you looking at UFW ([https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)) as a means to build you firewall rules.

I'm pretty sure that this is the problem, though I haven't got access to my dansguardian box where I am at the moment to confirm.

It might be worth reading reading this, [http://www.linuxjournal.com/article/10407](http://www.linuxjournal.com/article/10407), which is a series of articles from Linux Journal's security guru about setting up exactly what you have done and how.  Missing some details, but will point you in the right direction.

Cheers,

Jon

---

### Post by DaiLaughing on 2009-09-11
Thanks.  Today's a full day but I'll work on that asap.

---

### Post by DaiLaughing on 2009-09-12
I'm still not getting this straight in my head (and may never).  Does this allow tcp access to the box as a web server (needed because I use it to test PHP pages) but block access to the proxy which is only used for my local network?  The final rule then opens the route to the proxy just for local addresses.

Status: active

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
Anywhere                   DENY    8080/tcp
Anywhere                   ALLOW   192.168.0.0/24 8080/tcp

Edit: that blocked the proxy access so I changed it to this:

To                         Action  From
--                         ------  ----
22                         ALLOW   Anywhere
80                         ALLOW   Anywhere
Anywhere                   ALLOW   192.168.0.0/24

---

### Post by jondkent on 2009-09-12
For firewalling you need to deny all and then allow the connections you want.

Therefore for internal network you want to allow access to 22/80/whatever else you need for ingress and egress, and the external connection need ingress access denied unless you initiated the connection (iptables knows how to do that).

You could make your life easy and just allow all connections made from your internal network through, without over complex rules.  All you care about I think is that no external connections use you proxy here, or indeed any connection through.  This should make the UFW setup easier.

---

### Post by DaiLaughing on 2009-09-13
That seems not to be the case with UFW.  It seems to add the DENY all rule automatically.  With the three above rules if I delete the one which allows port 80 the web server is inaccessible so the firewall must be blocking it.

Those three are definitely allowing what I want but I am not sure if the proxy is not available from the Web and I don't know how to test that.  All I know is that there has been no access in 24 hours

---

### Post by jondkent on 2009-09-13
Hi,

Use [http://canyouseeme.org/](http://canyouseeme.org/) to test what can be accessed remotely. This'll give you a good idea whats open still and also give you, hopefully, a comfort should all look good.

Regard,

Jon

---

### Post by jondkent on 2009-09-13
After a little digging found this, [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo), which maybe more helpful to you than the higher level UFW, assuming my previous suggestion still shows up problems

Jon

---

### Post by DaiLaughing on 2009-09-13
Nope, you did it.  Thanks for the help the proxy is not seen by that very useful site.

---

### Post by jondkent on 2009-09-14
Hi,

No probs, enjoyed it :)

Jon

---

