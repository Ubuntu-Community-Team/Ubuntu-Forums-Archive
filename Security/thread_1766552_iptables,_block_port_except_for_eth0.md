---
title: "iptables, block port except for eth0"
date: 2011-05-24
forum: Security
---

### Post by SpinningAround on 2011-05-24
I would like to allow incoming and outgoing connections when I'm connected to a wired connection, but drop it otherwise. I noticed that ufw can't block outgoing traffic because of will I give iptables a try. I'm unsure if dropping packages that are outgoing will work, the rule after the block rule will allow all outgoing connections.

This what the rules are intended to do, unsure if that is actually the case.
Allow all loopback traffic.
Allow ping replys
Allow incoming on port 12345 if eth0, deny otherwise.
Allow outgoing on port 12346 if eth0, deny otherwise.
```

iptables -A FORWARD -j DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 0 -s  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 12345 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT --dport 12345 -j DROP
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -j DROP

iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 12346 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT --sport 12346 -j DROP
iptables -A OUTPUT -j ACCEPT

```

---

### Post by JKyleOKC on 2011-05-24
Once a rule matches and the jump to its target occurs, no more rules are examined. The one exception to this is the LOG target, which comes back and allows the filter to process subsequent rules.

Thus the final ACCEPT won't stop that single port from being blocked. However it will allow all outbound traffic addressed to other ports to go through. Is this really what you want? It's not what you describe in your text...

You could set the policy for all chains to DROP and do away with those final rules...

---

### Post by SpinningAround on 2011-05-25
> **JKyleOKC said:**
> Once a rule matches and the jump to its target occurs, no more rules are examined. The one exception to this is the LOG target, which comes back and allows the filter to process subsequent rules.

Thus the final ACCEPT won't stop that single port from being blocked. However it will allow all outbound traffic addressed to other ports to go through. Is this really what you want? It's not what you describe in your text...

You could set the policy for all chains to DROP and do away with those final rules...

My though is to define what bittorrent to use port 12345 and 12346, when using eth0 are bittorrent traffic allowed but it's not when using wlan0. I think that clients usually use 1024+ ports when connecting, Firefox for example uses some high value ports when connecting to http or https. The thought is to let all outgoing connections work as usual except for bittorrent traffic, that should be blocked except for eth0.

The input should be the ufw deny default in that way that connections that have been established from within my network are allowed to pass, but new incoming connections is not except for bittorrent. If I didn't allow ESTABLISHED past the firewall don't I think that it would be possible to connect to ubuntuforums.org .

I'm trying to replicate ufw behavior but with the modification that also outgoing connections from port 12346 are blocked except if the connection is over the eth0 interface. Similar with incoming connections where new connections are allowed on port 12345 if it's on eth0.

I was able to get the incoming connections working with ufw with, the problem is that I can't do the same with outgoing traffic with ufw.
```
ufw allow in on eth0 proto tcp from any to any port 12345
```

I think this is what my rules would do, let say that there are an outgoing connection from wlan0 from port 12346. The package first check against the loopback rule but it's not lo so it jump to the next one but it's not eth0 so this rule are also skipped. Then when the 3rd are tested does it match since it the source port is 12346 and the package is dropped. If a new outgoing connection from wlan with port source port 12233 then the traffic are allowed.

One question arise if let say firefox try to connect to a web page with the port 12346 how do I tell firefox to try an other port? If the rules work as they should.

---

### Post by JKyleOKC on 2011-05-25
I can't be much more help since I don't use wireless at all with my main system, and don't use BitTorrent at all so don't know its port selection rules. Usually, though, outgoing ports are chosen somewhat randomly.

Since the goal is to block torrent traffic over the wireless interface, I would set rules for wlan0 rather than for eth0, to block specific ports. Those rules would have no effect on eth0; this might make it possible to do the trick with ufw rather than trying to duplicate all of its actions manually.

Since ufw is simply a front-end to iptables, you can see exactly what it's doing by using the command "sudo iptables -L >iptables.txt" and then examining the text file that's created.

As for telling Firefox to try another port, I don't know of any way to do that. However if you use REJECT rather than DROP as a target, on the OUTPUT chain, then the program will be notified immediately of the block rather than having to wait for a timeout, and just might try again on a different port.

---

