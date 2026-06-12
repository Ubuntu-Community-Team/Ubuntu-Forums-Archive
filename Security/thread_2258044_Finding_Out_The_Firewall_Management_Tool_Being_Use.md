---
title: "Finding Out The Firewall Management Tool Being Used"
date: 2014-12-24
forum: Security
---

### Post by Mad-Halfling on 2014-12-24
I've got an Ubuntu 12.04 server that I'm looking at and I couldn't connect to a certain port on it.  Suspecting it was a firewall issue I SSHed on and forwarded the ports from my local machine, so it would appear the traffic was coming from the server itself and it wouldn't get filtered and that worked, plus scanning the server with nmap then showed the port to be closed.  Knowing what the culprit was, I then proceeded to poke an appropriate hole in the firewall but I then found that UWF/GUFW wasn't enabled and managing the firewall, and ufw status gives an inactive status message.  I know I can just use iptables commands, but some more poking around revealed that it seems to be firestarter that was managing/building the rules.  Is there a way of determining this without poking around to see what management tools are installed, for future reference?  I'm guessing not as I'm sure that firestarter just loads up the current iptables config then writes it back, but I thought I'd ask.  Just thinking of the situation (that may not exist, anyway) where a tool might maintain its own ruleset and overwrite the iptables rules, so that if rules were manually added then they would be lost the next time the management tool was used.

Cheers
MH

---

### Post by bashiergui on 2014-12-24
> Is there a way of determining this without poking around to see what management tools are installed, for future reference?Yes ask the owner. Or am I missing something.

---

