---
title: "Firefox Tor and FoxyProxy"
date: 2008-06-07
forum: Security
---

### Post by perito on 2008-06-07
I have installed FoxyProxy with Tor but I do not understand the whitelist and blacklist.... URLs on the whitelist get passed to Tor (and my IP is hidden from them) while the blacklist URL do not get passed to Tor(and can see my real IP) ? or is it vise versa ? thanks

---

### Post by Monicker on 2008-06-07
Foxyproxy is not a replacement for tor, although it can be used to connect to tor.  You would still need to have tor installed.

---

### Post by El Rogueo on 2008-06-14
Foxyproxy does word the explanation oddly, but you are correct in your interpretation of how Foxyproxy sorts URLs:

Whitelisted webpages are passed through Tor, and do not reveal your IP
Blacklisted webpages are not passed through Tor, and will show your IP as normal

---

### Post by Foxy John on 2009-11-07
Indeed, whitelist means the proxy works, blacklist means it doesn't. Personally I do not prefer FoxyProxy, but rather, IpRental, or simply tor (though IpRental is faster). Unfortunately, IPRental costs lots of money per month, while Foxyproxy is free, but it is very hard to find the millions of fast, us only, high speed, elite anonymous proxies available in IpRental. 

Unfortunately you cannot simply load those proxies into FoxyProxy but must actually purchase and download a special firmware provided by IpRental. If the FoxyProxy developer can find a way around this to get some form of IpRental for free, perhaps working with them to do that, then I would be the first to [download the next version of FoxyProxy]("http://foxyproxy-1.blogspot.com/2009/10/foxyproxy-download.html").

---

