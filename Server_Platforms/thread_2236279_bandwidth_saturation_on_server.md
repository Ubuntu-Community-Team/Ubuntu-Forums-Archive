---
title: "bandwidth saturation on server"
date: 2014-07-25
forum: Server Platforms
---

### Post by teaker1s-gmail on 2014-07-25
my server is saturating connection so i have QOS in router, what I would like is to give website bandwidth over downloads and control file flow through webmin or gui utility.


please can someone point me to information to do this as download's from my site currently negatively impact whole server bandwidth

thanks

---

### Post by teaker1s on 2014-07-25
seeing as I talk to myself on these forums:rolleyes:
[http://netactview.sourceforge.net/](http://netactview.sourceforge.net/)
nload
iftop
so far

---

### Post by TheFu on 2014-07-26
My router controls bandwidth nicely (VoIP gets priority), so I've never worried about making 20 servers manager their own.  

I have read that iptables is the way to control it, however. Never used it myself.  Searches point to Wondershaper scripts as the easiest answer.

---

### Post by sandyd on 2014-07-26
> **TheFu said:**
> My router controls bandwidth nicely (VoIP gets priority), so I've never worried about making 20 servers manager their own.  

I have read that iptables is the way to control it, however. Never used it myself.  Searches point to Wondershaper scripts as the easiest answer.

Wondershaper mainly controls down/upload speed so that the latency of the network does not skyrocket when its saturated - but it wont tell the difference between downloads and html.

I would recommend hosting the downloads elsewhere such as on dropbox where it will not affect your server.

---

### Post by elico on 2014-07-28
There are apache plugins which does exactly that and you can select different rates for lan and wan connections.
[http://packages.ubuntu.com/lucid/libapache2-mod-bw](http://packages.ubuntu.com/lucid/libapache2-mod-bw)

---

