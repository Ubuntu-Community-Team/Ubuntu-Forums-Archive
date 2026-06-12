---
title: "Ubuntu Server, Webmin, DNS issues everything else works"
date: 2009-07-04
forum: Server Platforms
---

### Post by xleoo on 2009-07-04
Hello,

I just want to start by saying I am kind of new to linux, although I have been lurking around for a long while and messing with stuff here and there. I really enjoy reading the support here at the forums and the community.

Having said that, after searching for a long while I still cannot find an answer to my problem.

To make things easier, lets define the addresses and ip in use:

a) domain name **[www.xleo.com](www.xleo.com)** )
a1) moniker handles my domain registration, I have pointed the nameservers to my WHM webhosting account)
a2) under the A records in whm, I have pointed [www.xleo.com](www.xleo.com) to my static ip address from cable company (60.60.60.60) (MY WAN IP)


B)  nameservers at whm = **ns1.ns.com** ip of NS= **74.74.74.74**)
C) WAN remote static ip = **60.60.60.60**)
D) UBUNTU SERVER resides on **192.168.0.183**


If I visit [http://xleo.com](http://xleo.com) or [http://60.60.60.60](http://60.60.60.60) or [https://192.168.0.183:10000](https://192.168.0.183:10000) (WEBMIN)

They all work.

But if I visit from a remote site, outside my local network, I cannot access xleo.com or my static ip.

When I do a dns check on xleo.com I get:
@ checkdns.net
Error connecting to HTTP server [www.xleo.com](www.xleo.com) [60.60.60.60] port 80 : timed out waiting for connection
(this tells me, the DNS have the correct entries, but it cannot access it) 

Port forwarding is enabled, and I have previously tested xaamp on my mac and it worked so port 80 is not blocked from my isp, and port forwarding works.




So bottom line, I have installed ubuntu server and webmin, to act as a webserver. And it works perfectly on my local network. I can also access webmin from browers on other computers on my network.

But cannot access it remotly, when I try to change the DNS entries in webmin, they always change back to the localhost settings.
So I cannot find where or how I can change the dns entries to say:

search xleo.com
nameservers ns1.ns.com or 74.74.74.74

if I change it manually in the config file @ sudo vi /etc/resolv.con, it always changes back to my localhost settings.


I would really appreciate any help regarding this issue.

xleoo

(btw the ip address I have wrote are not the actual addresses its just to make things easier)

---

### Post by windependence on 2009-07-04
Go to canyouseeme.org from your server, and check port 80 to see if it's being blocked. Let me know the outcome.

-Tim

---

### Post by xleoo on 2009-07-04
its a good thing you asked. I am not sure why i was under the impression that it was working before. 

I tried xammp and mamp on mac os x again, and lamp on ubuntu desktop (not server) port 80 seems blocked. other ports do work though.

I guess now, i have to set it apache on another port which I am not sure how to do on ubuntu server.

Also, is there a way to use mod rewrite to take out the port number at the end?

---

### Post by xleoo on 2009-07-04
Update:

I configured apache to run on port 7678

and 

can you see me says

Success: I can see your service on xx.xx.xx.xx on port (7678)
Your ISP is not blocking port 7678

New update:

I used one of these anonymous web browsing tools, to check on my domain:7678

and it works... now only thing is how to deal with the using mod rewrite or web redirect to remove port 7678

---

