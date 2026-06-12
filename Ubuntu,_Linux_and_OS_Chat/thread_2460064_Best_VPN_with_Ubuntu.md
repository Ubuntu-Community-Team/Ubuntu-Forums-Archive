---
title: "Best VPN with Ubuntu"
date: 2021-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by thumper76 on 2021-04-01
Does anyone have a recommendation as to what is the best virtual private network to use with Ubuntu 20.04.

---

### Post by CelticWarrior on 2021-04-01
VPNs should be OS agnostic.

---

### Post by TheFu on 2021-04-01
> **thumper76 said:**
> Does anyone have a recommendation as to what is the best virtual private network to use with Ubuntu 20.04.

"best" is highly subjective.  What characteristics are important to you in a VPN?  Are there specific issues that need to be addressed?  What many well-meaning articles list as important for VPNs seldom consider the basics like - who runs the service, are they trustworthy, is it secure and does it stand up against legal filings in court?

---

### Post by cybereality on 2021-04-23
I've had good luck with NordVPN. They have a Linux (deb) client that works on the command line.

Speed in generally pretty decent and they have a ton of servers. Price is also good, they have sales regularly.

---

### Post by TheFu on 2021-04-24
> **cybereality said:**
> I've had good luck with NordVPN. They have a Linux (deb) client that works on the command line.

Speed in generally pretty decent and they have a ton of servers. Price is also good, they have sales regularly.

FYI, [https://www.theverge.com/2019/10/21/20925065/nordvpn-server-breach-vpn-traffic-exposed-encryption](https://www.theverge.com/2019/10/21/20925065/nordvpn-server-breach-vpn-traffic-exposed-encryption)
Always do your own research. Use our mentions as places to start, but since we all have different needs in a VPN and will tolerate different failures, they all have failures of some sort, the selection of a provider will be uniquely our own.  

Well-known VPN providers completely break the reason some people might want a VPN. Going with a smaller VPN might be needed to be able to access certain parts of the internet when traveling.  Many banks block access through VPNs as part of their security. That can be frustrating when traveling in less-known parts of the world that few customers from your bank visit.

Some people might find it safer to spin up a VPS and create their own VPN server for a few hours at a time for $0.02-$0.04/hour.  We are Linux people. This isn't THAT hard and can be automated.

Lots of considerations.

---

### Post by TheFu on 2021-04-30
Just out today: [https://www.howtogeek.com/722871/5-signs-a-vpn-isnt-trustworthy%c2%a0/](https://www.howtogeek.com/722871/5-signs-a-vpn-isnt-trustworthy%c2%a0/)
[LIST]
[*]Be Wary of Free
[*]Checking the Record
[*]Bad Policy
[*]Watch out for paid articles that are just marketing
[/LIST]

I disagree with their final choice for the last reason.

---

### Post by ayesc0tty89 on 2021-05-08
Any VPN that doesn't log what you do and uses WireGuard would be my suggestion.

---

### Post by kurt18947 on 2021-05-09
I'm using Private Internet Access. It seems to work well enough though there is some concern about a recent hire there, I don't remember name or details but he had something of an unsavory past. I think when my year's subscription runs out I'm going to look at Mozilla's VPN. The Mozilla VPN costs about a dollar a month more but it's worth that to do a bit for years use of their software.

---

### Post by dddman on 2021-05-10
Browsec; it&#8217;s free 24/7.
 

 Owned by Russian&#8217;s.  The server I use is next to Washington DC, lol

---

### Post by amaab on 2021-05-23
Happy with mullvad.
[https://mullvad.net/en/]("https://mullvad.net/en/")

---

### Post by m02g on 2021-07-06
I like Nord VPN. Easy to turn on and turn off. And easy to change settings all through the command line.

Plus I just signed up again for 2 years for $80. You can't beat that price.

---

### Post by TheFu on 2021-07-09
> **cryptik0x756c6f7573 said:**
> i suggest you read here [https://privacytools.io/providers/vpn/](https://privacytools.io/providers/vpn/)  Understand what a VPN does and what it doesn't before using one, and why even using one in the first place. IMO they are all lies and "Shenanigans" but i guess someone can find the proper "usecase" for them.

About 50% of VPN providers are not actually trying to protect anyone's privacy.  Whether that is important or not is a personal choice. For many people "not my ISP" is sufficient privacy protection.  For some people, insisting on privacy rights from their ISP, their Govt and most foreign Govts is the goal. A well selected VPN can certainly make it possible to have privacy for the connection from those 3 entities, but it won't magically prevent doing dumb things where they can trace traffic back to your location.  That's much harder.  

Using a VPN to appear to be in a different location isn't hard and is usually sufficient to get privacy against people sucking up data, but if we use facebook all day, all our friends are in London and all our tags and check-ins are in London, just because our IP appears to be in Vancouver, BC , well ... it doesn't take much to figure out that we're using a VPN or proxy and probably located in ... er ...  London.  Common sense stuff, but we all over-simplify stuff. Just don't over-simplify "vpn == privacy", since that isn't true.  Behavior while using the VPN matters.

When using a VPN hoping for privacy, there are a few rules.
[LIST]
[*]Never use the same account that you use for other purposes.  Have a VPN use account, but don't let the username contain VPN.  Usernames leak.
[*]Never login to accounts you've ever used from your real location under the VPN. That goes for local and remote accounts. Have a VPN-Vancouver Facebook and Tweeter account.
[*]Never connect your VPN accounts to your real location. This can be hard, since we are forgetful beings. 1 little click or knowing too much about a fake "remote" location (which is where you really are located) isn't smart.
[/LIST]

Those are just a few considerations. There are many others. Think through your VPN use, account use, and have a different persona under the VPN based on which exit node it being used.  Don't forget that using a VPN with an exit node in your city/state/province isn't a bad idea, under certain situations. 

And think about the VPN provider. They know your real location AND what your exit node is for the connection period. If they keep logs, which most do, then don't expect to be hidden.  The "no log" VPNs keep logs too, just they remove those logs quickly.  The VPN I've used would delete logs within 3 minutes of the connection ending.  If I kept a connection alive for a week, then they could have a weeks worth of logs.  I made it a point to only keep a connection up for 12 hours, at most. Shorter if I were "working" and didn't wish to have logs longer.  A quick reconnect to the VPN would cause minimal issues, but drop the older logs.

---

