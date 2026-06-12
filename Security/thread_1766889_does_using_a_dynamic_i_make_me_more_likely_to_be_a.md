---
title: "does using a dynamic i make me more likely to be attacked"
date: 2011-05-24
forum: Security
---

### Post by wlraider70 on 2011-05-24
I use dyndns to keep track of my external ip. However, I have noticed a huge amount of attempts to gain entry to my server. (brute force i guess).

Is this standard or does using a dyn address somehow put a bigger target on my back?
Even after setting up deny hosts and rsa keys i had to change port because I was getting crowded out.

---

### Post by CharlesA on 2011-05-25
It's normal. Most of the bruteforce attempts are bots that scan blocks of ip addresses.

I use iptables to limit connection attempts to a max of 3 in a minute. Any other attempts are dropped. That helps cut down on log chatter.

---

### Post by doas777 on 2011-05-25
it makes sense that dyndns registered IPs would be a good target for sweeps and automated attacks. the IP owner is almost guaranteed to have a public service, and there is a high likelyhood that some an inexperienced hobbyist administrators made critical configuration errors somewhere.

---

### Post by wlraider70 on 2011-05-25
@ charles 

I haven't done much with iptables, but what if you are the 4th attempt that minute does that mean that you are blocked?

---

### Post by CharlesA on 2011-05-25
> **wlraider70 said:**
> @ charles 

I haven't done much with iptables, but what if you are the 4th attempt that minute does that mean that you are blocked?
Yep.

I use two rules to do that:

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP

```

In my case, it will only allow 4 "hits" in a minute before dropping any traffic from that ip.

---

### Post by wlraider70 on 2011-05-25
> **CharlesA said:**
> Yep.

I use two rules to do that:

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
sudo iptables -A INPUT -m recent --update --seconds [COLOR="Red"]600 [/COLOR]--hitcount 4 --rttl --name SSH  --rsource -j DROP

```

In my case, it will only allow 4 "hits" in a minute before dropping any traffic from that ip.


Is that a typo in red?

---

### Post by CharlesA on 2011-05-25
> **wlraider70 said:**
> Is that a typo in red?
No typo, it blocks the offending IP for 10 minutes (600 seconds).

You can find a nice tutorial on iptables here: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by wlraider70 on 2011-05-25
thanks.

---

