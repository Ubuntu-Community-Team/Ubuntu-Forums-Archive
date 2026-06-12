---
title: "Suspicious unprotected wireless networks."
date: 2010-10-21
forum: Security
---

### Post by bedhead75 on 2010-10-21
In the last couple of days, I've noticed that 3 unprotected wireless networks with "familiar" names such as "attwifi" and "Optimumwifi" have popped up in the vincinity of my apartment at the same time.  I live in a residential neighborhood such that there are no Starbucks or internet cafes nearby.  I put my wireless card into monitor mode and using Kismet I've discovered that these 3 wireless networks all have the same BSSID's and are on the same channel.  Am I just being paranoid or is it likely someone trying to do a man-in-the-middle attack by setting up fake access points for people to connect to, in order to steal passwords, etc?  I know better than to use random unprotected wireless networks, but I'm just curious if there are valid reasons why 3 different access points would come from the same BSSID.

---

### Post by CharlesA on 2010-10-21
Sounds like someone is trying to get people to connect to the "free internet," and probably use it to gather information.

I always tunnel any traffic if I am connected to any AP that is not my own.

---

### Post by mainerror on 2010-10-21
It definitely looks like a trap.

---

### Post by The Cog on 2010-10-21
Could it be related to this article on free wi-fi points?
[http://mobile.slashdot.org/story/10/10/11/1738257/Why-You-See-Free-Public-WiFi-In-So-Many-Places](http://mobile.slashdot.org/story/10/10/11/1738257/Why-You-See-Free-Public-WiFi-In-So-Many-Places)

Are these ad-hoc or infrastructure networks?

---

### Post by bedhead75 on 2010-10-21
These are not ad-hoc networks as detailed in the article.  Just today a new open ESSID of "tmobile" has appeared which also corresponds to the same BSSID's of the other open networks.  There is also a WPA encrypted network of which the ESSID is hidden, that has the same BSSID as the others.

---

### Post by Chayak on 2010-10-22
It's a common attack, just don't connect to them.

---

### Post by nitrogensixteen on 2010-10-23
Are these the default id's for smartphones in wireless hotspot mode or purpose-built wireless hotspots?

"Never attribute to malice that which is adequately explained by stupidity."

---

### Post by tharpa on 2010-10-23
I'm not an expert, but I think it's just neighbors who are running unsecured wireless.  When I got my Mac several years ago, I was completely new to wireless, and I went through the Mac setup, and connected to a wireless connection I saw.  I spent all afternoon surfing the net, and didn't figure out I was surfing my neighbor's connection until the next day when they had secured it.  I have a friend who doesn't even pay for an internet connection, just surfs unsecured ones in his neighborhood.

Not that traps never happen, I just don't think that's the most likely explanation.  Setting up this kind of a trap requires know-how, patience and nets a relatively low pay-off.

---

### Post by mainerror on 2010-10-23
> **tharpa said:**
> I'm not an expert, but I think it's just neighbors who are running unsecured wireless.  When I got my Mac several years ago, I was completely new to wireless, and I went through the Mac setup, and connected to a wireless connection I saw.  I spent all afternoon surfing the net, and didn't figure out I was surfing my neighbor's connection until the next day when they had secured it.  I have a friend who doesn't even pay for an internet connection, just surfs unsecured ones in his neighborhood.

Not that traps never happen, I just don't think that's the most likely explanation.  Setting up this kind of a trap requires know-how, patience and nets a relatively low pay-off.

Well is really isn't that hard to setup such a trap. I'm not going to get into details on that tho.

The pay-off isn't that low. You can gather loads of sensitive information if you set it up in a crowded place.

From what the OP found out about this network is definitely sounds like some sort of trap in my opinion.

---

### Post by MechaMechanism on 2010-10-23
> **CharlesA said:**
> Sounds like someone is trying to get people to connect to the "free internet," and probably use it to gather information.

I always tunnel any traffic if I am connected to any AP that is not my own.
Do you mean SSH and or VPN?  I use SSH with X forwarding to use Chrome from my home computer and to use my computers own DNS at home.  I connect from my netbook to home computer.  Is this sufficient for open wifi?

---

### Post by sgosnell on 2010-10-23
Any Micky D's around?  They now offer free wifi, through ATT, I think.  When it was pay it was certainly ATT.  I haven't visited one of their fine dining establishments in a long time, but they probably still use the same provider.  There are also lots more places offering wifi these days, not just 'internet cafes'.

---

