---
title: "Home filtering proxy and Thunderbird images"
date: 2008-11-10
forum: Server Platforms
---

### Post by DaiLaughing on 2008-11-10
Apologies if this is answered elsewhere - I have searched but I don't know what terms to search for so may have missed it.  If I knew what I was looking for I wouldn't have this problem!

I have a fairly normal home system with 3 Windows PCs and an Ubuntu server which runs both Apache and Danguardian/tinyproxy.  The aim is to protect my children from what's out there until they are old enough to understand it (well some of it) and to play with web site hosting.

Internet access is through a router and ADSL with the PCs and server all wired to the router.  In theory this means that the PCs can access the 'net direct through the router but in practice I have used access control to block web and most other port use which comes from anything except the server.  I have allowed smtp/pop3 access to all systems as currently I only run a web proxy.

So the question is what do I need to have a full proxy which will also handle email?  Then I can close access on all ports except to the server.

The real reason I need this though is because Thunderbird (on the PCs) seems to have a problem.  If no proxy is set then mail is collected directly (through the router).  However, if any of the messages contain externally hosted images Thunderbird tries to access those and fails as the web ports it is trying to use are blocked.  I can change settings for it to use the proxy and then images download when messages are opened.  But of course then mail cannot download as the proxy cannot handle pop3.

Having done some reading I sort of felt SOCKS was relevant but can't work out whether it is or not and if so what package will do what I want.

I'm quite happy to work out the details myself all I really need is the name of the package and a general concept.  Of course you are quite welcome to tell me exactly what to do as well!

TIA

---

