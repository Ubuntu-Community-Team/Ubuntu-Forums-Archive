---
title: "Unable to connect to apache2 via remote IP"
date: 2007-09-19
forum: Server Platforms
---

### Post by gmbizzle on 2007-09-19
So I'm sitting here at a remote computer and I decided to check on my box at home. FTP, Telnet and Apache2 all work fine through cmd on this Windows computer. I can even telnet my.ip.he.re and get /index.php fine. When I try to view the IP via http in Firefox or IE, it won't connect. Port forwarding is on at home on my router, and I tried searching before I made this post, but I'm really baffled. I'm thinking it's probably the setting on the client computer. Any ideas?

---

### Post by gmbizzle on 2007-09-19
Ok. Disregard being able to telnet in and GET /index.php Looks like with all my cmd's open, I telneted through my shell instead of a windows telnet. I'll probably just check my apache2.conf and change some stuff. I also tried connecting through a website proxy, and that was a no go. Only computer I was able to connect remotely from was a computer on my home lan.

---

### Post by HermanAB on 2007-09-20
Many ISPs block certain ports to discourage people from running servers at home, unless you pay them more money for a server account.  You will likely find that ports 21, 25 and 80 are dropped by the ISP.  The workaround is to use a different port, like 2121, 2525 and 8080, then use a URL like: [http://www.mydomain.com:8080](http://www.mydomain.com:8080)

Cheers,

H.

---

### Post by gmbizzle on 2007-09-20
Yeah..I was thinking that maybe the ISP blocked it, but I'm not too sure about that. They definitely didn't block port 21, as I was able to port forward that to my 192.168.1.3:21 from the router and access it remotely. I went ahead and forwarded it to 8080 instead of 80, and am using no-ip.com so nobody has to type in my.ip.here:8080 just to access the site.
Still wondering if there's something I can do to make port 80 work, but it doesn't look like it. It's a netgear router, by the way.

---

