---
title: "Censoring web content via proxy"
date: 2008-04-09
forum: Security Discussions
---

### Post by evillawngnome on 2008-04-09
Hi all,

Been a long time since i've posted here. :D

Basically, what i'd like to do is have the computers on my lan accessing the web via a proxy, and i'd like this proxy to do arbitraty substitutions in web content. For example, any time the word "crap" comes up, i'd like to subsitute it with "stuff". I see a lot of pages using squid proxy and dansguardian to dny access to pages that contain "crap", but i've yet to find anything about turning "crap" to "junk" or "****".

Does anyone have experience with this? I don't need a step by step, just a point in the right direction - an application or module name would probably get me going.

---

### Post by stmurray on 2008-04-09
Privoxy ([www.privoxy.org](www.privoxy.org)) may help you out.  It allows you to change outgoing http requests to omit data and help ensure privacy, but I'm not sure if you can change the http response with it as well.  I just began using it with  dansguardian and it seems to work fine as a replacement to squid in the setup, but I am still exploring how to configure it.

---

### Post by evillawngnome on 2008-04-09
I'll look into that. I found this how-to:
[http://dev.riseup.net/grimoire/web-server/filtering-web-proxy/](http://dev.riseup.net/grimoire/web-server/filtering-web-proxy/)

I'm using apache to do it, and it lets me use sed, which i'm REALLY comfortable with. 

Thanks!

---

### Post by HermanAB on 2008-04-09
Squid-cache with Dansguardian is likely the best.

---

