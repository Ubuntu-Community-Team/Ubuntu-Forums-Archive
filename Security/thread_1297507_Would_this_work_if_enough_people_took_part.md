---
title: "Would this work if enough people took part?"
date: 2009-10-21
forum: Security
---

### Post by Ulysses_ on 2009-10-21
I hear criminals are infecting thousands of computers in order to launch distributed denial of service attacks and slow down to the point of unusability even sites with a lot of bandwidth.  

My question is whether the following would work against a small-scale ddos attack: say a very large number of friends offered their computers as web servers duplicating the same html content, and say a central server were available that did nothing but generate links to working web servers among these, much like p2p filesharing but with html pages being shared  and this happening transparently to the visitor (ie the visitor sees normal text and images in their browser), and if N web servers took part in this at a given time where N is large, say 1,000,000, how large would N have to be in order to prevent a significant slow-down when attacked by ddos from M other computers each with the same average bandwidth as any of the web servers?

PS. Please don't say that attacker ip's can be blocked, I just want to know how much more collective bandwidth the web servers must have relative to the attackers for ddos attacks to have no significant effect.  Note the web servers can all play the role of the initial server too, that server is only an entry point you go to once and it serves no content.

---

### Post by lloyd_b on 2009-10-21
> **Ulysses_ said:**
> I hear criminals are infecting thousands of computers in order to launch distributed denial of service attacks and slow down to the point of unusability even sites with a lot of bandwidth.  

My question is whether the following would work against a small-scale ddos attack: say a very large number of friends offered their computers as web servers duplicating the same html content, and say a central server were available that did nothing but generate links to working web servers among these, much like p2p filesharing but with html pages being shared  and this happening transparently to the visitor (ie the visitor sees normal text and images in their browser), and if N web servers took part in this at a given time where N is large, say 1,000,000, how large would N have to be in order to prevent a significant slow-down when attacked by ddos from M other computers?

PS. Please don't say that attacker ip's can be blocked, I just want to know how much more collective bandwidth the web servers must have relative to the attackers for ddos attacks to have no significant effect.  Note the web servers can all play the role of the initial server too, that server is only an entry point you go to once and it serves no content.

Congratulations - you just reinvented "load balancing".  Large web service companies (such as Google, for instance) have a very large number of web servers, with visitors being directed to different servers to keep the load even among all the servers (I believe these forums use two servers ("lingonberry" and "bilberry") to achieve the same result).

This does *not* help in a DDOS attack - the DDOS attack is directed against the "single point of failure".  In this case, that means the "central server" that directs traffic to the individual servers.

The problem is that when you try to connect to a service, your computer looks up the IP address via DNS.  Whatever IP address DNS returns is the one that you'll try contacting.  If that IP address is under a DDOS attack and not accessible, then it doesn't matter if you have a zillion alternate servers out that that can provide the content, because you'll never get the message telling you where to look for them.

Complicating this is the fact that many DNS servers cache (store) lookups for a certain period of time.  So even if you're switching the DNS to point to different "central servers", this information won't propagate instantly, and people will still be getting the "stale" DNS entry from their DNS servers. 

Lloyd B.

---

### Post by Ulysses_ on 2009-10-22
> **lloyd_b said:**
> This does *not* help in a DDOS attack - the DDOS attack is directed against the &quot;single point of failure&quot;.  In this case, that means the &quot;central server&quot; that directs traffic to the individual servers.  Then why don't p2p entry servers get attacked to extinction?  It's pretty much the same idea, entry servers have plenty of bandwidth and protection but do not serve anything.

In fact even an existing p2p server can be used as the entry point for my purposes. Perhaps transparently to the user if java accesses the p2p server. So if the baddies go after the weakest link, people's web servers behind adsl links, **how many computers can an infected computer slow down by launching dos attacks to each of them?**

---

### Post by lloyd_b on 2009-10-22
It *is* possible to DOS a P2P system, *if* the system relies on a single point of failure (such as a bittorrent "tracker").

Not all P2P networks have this vulnerability.  For instance, Gnutella (mostly Limewire/Frostwire/Frosty nowadays) has NO central servers to DOS - the entire system is distributed (Bearshare still relies on "GWebCache" servers to bootstrap, which could be hit with a DOS attack, but most of the other Gnutella clients are mostly independent of GWebCaches anymore).

Even Bittorrent has some immunity, using DHT (Distributed Hash Tables) rather than trackers.

So *if* someone were to build something like a Firefox extension that replaced the standard "look up address via DNS" with a DHT based search for the content, then your idea would work.  To the best of my knowledge, nobody has done any work in this direction (I imagine because there's such a limited need for it, as well as the fact that distributed systems are inherently less efficient than centralized systems).

Lloyd B.

---

### Post by Ulysses_ on 2009-10-22
So are you implying that maybe it does not matter how many computers take part, versus how many infected computers are doing dos attacks?

---

