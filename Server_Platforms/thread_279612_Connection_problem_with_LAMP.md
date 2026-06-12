---
title: "Connection problem with LAMP"
date: 2006-10-18
forum: Server Platforms
---

### Post by joe343 on 2006-10-18
Setting: Ubuntu 6.06, Apache2, Mysql 5, Php 5, D-Link DI624+ Router, no-ip.com account, Configured on port 8081 because my ISP block the port 80, High speed internet connection (cable modem).

Hi, here's my problem:

When I'm accessing my webserver directly from my Ubuntu box, everything is fine.

When I'm accessing from outside, the connection is very unstable:
-It may takes 5 or 6 page reload for the server to respond.
-Once it has responded, it is fast and working perfectly but all of the sudden, it may drops the connection for couples of minutes (server unavailable)
-After couples of minutes and a lot of reloads, it starts to respond again.

And that weather I access my server using directly with my IP or my no-ip.com alias ([alias].no-ip.org)


Maybe it's related with Ubuntu because I'm also having connection problems when I'm downloading a large system update (+ 50mb), the update manager seems to loose it's connection after a certain time unless I keep it active my manually visiting websites in Firefox.  Same thing when I'm downloading large files using Firefox or wget: if I don't keep my connection "alive" by surfing the web, the connection speed gets lower and lower until it completly stops.  This does not happen with azureus though. 

What's the problem ???
Thanks.

---

### Post by joe343 on 2006-10-23
Hi,

Could anyone give my some things to try out... I tried upgrading my router firmware to the latest version and I even replaced my network card. Now my download problems seems to be gone but I'm still reveiving a lot of "Server unavailable" when I'm accessing my website from outside my local network.

Any ideas ?

---

### Post by NewbieNik on 2006-10-23
Had a similar issue last year when ISP shared my IP address with another user by accident.
The fact its a cable-modem negates the on-demand connectionusually associated with ADSL, but you say you need to keep the connection active which sounds like your ISP or cable-modem is disconnecting.
Try running a ping command to a reputable site (Microsoft.com is a fun one) to see if the connection is actually stable or not, if so log into your cable modems web-inerface to see if there are any connection issues (Your ISP should be able to help)
Also check your "fair-usage policy" (Big brother policy more like) to see if they restrict your connection at peak times.

---

### Post by joe343 on 2006-10-23
I've contacted my ISP and they told me that everything is fine with my connection.  I'm getting "Server unvailable" message all the time when I'm accessing my webserver from outside my local network but never when I'm on [http://localhost](http://localhost)... 

What could it be ?

---

### Post by vivi4427 on 2006-11-01
I am using dial-up and I observed similar problem. I can browse the web alright using FF. However when downloading some bigger files (including updates) the connections (to that specific server only) seems to gradually slow down until it completely dies. For example I cant download FF2 - the download "dies" at around 200kb. I have dual boot system and the same dial-up on W2k works fine. Any help would be appreciated.

---

