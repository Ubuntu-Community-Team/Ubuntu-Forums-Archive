---
title: "speedup tor"
date: 2010-04-09
forum: Security
---

### Post by pythonsyntax on 2010-04-09
Is there a way to speed up Tor?

---

### Post by cdenley on 2010-04-09
> **pythonsyntax said:**
> Is there a way to speed up Tor?

Yes. Run a relay. This won't make your usage of tor any faster, but it helps to make the network a little faster for everyone else. The only way your performance will improve is if other people volunteer their bandwidth/system by running a relay.
[http://www.torproject.org/docs/tor-doc-relay.html.en](http://www.torproject.org/docs/tor-doc-relay.html.en)

---

### Post by bodhi.zazen on 2010-04-09
> **pythonsyntax said:**
> Is there a way to speed up Tor?

As yourself, do I really need TOR ? Or is privoxy sufficient ?

IMO TOR has significant limitations and, again, IMO, people blindly trust TOR to increase their privacy without understanding it's limitations.

IMO TOR does not add enough to privacy or to justify the slowed speed.

Otherwise +1 to setting up a TOR server node.

---

### Post by rookcifer on 2010-04-09
> **bodhi.zazen said:**
> As yourself, do I really need TOR ? Or is privoxy sufficient ?

IMO TOR has significant limitations and, again, IMO, people blindly trust TOR to increase their privacy without understanding it's limitations.

IMO TOR does not add enough to privacy or to justify the slowed speed.

Otherwise +1 to setting up a TOR server node.

Tor is not for privacy.  It's for anonymity.

---

### Post by cdenley on 2010-04-09
> **rookcifer said:**
> Tor is not for privacy.  It's for anonymity.

Lets not argue semantics. Tor hides your IP from anyone who can view your traffic remotely without tor's encryption. Call that whatever you want.

---

### Post by bodhi.zazen on 2010-04-09
> **cdenley said:**
> Lets not argue semantics. Tor hides your IP from anyone who can view your traffic remotely without tor's encryption. Call that whatever you want.

Within limits this is true, however even the TOR site lists (some) limitations. The list of limitations on the tor site is incomplete.

---

### Post by Soul-Sing on 2010-04-09
In an [COLOR="Red"]old[/COLOR] configuration with tor and vidalia you could do these tweaks:
editing your torrc 

```
gedit ~/.vidalia/torrc
```

Paste this at the beginning of the torrc:

> # Set the Tor Circuit Build time to find faster tor servers, increments of seconds

CircuitBuildTimeout 2

# connections while Tor is not in use.

KeepalivePeriod 60

# Force Tor to consider whether to build a new circuit every NUM seconds.

NewCircuitPeriod 15

# Set How many entry guards we should we keep at a time

NumEntryGuards 8

---

### Post by pythonsyntax on 2010-04-09
Does this edit file work for sure?

---

### Post by cdenley on 2010-04-09
> **pythonsyntax said:**
> Does this edit file work for sure?

It might help. You're never going to get performance like without tor.
[https://wiki.torproject.org/noreply/TheOnionRouter/FireFoxTorPerf#line-48](https://wiki.torproject.org/noreply/TheOnionRouter/FireFoxTorPerf#line-48)

---

