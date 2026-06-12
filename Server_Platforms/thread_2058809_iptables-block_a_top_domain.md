---
title: "iptables-block a top domain?"
date: 2012-09-16
forum: Server Platforms
---

### Post by tomdagreek on 2012-09-16
Hi all!

Did a quick search and dont think i saw what i was looking for.

a command to block all traffic from a top domain in iptables?

such as blocking all requests from msn.com?

thanks 
tom

---

### Post by SeijiSensei on 2012-09-16
You would have to identify all the IP addresses associated with msn.com and add deny rules for each one in the iptables ruleset.  Iptables can only work on addresses and ports.

If all you are interested in doing is blocking HTTP requests to that domain, you should consider using [Squid]("http://www.squid-cache.org/") instead.  It has very flexible rules to block objects by a variety of characteristics including domain names.  

Blocking HTTPS requests with Squid is much more difficult unless you can set up a Certificate Authority and issue certs to all the client browsers.  Otherwise, if you push SSL requests through Squid, the proxy cache will be detected as a "man-in-the-middle" attack.  The most recent releases of Squid have [mechanisms]("http://wiki.squid-cache.org/Features/SslBump") by which it can spoof the remote site's certificate and substitute its own.  This won't work with "transparent" proxying, however.

---

### Post by tomdagreek on 2012-09-16
Well i used msn.com for a example. In reality I am trying to block attacks from such webs that allow users to use a vpn to ddos my boxes. 
When i list a bad ip into iptables the great thing that it does is tell me a full domain such as 

badguy.vpnhoster.com

It is not a matter of national security- I just dont wanna mention names.
Of course i have seen many ports used in these attacks.

I would have to block all ports then? or try squid?
Tom

---

### Post by sandyd on 2012-09-16
It depends on the attack you are getting.

a) If the attack is <100mb/s (if your server has a 100mb line), or above 1Gib/s (gigabit line), Iptables is useless. Your tubes will be completely congested, because Iptables filters the traffic AT the server, but not at the router/line level. Even if you use Iptables, the upstream links/your link will be flooded, and any type of server software firewall (other than a upstream blackholing) will not help. In this case, either you get a DDOS protected VPS (Somewhere like BuyVM where you can get DDOS protection for a IP), or a DDOS protected dedicated server provider such as Staminus or Gigenet. Or upstream DDOS filtering.

Those are just providers off the top of my head - you should go to somewhere like WebHostingTalk to seek advice there.

b) Otherwise, Iptables does rate limiting. Here is an example.
```

iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --set

iptables -I INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT --with-icmp icmp-host-unreachable

```
It monitors port 80, and logs access to port 80. Once an ip accesses the port three times in a minute, the REJECT turns on. Of course, you wouldn't want to do that on a webserver, but that is only an example.

---

### Post by SeijiSensei on 2012-09-17
> **tomdagreek said:**
> I would have to block all ports then? or try squid?

No, squid is not helpful here.  From your use of msn.com I thought you were trying to block outbound connections, not inbound ones.

This is a problem you need to discuss with your ISP.  It is a lot easier for them to filter DDOS attacks upstream from you than you doing it yourself. 

Perhaps you should ask yourself why you are the target of these attacks.  If people are going to the trouble to attack you via VPNs, it sounds to me like you pissed someone off.  Maybe you should consider why this is happening rather than just trying to defend yourself.

---

### Post by tomdagreek on 2012-09-20
Well I dont think I made anyone that mad. I am running game servers and some clients have some truly badddass hacks or packet flooders of some sort. I am almost clueless on some of these attacks. 
They are young people.. with alot of time on their hands.I have seen it with my own eyes. These attacks can disrupt my network pretty good.

I am running a couple or rack servers behind routers with static ip's. These are all behind a comcast cable modem.

Any other suggestions? I actually like comcast, but getting thru to them can be a challenge.
Tom

Ps..
I am using iptraf just to keep an eye on this traffic. I kinda like iptraf...

---

### Post by sandyd on 2012-09-20
> **tomdagreek said:**
> Well I dont think I made anyone that mad. I am running game servers and some clients have some truly badddass hacks or packet flooders of some sort. I am almost clueless on some of these attacks. 
They are young people.. with alot of time on their hands.I have seen it with my own eyes. These attacks can disrupt my network pretty good.

I am running a couple or rack servers behind routers with static ip's. These are all behind a comcast cable modem.

Any other suggestions? I actually like comcast, but getting thru to them can be a challenge.
Tom

Ps..
I am using iptraf just to keep an eye on this traffic. I kinda like iptraf...
It is easy to get up to a 100mib/s flood today, as servers and VPSes with 100mib ports are becoming more and more popular. If you are getting network disruptions (not caused by the servers getting hammered, but by the tubes between the street hub and your modem filled), this is only something that comcast can fix, because you do not have control of the network beyond your modem.

Since I have experienced comcast's terrible support, I advise you to switch to switch to another provider. If you live near a fiber loop, you can likely get a 100mib/s drop off from NTT/Level3/HE, or whatever is in your area.

---

