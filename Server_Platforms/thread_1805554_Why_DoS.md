---
title: "Why DoS?"
date: 2011-07-16
forum: Server Platforms
---

### Post by fela on 2011-07-16
Someone ping flooded my home modem/router yesterday, bringing it right down and half-bricking the unit.

Are people seriously this bored? And more to the point, are all home modems this vulnerable to attack?

---

### Post by haqking on 2011-07-16
> **fela said:**
> Someone ping flooded my home modem/router yesterday, bringing it right down and half-bricking the unit.

Are people seriously this bored? And more to the point, are all home modems this vulnerable to attack?

Doesnt your router allow turning off ICMP requests ?

or set it in the firewall portion of the router ?

---

### Post by fela on 2011-07-16
> **haqking said:**
> Doesnt your router allow turning off ICMP requests ?

or set it in the firewall portion of the router ?

Nope, it's a really shoddy Thomson one supplied with the O2 'broadband package'. The firewall section is more just a statement saying 'this router has standard security settings' - literally just that. No configuration, not even a feature list! So I guess it's a blessing in disguise that I'm forced to order a new and much better modem/router.

---

### Post by ilovelinux33467 on 2011-07-16
Edit: never mind. haqking beat me to it.

---

### Post by haqking on 2011-07-16
> **fela said:**
> Nope, it's a really shoddy Thomson one supplied with the O2 'broadband package'. The firewall section is more just a statement saying 'this router has standard security settings' - literally just that. No configuration, not even a feature list! So I guess it's a blessing in disguise that I'm forced to order a new and much better modem/router.

Indeed, well said ;-)

---

### Post by CharlesA on 2011-07-16
> **fela said:**
> Nope, it's a really shoddy Thomson one supplied with the O2 'broadband package'. The firewall section is more just a statement saying 'this router has standard security settings' - literally just that. No configuration, not even a feature list! So I guess it's a blessing in disguise that I'm forced to order a new and much better modem/router.

Is that one of those modem/router combo ones?

I can't really think of a reason why someone would DoS a home connection. :(

---

### Post by haqking on 2011-07-16
out of interest.

Why do you assume a DoS anyways ?

if the router is that shoddy then i assume it wont show you logs even ?

---

### Post by Lars Noodén on 2011-07-16
If the router is not shoddy and is running a linux variant, then it's possible to prevent abuse of ICMP:

```

   iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
   iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

   iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT
   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   iptables -A INPUT   -j REJECT;       # hack for changing default policy
   iptables -A OUTPUT  -j REJECT;       # from DROP to REJECT
   iptables -A FORWARD -j REJECT;       # 

```

---

### Post by conradin on 2011-07-16
Whats the model?
do you keep a firewall log?
Does your router? are you sure it was a straight DoS?
maybe it was a bruteforce cracking tool?
A DoS sounds unlikely. but zombies sending out bruteforce cracking attempts occurs frequently.

---

### Post by fela on 2011-07-16
> **CharlesA said:**
> Is that one of those modem/router combo ones?

I can't really think of a reason why someone would DoS a home connection. :(

Yeah, it's an all in one. Although the one I've ordered is also all in one as I prefer to have as little transformers plugged in as possible :P

The reason they attacked is because I'm running some websites and hosting (for a friend of mine) a Minecraft server. People seem to like bringing down networks hosting game servers for some reason.

> **haqking said:**
> out of interest.

Why do you assume a DoS anyways ?

if the router is that shoddy then i assume it wont show you logs even ?

Well there aren't any logs as far as I could tell. Thing is, I reset the router and now I can't log in to it (won't accept anything), so I can't check the 'SuperUser' account (that o2 don't tell you about ;-)).

It's definitely a DoS attack, it couldn't be anything else. I was refreshing the Tx and Rx and every second it would go up drastically. After about an hour 10.9GB of whatever garbage was being sent/requested to/from the modem had gone through.

> **Lars Noodén said:**
> If the router is not shoddy and is running a linux variant, then it's possible to prevent abuse of ICMP:

```

   iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
   iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

   iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT
   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   iptables -A INPUT   -j REJECT;       # hack for changing default policy
   iptables -A OUTPUT  -j REJECT;       # from DROP to REJECT
   iptables -A FORWARD -j REJECT;       # 

```

This sort of configurability is why my dream is to have an ADSL card plugged into my Linux server and use that as a gateway ;-)

The new router that should come on tuesday runs Linux, so I shall see what sorts of tools it includes :D

> **conradin said:**
> Whats the model?
do you keep a firewall log?
Does your router? are you sure it was a straight DoS?
maybe it was a bruteforce cracking tool?
A DoS sounds unlikely. but zombies sending out bruteforce cracking attempts occurs frequently.

It doesn't have a model / make on it, however according to Windows' network device detection it's a Thomson TG585v7.

The router was the only in-use firewall on the network, and sadly it either didn't log or the logs were somehow hidden.

I think it's most likely some script hack kiddie running a ready-made DoS attack tool - there's lots apparently. Fortunately I'm 99% sure it's not DDoS (which no one can really completely prevent aside from ultra parallel redundant hosting). The most frustrating thing is that I have literally no idea where it was coming from.

I somehow doubt it was a bruteforce hacking attempt as I'm *pretty* sure the modem doesn't accept any connections from the outside over port 80 or 23 (AFAIK the only ports on which services run that allow you to log in).

---

