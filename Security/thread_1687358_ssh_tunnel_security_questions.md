---
title: "ssh tunnel security questions?"
date: 2011-02-13
forum: Security
---

### Post by riksaga on 2011-02-13
I created 2 ssh tunnels [ssh -R 2000:localhost:22 user@box] :
tunnel 1 = corpbox to homebox , tunnel 2 = homebox to corpbox

I open my firewall port 22 temporarily to set up.

My tunnels go through the closed ports on corp and home firewalls.

I check from a friends pc and did a free web port scan. All ports closed.

My ssh connections  look secure, but if someone assumed traffic was going through on port 22 could they piggyback in somehow?

How hard is my tunnel traffic to identify for the corp IT guys if they notice it?

Any help is appreciated.

---

### Post by uRock on 2011-02-13
Network security professionals in a corporate environment will have no problems spotting the ssh protocol. It they have their NIDS set to detect it, then I am sure they already know you are using it or they will when you do use it.

All they have to do is blacklist your IP and your ssh tunnel will be broken.

If you are breaking their rules, then ask yourself if it is worth getting fired for.

---

### Post by perspectoff on 2011-02-13
> **uRock said:**
> Network security professionals in a corporate environment will have no problems spotting the ssh protocol. It they have their NIDS set to detect it, then I am sure they already know you are using it or they will when you do use it.

All they have to do is blacklist your IP and your ssh tunnel will be broken.

If you are breaking their rules, then ask yourself if it is worth getting fired for.

I was an independent contractor with my own computer running an SSH tunnel behind a corporate firewall. They shut down my SSH tunnel so that I could no longer work. I quit on the spot.

When corporate security is that tight, it's time to find another job. It means the corporation does not know the difference between security and closure. It's one thing if they have "rules" against it (which I highly doubt); it's another when they just don't have a sensible security paradigm (which happens more often than discussed).

Too much security in computing means an inability to function.

---

### Post by uRock on 2011-02-13
> **perspectoff said:**
> I was an independent contractor with my own computer running an SSH tunnel behind a corporate firewall. They shut down my SSH tunnel so that I could no longer work. I quit on the spot.

When corporate security is that tight, it's time to find another job. It means the corporation does not know the difference between security and closure. It's one thing if they have "rules" against it (which I highly doubt); it's another when they just don't have a sensible security paradigm (which happens more often than discussed).

Too much security in computing means an inability to function.
Depends on the situation. If you work at an office that handles highly classified information, then you want to make sure people aren't sneaking info out. As world news has recently proven, people with security clearances are willing to break the law for a few bucks.

I see no reason for someone to use ssh for personal means at an office complex.

The "rules" against it may be along the lines of not allowing employees to check personal email or play apps on Facebook, which we know there are people out there who'd be willing to go through the trouble to do this via a ssh tunnel.

Back on topic, creating an NIDS that detects ssh is easy and blocking it is easy.

---

### Post by riksaga on 2011-02-13
Thank you for the info.  I will turn off my tunnel for now.


Can I reroute ssh through port 80 to avoid detection?

---

### Post by uRock on 2011-02-13
> **riksaga said:**
> Can I reroute ssh through port 80 to avoid detection?

That's not within the scope of the forums.:)

Sorry,
uRock

---

