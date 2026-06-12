---
title: "ping problem"
date: 2005-08-30
forum: Server Platforms
---

### Post by fartbarker on 2005-08-30
I have a linksys router wrt54g with with 2 comps connected (linux and mac).

I can't ping or traceroute any websites with my routers net utility, linux net utility, or mac net utility but internet, mail, downloading works great.

ping gives 100% packet loss and traceroute times out on 2nd hop

any ideas? I'm thinking it must be my router settings or is my isp blocking these requests?

---

### Post by 5-HT on 2005-08-30
I'm wondering if you can ping the router or the other pc (from either one) ?

I'm having the  same problems ever since installing ubuntu, but I can ping the router just not any sites (either by ip or domain name).

As to whether it's an ISP block, I've never really heard of any doing so (mostly just up to the servers to allow or not- though they may).

It's not a big issue, but would be nice to get it working.

As to how to solve it however, sorry i'm at a loss.

---

### Post by fartbarker on 2005-08-30
i can ping my router but my router cant ping me lol

---

### Post by csuspeedy on 2006-08-27
I am having a similar issue. I am sharing an internet connection with one other computer(WinXP Home) through a router. I can connect to the internet, I can ping localhost and my router, but not anything else (i.e. the other computer, google, etc.). However, the other computer can ping me, google, whatever.  Similarly with traceroute, none of the hops time out just none of them get resolved to an ip address or hostname. The WinXP box can tracert to anything, but I did notice on it that the first 2 or 3 hops did not get resolved. I'm pretty baffled and any assistance would be greatly appreciated.

---

### Post by MrHorus on 2006-08-28
> **fartbarker said:**
> 
ping gives 100% packet loss and traceroute times out on 2nd hop

any ideas? I'm thinking it must be my router settings or is my isp blocking these requests?

Yes.

Somewhere along the line ICMP packets are being filtered out, most likely for security reasons.

Can you ping ANY remote clients?
If not, then this is an issue at your end but if you CAN ping some then this is a remote issue.

---

### Post by geoff270 on 2006-08-28
If you're using firestarter for your firewall, open prefs, ICMP filtering, put an 'x' in 'enable ICMP filtering, and another in 'echo ping requests' and any other's you may need, uncheck those you wish not enabled.

---

