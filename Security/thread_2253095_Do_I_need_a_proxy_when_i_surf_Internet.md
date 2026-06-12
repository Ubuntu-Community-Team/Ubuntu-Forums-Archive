---
title: "Do I need a proxy when i surf Internet?"
date: 2014-11-17
forum: Security
---

### Post by flaymond on 2014-11-17
Hey everyone, 'I'm curious about my Internet Security, i found that people can trace our IP with several techniques. I want to protect my IP and data from shown and leak. So, i google for surfing privacy and found that I need proxy to do that. Is there anyway I can use proxy with my mozilla firefox? I dont like proxy websites because everytime you wanna go to any sites or pages  you need to go through to the proxy websites first. I also don't have any money to purchase proxy servers or VPN. So my question is :

Is there anyway to get free proxy server (I mean that you can go to any sites without need to type the url on proxy websites like proxify, eanonymouswebsurfing etc.)


And can you show me the steps to get it done and worked?

I'm using Lubuntu

---

### Post by slickymaster on 2014-11-17
It's important that you know how anonymizing proxies work so you can understand their inherent flaws. They act as a man in the middle while you're browsing the Web, handling communications between your PC and the website you want to access anonymously. If you do everything correctly, the target website only sees information from the anonymizing service, so it can't identify your home IP address or other personal information, but the man-in-the-middle anonymizing service certainly will (and some proxy services keep server logs of user activity that can be subpoenaed). For these reasons, it's important to do your research before you pick a proxy service.

---

### Post by jamal5 on 2014-11-17
There's tons of sites that give ip : port proxies for free, you can set your browser to use the server so you don't need to go through any website. Do a DDG search for ip : port proxies and watch a tutorial on how to use them on Youtube, it's very easy.

Also, you can do just about anything you can in a normal browser with the free Tor browser, and there is much less risk of an exit node spying on you or logging compared to a proxy since they don't even know where you're coming from.

There's a few free vpn's out there too, I think frootvpn is one of the very few that'll work on linux though

Proxies tend to leak your ip and/or dns through java and flash, so I wouldn't rely on them for anything that requires a login (typically runs through java) or videos (unless it's through HTML5). And the people that set up public proxies tend to be blackhats out to steal your data so I'd steer clear...

---

### Post by Thee on 2014-11-17
If you really want good security and anonymity then VPN is a better choice than a Proxy.

---

### Post by bashiergui on 2014-11-17
> **Thee said:**
> If you really want good security and anonymity then VPN is a better choice than a Proxy.
+1
VPN is a better choice than Tor because it will be a lot faster. Plus you'll get the added benefit of being much more secure when you're on public wifi.

just to be clear, you won't be completely "anonymous" with a VPN. You'll have security. and your true IP will be hidden from web sites you visit. But law wnforcement can probably obtain records from the VPN service and determine it was your account. Not sure who the "people" are that you want to hide your IP from, if you define them you'll get better advice.

---

### Post by flaymond on 2014-11-17
Thanks all. You give a good advise to me. I'm pretty sure to use them after I got money to afford those. Thanks.

---

### Post by sammiev on 2014-11-17
I do a little traveling and find that a VPN is great for public places such as hotels, etc.
Been using such services for 3 years now.

---

### Post by Thee on 2014-11-18
> **InterProg said:**
> Thanks all. You give a good advise to me. I'm pretty sure to use them after I got money to afford those. Thanks.

If you are using Linux, you can get a free secure VPN from Riseup [https://help.riseup.net/en/vpn](https://help.riseup.net/en/vpn)
They don't keep any logs and they take privacy very seriously. I have been using it for few months now and its great.

---

