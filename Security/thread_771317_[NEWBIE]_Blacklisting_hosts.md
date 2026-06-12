---
title: "[NEWBIE] Blacklisting hosts"
date: 2008-04-27
forum: Security
---

### Post by damatta on 2008-04-27
Hiya,

What would you say is the most efficient method of blocking huge iprange blocks?
I am not aware of anything like that in Transmission bittorrent client, so I thought I would have to do it through iptables, but I suspect it might get encumbered with so many ip's to process.

What do you suggest?

Cheers

---

### Post by Chayak on 2008-04-27
Use wildcards when you're inputting the IPs you want to block, simple

---

### Post by The Cog on 2008-04-28
iptables is the right way to do it.

If you have already configured some firewall rules, you need to edit your firewall config.

If no firewall rules already, things like this will do the trick:
```
sudo iptables -A INPUT -s 1.2.3.0/24 -j REJECT
sudo iptables -A OUTPUT -s 1.2.3.0/24 -j REJECT
```
I assume you know about subnet masks and the /24. If not, google for subnet mask - you have some learning to do.

If you are usign BitTorrent, I suggest you block both directions (as above) to prevent then connecting to you and also prevent your client from connecting to them.

---

### Post by damatta on 2008-04-28
Thank you people.
The Cog, I was doing as you suggested, however I have numerous IP blocks to add to iptables. This is just a tiny bit of it:
```
iptables -A bogons -s 0.0.0.1/3.255.255.255 -j REJECT
iptables -A bogons -s 4.0.25.146/4.0.25.148 -j REJECT
iptables -A bogons -s 4.0.26.14/4.0.29.24 -j REJECT
iptables -A bogons -s 4.0.38.0/4.0.38.255 -j REJECT
iptables -A bogons -s 4.0.159.0/4.0.159.255 -j REJECT
iptables -A bogons -s 4.0.181.0/4.0.182.255 -j REJECT
iptables -A bogons -s 4.1.75.0/4.1.75.255 -j REJECT
iptables -A bogons -s 4.1.129.0/4.1.140.255 -j REJECT
```
I do not intend using Moblock for such purpose because it seems to meddle with my current firewall rules.

Thanks

---

### Post by The Cog on 2008-04-29
That's a good idea. You can call that chain from b oth INPUT and OUTPUT chains.

I would double-check that subnet masks that aren't 1s followed by 0s actually work in iptables.

---

### Post by jre on 2008-04-30
> **damatta said:**
> I do not intend using Moblock for such purpose because it seems to meddle with my current firewall rules.

Thanks
I doubt that you can block IP ranges the way you posted above ...

The current MoBlock **0.9** (with the new feature MARKing) should work nicely with your iptables rules. Just make sure that MoBlock (the package from moblock-deb.sf.net) is started after you have inserted your rules and that no other firewall application removes MoBlock's rules.

---

